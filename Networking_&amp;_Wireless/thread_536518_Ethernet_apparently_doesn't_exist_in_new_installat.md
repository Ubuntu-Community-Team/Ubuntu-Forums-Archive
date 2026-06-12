---
title: "Ethernet apparently doesn't exist in new installation"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by nomenclature3000 on 2007-08-27
Dear Ubuntu Experts,

I just installed the amd64 build of 7.0.4 on a brand-new Core 2 Duo which -- who knows -- might have a bad ethernet socket. I have a DSL connection that goes to our DSL modem, then an ethernet cable goes from that to our trusty router, and then I've got an ethernet cable plugged into that. When the business end of that ethernet cable is plugged into my Windows or Gentoo machine, I get a network connection. When I plug it into my new Ubuntu machine and then access System->Administration->Network, the only connection that shows up is "Modem connection". I cannot ping my router; I get "connect: Network is unreachable". When I type "ifconfig", I am greeted with the word "lo" followed by some indented inscrutable text. The word "eth0" doesn't appear in response to this command. I am wondering if this is a software or a hardware problem. Can one of you nice folks please give me a clue about determining which it is?

Thank you very much,
Adam

---

### Post by nomenclature3000 on 2007-08-27
Some more information:

When I enter the BIOS SETUP UTILITY and go to "Onboard Devices Configuration", I see that "Onboard PCIEX 10/100Mb LAN" is marked [Enabled]. This makes me think that maybe there is not a problem with my hardware, though I'm still not completely sure.

A few more data points:

[LIST]
[*] As far as I know, my router assigns IP addresses to the machines that connect to it.
[*] My /etc/network/interfaces file contains the following text: "auto eth0\niface eth0 inet dhcp
[*] When I execute /etc/init.d/networking restart I obtain a result that contains the following line repeated three times: "eth0: ERROR while getting interface flags: No such device". It also says "SIOCSIFADOR: No such device" and "Bind socket to interface: No such device".
[/LIST]

I have read through all recent posts that contain the string "ethernet" and none seem to help with my problem. Any advice whatsoever is appreciated!

Thanks again!
Adam

---

### Post by nomenclature3000 on 2007-08-27
New information: I plugged in a wireless networking card, and now I seem closer to having networking. I believe that I do have a hardware problem with the ethernet jack. I am wondering why I didn't have to install the wireless card; at least it should have required the driver. Unfortunately now when I open Network Settings, that window freezes. I'll try to keep hacking away at this problem to see if I can fix it. Apologies for writing so much here.

---

### Post by wirelessmonkey on 2007-08-28
You may need a driver for your ethernet card.. ubuntu server was missing the realtek gigabit nic drivers of my ati motherboard.

---

### Post by nomenclature3000 on 2007-08-28
Thank you very much for the tip! I actually got the network connection working from the wireless card -- deleting lo from the interfaces file is what caused the Network dialog to hang, apparently. I would like to get the ethernet jack working also, of course.

---

