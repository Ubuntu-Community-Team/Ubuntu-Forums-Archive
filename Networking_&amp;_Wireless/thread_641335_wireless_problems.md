---
title: "wireless problems"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by florus on 2007-12-15
I have a new laptop which came with Vista installed, and is now a dual boot with Gutsy. My wireless router is set up with mac address filtering but no other security. Vista always connects automatically with no problem, and I have managed to connect twice using Gutsy so all the hardware is working ok, and I have installed all patches and updates. What do I need to do to get Gutsy to log onto my network automatically? And why is there no device manager listed under System>Administration?

---

### Post by AngelAir on 2007-12-15
I do not know I your problem is the same that I am having were the wireless card is off after boot-up and after I go to the Terminal and enter :  **_sudo ifconfig wlan0 up_** then it starts working fine.  Because some other situation I got into; I had to reinstall again, but the first time I had found how to get it working and after rebooting it was still working automatically.  I am still searching for that original fix (don't remember where I found it).

I found Device Manager in **System > Preferences > Hardware Information**.:)

---

### Post by florus on 2007-12-15
Thanks, AngelAir, that solves where to find my hardware profile. I will try the wireless fix next time I lose the connection. When I booted into Gutsy this time the wireless link was there immediately. Intermittent problems can be the hardest to diagnose. :-)

---

### Post by WedgeHG on 2007-12-26
I have a similar issue: I boot into XP and the wireless works fine. Boot into Fiesty and it's a crapshoot. Sometimes it works just fine, others it refuses to connect. Even more infuriating is that sometimes when it won't connect it will just all of the sudden decide to connect after half an hour or so.

What I've ruled out so far:

Hardware problem with my computer: works fine under Windows. Also seems to be fine sometimes in Fiesty. Interestingly, when it refuses to connect to my wireless it will readily hop onto the neighbors... it's just mine that won't connect. 

My wireless network: I know that it isn't just my network because I type this message on a laptop (also running Fiesty) that is wirelessly connected to my network while my desktop refuses to connect.

Network configuration problem on my desktop (at lease I think so): Because it works after a while sometimes (and sometimes immediately) and has no trouble hopping on my neighbors network.



I thought that maybe the fact that I dualbooted was somehow confusing my router... it would see a different hostname attached to the same MAC and get confused or something. But then I came back to my parents house for the holidays and encountered the same problem on their wireless router. I have a D-link and they have a Westell. I find it unlikely that two different brands would have the same bug (if that is even what is going on here).


What I've tried:

Restart my router... no effect.

Restart my computer... nothing.

Restart the networking (sudo /etc/init.d/network restart)

Boot back into Windows and release the IP address before booting into Linux.



Does anybody have any idea what could be causing this and, more importantly, how to resolve it? I would be most appreciative.


Thanks in advance,
-Wedge

---

### Post by florus on 2007-12-28
It seems to me to be a boot problem. Sometimes I can access the internet but not the other computers on the network, sometimes both internet and computers, and sometimes neither. Rebooting often changes things, but not predictably. It is worrying if this problem affected Feisty as well - surely it should have been sorted by now. I would like to dump Windows completely, but it seems the time is not yet come.:(

---

### Post by florus on 2008-01-03
A further development : after a successful boot with the wireless network working properly, I used suspend and when I woke the computer - no network.

---

### Post by MacAnthony on 2008-01-03
In the ubuntu wiki, it outlines a couple of scripts to handle starting and stopping the network on suspend and hibernate. I haven't tried it out, but should work for what you seem to be asking:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-5c71df23d1410c1c5c1c0bcd216353a41e6f935c](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-5c71df23d1410c1c5c1c0bcd216353a41e6f935c)

---

### Post by florus on 2008-01-03
Part of the trouble is that the behaviour is so inconsistent. I had suspended the computer again, but this time when I woke it the network was back and fully functional. I am reluctant to run scripts or change settings when half the time everything is working properly. At least now I can reactivate the network by restarting or suspending even if I have to do it two or three times. There are plenty of other users on this forum with the same problem, and I have not yet seen a definitive answer.:confused:

---

