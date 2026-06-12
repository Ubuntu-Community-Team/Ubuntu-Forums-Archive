---
title: "Wireless"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by Bob Abouille on 2011-03-13
Just got ndiswrapper installed yesterday, with no interruption of service, until today.

Now, the wireless goes out intermittently, usually when idle.

I was warned several times of using ndiswrapper as my primary connection yesterday - is this why? I was toying with the idea of not installing windows onto this machine, but with this recent news, I may have to. 

Any suggestions would be appreciated!

---

### Post by Eiji Takanaka on 2011-03-13
Research and persevere dude. It'll be worth it in the long run.

I had all sorts of fun and games getting the right driver for my wireless think it was 
Rtl819xe ih the end, but i was half-tempted to give up as well. 

If you do persevere a handy hint is to keep a list of all the tweaks you might have to do to your system, so that if you decide to upgrade further along the line, you remember the settings/configurations you changed e.t.c. 

Stick with it dude, the answer'll be out there somewhere, or someone on these here forums has probably experienced what you have also.

---

### Post by Eiji Takanaka on 2011-03-13
p.s listing your system specs and o/s nuances usually helps!! I.e machine your using/ ubuntu version e.t.c it gives people a common ground to work from ;)

---

### Post by wep940 on 2011-03-13
And post the output of 
 
lspci  
 
-and-
 
lsusb
 
so we can see the adapter you have.  Ndiswrapper itself is not at fault, but rather the driver being used.  For ndiswrapper (and hopefully you used the GUI'd front-end ndisgtk), the driver must be Windows XP only, and must match the architecture - 32-bit for 32-bit Ubuntu, 64-bit for 64-bit Ubuntu.
 
With the changes that have been made in restricted drivers and open source drivers, it's better to start by not using ndiswrapper first, using ndiswrapper if everything else fails.  The normal procedure would be:
 
- if possible, hard-wire your PC to the router and then do sudo apt-get update in a terminal window
 
- check in system/administration/additional drivers (depending on your version of Ubuntu, it might also say Restricted Drivers).  If there is a driver there, be sure it is enabled.
 
If no driver shows in the restricted drivers then try ndiswrapper & ndisgtk.
 
After you post back the outputs I asked for we can try to go from there.

---

### Post by lkraemer on 2011-03-15
While you are at it....Open a Terminal Window and use these commands to get more information on your hardware, wireless, Windows loaded drivers, and Linux drivers that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci > junk.txt
lsusb >> junk.txt
lshw -C network >> junk.txt
lsmod >> junk.txt
ndiswrapper -l >> junk.txt
cat /etc/modprobe.d/blacklist.conf >>junk.txt
iwconfig >> junk.txt

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the file.


lk

---

### Post by wep940 on 2011-03-16
> **lkraemer said:**
> While you are at it....Open a Terminal Window and use these commands to get more information on your hardware, wireless, Windows loaded drivers, and Linux drivers that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci > junk.txt
lsusb >> junk.txt
lshw -C network >> junk.txt
lsmod >> junk.txt
ndiswrapper -l >> junk.txt
cat /etc/modprobe.d/blacklist.conf >>junk.txt
iwconfig >> junk.txt

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the file.
 
 
lk
 
Hey lk - hope you are doing well!  Noticed something in your post - you may want him to post/attach the junk.txt file after it's created ;)  I've tried this same thing in the past but for some reason the users I tried it with didn't understand 2 ">"'s on all the lines but the first one, so I always ended up with only 1 little part of what I needed!

---

