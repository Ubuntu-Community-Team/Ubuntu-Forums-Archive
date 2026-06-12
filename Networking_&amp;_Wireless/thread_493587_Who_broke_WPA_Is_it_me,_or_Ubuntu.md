---
title: "Who broke WPA? Is it me, or Ubuntu?"
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by kgr132 on 2007-07-05
My WPA just stopped working a couple of weeks ago, and now even a clean (although updated with Update Manager) install of Fiesty doesn't work.

I was on the road for 10 days a couple of weeks ago and my WPA was working perfectly fine using Network Manager before I left. After using open networks in hotels for a week and a half and I'm sure receiving some updates to Ubuntu, I came home and my WPA wouldn't connect anymore. I followed every thread I could find in this forum regarding how to set it up again, all to no avail.

I eventually resorted to a clean install of Fiesty 7.04 earlier today. Since I wasn't at home again, I began with a clean install of Fiesty and used my Sprint broadband card to get all of the updates available for Fiesty and I installed a few apps (Mozilla Thunderbird, VMWare Server, etc.). I didn't even use any wireless networks until I got home this evening. 
I tried Network Manager with WPA: no connection. 
I tried Wicd with WPA: no connection. 
I tried manually configuring wpa_supplicant with my SSID and hex version of my key in /etc/network/interfaces: no connection. 
If I reconfigure my wireless router to provide an open network without encryption, I can connect every time with either Network Manager or Wicd, so I know it's not a wireless card driver related problem. 

Yes, I'm sure the key is correct. I followed many detailed HowTo's from this forum with various methods for setting up WPA including using Network Manager, Wicd, Wifi Radar, direct config. of wpa_supplicant, etc. I even switched to an ASCII key with only 8 characters just to keep it simple. 

I'm about to perform another clean install but without any updates to Fiesty this time just to see if WPA still works out of the box, but it's so tedious I'd rather not, especially since I just did a clean install earlier today. WPA used to work just fine a month ago with Fiesty and my home network, but now, nothing. I've been using Ubuntu for over a year now and have never been this frustrated by it. :( Thank goodness the Sprint broadband connection is so easy to setup and connect with, or I'd have to resort to being tied to my wireless router by a 6 foot cable. Any help with this WPA dilemma will be greatly appreciated.
-K-

---

### Post by kevdog on 2007-07-06
Is your wireless card turned on??  Can you get any connection from your wireless card at all??

---

### Post by kgr132 on 2007-07-06
Quote from original post: If I reconfigure my wireless router to provide an open network without encryption, I can connect every time with either Network Manager or Wicd, so I know it's not a wireless card driver related problem.

Well I gave up and did another clean installation of Fiesty 7.04. No updates, no changes from the default load off of the CD except to add ndis-wrapper with Synaptic. Lo and behold, WPA works again. I'm going to let Ubuntu get its' security updates and if WPA still works, I'll try a few apps, one at a time to try to catch what's killing my WPA. 

Keeping my fingers crossed :)
-K-

---

### Post by kgr132 on 2007-07-08
Sorry to anyone who wasted time reading this. Obviously I did something to break Ubuntu's support for WPA authentication. I've now completely reconstructed my system down to the last application and tweak. WPA works perfectly using Network Manager from the default installation. Now, if only I knew what I did that broke it so I could avoid doing it again. Oh well. Ubuntu Rocks!
-K-

---

### Post by marsmissionaries on 2007-07-08
Wireless in linux is still barbaric...it probably was not you that broke it.

---

