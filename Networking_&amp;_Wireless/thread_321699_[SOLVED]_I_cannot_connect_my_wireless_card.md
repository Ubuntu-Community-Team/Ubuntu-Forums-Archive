---
title: "[SOLVED] I cannot connect my wireless card"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by pappo on 2006-12-19
--------------------------------------------------------------------------------

I am using Kubuntu 6.10.
I installed ndiswrapper and was able to enable and activate my wireless card.
I did "sudo iwlist eth0 scan" and can see my router in the list.
I used System settings --> Network settings and configured the card for DHCP, with my essid and wep encryption key.
It goes off and says it is activating, but when I check "ifconfig eth0", there is no IP assigned.
I am not seeing any errors in the log files, it just is not connecting.

---

### Post by pappo on 2006-12-19
I got it working, but I had to use Ubuntu instead of Kubuntu.
I couldn't get wifi-radar to load because it needed python-gtk2 and then the dependencies just kept adding on in Kubuntu.
So I just loaded Ubuntu 6.10, installed the ndiswrapper files:
ndiswrapper-common version 1.18
ndiswrapper-utils version 1.1-5
ndiswrapper-utils-1.1 version 1.1-5
ndiswrapper-utils-1.8

Then I followed the Dapper wireless networking Howto and used ndiswrapper to load my firmware, modprobe to add ndiswrapper to my kernel.
Then, since Gnome desktop was part of Ubuntu, I was able to load and run wifi-radar and 'VOILA' I was connected.
In fact I am sending this reply to you from Firefox, running on my new Ubuntu installation.
Linux life is good....
Edit/Delete Message

---

### Post by BlkPhoenix on 2006-12-20
I too am using Kubuntu 6.10 and I can't get my wireless card to work.  I followed the instructions on many threads on this forum and it still doesn't work.  I installed ndiswrapper and all the assorted dependencies however I still can't connect to my router.  When I look at the network settings I can see that there is a wireless interface but it's not getting an IP address.  Puhleez help me.

---

### Post by pappo on 2006-12-20
I got it working, but I had to use Ubuntu instead of Kubuntu.
I couldn't get wifi-radar to load because it needed python-gtk2 and then the dependencies just kept adding on in Kubuntu.
So I just loaded Ubuntu 6.10, installed the ndiswrapper files:
ndiswrapper-common version 1.18
ndiswrapper-utils version 1.1-5
ndiswrapper-utils-1.1 version 1.1-5
ndiswrapper-utils-1.8

Then I followed the Dapper wireless networking Howto and used ndiswrapper to load my firmware, modprobe to add ndiswrapper to my kernel.
Then, since Gnome desktop was part of Ubuntu, I was able to load and run wifi-radar and 'VOILA' I was connected.
In fact I am sending this reply to you from Firefox, running on my new Ubuntu installation.
Linux life is good....

---

