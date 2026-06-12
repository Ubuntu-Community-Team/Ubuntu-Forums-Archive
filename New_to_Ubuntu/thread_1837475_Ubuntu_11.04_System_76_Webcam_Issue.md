---
title: "Ubuntu 11.04 System 76 Webcam Issue"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by McTwitch on 2011-09-01
So, I have a System 76, Pangolin Performance, laptop, with webcam. I've recently downloaded aMSN for a chatting program, but I can't get my webcam to work with it. The program doesn't even pick up the webcam! But other stuff, like Cheese Webcam Booth, and Camorama will. Any ideas?

---

### Post by ubudog on 2011-09-01
Hi, try this: 

Close aMSN, and make sure it's not running (like in the task bar or something)

Then, open a terminal (searching for "Terminal" in 11.04, or Applications>Accessories>Terminal, in 10.10 and below).

Type the following:
```
amsn
```

Post the output; if there is an error there, you should see it.

---

### Post by McTwitch on 2011-09-01
Um...typing that into Terminal opens the aMSN program. Other than that, there isn't any other results, just a blinking cursor. At least, that's all I got. I waited for awhile, but nothing.

---

### Post by ubudog on 2011-09-02
> **McTwitch said:**
> Um...typing that into Terminal opens the aMSN program. Other than that, there isn't any other results, just a blinking cursor. At least, that's all I got. I waited for awhile, but nothing.

So in the terminal window, there was nothing?  Did you try testing the webcam and then checking the terminal?

---

### Post by McTwitch on 2011-09-02
Depends. What do you mean by that?

---

### Post by ubudog on 2011-09-03
> **McTwitch said:**
> Depends. What do you mean by that?

Like try to initiate a chat with someone using the webcam, or go to the preferences and test the webcam.  (while running aMSN from the terminal)

---

### Post by McTwitch on 2011-09-03
To initiate the webcam in a conversation, I have to configure the webcam, which is where I run into problems. It isn't being picked up, and the Terminal read-out isn't saying anything about the webcam.

```
jer@Cobalt:~$ amsn
Created new window in existing browser session.
Playing WAVE '/usr/share/amsn/skins/Oxygen/sounds/type.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Playing WAVE '/usr/share/amsn/skins/Oxygen/sounds/type.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Playing WAVE '/usr/share/amsn/skins/Oxygen/sounds/type.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Playing WAVE '/usr/share/amsn/skins/Oxygen/sounds/type.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo


```

---

### Post by no2498 on 2011-09-04
with the cam plugged in and turned on if its the kind that needs turned on
open a terminal type dmesg   click enter
does it say it found a new usb device
type lsusb click enter
should give a number and name of the cam
close the terminal
open your package manager look for and install guvcview 
try the cam in guvcview if it comes on retry whats up top

---

