---
title: "Reverse driver help - bcm94306mp"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by wep940 on 2011-06-26
Here I just got help to get this adapter going again in Linux, only to find that I can't get WPA2 working in Windows.  I lost my hard drive so I've been starting over, and guess where all the drivers are that actually worked?

So, since everyone was great getting this working for me in Ubuntu - WPA2 and all, and since before I actually had it working with WPA2 in Windows, I thought I beg for a little reverse driver help, if possible.

What I need is the Windows XP Pro SP3 driver for the BCM94306MP (4306) that supports WPA2.

I've tried the driver from Compaq (it's a Compaq laptop) but no WPA2 support.  I've tried other bcmwl5.inf, bcmwl5a.inf and bcmwl5.sys files I could find and still no luck.  I even used to have a Macrium Reflect image of the old disk so I could pull files out as I needed, but I didn't realize when I used that hard disk in another PC for a friend that it was the one that had my backups on it!!

If anyone out there can help me with this it would be greatly appreciated!

---

### Post by wep940 on 2011-06-26
Finally tracked down what I needed and all is well now.

---

### Post by iconoclast hero on 2011-08-21
What did you do to get this working with Ubuntu.  I have a fresh install of 10.04.3 LTS on a Compaq dual boot with XP.  It worked fine with XP yesterday and I can get the thing to see my router but it won't connect to it.  It appears that I have a valid driver, i've manually set the IP, i've turned of the WPA/WPA2, it can see my neighbor's wireless, i'm currently on my wireless on another computer...  i'm somewhat lost trying to figure out what is missing.

---

### Post by anewguy on 2011-08-22
It's been a while, but I think what I did to solve this was:
[LIST]
[*]installed the firmware cutter 
[*]followed the instructions in jospeh mills post in this thread:
[http://ubuntuforums.org/showthread.php?t=1788272]("http://ubuntuforums.org/showthread.php?t=1788272")[/LIST]

---

