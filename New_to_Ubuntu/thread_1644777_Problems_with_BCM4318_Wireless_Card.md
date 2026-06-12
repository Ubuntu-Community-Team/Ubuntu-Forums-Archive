---
title: "Problems with BCM4318 Wireless Card"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by thk123 on 2010-12-13
Hello, I am having a problem getting Ubuntu 10.10 (x64) to work with my wireless card (Broadcom BCM4318 ). I am aware there are many posts about this problem (or very similar) and I apologise in advance for probably wasting your time. However, I have been trying to follow the other posts and have ended up making matters worse.

When I first installed Ubuntu the wireless card didn't work and when I clicked on the connection logo it said drivers missing (or something similar). 

I followed various forum posts and installed fwcutter, bcmwl-kernel-source and dkms. However, now when I run iwconfig or ifconfig, wlan0 no longer shows up and the wireless option is not visible in the connections icon (just wired connection). In a last ditch attempt, I installed ndiswrapper but this achieved nothing.

I have no way of connecting the computer to the internet (I am currently using my laptop and transferring debians by memory pen)

Thanks in advance for any help,
Thomas

---

### Post by lkraemer on 2010-12-14
WOW, a classic example of what not to do to get the Broadcom Hardware
working......Mix-n-Match.........different methods......

But, there is hope.......We just have to figure out what you did,
reverse probably 90% of it, and then correct what remains.  That
means you need to be able to READ & FOLLOW Directions.  So, the hard
work is up to you.

Go read this Posting, then post back the results of the first 7 commands.

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom)

We'll go from there.  You will be using Method #2, and using whatever
Broadcom Driver Ubuntu 10.10 uses for default.  You probably will need
a Hardwire Ethernet connection to get all the Ubuntu updates before we
start.  That would be best.  So, pop in at a friends place with your
Ethernet cable and do the Update first.

You also need to locate the Switch or the Keystrokes to Enable/Disable
the Wifi.  Just locate them so you can toggle them later......Don't
mess with them for now.

Also, I'd like a listing of all your Terminal commands.  Open a Terminal
Window and do:
```

history > lk.txt

```
Then attach lk.txt, so I can view it for now, and go over your commands.


lk

---

