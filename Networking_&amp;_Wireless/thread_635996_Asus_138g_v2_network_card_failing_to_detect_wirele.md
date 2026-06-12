---
title: "Asus 138g v2 network card failing to detect wireless network in Kubuntu 7.10"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by sherrife on 2007-12-09
Hi,

I've installed the Asus 138g v2 network card ontu Kubuntu 7.10 using the howto on this site (thanks for that!) and that's correctly showing up in the network configuration screen along with an inbuilt LAN connection. 3 things:

a) The LAN card won't let itself be disabled, as in every time i do it, and return to the manual config settings in the GUI it just enables itself again. Not sure if this has anything to do with the problem, but it's wierd.

b) The wireless card is showing up on ifconfig screens, showing up in the gui manual config screen, but not showing up when i right click on the icon in the taskbar. Furthermore, when I go into "show connections" nothing comes up, signifying to me somehow the wireless device isn't being read properly? But I'm a total newb and that might be normal.

c) The computer is totally failing to sense the wireless network we've set up at home, that's running running off a Belkin f5d7230-4 router. Obviously, this is my main problem! When i set it to auto config of the wireless network it comes up with a wierd ip that has nothing to do with any of the ip's on my network, and when i do it manually nothing happens.

Oh, I can ping the "WAN IP", not sure if that's relevant at all.

Oh, the light on the stupid network card isn't lighting up.

Oh, I've read around the forums, tried iwconfig, and the wireless adapter comes up. I've checked the driver, and it says bcmw5l.inf is installed and Bcm43xx is the backup. I've blacklisted the backup as far as I can tell.

I tried sudo dhclient, and it tries to send and/or detect something @ 255.255.255.255, is that meant to be the subnet mask? Because it's finding nothing, and my actual subnet mask is 255.255.255.0 so not sure if I have to change it in the command line, or how.

To repeat what I said earlier, the light on the back of the modem is not turning on, ever.

ARGH!

---

### Post by sherrife on 2007-12-10
I'm a bit disappointed that no one is able to help :(  Anyway, I've totally exhausted the help on all these sites, and I still can't get the light to come on!!!

Also I have been consistently unable to change the subnet mask.

I've used "sudo ifconfig eth2 192.2.4 netmask 255.255.255.0" but it still checks 255.255.255.255 when i run "sudo eth2 dhclient"...

HELP please!

---

### Post by sherrife on 2007-12-11
I guess I'll just let this thread die, continue to use windows (boooo) and wait for someone else to have a similar problem...

---

### Post by Peffse on 2007-12-31
Instead of making a new thread, I'll bump this one, since I'm having the same exact problem.

BUT, I'm using an RT2500 wireless, and Kubuntu 7.04 (since I can't get online to update it).

Like I said, I'm having the same problem.... no light, stange IPs, not detecting my network, a NIC card re-enabling itself, oh... and I suppose it's good to mention that the NIC card doesn't have lights either... despite both the NIC and wirless lighting up on boot and in BIOS. 

Also, the card is confirmed good, as I just pulled it out of a working machine.

---

