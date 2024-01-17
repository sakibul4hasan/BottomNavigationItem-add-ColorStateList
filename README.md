# BottomNavigationItem-add-ColorStateList
In Android, changing the color of the active icon and label in a Bottom Navigation Bar can be done through various approaches. One common method is to use a combination of XML attributes and code. Below is an example using the BottomNavigationView and a ColorStateList for the active state:




### Step 1. Define Color Resources:
- Open your `res/values/colors.xml file` and define the colors you want to use for the active and inactive states.
```bash
<resources>
    <color name="colorInactive">#8A8A8A</color>
    <color name="colorActive">#FF4081</color>
</resources>

```



### Step 2. Create a ColorStateList:
- Create a new XML file `(e.g., res/color/bottom_nav_item_color.xml)` to define a ColorStateList for the active and inactive states.
```bash
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:color="@color/colorActive" android:state_checked="true" />
    <item android:color="@color/colorInactive" />
</selector>

```



### Step 3. Apply ColorStateList to BottomNavigationView:
- In your layout file `(e.g., res/layout/activity_main.xml),` apply the created `ColorStateList` to the `app:itemIconTint` and `app:itemTextColor` attributes of the `BottomNavigationView.`
```bash
<com.google.android.material.bottomnavigation.BottomNavigationView
    android:id="@+id/bottomNavView"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:itemIconTint="@color/bottom_nav_item_color"
    app:itemTextColor="@color/bottom_nav_item_color"
    app:menu="@menu/bottom_nav_menu" />

```



### Step 4. Handle Item Selection:
- In your activity or fragment code, handle the item selection and update the colors as needed.
```bash
BottomNavigationView bottomNavigationView = findViewById(R.id.bottomNavView);
bottomNavigationView.setOnNavigationItemSelectedListener(item -> {
    // Handle item selection here

    // For example, change the icon and label colors programmatically
    item.setIconTintList(ContextCompat.getColorStateList(this, R.color.bottom_nav_item_color));
    item.setTextColor(ContextCompat.getColorStateList(this, R.color.bottom_nav_item_color));

    return true;
});

```
