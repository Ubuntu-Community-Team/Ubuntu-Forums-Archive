---
title: "Need help configuring webcam"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by Sleven7 on 2010-08-26
I was trying get my webcam to work with google chat.  All I got was a blank screen.

I down loaded two different webcam programs to see if I could get any signal.

Cheese and Kamoso

Both cause the usb cam to turn on but receive no signal.

lsusb returns- Bus 003 Device 002: ID 093a:2460 Pixart Imaging, Inc. Q-TEC WEBCAM 100

lsmod | grep videodev returns- videodev    34361  1 gspca_main
v4l1_compat    13251  1 videodev

When I try to record video with Kamoso, at the bottom of the screen it says-

v4l2:///dev/video1:caching=100

Neither program will allow me to change the device number.

Any ideas?

---

### Post by spcwingo on 2010-08-26
It might not be blank...it may just be too dark to distinguish anything from it.  This worked in Hardy so it might just work for the later versions also.  First, press ALT+F2 and enter:

```
gksudo /etc/modprobe.d/options.conf
```

Enter this into the blank file (with the webcam unplugged):

```
options gspca gamma=4
```

Save and plug in your webcam.  Then fire up a webcam viewer (I prefer Cheese).  If the picture is too bright or too dark you'll have to adjust the numeric value in /etc/modprobe.d/options.conf (the higher the number the brighter).  If you have to change the value in between modifications I would recommend opening a terminal and issuing this command before the change:

```
sudo rmmod gspca
```

and after:

```
sudo modprobe gspca
```

Let me know how it goes.  :)

---

### Post by cgroza on 2010-08-26
Try taking a flashlight and put it in front of the webcam and start your webcam viewer to check if its really receiving no signal or if its too dark to distinguish something.

---

### Post by Sleven7 on 2010-08-26
Thanks peeps, I took the cam and turned it toward the lamp and it just barely showed the light, I'm off to change the setting, thank again.

---

### Post by Sleven7 on 2010-08-26
gksudo /etc/modprobe.d/options.conf

this command did not open a blank file, I can't tell that it did anything

---

### Post by ender4 on 2010-08-26
try ```
gksudo gedit /etc/modprobe.d/options.conf
```

or if that doesn't work 
"sudo nano /etc/modprobe.d/options.conf"

---

### Post by spcwingo on 2010-08-26
> **Sleven7 said:**
> gksudo /etc/modprobe.d/options.conf

this command did not open a blank file, I can't tell that it did anything

:oops: Oops, I forgot one little part of that command...it should be

```
gksudo gedit /etc/modprobe.d/options.conf
```

EDIT:  Ender4 beat me to it. :)

---

### Post by Sleven7 on 2010-08-27
The gamma=4 line did nothing to the brightness.  So I was going to increase the value and I ran 

sudo rmmod gspca  in the terminal and it returned this error

ERROR: Module gspca does not exist in /proc/modules

???

---

### Post by Sleven7 on 2010-08-27
I changed the gamma to 8 and it still made no difference.

---

### Post by spcwingo on 2010-08-27
Please post the full output of:

```
lsmod
```

---

### Post by no2498 on 2010-08-29
this is an old how to from skype

after you get it working you can change more settings in the cam program you use

i like/use wxcam
read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)




Go to the the Linux Video settings directory:
CODE
cd /sys/module/gspca/parameters/


EVERY FOLLOWING COMMAND MUST BE RUN AS ROOT! (sudo doesn't handle the ">" redirection stuff elegantly without weird escaping, which I haven't mastered yet)

CODE
sudo su


And echo new values to the gamma and color files:
CODE
echo 4 > /sys/module/gspca/parameters/gamma
OR
echo 290 > /sys/module/gspca/parameters/GRed
OR
echo 310 > /sys/module/gspca/parameters/GGreen
OR
echo 315 > /sys/module/gspca/parameters/GBlue

After tweaking with these, right click the skype systray icon, and chose "Options", then "Video Devices", then click the video "Test" button to check it out. You'll need to close and reopen the options window after each change.

Once you've tweaked to the best config possible, save the module settings permanently to /etc/modprobe.d/options:

Add these lines (with your values) to the "/etc/modprobe.d/options" file:
CODE
options gspca gamma=4
options gspca GRed=290
options gspca GGreen=310                    
options gspca GBlue=315

  

 sudo gedit /etc/modprobe.d/options

---

