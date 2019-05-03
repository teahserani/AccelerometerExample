# AccelerometerExample
Basic accelerometer app for an Android device to demonstrate ease-of-use with the GWearCloud system. The source code for this project can be found [here](https://examples.javacodegeeks.com/android/core/hardware/sensor/android-accelerometer-example/) and was not modified to make easier to use with the GWearCloud system in any way.

## Required Software
- [Android Studio](https://developer.android.com/studio)

## Usage
Open the project in Android Studio, either as a git repository or as a directory downloaded from the zip file.

Build the project using Gradle.

Run it in an emulator or on a test device.

## Adding GWearCloud capabilities
The purpose of this repository is to serve as a basis for testing the ease-of-use for the GWearCloud system. To participate in this study, download this project and add [libgwearandroid](https://github.com/gwulilab/libgwearandroid) to the project using the instructions found in the libgwearandroid README file.

For this project, new sensor data is read and processed in the `onSensorChanged(SensorEvent event` method. The method is copy-and-pasted below:

```java
@Override
    public void onSensorChanged(SensorEvent event) {

        // clean current values
        displayCleanValues();
        // display the current x,y,z accelerometer values
        displayCurrentValues();
        // display the max x,y,z accelerometer values
        displayMaxValues();

        // get the change of the x,y,z values of the accelerometer
        deltaX = Math.abs(lastX - event.values[0]);
        deltaY = Math.abs(lastY - event.values[1]);
        deltaZ = Math.abs(lastZ - event.values[2]);

        // if the change is below 2, it is just plain noise
        if (deltaX < 2)
            deltaX = 0;
        if (deltaY < 2)
            deltaY = 0;
        if ((deltaX > vibrateThreshold) || (deltaY > vibrateThreshold) || (deltaZ > vibrateThreshold)) {
            v.vibrate(50);
        }
    }
```

### Visualization 
You do not need to use this if you have an Android device to test on. 

Open the AVD Manager 
Select Create Virtual Device 
Select a Device and Press Next 
Select Oreo with an API level 26 and Press Next 
Press Finish 
Under Action select launch this AVD in emulator 

## Reporting Bugs
If you found any bugs or have any suggestions for this project, please feel free to [submit an issue](https://github.com/gwulilab/AccelerometerExample/issues).
