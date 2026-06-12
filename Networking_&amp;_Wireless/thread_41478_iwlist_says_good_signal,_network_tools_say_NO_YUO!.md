---
title: "iwlist says good signal, network tools say NO YUO!!!"
date: 2005-06-13
forum: Networking &amp; Wireless
---

### Post by NumberMonkey on 2005-06-13
When I installed hoary on my new 700m, the ipw2200 driver set up and worked great.  Recognized my wireless router and everything, right out the box, so to speak.

When I took it to work, all hell broke loose.  iwlist scan recognizes the AP here at work, and tells me that the signal is strong.  When I set up my modem with iwconfig, it says that I have no signal.  I tried to use wifi-radar to see if that would work, but no matter what AP I look at, it's telling me that there is no signal present.  

I really have no idea what to do at this point.  I've looked through here trying to find a solution, but nothing seems to be working.  The only other thriead I found with similar problems had no replies, so I hope that there's somone here that can help me.  I feel like impaling my head on a spike at this point

Please help me before I pull a Mr. Morden

---

### Post by kleeman on 2005-06-13
What does iwconfig show?
If your work network is called WORK do this

sudo iwconfig wlan0 essid WORK

(I am assuming your wireless interface is wlan0- iwconfig should show the right name here)

Then

sudo dhclient wlan0

(again wlan0 is assimed to be your wireless interface)

report output and fuggitabout Dr. Morden whoever he is  :)  :)

---

### Post by NumberMonkey on 2005-06-13
Thanks for the reply.

After looking deeper into the forums I found  [this thread](http://ubuntuforums.org/showthread.php?t=30856), and  discovered that I was still using the 0.19 version driver that came with the Hoary installation, and after updating it to the stable version, I could find the signal again.  Once I got that working, I diddled around for a bit and finally got it up and running.

---

