---
title: "Netgear WG111T USB Problems"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Spike_UK on 2008-04-29
Morning Peeps

I am currently having a problem with the wireless network on 8.04 and the WG111T USB Dongle. I had it installed with ndiswrapper on 7.10 and everything was running smoothly. I decided to do a complete re-install and upgrade to 8.04. Ndiswrapper shows the WG111T driver and USB dongle installed however it is not showing up in the network window. I however did get it to show in the network window once however it would not connect to the network and rejected my password and would not connect. 

I decided to revert back to 7.10 and do a upgrade from there. 7.10 was running perfect and when I upgraded it stopped working. When I shut down I keep getting messages that network manager has bugs etc etc. 

I have followed all the instructions on the forums to getting the Netgear WG111T to work on 8.04 but to no avail. Does anyone know why it won’t work on 8.04 and/or is there a serious bug in Network Manager in 8.04??

Thanks in Advance.

---

### Post by fjrreseda on 2008-05-02
I'm having the exact same problem.  Is there a bug in ndiswrapper or can it be a bug in the newer kernel?

In Gutsy, I was also able to get the Netgear WG111T working fine.  In Hardy, I can connect to the network, but I can not get any data to transfer.  The network manager shows I'm connected, and the hardware looks like it's working.  However, when I try connecting to the internet, nothing happens.

When I check the drivers, netwg11t.inf driver shows the hardware has been detected.  The athfmwdl.inf driver shows the hardware as not being detected.  This is the same configuration of drivers that I had in Gutsy!  I've gotten so frustrated that I have given up and will now go back to using Gutsy.

For now, I'll refrain from upgrading to Hardy again, until there is a permanent fix for the WG111T.  I've read in this link:

[https://help.ubuntu.com/community/WifiDocs/Device/WG111T](https://help.ubuntu.com/community/WifiDocs/Device/WG111T)

that you can get the WG111T working in hardy, but it doesn't look like a permanent solution.

Unless Ubuntu can come up with a definitive list of products that are guaranteed to work, I won't buy a different wireless adapter.  I don't mind spending some money on hardware to get the wireless working, but I need to be guaranteed that the hardware will work.

---

