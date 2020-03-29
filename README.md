# Smiley Rating
SmileyRating is a simple rating bar for android. It displays animated smileys as rating icon.
  - Drawn completely using android canvas
  - Inspired by [Bill Labus](https://dribbble.com/shots/2790473-Feedback)

## Demo

 <img src="https://raw.githubusercontent.com/sujithkanna/SmileyRating/master/app/src/main/assets/demo.gif" alt="" data-canonical-src="https://gyazo.com/eb5c5741b6a9a16c692170a41a49c858.png" width="575" height="205" />

## Integration
Integrating SmileyRating in your project is very simple.
### Step 1:
Add this dependency in your project's build.gradle file which is in your app folder
```groovy
compile 'com.github.sujithkanna:smileyrating:2.0'
```
add this to your dependencies.
## Step 2:
Now place the SmileyRating in your layout.
###### *Note: The height of the SmileyRating will be automatically adjusted according to the width of this component.*
```xml
<com.hsalf.smileyrating.SmileyRating
        android:id="@+id/smile_rating"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />
```
### Set this SmileySelectedListener to get notified when user selects a smiley
*By default the selected smiley will be NONE*
```java
smileyRating.setSmileySelectedListener(new SmileyRating.OnSmileySelectedListener() {
            @Override
            public void onSmileySelected(SmileyRating.Type type) {
                // You can compare it with rating Type
                if (SmileyRating.Type.GREAT == type) {
                    Log.i(TAG, "Wow, the user gave high rating");
                }
                // You can get the user rating too
                // rating will between 1 to 5
                int rating = type.getRating();
            }
        });
 ```

### Get current selection
```java
SmileyRating.Type smiley = smileyRating.getSelectedSmiley();
// You can compare it with rating Type
if (SmileyRating.Type.GREAT == type) {
    Log.i(TAG, "Great rating is given");
}
 // You can get the user rating too
 // rating will between 1 to 5, but -1 is none selected
 int rating = type.getRating();
 ```

### You can set selected smiley without user interaction
#### Without animation
```java
smileRating.setRating(SmileyRating.Type.GREAT);
// Or you can give rating as number
// Valid inputs are 1 to 5.
// Giving -1 will reset the rating. Equivalent to Type.NONE
smileRating.setRating(5);
```
#### OR
```java
smileRating.setRating(SmileyRating.Type.GREAT, false);
smileRating.setRating(5, false);
```
*The smiley will be selected with animation and the listeners will be triggered*
#### With animation
```java
smileRating.setRating(SmileyRating.Type.GREAT, true);
smileRating.setRating(5, true);
```
*Smiley will be selected with animation and listeners will also be triggered(Only if the second param is true)*

#### Disallow selection
```java
smileRating.disallowSelection(true);
```
*You can disallow user input by passing true to this. You can set the smiley only using [this](https://github.com/sujithkanna/SmileyRating/tree/develop#you-can-set-selected-smiley-without-user-interaction). This is useful when you just want to show the rating.