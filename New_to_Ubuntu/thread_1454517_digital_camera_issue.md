---
title: "digital camera issue"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by us11csalyer on 2010-04-14
I plugged my digital camera in via usb and it opened up with no problem. I started going through the images and videos and the screen just closed on me. Now my camera won't connect to ubutnu at all. I tried restarting but that didn't fix the issue. I can plug flash drives in via USB and they open right up.

---

### Post by WinterRain on 2010-04-14
See if gthumb recognizes the camera.
```
sudo apt-get install gthumb
```
Open gthumb and go to file>import photos.

---

### Post by us11csalyer on 2010-04-14
Nope. Didn't work. I got an error: operation not supported when I clicked import.

---

### Post by no2498 on 2010-04-14
hope you have some thing diff to plug in usb you had a bad unmount
you need to unplug the cam try to mount some thing restart the computer
plug the cam back in and hope it comes up
this is a usb bug

hope this helps you

---

### Post by us11csalyer on 2010-04-14
i tried a flash drive and it worked, but i didn't try restarting the computer. So ill try it.

---

### Post by f1r3flie on 2010-04-14
Do you have the latest drivers for your camera? Try running System>Administration>Hardware Drivers when you have the camera plugged in. If that doesn't work, do a search for Ubuntu Drivers for your camera.

---

### Post by shazbut on 2010-04-15
I had this issue once before: plug camera in, nautilus pops up then immediately closes.  It was caused by a PPA installing a newer version of a library that didn't integrate well with the rest of the system.  I had to disable the PPA and remove the offending library in synaptic to fix the problem.

Unfortunately I can't remember the particular lib/PPA, but I do know I found it by watching for the nautilus crash error sent to the logs, and googling it.  You might need to reproduce the error whilst watching the logs, either using System-> Administration -> Log file viewer, or by running
```
tail -f /var/log/messages
```
in a terminal.

---

### Post by ElSlunko on 2010-04-16
My camera won't mount anymore either. It's having problems locking the device

---

### Post by no2498 on 2010-04-16
if my batteries get a bit low my cam wont mount

---

### Post by ElSlunko on 2010-04-16
Just found out that rhythmbox was interfering somehow. I closed it and magically my camera mounted. I think it has something to do with using the same usb cable for my MP3 player. However, even after a restart and not having the MP3 player plugged in, it still didn't work. Strange. Try closing rhythmbox if it's open and you're having issues.

---

