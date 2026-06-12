---
title: "Redefine mouse buttons"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by bdron on 2009-11-13
Is it possible to redefine mouse buttons so one of them will acting like PageDown on keyboard?
I have a 4-buttons mouse (trackball actually) and I would like to define a Go-Forward button as PageDown.

Currently my xorg.conf contains the following lines:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Buttons"               "4"
        Option          "Device"              "/dev/input/mice"
       Option          "Protocol"        "MouseManPlusPS/2"
        Option          "EmulateWheel"          "true"
        Option          "EmulateWheelButton"    "3"
        Option          "YAxisMapping"          "5 4"
EndSection

```

Thanks in advance.

---

### Post by coldReactive on 2009-11-13
This might help: [https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

