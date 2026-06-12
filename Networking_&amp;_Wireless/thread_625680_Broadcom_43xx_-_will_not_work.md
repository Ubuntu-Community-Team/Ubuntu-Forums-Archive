---
title: "Broadcom 43xx - will not work"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by warwon on 2007-11-28
Helllo,

After losing a battle on the weekend my Ubuntu drive was lost for various reasons, and I was unable to recover the install

So I went through the trouble of reinstalling Ubuntu Studio 7.10, as this has worked well in the past from 7.4 to 7.10.

I just after the reinstall had massive issues, no sound at all, no video card, no wireless.

The sound was odd as this had worked in all the installs before. 

Dell Inspiron 1720.

So I installed all the updates, changed sources, updated more. Did a manual install of Asla, and the Nivida drivers which failed a few times before I got it working.

Once I solved that I quickly checked this form for my old method of getting the wireless card working, I did the quick way install that never worked.

Issues:

1. Sometimes my wireless card appears in networking, somtimes I only see see "wired"
Running "sudo modprobe bcm43xx" will make it appear for only that session

2. I can get the card up and running for say, I can see wireless networks, but nothing will connect even my open test one.

3. I did try to remove the installed options from the quick way and use the firmware in Restricted drivers, again that never worked either

Anyone have any ideas?

---

### Post by csat on 2007-11-28
Try this tutorial:

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

---

### Post by spd106 on 2007-11-28
Sounds like you might have a driver conflict.
See which is currently in control by running this command.
```
sudo lshw -class network
```

If it says UNCLAIMED, then you should be able to insert the bcm43xx driver to make it work. After that check that it's not blacklisted in the /etc/modprobe.d/blacklist file. If it is then remove the 'blacklist bcm43xx' line and it should work on startup.

If you look in the /lib/firmware directory, then there should be lots of bcm43xx-*.fw files. If not use the Restricted Drivers Manager to extract and install them.

Hopefully you won't have ndiswrapper installed, if so then you'll probably want to remove it first. You can always add it back later if you can't get bcm43xx to work.

---

### Post by warwon on 2007-11-28
Thats a few good ideas, I will try that tonight. As i don't want to have to reformat the drive again

---

### Post by warwon on 2007-11-29
Well, strange.

I went through everything top to bottom, nothing worked.

I have reinstalled, and still getting the same errors.

I can confirmed that this is no hardware issues, as the hardware works fine on another opearting system.

Nothing in Ubuntu seems to be working as good as used to be...

So I have no wireless still any ideas?

---

### Post by spd106 on 2007-11-29
Perhaps it's worth browsing through the Dell support forum for ideas. From what I can see there are others who have had similar problems, but it's difficult for me to tell you what to do without a Dell in front of me.

For reference most of the difficult parts are now handled by the Restricted Drivers Manager. This page may be useful [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

### Post by AJB2K3 on 2007-11-29
Google for the bcmwl5a.inf file instead of the bcmwl5.inf file.

---

### Post by warwon on 2007-11-29
I went through [https://help.ubuntu.com/community/Wi.../bcm43xx/Gutsy](https://help.ubuntu.com/community/Wi.../bcm43xx/Gutsy) ; that didn't work

I will try for that bcmwl5a.inf and see if that helps tonight....

This is getting crappy

---

### Post by NullHead on 2007-11-29
Use [this guide]("http://ubuntuforums.org/showthread.php?t=405990"). It worked for me every time I've used it ... witch was three times one one of my broadcom cards and once on my other broadcom cards.

---

### Post by Maci_01 on 2007-12-06
Hey War I'm in the same boat as you. Any update?

---

### Post by Lorac1949 on 2007-12-06
> **NullHead said:**
> Use [this guide]("http://ubuntuforums.org/showthread.php?t=405990"). It worked for me every time I've used it ... witch was three times one one of my broadcom cards and once on my other broadcom cards.

That was the first "fix" I tried.  No luck at all.  I've tried another suggestion from another post and finally was able to view my network in Network Manager - but couldn't connect to the Internet.  In NM I sometimes see a signal of 98%, 0% and sometimes it's not on the list of local networks at all.  Aaaagh!  It comes through great in my Windows boot.  I've literally spent about a week working on this issue.  I hope someone can come along with a workable fix for my 43xx issue.

---

