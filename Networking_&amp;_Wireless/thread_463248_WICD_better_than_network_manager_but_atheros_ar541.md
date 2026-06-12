---
title: "WICD better than network manager but atheros ar5418 still fails intermittently"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by thebasard on 2007-06-03
I've got a Lenovo Thinkpad R60 with the Atheros 5418 wireless card.  Network manager gave me tons of problems and I only really got it to work after installing the windows driver and using ndiswrapper.  Now with wicd, the connection is easier to establish but periodically the wlan0 card seems to just stop working.  The only thing that brings it back is to reboot.

---

### Post by maestrobwh1 on 2007-08-29
I am having a very similar problem with my atheros card in my laptop.  Network manager shows strength numbers all over the map, and speed varies instantly from 1 MBPS to 54 and anywhere in between.

If I run kwifimanager, it shows a fairly constant signal strength and speed hovers at half speed of 22 or above.

If I use kwifimanager to change networks, I get a connection for a bit, then it dies... although it still shows it is connected.

Weird.

---

### Post by maestrobwh1 on 2007-08-30
Yep, installed wicd... and all seems well with my atheros card.  Card is running at half/full speeds, and radar in kwifimanager (I wanted a monitor to replace network-manager), shows stable and higher strength numbers.

THANKS!!!

---

### Post by imdano on 2007-08-30
> **maestrobwh1 said:**
> Yep, installed wicd... and all seems well with my atheros card.  Card is running at half/full speeds, **and radar in kwifimanager (I wanted a monitor to replace network-manager), shows stable and higher strength numbers.**

THANKS!!!Wicd has it's own tray icon that displays signal strength.  Run /opt/wicd/tray.py and it should appear.

---

### Post by tak1150 on 2007-09-03
Not sure if it's related (sorry if I'm hi-jacking this thread), but I have AR5212 card and **worked flawlessly** with network manager (I'm using the latest madwifi driver that I compiled).

Recently I put in a proxy server in the DMZ. I had much trouble setting the **new gateway with network manager**. So I switched to WICD, which works flawlessly as long as I do NOT:
[LIST]
[*]download anything
[*]watch FLASH movie
[/LIST]

Then the connection just dies even though WICD still says I have connection.
Can anybody think of what is going wrong here? Thanks!

---

### Post by walkerk on 2007-09-03
> **thebasard said:**
> I've got a Lenovo Thinkpad R60 with the Atheros 5418 wireless card.  Network manager gave me tons of problems and I only really got it to work after installing the windows driver and using ndiswrapper.  Now with wicd, the connection is easier to establish but periodically the wlan0 card seems to just stop working.  The only thing that brings it back is to reboot.

instead of rebooting you could try:
```
sudo /etc/init.d/networking restart
```

---

### Post by maestrobwh1 on 2007-09-13
Try this post... I was frustrated with my atheros dropping in and out and was all over the place with spe

This method is sort of a hybrid of installing from source. It installs the latest debian madwifi and configures it specifically for your kernel:
[URL="http://ubuntuforums.org/showthread.php?t=485579&hi ghlight=how+to+madwifi+source"]
http://ubuntuforums.org/showthread.php?t=485579&hi ghlight=how+to+madwifi+source[/URL]
__________________

---

