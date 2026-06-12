---
title: "Ubuntu finally on my WPA network...what about connecting to others?"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by dougr on 2007-03-29
After a few hours, I finally got my installation of ubuntu with my RT61 chipset wireless card connected to my WPA-AES access point.

This included a lot of manual configuring of not only a datafile called rt61sta.dat, but also /etc/network/interfaces.

My big concern is getting this thing on other networks now.  My main concern is my school network, which uses an open wireless point, and a webpage for verification.

Connecting should not be a problem as "wireless assistant"(I use kubuntu) sees all of the access points fine, of course it cannot handle configuring WPA, or at least I could not get it to. 

So I guess the question is, if I go into "wireless assistant" and choose to connect to my school network, what will happen when I come home?  Will I lose all of the settings for my home network?  Do I need to setup for additional networks somewhere.

After all the time I spent getting my home network setup, I really don't want to screw it up.  So I am hoping someone can explain to me exactly what I should do from here on out to get on other networks.  

Thank You
Doug

---

### Post by Austin_KW on 2007-03-30
You should be able to use command line to configure and bring the nic up on a new network. Write yourself a script for each network with the series of command's needed.

In general bring the interface down with ifconfig, configure the wireless with iwconfig and iwpriv and then bring the interface up with ifconfig or dhclient for a dhcp address.

The only gotcha might me the sta.dat file which I think is read when the driver starts. I dont use it so I am not sure if it might conflict with the iwconfig/iwpriv settings.

---

### Post by dougr on 2007-03-30
Ok, thanks for the bump in the right direction.  Hopefully someone will come along with a little more info on my specific situation.  I am going to see if I can maybe have multiple configs in that .dat file.  I think I remember reading you can.

---

### Post by Austin_KW on 2007-03-30
You might also look at rtutil the graphical utility [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/) which I think uses the sta.dat file to configure ralink wireless nics

---

### Post by dougr on 2007-03-30
oh cool, ill check that out...thanks a lot.

---

### Post by dougr on 2007-03-30
using rtutil I found somewhat of a solution.  Probably not a solution to some, but for me it works ok.

If I use rtutil I can connect to any other network that is either open, or encrypted with WEP(I have not tried WPA on another network, but I think it would be problematic).  When I am done with that network, I just bring the adapter down and up, and reset the DHCP, and it works fine, brings my home network right back up.  I setup a script to do all that automatically and now it's just a button in my toolbar.

For the next 2 years the networks(home/school) I use should be the same...and I can hope for a better solution for linux in 2 years :)

---

