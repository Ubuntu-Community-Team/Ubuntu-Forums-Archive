---
title: "wireless, network manager, and default keyring"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by haloedrain on 2006-09-09
Hi, all.  I'm new to ubuntu and to linux generally.  Just installed ubuntu on my laptop and I'm loving it so far, but I can't get the wireless card to work consistently.

I've got a Dell Inspiron B130--full specs are basically the same as on [this page]("http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&l=en&oc=iB130S1&s=dhs").  The card is a Dell Wireless 1370 WLAN MiniPCI Card.

I've got ndiswrapper, and I've got the current driver correctly installed with it--it recognizes that the hardware is there, etc.  I also have the network manager tool, which works fine with the wired connection and can (kinda) recognize available networks.

I have gotten the wireless connection working several times, but most of the time it doesn't work.

Sometimes network manager won't see the wireless network in a room that I know has it--other people can get onto the network in those locations with no problems.  If I go to the network manager thingy and select "connect to other network" and enter the name, WEP, etc. etc. for the network it will actually connect maybe 10% of the time, and if it does it asks for a new password for the default keyring.

Sometimes network manager will recognize the wireless network that I can access and try to connect to it automatically and ask for the default keyring password, which I will enter and it seems to accept it.  When this happens it *never* manages to establish a connection, and if I then attempt to use the "connect to other network" trick as above it will continue to fail until I shut down the computer and restart it and hope it can't see the network so I can try the trick above.

A potentially related problem: the network manager thingy can't see all available networks all the time and it will claim that all the networks it can see have full signal strength, even when I'm pretty sure that's not true.

My guesses to what might be going wrong:
-the driver is not fully compatible even with ndiswrapper - this would explain not being able to see networks and showing full strength for all of them, but not necessarily the rest
-there is a problem getting things into and out of the keyring

Does anyone have any suggestions how to fix this so my network card works most of the time?  This really is a big problem for me, and if I can't get it fixed I may have to go back to windows.

---

