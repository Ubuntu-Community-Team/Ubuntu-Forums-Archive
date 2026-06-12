---
title: "losing connection to the web"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by itp77 on 2007-04-16
Hello everyone,first of all,I'm new to Ubuntu,but not to the PC world...
after installing Ubuntu 6.10,and crashing it,and reinstalling it,I've installed the latest 7.04 beta.
everything's going great,exept for one annoying problem...
after the installation,i've ran pppoeconf,to configure my ADSL connection.
in order to connect to the net,I've got to follow this procedure:
sudo pon dsl-provider
sudo poff dsl-provider
and then again sudo pon dsl-provider

only then I can connect to the net.

and the weird part of it all,is,that while I can't surf the net via firefox,azureus does work (although very slowly...)

I've searched the web for an aswer but without any luck.

Please HELP](*,) 

P.S.
I've blacklisted IPv6 and (when I get the damn thing to work) I surf a lot faster.

---

### Post by nautilus on 2007-04-16
if you keep breaking your networking by disabling standard protocols, your issues will only amplify...

anyway, the key here is to know what 'pon' does, and what it does differently the second time around to make it work.

if you could provide some output it would help more than a little bit to know what the issue is.

---

### Post by itp77 on 2007-04-16
this are the output from the terminal:
itp2177@itp2177-desktop:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
itp2177@itp2177-desktop:~$ plog
Apr 16 20:31:37 itp2177-desktop pppd[28776]: Plugin rp-pppoe.so loaded.
Apr 16 20:31:38 itp2177-desktop pppd[28782]: pppd 2.4.4 started by root, uid 0
itp2177@itp2177-desktop:~$ sudo poff dsl-provider
itp2177@itp2177-desktop:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
itp2177@itp2177-desktop:~$ plog
Apr 16 20:31:58 itp2177-desktop pppd[28829]: Using interface ppp0
Apr 16 20:31:58 itp2177-desktop pppd[28829]: Connect: ppp0 <--> eth0
Apr 16 20:32:00 itp2177-desktop pppd[28829]: PAP authentication succeeded
Apr 16 20:32:00 itp2177-desktop pppd[28829]: peer from calling number 00:02:3B:02:97:71 authorized
Apr 16 20:32:00 itp2177-desktop pppd[28829]: replacing old default route to eth0 [10.0.0.138]
Apr 16 20:32:00 itp2177-desktop pppd[28829]: Cannot determine ethernet address for proxy ARP
Apr 16 20:32:00 itp2177-desktop pppd[28829]: local  IP address 217.132.26.152
Apr 16 20:32:00 itp2177-desktop pppd[28829]: remote IP address 212.143.208.133
Apr 16 20:32:00 itp2177-desktop pppd[28829]: primary   DNS address 212.143.212.143
Apr 16 20:32:00 itp2177-desktop pppd[28829]: secondary DNS address 194.90.1.5

and only then I can connect...any ideas?

and I also get this a lot:
Apr 17 00:37:30 itp2177-desktop pppd[6791]: Unable to complete PPPoE Discovery
Apr 17 00:38:35 itp2177-desktop pppd[6791]: Timeout waiting for PADS packets
Apr 17 00:38:35 itp2177-desktop pppd[6791]: Unable to complete PPPoE Discovery
Apr 17 00:39:40 itp2177-desktop pppd[6791]: Timeout waiting for PADS packets
Apr 17 00:39:40 itp2177-desktop pppd[6791]: Unable to complete PPPoE Discovery

---

