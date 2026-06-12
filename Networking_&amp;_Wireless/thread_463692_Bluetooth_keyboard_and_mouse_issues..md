---
title: "Bluetooth keyboard and mouse issues."
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by TheFoe92 on 2007-06-03
I'm not sure if this is the right forum, but considering that Bluetooth is wireless, I took a shot and wrote here. I recently bought a new Rocketfish keyboard and mouse (mouse serial : RF-BTMSE ; keyboard serial : RF-BTMKY). I tried inserting the setup CD, but it obviously does not work. my problem is this: all basic functions of the two devices work except for the keyboard's hotkeys and the mouse's scroll wheel. Any suggestions on how I can install the two devices so they work completely and seamlessly together? Thanks in advance!

EDIT : If it is of any use, the Bluetooth dongle model number is RF-BTAPDT. All of these (the keyboard, mouse, and dongle came in a bundle package.

---

### Post by TheFoe92 on 2007-06-04
Here's something else: after searching the Net for some helpful step-by-step instructions, I came across this one: [https://help.ubuntu.com/community/BluetoothSetup]("https://help.ubuntu.com/community/BluetoothSetup"). I cannot get past the 'Find Device Addresses' step.  While trying to use the ```
sudo hidd --search
``` command, this is all that happens: ```
filip@computer-Laptop:~$ sudo hidd --search
Searching ...
```After that it just displays: ```
filip@computer-Laptop:~$
```While trying to use the ```
hcitool scan
``` command, this is the response: ```
filip@computer-Laptop:~$ hcitool scan
Scanning ...
Inquiry failed: Connection timed out
```This is very strange. The computer cannot detect the Bluetooth devices, although this post is typed up using my Bluetooth devices.

---

### Post by matthew.lns1 on 2007-06-12
I had the exact same thing. However I found out what it means. It means your adapter is not compatable. I would suspect that the one that comes with the box is usually that way.

---

### Post by TheFoe92 on 2007-06-25
Hmm..

So then does that mean I cannot configure it to be able to fully use it?

---

### Post by Unicast on 2007-07-21
> Inquiry failed: Connection timed out

Try ```
sudo hciconfig hci0 reset
```

Taken from:

[http://ubuntuforums.org/showthread.php?t=366485&highlight=inquiry+timed+bluetooth](http://ubuntuforums.org/showthread.php?t=366485&highlight=inquiry+timed+bluetooth)

---

### Post by chaz_winter on 2008-05-07
Excellent!

So, the proper method for getting the RocketFish bluetooth keyboard & mouse combo working using the RocketFish bluetooth dongle is as follows:

```
sudo hciconfig hci0 reset
sudo hidd --search
```

If that doesn't work, set Bluetooth preference "Visible and Connectable" and try again.

This enables mouse scroll wheel & keyboard convenience keys.  

Now, we'll see how it holds up.

Charles

---

