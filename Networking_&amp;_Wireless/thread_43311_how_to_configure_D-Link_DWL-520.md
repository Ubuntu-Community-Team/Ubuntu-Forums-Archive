---
title: "how to configure D-Link DWL-520"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by Simplimus on 2005-06-21
I bought a DWL-520 today and am seeking to install it. I configured my wired networkcard during installation, but now I'm stuck. I have no idea where to start. I'm not new to Ubuntu, but I never had to do something like this. I googled on this problem and found that the card is 100% supported and supposed to work out of the box.

lspci -v told me the following:

0000:02:03.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc: Unknown device 3a13
        Flags: medium devsel, IRQ 19
        Memory at fe7f0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

Can anyone help me?

---

### Post by Lunde on 2005-06-21
[QUOTE=Simplimus]I bought a DWL-520 today and am seeking to install it. I configured my wired networkcard during installation, but now I'm stuck. I have no idea where to start. I'm not new to Ubuntu, but I never had to do something like this. I googled on this problem and found that the card is 100% supported and supposed to work out of the box.

lspci -v told me the following:

0000:02:03.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc: Unknown device 3a13
        Flags: medium devsel, IRQ 19
        Memory at fe7f0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

Can anyone help me?[/QUOTE]

your card is most likely a** ACX111** chipset, I had the same problem. Ubuntu tries to give the card the drivers for the **ATH100** chipset.

