---
title: "[SOLVED] Gutsy + Wicd + WPA"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by mtdewulf on 2008-01-11
So I have a WPA network at home that I'm trying to connect to (running Tomato firmware on a buffalo router).  I'm using gutsy and could not connect with the default network manager.  So I read that I should install wicd instead.  I like the wicd layout and this allowed me to connect and seemed to work... at least at first.  

After some use, I notice that my connection is being dropped.  I noticed this when an rsync network backup I was running stopped working.  Then I tried to browse the internet, but that failed too.  I can get back on the network by clicking connect again.  However, I will usually get disconnected (no data is transferred, but wicd thinks I'm still connected) again after a few minutes. 

In short, my wicd + wpa connection is unreliable on linux, but works fine under Windows.

I should mention that I have an HP laptop with a broadcom chip (I believe).

Also I should probably report this as a bug somewhere, but wicd allows you to chose WPA "agents" / "encoders" (I forget the word - not on that computer right now).  One of them seems to crash wicd and prevent new programs from starting (I could not even start a terminal).  Even worse, if this setting is selected (and since the computer essentially freezes, you cannot unselect it), you will not be able to login on next boot.  I had to boot to "safe mode" and `sudo apt-get remove wicd` and then `rm -rf /opt/wicd` to be able to boot again.

I have a few questions:
1) Is one "agent"/"encoder" preferable?  I was just using the default.
2) If this turns out not work work, I can change the security settings on my home network.  What encryption scheme would you recommend for ubuntu?  Ideally I would like to get this to work with my laptop without sacrificing security.  I am hesitant to use WEP, but I will if I have to.

Thanks,
Mike

---

### Post by csat on 2008-01-11
> **mtdewulf said:**
> 

I should mention that I have an HP laptop with a broadcom chip (I believe).

Thanks,
Mike

Hi, Mike

This link provides a good solution [=>HERE<=](http://ubuntuforums.org/showthread.php?t=297092) for such broadcom chip.  My notebook works very stable after reading this.  Here using Gutsy with Dell 131-L Broadcom 43xx wireless.

---

### Post by mtdewulf on 2008-01-11
OK, I'll try that and report back.

---

### Post by mtdewulf on 2008-01-12
So I installed ndiswrapper, however, instead of using the dell drivers, I used the ones from HP's website (sp330088.exe for my L2005co) .  I had to install wine to run the self extractor for the drivers - I needed the bcmwl5.inf file for ndiswrapper.

Anyway, seems to work so far.  Anyone reading this in the future can assume this method works fine unless I report back otherwise.

-Mike

---

### Post by csat on 2008-01-12
> **mtdewulf said:**
> So I installed ndiswrapper, however, instead of using the dell drivers, I used the ones from HP's website (sp330088.exe for my L2005co) .  I had to install wine to run the self extractor for the drivers - I needed the bcmwl5.inf file for ndiswrapper.

Anyway, seems to work so far.  Anyone reading this in the future can assume this method works fine unless I report back otherwise.

-Mike

Oh, great!  I think there was an instruction on how to unzip Dell EXE file (unzip -a file.EXE) so that you could get it the same way, I think.

Anyway, what matter is that you get it working, so I suggest you to add SOLVED to title message.

Good luck and enjoy your wireless.

---

### Post by mtdewulf on 2008-01-12
Done.

---

### Post by deblike on 2008-05-19
> **mtdewulf said:**
> So I installed ndiswrapper, however, instead of using the dell drivers, I used the ones from HP's website (sp330088.exe for my L2005co) .  I had to install wine to run the self extractor for the drivers - I needed the bcmwl5.inf file for ndiswrapper.

Anyway, seems to work so far.  Anyone reading this in the future can assume this method works fine unless I report back otherwise.

-Mike


I can confirm this is working fine for me too, with a Presario V3000 (V3418LA) and HP drivers (sp36684.exe).

---

