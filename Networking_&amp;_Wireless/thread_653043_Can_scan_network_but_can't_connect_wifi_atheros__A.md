---
title: "Can scan network but can't connect wifi atheros  AR5006EG"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by tictacman on 2007-12-29
On Gutsy amd64  I tried to run a built in wireless card on my Toshiba Satellia pro a210-11p.  The wireless is an atheros.  At first the restricted atheros driver was running but failed to pick my card up when typing iwconfig command in the terminal.  I disabled the driver, lspci shows the wifi to be atheros  AR5006EG, so I installed ndiswrapper and downloaded the windows 64bit driver xp64-5.3.0.56-whql.  Which seemed to run fine in ndiswrapper.

I can scan the network but can't connect even with encryption turned off.  

I wandering about two things.

 ifconfig says:

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Memory:cfcf0000-cfd00000 


shouldn't there be a mac address instead of 00:00:00.....?

On restarting the network in the terminal I get 

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 7428
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:38:3f:0b:ce
Sending on   LPF/eth0/00:1b:38:3f:0b:ce
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 7490
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:38:3f:0b:ce
Sending on   LPF/eth0/00:1b:38:3f:0b:ce
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 41194 seconds.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

why is it repeteadly warning of an existing pid?

Hoping that answers to these questions might help me figure out what's going wrong here:)

---

### Post by tictacman on 2007-12-29
I've also tried removing ndiswrapper and downloading the latest madwifi drivers.  The card then completely disappears from ifconfig.  In dmesg the following is written:

33.697337] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   33.697347] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   33.721707] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   33.722629] ACPI: PCI interrupt for device 0000:04:00.0 disabled

---

### Post by tictacman on 2007-12-30
I notice this seems to be a bit of an issue as there is a support ticket raised on the madwifi site:

[http://madwifi.org/ticket/859](http://madwifi.org/ticket/859)

---

### Post by tictacman on 2007-12-30
ok thanks guys. I think i'm giving up on this one. Clearly this system isn't compatible with linux, probably just a bit new.  I'll probably try again in six months time.

---

### Post by swampdweller on 2008-03-04
For what it's worth (at this late date) I had the same experience with
AR5006EG under Gutsy 64, however it works perfectly for me
(with ndiswrapper) under Gutsy 32 (and also Hardy Alpha 4 32).
If your alternative is to give up on Ubuntu (even Linux) altogether,
surely it is better to merely give up on 64 bits for now.

---

### Post by kiisu on 2008-03-13
If your computer is telling you its a ar5006 it might actually be the ar5007 .. I spent weeks working on my wireless before I read that somewhere else ...
search for a thread on these forums for the ar5007, when I tried that I finally got my wifi working!

---

### Post by scottro on 2008-03-13
There are several threads on the 5007EG.  On 64 bit, it seems that your only shot right now is with ndiswrapper.  (I wasn't successful, but others were.)

I have a page that covers that card (among other things) heavily based upon advice from these forums.  It also has a link to a thread on these forums where someone explained how he got it working on 64 bit.  

My page is at [http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007)

The thread on getting it working on 64 bit is at

[http://ubuntuforums.org/showthread.php?p=4463071](http://ubuntuforums.org/showthread.php?p=4463071)

Good luck.  It does make one want to call the people at Atheros, as well as the laptop manufacturers who use this card, bad names.  I confess, I believe at one point I said, "Those doody heads!"

---

