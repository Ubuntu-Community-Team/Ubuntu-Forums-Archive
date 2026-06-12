---
title: "Windows to Linux Internet Sharing"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by Shai Hulud on 2008-01-03
Hello, i'm fighting for some time, and i don't have any google results to try, so here i am :(

Here is my setup: Internet -> Windows XP desktop with 2 lan cards -> Slackware laptop (when there was Ubuntu on it, the problem was the same)

So on my Win machine, everything is set up. The ICS is runnig, the second card has the 192.168.0.1 IP, and the hand icon (to show that it is shared) on the internet lancard is there.

When i plug the cable in the laptop (it is a crossover cable), the "two-computers-icon-in-the-tray", for the second card lights up, saying "Local Area Connection 2 is now connected / Speed: 100.0 Mbps"

Then i run "dhclient" on the linux client, and the result is:

DHCPACK from 192.168.0.1
bound to 192.168.0.123

Well, everything should be working fine. But it isn't... :(

When i try to ping 192.168.0.1 from the linux machine, all packets are lost. The same thing happens when i try to ping 192.168.0.123 from the windows machine - Request timed out.

I've tried to setup the linux machine trough netsetup, but it is the same... No ping. I've tried DHCP, i've tried to set manually the settings for eth0, but nothing works.

The weirdest thing is, that when i plug my internet cable (it's a LAN ISP) in the laptop lancard and change my MAC address (the ISP uses MAC locks), i get my settings trough DHCP and everything is just fine.

But when i try to do a simple LAN between the two machines - it doesn't work. The cable is tested on two cable testers, and is working fine, so the problem isn't in the cable between the two machines.

So... if someone can think of something, i'll be very thankful. :)

P. S. I'm running Slackware now, but when i had Ubuntu on the laptop, the problem was the same. So it's something general, not distro related.

---

### Post by gazj on 2008-01-03
its so long since using xp, and have not got a window installlation about so this could be wrong
for get ics in the sense that you are trying

on xp go to control panel and open up the page that shows your network interfaces

i believe if you right click your main network adaptor you should get the option of bridge, can't remember the exact details, but it should ask for the second network card to bridge too.  This should join them through.

I haven't done this for a long time so please don't shoot me down in flames too much if this is all wrong.

Thanks

Gary

---

### Post by Shai Hulud on 2008-01-04
No, it's not working that way. :(

---

### Post by agamalce on 2008-01-17
i am not sure if that is gonna help you or not if you want to make a bridge on the xp go to control panel as gazj said then go to network connections select the 2 interfaces and right click you will see the bridge option click and wait a while the enter the ip's to that bridge

---

