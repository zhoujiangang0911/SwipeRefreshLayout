## SwipeRefreshLayout ##
An extension of android.support.v4.widget.SwipeRefreshLayout with loading more function for ListView

## Note ##
It only serves for ListView now.

## Demo ##
[Download apk](/demo.apk)

![Gif](/demo.gif)

## Use ##
Use it in your layout xml
````xml
<com.demievil.swiperefreshlayout.RefreshLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/swipe_container"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ListView
        android:id="@+id/list"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:background="#FFFFFF"
        android:dividerHeight="1px" />
</com.demievil.swiperefreshlayout.RefreshLayout>
````

Customize your footer layout to indicate a loading progress like:
````xml
<RelativeLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:background="#FFFFFF"
    android:gravity="center"
    android:padding="8dp"
    android:visibility="gone">

    <ProgressBar
        style="@android:style/Widget.DeviceDefault.Light.ProgressBar.Inverse"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:indeterminate="true" />

</RelativeLayout>
````
Get instance and use it.
````java
    RefreshLayout mRefreshLayout;
    ListView mListView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        mRefreshLayout = (RefreshLayout) findViewById(R.id.swipe_container);
        mListView = (ListView) findViewById(R.id.list);
        mRefreshLayout.setFooterView(this, mListView, R.layout.listview_footer);

        mRefreshLayout.setColorSchemeResources(R.color.google_blue,
                R.color.google_green,
                R.color.google_red,
                R.color.google_yellow);

        mRefreshLayout.setOnRefreshListener(new RefreshLayout.OnRefreshListener() {
            @Override
            public void onRefresh() {
	         // start to refresh
            }
        });
        mRefreshLayout.setOnLoadListener(new RefreshLayout.OnLoadListener() {
            @Override
            public void onLoad() {
                // start to load   
            }
        });
    }
````

## Thanks ##
[SwipeRefreshLayout](https://developer.android.com/reference/android/support/v4/widget/SwipeRefreshLayout.html)

## License ##
> Copyright (c) 2015 Demievil
> 
> Licensed under the Apache License, Version 2.0 (the "License");
> you may not use this file except in compliance with the License.
> You may obtain a copy of the License at
> 
>    http://www.apache.org/licenses/LICENSE-2.0
> 
> Unless required by applicable law or agreed to in writing, software
> distributed under the License is distributed on an "AS IS" BASIS,
> WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
> See the License for the specific language governing permissions and
> limitations under the License.

