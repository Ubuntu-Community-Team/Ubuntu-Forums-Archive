---
title: "No Login"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by rednano12 on 2009-01-20
I was attempting to install the nvidia drivers for my GeForce 6200A:

[IMG]http://www.terminally-incoherent.com/blog/wp-content/uploads/2008/05/facepalm.jpg[/IMG]

Aaaaaaaaaaaaaanyway...

I hit Ctrl-alt-F1 and typed this code in

```
cd /etc/init.d
sudo gdm stop
sh ./NVIDIADriver.run
```

It compiled, installed, and then my computer was forced off due to a power outage. Now when I boot into ubuntu, after the loading bar, I just get a black screen. I can still Ctrl-alt-F1 and login, but I have no idea how to get my login back. I've tried gdm start and gdm service start from within init.d but no luck. Help?

---

### Post by sowelie on 2009-01-20
What happens when you run /etc/init.d/gdm start, are there any error messages?  Have you tried re-running the nvidia installer?

---

### Post by rednano12 on 2009-01-21
I get an error like this

WARNING: GDM is already running. Aborting!

I have not tried re-installing the nvidia drivers. I'll try that again. Thank you.

---

### Post by emarkd on 2009-01-21
What happens when you press <ctrl><alt>F7?  that's where the gui should be if gdm is running properly.

---

### Post by rednano12 on 2009-01-22
Ctrl-Alt-F7 gives me a blinking underscore.

---

### Post by TJCIB on 2009-01-22
I'll take a shot:

reconfigure X?

```
sudo dpkg-reconfigure xserver-xorg
```

Maybe?  I usually start there with video issues.

---

### Post by rednano12 on 2009-01-22
I reconfigured x, but made no difference.

---

### Post by handydan918 on 2009-01-22
It does sound like a driver issue. 
If you are sure you installed the right driver, I'd try running the script again.

---

### Post by rednano12 on 2009-01-22
I installed the official driver from NVidia. Twice. The one for my card. Are there any other options?

---

### Post by handydan918 on 2009-01-23
Try ```
nvidia-config
``` or ```
nvidia-settings
```
I don't know if these are still used in the current nvidia drivers, but it can't hurt to try.

---

### Post by rednano12 on 2009-01-24
Haha! nvidia-settings gave me a segmentation error. I reinstalled for a third time, and it indeed is the charm. Works great! Thank you for that advice! :KS

---

