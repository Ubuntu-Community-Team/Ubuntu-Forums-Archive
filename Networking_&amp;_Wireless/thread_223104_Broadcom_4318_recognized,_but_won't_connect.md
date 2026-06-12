---
title: "Broadcom 4318 recognized, but won't connect"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by jeff_ on 2006-07-25
I just installed ubuntu for the first time, although I have used mandrake and gentoo (with wireless) in the past. iwconfig seems to show that it recognizes my Broadcom 4318 card, but after entering my wireless network's essid and WEP key in the network settings it isn't able to connect. To further complicate matters ubuntu seems to have some policy about not letting me su to root. iwconfig won't let me change eth1 settings unless I'm root and when I try to sudo iwconfig nothing happens.
I had the same problem from the install cd, but was able to sudu su to root there (not that this helped at the time).

Thanks for any help, I hope to try ubuntu and possibly switch to it from gentoo, although without internet access I can't really use it.

---

### Post by cilynx on 2006-07-26
Hey,

In Ubuntu, you can get a root prompt with "sudo -s".  

As for the BCM4318, welcome to Hell.  It works, sorta.  I installed Dapper64, the firmware slicer thing, and the genuine firmware to slice.  After that, it really looked like it was going to work, but didn't.

I found hunting around on Google that you have to pass it
```

# iwconfig eth1 rate 11M

```
(sub eth1 as appropriate).  It has to be 11M.  I don't know why, it just worked.  Even if it showed 11M in iwconfig before, you still have to pass the line.

Anyway, a bit later, I decided to hop up to the k8 kernel instead of the generic 64bit.  As of now, I am running 2.6.17-5-amd64-k8 and no longer need the 11M line.  It Just Works.  

If none of this works for you, there's a thread on using ndiswrapper instead over here:
[http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto]("http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto")

---

### Post by jeff_ on 2006-07-26
sudo -s just prompts me for the root password (which is nothing) and then returns to my user prompt. From my user account I can't edit wireless settings using iwconfig, and sudo iwconfig won't change settings either and just returns to my user prompt. So as of now I cannot change the rate or any other setting for my wireless interface.

---

### Post by cilynx on 2006-07-26
'sudo -s' does not prompt for "the root password".  'sudo -s' prompts for "your user password".  If you just hit enter at the sudo password prompt, it assumes you didn't mean to do it and drops you back to your user prompt.  It's a bit confusing.  If you use 'su' give it your root password (non-existant under Ubuntu...thus you can't do this).  If you use 'sudo', it wants your user password.

---

### Post by jeff_ on 2006-07-26
Thanks, now I can set my essid, rate, and key, but iwconfig still says that the access point is invalid, which I assume just means that it can't connect. Also when I go to the network preferences it says that the interface is not active, but activating it takes quite some time and doesn't seem to do anything. I'm going to try ndiswrapper which I used under gentoo now unless you have any other suggestions.

---

### Post by Slicedbread on 2006-07-26
ndiswrapper + network-manager-gnome = almost as easy as windows, except for the annoying prompt for a password every time you want to connect.

The bcm43xx driver is slow, buggy and I have heard not much range. Ndiswrapper is still the way to go, plus your wifi light should still work.

---

### Post by generals8 on 2006-07-26
It took me quite some time to get mine working as well. My broadcom chipset is 4318. I used firmware cutter in kubuntu, but it wouldn't work in ubuntu. I did find a link that worked very well and only took a second. [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

Hope this helps

---

### Post by jeff_ on 2006-07-26
Thanks for all of your help guys. I used ndiswrapper and now have my wireless connection up and running. I'm not sure why you have to enter your password every time you connect, I don't seem to have that problem.

---

### Post by krazyd on 2006-07-26
That's only for WPA-PSK networks, AFAIK.

For anyone who's interested, there is a way* to get network-manager to just remember your password so it doesn't have to ask every time: [http://www.ubuntuforums.org/showthread.php?t=192281](http://www.ubuntuforums.org/showthread.php?t=192281)

*I haven't tried it. :D

---

### Post by auberginepop on 2006-07-29
A big thank you to cilynx

My wireless worked but stopped working when I uninstalled Network Manager so that networking was handled at boot.

The line...
iwconfig eth1 rate 11M

...made everything sweet once more!

---

