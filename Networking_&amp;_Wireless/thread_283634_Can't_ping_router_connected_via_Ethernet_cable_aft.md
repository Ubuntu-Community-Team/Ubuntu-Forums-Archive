---
title: "Can't ping router connected via Ethernet cable after Edgy upgrade"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by eb_oesch on 2006-10-24
I had 5.10 running until recently (dual boot with XP) on my AMD64 system, but I did a reinstall with Edgy (6.10)(overwriting the old Linux partition), and now I can't reach the Internet from Linux. I can't ping the router at 192.168.1.1; I can't ping *anythhing* but localhost. The "network is unreachable" errors I get appear to fully describe my network status, and "ifup eth0" results in "no dhcpoffers received". Under 5.10, the Internet connection came up automatically, and under XP, it still does (I'm posting this from XP, after bouncing back and forth between Linux and XP a dozen times.)

My network card is a Realtek RTL81939/810x. My router is a Westell VersaLink 327W. I tried pppoeconf just in case, and then installed the patched version so pppoeconf actually ran, but I believe that was irrelevant and pointless, because I believe the router itself handles the authentication with DHCP.

Here's some ifconfig, dhclient eth0, and "networking restart" output. It's possible that my netmask is wrong, or that I need to statically set some routing or host settings or whatever. All I can say is that the automatically selected networking settings  did not work (this was a total reinstall, remember) and if any manual changes are needed, it was not obvious where they should happen. I would appreciate any help that you could provide.

root@boeschu: ifconfig                                                   
eth0      Link encap:Ethernet  HWaddr 00:13:D4:D4:E5:75  
          inet6 addr: fe80::213:d4ff:fed4:e575/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:90 (90.0 b)
          Interrupt:169 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18488 (18.0 KiB)  TX bytes:18488 (18.0 KiB)

root@boeschu:~# dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:d4:d4:e5:75
Sending on   LPF/eth0/00:13:d4:d4:e5:75
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@boeschu:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4657
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:d4:d4:e5:75
Sending on   LPF/eth0/00:13:d4:d4:e5:75
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Message from syslogd@boeschu at Tue Oct 24 11:49:56 2006 ...
boeschu kernel: [  116.893105] Disabling IRQ #169
Listening on LPF/eth0/00:13:d4:d4:e5:75
Sending on   LPF/eth0/00:13:d4:d4:e5:75
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'
Failed to bring up dsl-provider.

---

### Post by Jussi Kukkonen on 2006-10-24
That adapter works with the pegasus driver, doesn't it (I could be wrong)? Mine does too and the same thing happened -- the device is not recognised or something. A fix (or rather a workaround) was to use the last Dapper kernel instead of the Edgy default kernel.

Please add a comment/confirmation in [https://launchpad.net/distros/ubuntu/+bug/67347](https://launchpad.net/distros/ubuntu/+bug/67347) if the driver is Pegasus, the bug probably won't get looked at before it's confirmed...


EDIT: of course you won't have the old kernel installed on a new install of Edgy, so the work-around's not very usable for you... You'd have to install it from the Dapper repos, and you could break things doing that.

---

### Post by eb_oesch on 2006-10-24
> **Jussi Kukkonen said:**
> That adapter works with the pegasus driver, doesn't it (I could be wrong)? Mine does too and the same thing happened -- the device is not recognised or something. A fix (or rather a workaround) was to use the last Dapper kernel instead of the Edgy default kernel.

Thanks for your thoughts. It is a Pegasus driver, and given the totality of the failure, it does make sense to me to blame network adapter issues instead of the router. I will indicate in your bug report that I have confirmed it to the best of my knowledge.

---

### Post by eb_oesch on 2006-10-26
I fixed my problem; the solution was spelled out right in the dmesg logs -- add "irqpoll" to the Linux bootup options for  /boot/grub/menu.lst. So the default and single user bootup lines for Linux in my installation look like

kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro single irqpoll

where the "irqpoll" part is new.

(Warning -- ranting from here on out!) This issue would have been just a tiny speedbump for me if not for the new "quiet" bootup option being the default. The new install is so pseudo-friendly, it won't even tell you what it's not telling you! It may seem odd that an experienced Unix user could forget to try dmesg, but while I use Unix daily, I upgrade only rarely, and usually the dmesg text is visible during bootup anyhow. Normal OS installers, including those of other Unixes, earlier Ubuntu releases, and, yes, even Windows XP, show the most important errors and potential errors on screen and also direct users to key log files for additional details. So AFAICS Ubuntu's new see-no-evil install and bootup process, taken together as a system, have the worst on-screen diagnostics I have encountered. In an imperfect reality, where installs seldom function flawlessly off the bat, the lack of diagnostics, even if 90% of the messages are unimportant, just makes things worse. Anyhow, the distro as a whole looks good -- but it's always the broken parts that stick out.

---

