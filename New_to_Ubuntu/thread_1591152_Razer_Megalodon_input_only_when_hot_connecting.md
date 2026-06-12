---
title: "Razer Megalodon input only when hot connecting"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Mobidoy on 2010-10-08
I have a Razer Megalodon Headset and Ubuntu only see Analog Mono Input when I Hot Plug it but, If I boot/reboot with it already connected in the USB port, It will be recognized has an output device (I can even pick either Stereo, 5.1 or 7.1).

Can I use some commands to fix this or even add lines to a file that will have it recognized correctly when Hot plugged ?

---

### Post by Mobidoy on 2010-10-08
After some testing, if I boot with it connect it, as I said, it recognize it and, if I unplug it and reconnect it with out shutting down or rebooting, It will still see all the functions. Only problem is if I boot my laptop without that Surround USB headset connected, the system will only detect it has an input (microphone) when I connect it while the system is running so, no audio :(

---

### Post by Mobidoy on 2010-10-09
Issue still exist, this is my lsusb output:

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 005 Device 002: ID 1532:000e Razer USA, Ltd **
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I will reboot with it connected and add the lsusb output to see if there is any differences. **Edit: It is the same lsusb output**

Is there another command I could use or file to compare with it working and not working to see any differences ?

---

### Post by Mobidoy on 2010-10-29
I have talked with someone who has the same headset and never had that issue with it... He is on 10.10 and was on 10.04 not long ago. He is using Ubuntu for only a month or so, just like me.

Also, I have discovered that, after hot pluging them, if I do a 

```
sudo alsa force-reload
```

My headset works properly.... 

Any clue ?

---

### Post by Sugi on 2010-11-15
It looks like some have issues while others have no problems at all with the Megalodon. I am thinking about buying a pair and this thread is useful.  Did the force-restart fix your problem?

EDITTED: Everything works outside-of-the-box, though I did have one conflict internally.  Ubuntu was still picking up "Internal Stereo Audio", but nothing was plugged into it. All I had to do was disable it through the Sound Preferences.  That's it. :D

Sugi

---

### Post by tannerwatson on 2011-09-22
Have you all had any problems with Natty 11.04? I'm probably going to pick up the headset and it the only problems are the ones mentioned earlier I can just live with them.

---

