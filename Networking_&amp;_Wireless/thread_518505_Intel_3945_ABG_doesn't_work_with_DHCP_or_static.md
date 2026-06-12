---
title: "Intel 3945 ABG doesn't work with DHCP or static"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by mpompey on 2007-08-05
I'm running into issues with my Intel 3945ABG card. If I use a static IP, I can see that it's connected to the access point, but I can't get to the internet, ping my router, etc. If I set the wireless card to DHCP, it sees the access point but doesn't pick up an IP.

I originally thought it was a problem with my router, however my wired connection works with the same settings for both DHCP and when given a static IP.

When setting wireless to DHCP, KWifiManager shows my access point's MAC address but no IP. When I assign an IP to the wireless connection, packets go out, but nothing comes back. I'm at a lost.

I'm using a Dell Inspiron 9400 that I dual boot between Ubuntu 7.04 and Windows XP. Everything works fine in the XP environment, so something must be wrong in the Ubuntu environment. I'm a noob in Ubuntu so I don't know where to begin to address this issue.

MP

---

### Post by Anakashar on 2007-08-06
I'm getting the exact same thing you are.  It worked at first on my laptop right after a fresh install, then I did a full update and next reboot, it simply stopped working.

Have you tried using wicd?  Some people have gotten some success with it..  I haven't, though, but it appears to work for others.

---

### Post by mpompey on 2007-08-06
No I haven't. I may try that this evening.

---

### Post by draconastar on 2007-08-14
Yes, I'm having the same problem as the two of you, and am also a complete Ubuntu noob.  I hooked up my wireless card, which can find and connect to wireless access points, but doesn't have an IP assigned.  I don't even know where to start, other than this "wicd".  My card is a Linksys WUSB54G, which worked fine in Edgy.  After I updated Feisty, I had this problem.

Is wicd already integrated into Ubuntu?  I'm currently on a Windows machine, so I can't check.  Also, how do I go about using it?

Thank you for the information.

 - Daren -

**EDIT**

I have noticed that I can only actually connect to the access point after having attempted "Manual Configuration".  Beforehand, it sees the network and doesn't let me connect at all.  Could this be because I don't have correct drivers installed, and how would I go about getting Linux drivers for my wireless card?

---

### Post by mpompey on 2007-08-14
I'm sorry to say I haven't found a solution as of yet, besides using a really long CAT5 cable when I'm at home. This whole wireless Linux thing has been more aggravating than I can say. I wish I could get it to work, as Linux is much leaner for web browsing and work.

I haven't found any help on this forum yet, I think I may end up wiping my linux partition and starting with 6.10 and staying there, since that worked.

---

### Post by bmartin on 2007-08-14
> **draconastar said:**
> Is wicd already integrated into Ubuntu?  I'm currently on a Windows machine, so I can't check.  Also, how do I go about using it?
Here's the [wicd download page]("http://wicd.sourceforge.net/download.php"). If you'd like steps to add the repository, download it, and make it easily executable, you can find them [here]("http://blakecmartin.googlepages.com/wicd.html").

---

### Post by draconastar on 2007-08-15
Well, I have done several things, without any real progress made.  

At first, I figured I would try out widc.  After adding the repository and beginning to install, it informed that in order to install widc, I would have to uninstall network-manager-gnome, I believe.  I didn't think I wanted to do that, so I gave up.

I also attempted installing the correct drivers using ndiswrapper.  I don't really know if the drivers actually installed correctly, but I do know that it still wasn't connecting through the wireless.  

So I'm back to square one.  Here's my next question:  are there any wireless cards that work really well with Linux WITHOUT having to bend over backwards to make it work?

I will totally buy it to save the damn trouble.  :-P

Thanks for all the help so far guys!

 - Daren -

---

### Post by imdano on 2007-08-15
The Intel 3945 is actually one of the best out of the box, normally.  Give wicd a shot before you spend money on a new card.  It won't hurt to uninstall network-manager-gnome if you can't get internet with it right now anyways.  Wicd is meant to replace network manager, and unfortunately having more than one management app at once causes conflict issues, so you have to uninstall any others before getting a new one.  If you don't like it you can just remove it and reinstall network manager.

---

### Post by bmartin on 2007-08-15
If you give up, I made a [recommendation]("http://ubuntuforums.org/showthread.php?t=525936") to someone else earlier tonight. It's available at circuitcity.com.

---

### Post by imdano on 2007-08-15
If switching to wicd doesn't work and you want to stick with it, post the output of the following commands ```
sudo lshw -C network
lspci -nn
ifconfig
iwconfig
```

---

### Post by draconastar on 2007-08-16
I'll make sure to post the results once I get around to running a cable through my house again.  :-P

Thanks for your help. =)

---

### Post by Normand on 2007-08-17
I have had the same problem with Intel 3945ABG and also couldn't connect wired either, on my ASUS laptop.
I uninstalled network manager and installed wicd.
It now works like a dream and is finally installing a bunch of updates.
Thanks

---

### Post by punkrokk on 2007-08-17
what is the output of iwconfig?

Also, are you using WPA2? I'm not sure the current drivers support that.

---

### Post by draconastar on 2007-08-20
Actually, installing and using wicd has solved my problem completely.  

I don't know what it's doing that Linux isn't to assign an IP address, but it's certainly working now.  :-D

Thank you to everyone who helped!

 - Daren -

---

