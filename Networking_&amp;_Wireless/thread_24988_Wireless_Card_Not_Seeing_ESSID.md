---
title: "Wireless Card Not Seeing ESSID"
date: 2005-04-08
forum: Networking &amp; Wireless
---

### Post by bfisher on 2005-04-08
This should be something easy, I'm just a relative newbie and am overlooking something...

I have installed Kubuntu 5.04 and am attempting to get my wireless card working. I've installed ndiswrapper utilities, downloaded the appropriate Windows drivers from the SourceForge site, and loaded them. Everything has went perfectly fine up until I need to associate the card with my AP. I know the base station is broadcasting the ESSID, but I cannot see it (by running iwlist wlan0 scan). KWifiManager cannot see the ESSID. I cannot manually set the ESSID using iwconfig wlan0 essid <essid_name>. I have verified that the card is powered up and radio is working. I have verified with another computer that the base station is broadcasting the ESSID. I have checked the *conf files to make sure RadioState is "1" and not "0."

The wireless card works under Knoppix 3.7 live CD, so I know it works with the drivers I am using. Anyone have any suggestions as to what else it could be?

Brandon

---

### Post by bfisher on 2005-04-09
Just as a follow up... at the suggestion of a friend, I booted the system and passed the acpi=noirq option to the kernel to disable IRQ routing. That didn't help any - same problems as above.

Brandon

---

### Post by Yatsushiro on 2005-04-09
Is this a Linksys card ?

If so, RadioState should be 0, not 1 (This is a known bug, apparently)

---

### Post by bfisher on 2005-04-09
No, it's a Dell Truemobile 1350 in a Latitude D600. I can try making RadioState 0 and see if that does anything. Maybe it's messed up for these cards too.

Brandon

---

### Post by jonny on 2005-04-09
I'm typing this with a Dell Latitude notebook with (I think) the same wireless card that you're using - so it can be made to work.  Some of the problems I encountered were:

1. I had to use the drivers that came with my laptop, not the more recent ones that are on Dell's site.  For me, Dell had helpfully put a copy in the windows partition under c:/drivers/network/onboard but for some reason they wouldn't install properly from a mounted Windows drive - I had to move them to my home folder first.

2. I had to edit the conf files in /etc/ndiswrapper/bcmwl5 to set radiostate=0

3. I used the gnome networking tool to configure the ESSID and the WEP key.  This worked perfectly once I discovered a cryptic bug that meant I had to prefix the WEP key with s:

4. I had to manually edit a config file (can't remember which one, sorry) to get ndiswrapper to start when the computer is turned on.  The official ndiswrapper -m didn't work for me.

5. I completely failed (despite the assistance of a qualified unix network administrator!) to get things working using ifconfig and iwconfig.  It's pretty easy from the command line, though, if you edit /etc/network/interfaces (it has some very good man pages) and use ifup and ifdown.

---

### Post by bfisher on 2005-04-10
jonny - you are the man! The solution to all of these problems is to set RadioState to 0 instead of 1 in the *conf files (located in /etc/ndiswrapper/<driver>). Once I changed these *conf files (and restarted for good measure), the device appeared in the network configuration utility and I was able to type everything in.

The only thing I had to change was on the command line, I had to explicitly type in "ifdown eth0" to bring eth0 down and "ifup wlan0" to bring the wireless card up. I am going to go Google now what *conf files to change so I don't have to do that each time.

Woohoo Hoary!

Brandon

---

### Post by jonny on 2005-04-10
[QUOTE=bfisher]I had to explicitly type in "ifdown eth0" to bring eth0 down and "ifup wlan0" to bring the wireless card up. I am going to go Google now what *conf files to change so I don't have to do that each time.[/QUOTE]You should be able to do this through the Gnome Networking applet - simply change the default gateway device from eth0 to wlan0 and hit apply.  You can also save your configuration on that screen to allow you to switch quickly from one network to another.

---

### Post by hyde on 2005-04-11
[QUOTE=jonny]You should be able to do this through the Gnome Networking applet - simply change the default gateway device from eth0 to wlan0 and hit apply.  You can also save your configuration on that screen to allow you to switch quickly from one network to another.[/QUOTE]
 Great!

I got mine Broadcom based Asus WL-100g card working after editing those *.conf files.
Thank you jonny and Brandon!

I might add that I'm using Kubuntu, so Gnome applets are not there by default...

---

### Post by LokiJon on 2005-04-14
I'm having the same trouble as OP, but I've got a Broadcom card in a HP Presario 3120ca notebook. I've got the proper drivers, wlan0 is showin in my network settings, ndiswrapper sees hardware and driver ok, but no APs are being detected, the essid refuses to set, and generally I can't get a lick of this wireless going.

 Tried setting all .conf files' radiostate|0, that doesn't seem to get it done, either.

 Any ideas/suggestions/similar fixes? So many threads seem to have solved this problem for so many cards. Anyone have the magic touch for mine?

---