**Try this:**
[http://www.houseofcraig.net/old_acx100_howto.php](http://www.houseofcraig.net/old_acx100_howto.php)
[B]
Here's some more reading:[/B]
[http://sourceforge.net/forum/forum.php?forum_id=257272](http://sourceforge.net/forum/forum.php?forum_id=257272)

---

### Post by Lunde on 2005-06-21
[QUOTE=Lunde]
**Try this:**
[http://www.houseofcraig.net/old_acx100_howto.php](http://www.houseofcraig.net/old_acx100_howto.php)
[/QUOTE]

**Sorry I sent you the wrong link, here's the correct new version:**

[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

---

### Post by Simplimus on 2005-06-21
thanks, Ill give it a try

---

### Post by Simplimus on 2005-06-21
Im currently giving my best on this but I ran into a problem. In the text it states that:
> That listing is taken from running lspci -n on my ThinkPad 600 with my SMC 2435w CardBus card plugged in. Out of those 9 lines listed, we're only interested in that last one:

05:00.0 Class 0280: 104c:8400

because it contains one of the 3 combinations listed below at it's end:

    * 104c:8400 (acx100 CardBus)
    * 104c:8401 (acx100 PCI)
    * 104c:9066 (acx111 Cardbus/PCI) 

Well, my pc showed this:> /etc/network # lspci -n
0000:00:00.0 0600: 8086:2578 (rev 02)
0000:00:01.0 0604: 8086:2579 (rev 02)
0000:00:1d.0 0c03: 8086:24d2 (rev 02)
0000:00:1d.1 0c03: 8086:24d4 (rev 02)
0000:00:1d.2 0c03: 8086:24d7 (rev 02)
0000:00:1d.3 0c03: 8086:24de (rev 02)
0000:00:1d.7 0c03: 8086:24dd (rev 02)
0000:00:1e.0 0604: 8086:244e (rev c2)
0000:00:1f.0 0601: 8086:24d0 (rev 02)
0000:00:1f.1 0101: 8086:24db (rev 02)
0000:00:1f.2 0101: 8086:24d1 (rev 02)
0000:00:1f.3 0c05: 8086:24d3 (rev 02)
0000:01:00.0 0300: 1002:4e48
0000:01:00.1 0380: 1002:4e68
0000:02:01.0 0401: 1102:0004 (rev 04)
0000:02:01.2 0c00: 1102:4001 (rev 04)
0000:02:02.0 0200: 10b7:9055 (rev 30)
0000:02:03.0 0200: 168c:0013 (rev 01)
0000:02:08.0 0200: 8086:1050 (rev 02) 
of which my card is this one
0000:02:03.0 0200: 168c:0013 (rev 01)

So, Im not sure if this article applies to my card.

In fact, I found out that my card is based on a different chip, manufactured by Atheros, the AR5212. The text however is made for Texas Instruments' acx100 or acx111.
> 0000:02:03.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: D-Link System Inc: Unknown device 3a13
        Flags: medium devsel, IRQ 19
        Memory at fe7f0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

I believe the right driver project might be madwifi

---

### Post by Lunde on 2005-06-21
[QUOTE=Simplimus]Im currently giving my best on this but I ran into a problem. In the text it states that:
 

Well, my pc showed this: 
of which my card is this one
0000:02:03.0 0200: 168c:0013 (rev 01)

So, Im not sure if this article applies to my card.

In fact, I found out that my card is based on a different chip, manufactured by Atheros, the AR5212. The text however is made for Texas Instruments' acx100 or acx111.


I believe the right driver project might be madwifi[/QUOTE]

I'm sure you're right, and you sure have this link. Sorry for my lack of knowledge I thought the chipset was the same as for DWL-520+ witch I have

[http://madwifiwiki.thewebhost.de/wiki/MadWifi](http://madwifiwiki.thewebhost.de/wiki/MadWifi)

---

### Post by Simplimus on 2005-06-22
Alright, I downloaded a cvs snapshot of madwifi, but how do I find out, wether I meet these conditions>     * wireless extensions version 14 or later (version 16 is preferred)
    * target kernel needs to have sysctl support turned on
    * crypto API support turned on with HMAC and MD5, if you want to use the 802.1x authenticator
I never compiled a kernel.

---

### Post by Lunde on 2005-06-22
[QUOTE=Simplimus]Alright, I downloaded a cvs snapshot of madwifi, but how do I find out, wether I meet these conditions
I never compiled a kernel.[/QUOTE]

Here's a Howto for kompiling it for ubuntu:
[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)

Hope this helps

---

### Post by Simplimus on 2005-06-26
I did what it said there, but dmesg now gives me this
> ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212)
ath_rate_onoe: 1.0
ath_pci: disagrees about version of symbol ath_rate_tx_complete
ath_pci: Unknown symbol ath_rate_tx_complete
ath_pci: disagrees about version of symbol _ath_hal_attach
ath_pci: Unknown symbol _ath_hal_attach
ath_pci: disagrees about version of symbol ath_rate_attach
ath_pci: Unknown symbol ath_rate_attach
ath_pci: disagrees about version of symbol ath_rate_newassoc
ath_pci: Unknown symbol ath_rate_newassoc
ath_pci: disagrees about version of symbol ath_hal_computetxtime
ath_pci: Unknown symbol ath_hal_computetxtime
ath_pci: disagrees about version of symbol ath_hal_detach
ath_pci: Unknown symbol ath_hal_detach
ath_pci: disagrees about version of symbol ath_rate_node_copy
ath_pci: Unknown symbol ath_rate_node_copy
ath_pci: disagrees about version of symbol ath_rate_node_cleanup
ath_pci: Unknown symbol ath_rate_node_cleanup
ath_pci: disagrees about version of symbol ath_rate_node_init
ath_pci: Unknown symbol ath_rate_node_init
ath_pci: disagrees about version of symbol ath_rate_findrate
ath_pci: Unknown symbol ath_rate_findrate
ath_pci: disagrees about version of symbol ath_hal_init_channels
ath_pci: Unknown symbol ath_hal_init_channels
ath_pci: disagrees about version of symbol ath_rate_newstate
ath_pci: Unknown symbol ath_rate_newstate
ath_pci: disagrees about version of symbol ath_rate_setupxtxdesc
ath_pci: Unknown symbol ath_rate_setupxtxdesc
ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
ath_pci: Unknown symbol ath_hal_getwirelessmodes

I guess it may be because I had the problem that, unlike in the text, here the directory /usr/src/linux-2.6.10-5-386 did not exist, so I changed it to /usr/src/linux-headers-2.6.10-5-386, which did exist

---

### Post by Lunde on 2005-06-26
> **Simplimus]I did what it said there, but dmesg now gives me this


I guess it may be because I had the problem that, unlike in the text, here the directory /usr/src/linux-2.6.10-5-386 did not exist, so I changed it to /usr/src/linux-headers-2.6.10-5-386, which did exist[/QUOTE]

I think that should be OK.. Does it work? Are you able to set any settings through 

$ iwconfig

what is the output from iwconfig?

I'm not sure what this fixes, but it was posted a bit further down in the howto.
[QUOTE=rlklee]Fixed the problem: 

Everyone following Elvis' instructions (which are tip-top) should make sure to uninstall the linux-restricted madwifi package (using synaptic said:**
> 

Here's some more info that might help

[QUOTE=IcemanV9]Your info does help me to resolve the problem with my new cardbus adapter, D-Link DWL-G650.

Here's what I did:

wget [http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz](http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz)
sudo apt-get install build-essential (only if you don't have it)
sudo apt-get install linux-headers-(uname -r) (again, only if you don't have it)
sudo apt-get install sharutils

tar xvzf madwifi-cvs-current.tar.gz
cd madwifi
KERNELPATH=/usr/src/linux-headers-(uname -r); export KERNELPATH
KERNELRELEASE=(uname -r); export KERNELRELEASE
sudo make
sudo make install

sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko.orig
sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko.orig
sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko.orig

sudo cp /lib/modules/2.6.10-5-686/net/ath_rate_onoe.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko
sudo cp /lib/modules/2.6.10-5-686/net/ath_hal.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko
sudo cp /lib/modules/2.6.10-5-686/net/ath_pci.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko

reboot (leave your cardbus in the slot)

when boot up, it will recongize the cardbus adapter (without an error message)!

To TEST ath0, I just used some commands from jaykay's instruction. AND, it works great.

---

### Post by Simplimus on 2005-06-27
iwconfig gives me > mk@simplimus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

---

### Post by Simplimus on 2005-06-27
I did that other thing and now iwconfig tells me this
> lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:0 kb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions. 
so what do I do now, the router is transmitting on channel 6 in open system mode with WEP
> root@simplimus:/home/mk # iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ath0      Interface doesn't support scanning : Invalid argument

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

I also wonder what that sit0 is....

---

### Post by Lunde on 2005-06-27
[QUOTE=Simplimus]I did that other thing and now iwconfig tells me this
 
so what do I do now, the router is transmitting on channel 6 in open system mode with WEP


I also wonder what that sit0 is....[/QUOTE]

Are you sure your supposed to use channel 6 not channel 11?

OK you need to insert the ESSID and WEPkey to be able to connect to the access point

$ iwconfig ath0 essid the_name_of_your_accesspoint
$ iwconfig ath0 key your_wep_key
$ iwconfig ath0 channel 11 

Channel 11 is the most used by accesspoints, you might have another channel on yours

If you use dhcp from your access point, try:

$ dhclient ath0

If you now got a dhcp address we know yur configuration is OK. If not check iwconfig and see if it found the hardware address of your accesspoint / mac address at least.

---

### Post by Simplimus on 2005-06-27
Looks great> root@simplimus:/home/mk # dhclient
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth1/00:07:e9:47:87:e8
Sending on   LPF/eth1/00:07:e9:47:87:e8
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/ath0/00:11:95:bb:4d:10
Sending on   LPF/ath0/00:11:95:bb:4d:10
Listening on LPF/eth0/00:10:5a:a5:a0:df
Sending on   LPF/eth0/00:10:5a:a5:a0:df
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.101 -- renewal in 267543 seconds. 
looks like I got an adress

---

### Post by Lunde on 2005-06-27
[QUOTE=Simplimus]Looks great 
looks like I got an adress[/QUOTE]

OK I connect with a script specially made for the acx111 chipset, so I'm not sure how it works for you from now. Are you able to access the network? Are you still connected after a reboot? If not maybe it will help setting the connection in:

System -> Administratoin -> Networking

---

### Post by Simplimus on 2005-06-27
No, I am not able to access the network and no, after a reboot it's all gone

what do you mean by System -> Administratoin -> Networking
I am using Kubuntu, is there a tool for gnome?
can I change to gnome and what do I have to install?

---

### Post by Lunde on 2005-06-27
[QUOTE=Simplimus]No, I am not able to access the network and no, after a reboot it's all gone

what do you mean by System -> Administratoin -> Networking
I am using Kubuntu, is there a tool for gnome?
can I change to gnome and what do I have to install?[/QUOTE]
 Sorry I assumed you were on Gnome, yes it's a gnome tool. There should be similuar for KDE

Maybe there are something here that helps:
[http://www.linuxquestions.org/questions/archive/63/2005/05/3/322053](http://www.linuxquestions.org/questions/archive/63/2005/05/3/322053)

Maybe this is something for you
[http://kifi.staticmethod.net/](http://kifi.staticmethod.net/)

I have to go for one hour but I can probably sort you out after if you can't find a solution in the above links

---

### Post by Lunde on 2005-06-27
There is a howto here that may hep you, this is for MadWifi which also supports your card. 

Compatibility list:
[http://madwifi.sourceforge.net/dokuwiki/doku.php?id=compatibility_list](http://madwifi.sourceforge.net/dokuwiki/doku.php?id=compatibility_list)

Atheros AR5212 Madwifi HowTo
[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)

---

### Post by Simplimus on 2005-06-30
well, I dont really know what did the trick, but Im on air right now. However, I still have to do the> iwconfig ath0 channel 6
iwconfig ath0 key s:xxxxxxxxx 
how can I automate this?
And I have to dhclient about every 3 minutes to stay online, otherwise I lose my connection. 
Edit: This is really starting to bug me big time

---

### Post by Lunde on 2005-06-30
[QUOTE=Simplimus]well, I dont really know what did the trick, but Im on air right now. However, I still have to do the 
how can I automate this?
And I have to dhclient about every 3 minutes to stay online, otherwise I lose my connection. 
Edit: This is really starting to bug me big time[/QUOTE]
 OK.. Congratulations:

I think this might help:
[http://www.mybizguard.com/modules/wfsection/print.php?articleid=11](http://www.mybizguard.com/modules/wfsection/print.php?articleid=11)

This will guide you through setting up a automated start script for your device. you can probably skip the last steps of making a bridge to your other network if you don't have it.

Alernatly you can set a static ip if there's any problems with the DHCP lease

---

### Post by Simplimus on 2005-06-30
My router log tells me this
Jun/30/2005 21:42:39 	DHCP lease IP 192.168.0.100 to unknown			00-11-95-BB-xx-xx
Why does it say "unknown"?
The other two in the network using windows machines have their network name listed there.

Well I can access the local network  anytime, just not the internet. I have to re-dhclient to get access.

---

### Post by Lunde on 2005-06-30
[QUOTE=Lunde]OK.. Congratulations:

I think this might help:
[http://www.mybizguard.com/modules/wfsection/print.php?articleid=11](http://www.mybizguard.com/modules/wfsection/print.php?articleid=11)

This will guide you through setting up a automated start script for your device. you can probably skip the last steps of making a bridge to your other network if you don't have it.

Alernatly you can set a static ip if there's any problems with the DHCP lease[/QUOTE]
 Note that this is for Fedora linux, but it should work with minor configuration, if you have problems just ask

---

### Post by Lunde on 2005-06-30
[QUOTE=Simplimus]My router log tells me this
Jun/30/2005 21:42:39 	DHCP lease IP 192.168.0.100 to unknown			00-11-95-BB-xx-xx
Why does it say "unknown"?
The other two in the network using windows machines have their network name listed there.

Well I can access the local network  anytime, just not the internet. I have to re-dhclient to get access.[/QUOTE]
 You should reserve an IP or set a static ip address in your router configuration
Then set the connection script to also use a static IP.

In your log, does your Mac address come up with xx-xx in the end? or did you do this yourself? strange that your box is not broadcasting the name. 

Anyway try to connect with the script, and set a static IP and lets get back to that problem if it's still there

---

### Post by Simplimus on 2005-07-01
Well, I wanna get this DNS-Problem straightend first. Apparently, when I get an IP adress then my computer assumes the dhcp server to be the dns server. however, after a minute or so this is all forgotten. where can I set the adress for my dns server manually?

Edit: I configured my computer as a DMZ in my router. This works for now but is definitely not a solution. The script itself works but where do I have to put it now? I know that in Ubuntu all runlevels are the same so the question is where to put the script.

Edit#2:The last time my pc was up it worked, this time, though I changed nothing, it doesnt. This §$%&er is messing with me.

Edit#3:I got it. I set another DNS server which I knew from my dorm. The router is supposed to work as DNS as well, but it doesnt. I disabled the DMZ and it still works. The trouble thats left is that during boot the network init fails and takes like 2 minutes. How do I shut that off? The script does all of that.

---

### Post by Lunde on 2005-07-01
[QUOTE=Simplimus]Well, I wanna get this DNS-Problem straightend first. Apparently, when I get an IP adress then my computer assumes the dhcp server to be the dns server. however, after a minute or so this is all forgotten. where can I set the adress for my dns server manually?

Edit: I configured my computer as a DMZ in my router. This works for now but is definitely not a solution. The script itself works but where do I have to put it now? I know that in Ubuntu all runlevels are the same so the question is where to put the script.

Edit#2:The last time my pc was up it worked, this time, though I changed nothing, it doesnt. This §$%&er is messing with me.

Edit#3:I got it. I set another DNS server which I knew from my dorm. The router is supposed to work as DNS as well, but it doesnt. I disabled the DMZ and it still works. The trouble thats left is that during boot the network init fails and takes like 2 minutes. How do I shut that off? The script does all of that.[/QUOTE]
 This is one of the reasons for using a static IP address.

The DNS you can set as described here:
[http://www.linuxquestions.org/questions/history/335288](http://www.linuxquestions.org/questions/history/335288) (Post#2) (Do also read the post#1 for some idea about static IP)

---

### Post by Lunde on 2005-07-01
Starting it at boot. I assume you put the script you made in /etc/init.d and named it wireless

cd /etc/rc5.d/
ln -s /etc/init.d/wireless S09wireless

---

### Post by Simplimus on 2005-07-01
This works so far, I already did all of that, but to get a stable connection I had to take my other network card out. Now it all works fine, thx. 

Now only the Postfix system always fails to stop during shut down. And the time update from ntp.....org or something doesnt work during boot , because the script is started to late. Can I get it to be started a little earlier during boot?

Can you recommend a simple and secure ftp-server? I read that pure-ftpd is supposed to be a good one, but I cant get it to work.

---

### Post by Lunde on 2005-07-01
Congratulations!! finally up on the net..

the clock sync at startup is just taking up extra boot time and is better removed I think.
[http://www.ubuntuguide.org/#synchronizingclocktooslow](http://www.ubuntuguide.org/#synchronizingclocktooslow)

Postfix: You should start a new tread for this so it's more searchable for other people with the same problem. But for us to be able to help you , you need to post the error messages from syslog /var/log/syslog 

Ftp server: 
$ sudo apt-get install proftpd

Documentation
[http://www.proftpd.org](http://www.proftpd.org)

---

### Post by Simplimus on 2005-07-05
Hi, I thought I was done, but it appears I'm not. My printer didnt work after the setup of my wireless so I was searching around and trying some things until I got to the point where I believed it might have something to do with that. Finally, I found that starting dhclient not only kills the postfix system, it also kills my CUPS. Currently I have  my system configured as dhcp. My router works as a dhcp client. Can I set a static IP?
Where do I have to do that?

---

### Post by Simplimus on 2005-07-05
How can I check weather the CUPS daemon is running?

---

### Post by Simplimus on 2005-07-05
I figured it out. It was that dhclient whcih killed all servers on my box. I manually configured the gateway with 
sudo route add default gw 192.168.XXX.XXX (X for the adress)
and removed the dhclient from the skript, now it works just the way it should. dhclient sucks.

---

### Post by Lunde on 2005-07-05
[QUOTE=Simplimus]I figured it out. It was that dhclient whcih killed all servers on my box. I manually configured the gateway with 
sudo route add default gw 192.168.XXX.XXX (X for the adress)
and removed the dhclient from the skript, now it works just the way it should. dhclient sucks.[/QUOTE]
 Glad it worked out for you. I also prefere to use static addresses

---

### Post by Simplimus on 2005-07-06
But there is one thing that bugs me still. From time to time my connection is interrupted for seconds and then reestablished. I had to use smbget to be able to load anything through LAN. The ability to resume is very helpful.

Yesterday my flatmate had trouble getting a connection at all after I used the static IP. Weird.

---

### Post by Lunde on 2005-07-06
[QUOTE=Simplimus]But there is one thing that bugs me still. From time to time my connection is interrupted for seconds and then reestablished. I had to use smbget to be able to load anything through LAN. The ability to resume is very helpful.

Yesterday my flatmate had trouble getting a connection at all after I used the static IP. Weird.[/QUOTE]
 You should reserve your IP also in the router. Also your flatmates IP and the printer if you have one connected to the router even if they are connected with DHCP. I used to have some problems before I did the same, but now my wireless network / router has'nt been restarted for 3months

---

