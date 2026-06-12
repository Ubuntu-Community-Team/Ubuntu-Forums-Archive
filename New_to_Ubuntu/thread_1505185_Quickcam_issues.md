---
title: "Quickcam issues"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Jshaw on 2010-06-08
I just installed Lucid on my laptop the other day, and after installing cheese, I plugged in my webcam (Logitech Quickcam for Notebooks) and it worked just fine. I then installed Skype and called another computer to see if it worked, according to my mother, it worked fine and she could see me perfectly. Later on I turned my laptop on to Skype someone and I noticed that my webcam stream is perfect for a split second when it initializes, but then it immediately becomes dark. I don't understand what's wrong with it and I'd appreciate any help.

---

### Post by Breambutt on 2010-06-08
There's something fishy going on with Logitech cams: [http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities](http://www.quickcamteam.net/documentation/faq/logitech-webcam-linux-usb-incompatibilities)

Though I have a QuickCam Fusion, I experienced similar behavior in Lucid LTS even though it was working perfectly fine in alpha and beta. Just reloading the uvcvideo modules fixed my problems.

```
sudo rmmod uvcvideo && sudo modprobe uvcvideo trace=15
```

I've seen a bunch of QuickCam threads around these forums, might want to search around some. I don't really use the camera for anything so I didn't bother investigating any further, just wanted to try it out.

---

### Post by Jshaw on 2010-06-08
I got an error when I entered that command into the terminal

> ERROR: Module uvcvideo does not exist in /proc/modules

Perhaps this is related to the problem?

---

### Post by Breambutt on 2010-06-08
In that case try only

```
sudo modprobe uvcvideo trace=15
```

Also try booting into Ubuntu with and without the camera plugged in and run *lsmod | grep uvcvideo* in terminal. If it produces any output like...

[I]uvcvideo               56990  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev[/I]

...the modules are loaded properly.

Some might object my advice to reboot, but I think when I plugged the camera in the modules loaded automatically but somehow died on their own and failed to load when booting with the camera plugged in.

I wouldn't mind trying to reproduce the problem but my desktop case is located in a place where I have to put my butt up in the air and accidentally bonk my noggin a few times while desperately trying to juggle the USB connector in. ;(

---

### Post by Jshaw on 2010-06-08
Well it seems that your suggestion solved my problem! I'm going to restart and then attempt a Skype call to see if the problem arises again.

Update: I just restarted and booted up Cheese to see if the webcam was working, and it seems that I'm going to have to run the "sudo modprobe uvcvideo trace=15" command every time I turn my laptop on, I'm going to try and run it at startup.

Update 2: I'm not entirely sure how successful the startup script was, but the webcam works in Cheese, but in Skype I still have the same problem. I'm stumped.

---

### Post by Breambutt on 2010-06-08
Nevermind the trace by the way, it's just for... tracing. I was just copypasting my own notes without thinking. You can load modules upon startup by adding the name (simply "uvcvideo" in this case) in /etc/modules with **sudo gedit /etc/modules** and applications/crap through Main Menu > System > Pref > Startup.

As for Skype I have no idea, never used it. Maybe some Skype fellow would know better, compiling a more recent version of it or something.

---

### Post by BandD on 2010-06-09
You can try the solution posted [here]("http://ubuntuforums.org/showpost.php?p=9317367&postcount=4")  If that works then you can make it "permanent" by following this [post]("http://ubuntuforums.org/showpost.php?p=9321876&postcount=9").

---

