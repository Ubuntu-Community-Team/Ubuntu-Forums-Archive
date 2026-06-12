---
title: "xorg.conf doesn't show mouse"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by ~zoey~ on 2009-01-19
I am running ubuntu 8.10 using a Logitch Marble Mouse.  All of the buttons work, but I would like to make the small left one scroll.  I found this in another forum;  

Code:
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
      #Option          "Vender"                "Sysp"
      #Option          "Name"                "AutoDetected"
        Option          "Buttons"               "5"
      #Option          "ButtonMapping"         "1 2 3 4"
        Option          "Device"              "/dev/input/mice"
       Option          "Protocol"        "MouseManPlusPS/2"
      #Option          "Emulate3Buttons"       "true"
        Option          "EmulateWheel"          "true"
      #Option          "EmulateWheelTimeout"   "200"
        Option          "EmulateWheelButton"    "2"
        Option          "YAxisMapping"          "4 5"
      #Option          "XAxisMapping"          "6 7"
      #Option          "ZAxisMapping"          "6 7"

I don't know what file to edit though because no mouse shows in /etc/x11/xorg.conf and it messed things up when I tried adding it to that file!

I would appreciate some suggestions.

Thanks, zoey

---

### Post by Ardghal on 2009-01-19
I don't know where that information is stored on this version, but they say 8.10 doesn't use Xorg anymore. I don't know *how* they do it now.

Though I hear they'll go back to Xorg on the next version...

Maybe if you have an old copy of the file from a previous installation, you can use that to put the code in... :???:

---

### Post by ~zoey~ on 2009-01-19
I do have /etc/x11/xorg.conf in Intrepid, but all it shows is the monitor, nothing else.

zoey

---

### Post by benerivo on 2009-01-19
In what way did you mess it up? You are fine to add stuff to your xorg.conf file, such as the code you posted. It does need to end with EndSection.Eg...```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
```Where did you get your code from? It looks like it says that you have five buttons and are using a ps/2 input rather than usb.

EDIT - try looking at [this]("http://wiki.archlinux.org/index.php/Logitech_Marble_Mouse") code for use in xorg.conf. Also check [this]("https://bugs.launchpad.net/bugs/313148") page.

---

### Post by ~zoey~ on 2009-01-19
I got the code from here; [http://www.linuxquestions.org/hcl/showproduct.php/product/670](http://www.linuxquestions.org/hcl/showproduct.php/product/670)  and you are correct, it does say to use a ps2 connector, which my motherboard doesn't even have.  I missed that, which is one reason I'm in the beginner's forum!
I'm thinking that maybe I should leave well enough alone before I really mess things up, but I would like to get the scroll working.

Thanks, zoey

---

### Post by skueppers on 2009-02-04
This type of configuration is now done using HAL instead of xorg.conf.  I was successful getting this to work using the procedure at:

[https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

---

