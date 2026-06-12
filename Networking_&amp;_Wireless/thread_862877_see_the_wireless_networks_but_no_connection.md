---
title: "see the wireless networks but no connection"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by Rastus on 2008-07-17
Hi,
New user here.
I went out and bought a brand new Dell 1525 inspiron with a Broadcom 4310 wireless adapter. I took it out of the box and installed ubuntu 8.04 from CD.  Initially, there was no wireless at all in the network manager but after installing about 100 updates (with a wired internet connection that worked fine) and viola, the wireless networks showed up in the network manager.

Then, they would identify the network and show the strength.  I choose connect and then the dialog comes up to ask for the WEP key, it thinks for a while and then the dialog comes back up asking for the WEP key.  No connection.

This was initially using the built-in non-ubuntu drivers.  So I did some research and read about ndiswrapper so I took all afternoon and got that installed with the driver file bcmwl5.  Reboot and the same thing happens.

I tried to do the manual connection but the command "sudo iwconfig <interface> key HEX_KEY" returns a message saying there is a bad argument (even with the s: for ASCII)so I can't get any farther along that diagnostic path. 

 I also saw a suggestion to "updating to svn 0.7 network manager" but I couldn't find the thread in the Community Cafe.

I am somewhat at a loss and I would appreciate any guidance that anyone can offer.

Thanks

---

### Post by lincoln32 on 2008-07-18
I have a 1507 try system administration hardware drivers then broadcom and reinstall and look for a pop up that asks to install bfwcutter and check yes and reboot. I missed the window a few times ti I went slow and read the window to down load the addl. files then it worked great

---

### Post by halln on 2008-07-18
We had the same problem with dell 1525. I've been battling for some time but I finally made it to work by right clicking the wireless signal icon (panel) and click edit wireless then remove your network, after that left click the wireless icon select your network, enter your wireless security and try your connection again. If still you couldn't connect, try to power off your modem by totally unplugging it, then back on again. You may or may not need to enter your network again. This made me shout for joy after nearly a week battling it. You can check my post here. Hope this helps.

---

### Post by Rastus on 2008-07-18
OK, I am not sure why but when I turned off the roaming mode and did a manual setup it all connected immediately and everything worked.  Interesting.  Hope this helps anyone else who is experiencing problems.

---

