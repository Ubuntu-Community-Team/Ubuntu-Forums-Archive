---
title: "Wireless: Had it, Then Lost It!  Help!"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by Peter108 on 2007-08-09
{
[COLOR="Red"]Update:Additional Info: [/COLOR]
[COLOR="Red"]1. [/COLOR] peter@cosmo:/etc/modprobe.d$ [COLOR="Red"]lshw -C network[/COLOR]
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth1
       version: 10
       serial: 00:0f:b0:4c:46:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.115 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:17
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 03
       serial: 00:90:4b:b7:e2:40
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-server latency=64 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e0104000-e0105fff irq:21

[COLOR="Red"]2.[/COLOR]
I tried disabling IPv6 per [this post]("http://ubuntuforums.org/showthread.php?t=87798&highlight=disabling+ipv6"), but neither of the approaches actually seemed to work.  I.e., I created an /etc/modprobe.d/bad_list file, populated it per the post, and rebooted.  But afterward the cmd " ip a | grep inet6" was still returning output, so I assumed IPv6 was not disabled.  Nor was it disabled when I directly edited the aliases file and made the changes suggested in the post.   OTOH, one poster indicates the "Having IPv6 be the cause of 'slow' connection is actually a common
misconception", so I'm not sure whether the exercise was even worthwhile.  

[COLOR="Red"]3.[/COLOR]
I tried also to update my resolv.conf file w/ a different nameserver entry than my router, but network manager just overwrites the file sans the entry.  I also notice that even communicating w/ my *router* (i.e., via [http://192.168.0.1](http://192.168.0.1)) is slow as a slug.
 I'm out of ideas.  Please help.
}

New user w/ wireless probs.  I could SWEAR I had it all working at one time, using the instructions in  [Howto:Broadcom Wireless Cards]("http://ubuntuforums.org/showthread.php?t=185174")

[COLOR="Red"]Symptoms: [/COLOR]Glacially slow to non-existent response time; Wired is fine; Wireless connection recognized by network manager w/ strong signal, but that's it.  Ping -c 10 yahoo.com, for example, will usually time out w/ no output at all, but every so often output a line or two, tops.  
[COLOR="Red"]
Configuration:[/COLOR] Compaq R3000z laptop; FF 7.04 server w/ Gnome installed on top.  Dual boot w/ WinXP.  512MB. AMD 2800 (32-bit). Gnome-network-manager installed. On-board Broadcom wireless.  D-Link DI-514 router.  2 other Windows machines hung off this router (*and* the WinXP instance running on the dual-boot machine) all have full wireless functionality.
[COLOR="Red"]
Comment: [/COLOR]I swear, this is all that stands between me and defenestrating Windows once and for all!  Also, I have a Netgear WG511T PCMCIA cardbus  in hand.  Is it possible to override the default Broadcom hardware and try this card instead?  Thanks.  Peter


[COLOR="Red"]Diagnostics:[/COLOR]

[COLOR="Red"]lspci:[/COLOR]
peter@cosmo:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

[COLOR="Red"]iwconfig:[/COLOR]
peter@cosmo:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"peter"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0D:88:28:D7:94   
          Bit Rate=11 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=71/100  Signal level=-53 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[COLOR="Red"]ifconfig (FWIW):[/COLOR]
peter@cosmo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:4B:B7:E2:40  
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:feb7:e240/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:340 errors:0 dropped:1 overruns:0 frame:0
          TX packets:542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:112262 (109.6 KiB)  TX bytes:25295 (24.7 KiB)
          Interrupt:11 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:0F:B0:4C:46:89  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:245571 (239.8 KiB)  TX bytes:32240 (31.4 KiB)
          Interrupt:17 Base address:0xe800 

eth1:avah Link encap:Ethernet  HWaddr 00:0F:B0:4C:46:89  
          inet addr:166.254.5.21  Bcast:166.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:727 (727.0 b)  TX bytes:727 (727.0 b)"]

Many thanks. Peter.

---

### Post by spoonernash on 2007-08-12
Peter, this is just a quick response that may or may not help. I'm busy looking for a solution myself and did not study the details of your posting. I recently got my wireless going by setting my access point to beacon the SSID. Befoe that I had it off for security. I became convinced that the extra security provided was not worth the effort. I turned on beaconing and my wireless worked.

What I am looking for now is that every time I restart the computer my resolv.conf gets over-written (by Network Manager?) and I have to enter dns and gateway info to get it connected. Could you also have such a problem?

---

### Post by Peter108 on 2007-08-12
Not only does resolve.conf get overwritten by Network Manager on restart, I've seen it do the overwrite in mid-session.  Such efficiency!:mad: Since my problems manifest even between my laptop and the router, I'm pretty sure I don't have a DNS problem, so am looking elsewhere.  And since the WinXP side of my dual-boot setup runs wireless perfectly, then I'm told I don't likely have a hardware problem.

Can you say more about how you "turned on beaconing"?  I realize this may be hardware-dependent, but maybe I can figure out my own if you provide more detail.  Thanks. 

BTW, when I received no reply to my post here I went over to[ Linuxquestions.org]("http://www.linuxquestions.org/questions/showthread.php?t=576190") and posted a more thorough accounting of my situation.  I'm about to post links to syslogs and packet sniffer output there and hopefully get to the bottom of this. We'll see. 

Thank you for your reply.

---

### Post by hobojjr on 2007-08-12
I have a wireless card. The problem I have it that I only get connection for like half a minute. Then I have to reconnect and obtain the ip manually just so that I have another half a minute of connection. WTF? Any ideas of how to fix this, besides sticking to winXp (Oh how I love thee)?

---

### Post by spoonernash on 2007-08-13
On my access point setup page is an option to broadcast, or not, the SSID. I used to have it set to no. I changed it to yes. From what I read the AP broadcasts more info than just the SSID. It includes a lot of settings that lets the connection get made.

Again, I have not taken the time to read the details of your issue. but I think I just solved my problem of resolv.conf getting overwritten by networkmanager from postings here. It had to do with editing /etc/dhclient.conf to set dns and have dhcp not get dns settings.

Linuxquestions.org is a great place. I go there for Slackware and other Linux questions. But it seems to me that this is a better place for Ubuntu and related.

Cheers.

---

### Post by spoonernash on 2007-08-13
hobojjr, when I first tried to set up wireless I got a connection then lost it. I am not sure but I think it may have had to do with MAC filtering on my access point. Try turning that off if you have it on.

---

### Post by Peter108 on 2007-08-14
All,

I wanted to provide a complete refresh of my information, since I've been doing a lot of work behind the scenes since the original post.   I conducted a troubleshooting session Sunday and saved off the syslogs, which are [here]("http://www.mediamax.com/peter108").  In addition to the 6 logs, there is a .pcap file showing Wireshark packet sniffer output for the session, plus PeterUserLog.odt in which I describe and timestamp my mouse and keyboard actions (so you can more or less see what user actions are associated with what log entries).

Here are some excerpts (though I have no idea whether they are what I'm after):

1) A couple of entries suggesting conflict in the assignment of wireless drivers. See messages0812 file:
[COLOR="Blue"]Aug 12 07:47:56 cosmo kernel: [ 8.430000] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Aug 12 07:47:56 cosmo kernel: [ 8.430000] 8139cp 0000:02:01.0: Try the "8139too" driver instead.
Aug 12 07:47:56 cosmo kernel: [ 8.480000] 8139too Fast Ethernet driver 0.9.28
Aug 12 07:47:56 cosmo kernel: [ 8.480000] eth0: RealTek RTL8139 at 0xe09a6800, 00:0f:b0:4c:46:89, IRQ 17[/COLOR]

versus
[COLOR="Blue"]Aug 12 07:47:56 cosmo kernel: [ 26.030000] bcm43xx driver[/COLOR]
2) Also from the messages0812 file
[COLOR="Blue"]Aug 12 07:48:54 cosmo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug 12 07:49:17 cosmo kernel: [ 114.540000] SoftMAC: Open Authentication completed with 00:0d:88:28:d7:94
Aug 12 07:49:18 cosmo kernel: [ 114.830000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug 12 07:49:28 cosmo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Aug 12 07:49:28 cosmo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Aug 12 07:49:28 cosmo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Aug 12 07:49:28 cosmo dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers[/COLOR]

3) From dmesg:
[COLOR="Blue"][ 8.480000] eth0: RealTek RTL8139 at 0xe09a6800, 00:0f:b0:4c:46:89, IRQ 17
[ 8.480000] eth0: Identified 8139 chip type 'RTL-8101'
and
[ 26.030000] bcm43xx driver[/COLOR]

4) From kern.log (2 messages displayed on startup every time):
[COLOR="Blue"]Aug 12 07:47:56 cosmo kernel: [ 20.329173] PCI: Failed to allocate mem resource #10:4000000@e4000000 for 0000:02:04.0
Aug 12 07:47:56 cosmo kernel: [ 20.329232] PCI: Failed to allocate mem resource #10:4000000@e4000000 for 0000:02:04.[/COLOR]

5) From the syslog:
A ton of messages from Network Manager best viewed via the link at the top of this post.

6) From udev:
[COLOR="Blue"]UEVENT[1186904802.789611] add /class/net/eth0 (net)
ACTION=add
DEVPATH=/class/net/eth0
SUBSYSTEM=net
SEQNUM=1724
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0/0000:02:01.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=8139too
INTERFACE=eth0[/COLOR]

and

[COLOR="Blue"]UDEV [1186904802.971685] add /class/net/eth1 (net)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/net/eth1
SUBSYSTEM=net
SEQNUM=1724
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0/0000:02:01.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=8139too
INTERFACE=eth1
UDEVD_EVENT=1
INTERFACE_OLD=eth0[/COLOR]

and

[COLOR="Blue"]UEVENT[1186930069.392520] add /class/net/eth0 (net)
ACTION=add
DEVPATH=/class/net/eth0
SUBSYSTEM=net
SEQNUM=2522
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0/0000:02:02.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=bcm43xx
INTERFACE=eth0[/COLOR]

and finally

[COLOR="Blue"]UDEV [1186930069.739166] add /class/net/eth0 (net)
UDEV_LOG=3
ACTION=add
DEVPATH=/class/net/eth0
SUBSYSTEM=net
SEQNUM=2522
PHYSDEVPATH=/devices/pci0000:00/0000:00:0a.0/0000:02:02.0
PHYSDEVBUS=pci
PHYSDEVDRIVER=bcm43xx
INTERFACE=eth0
UDEVD_EVENT=1[/COLOR]

Today, following another suggestion, I did this (on the theory that maybe I do have a driver conflict which could be resolved by knocking out bcm43xx in favor of 8139too)

I did this:

Edited /etc/modprobe.d/blacklist  and added these two lines:
[COLOR="Blue"]#blacklist broadcomm wireless driver in favor of 8139too
blacklist bcm43x[/COLOR]

Shut down, inserted the WG511T and restarted.

Results:
Pretty much no recognition of the card. iwconfig returns nothing at all for eth0
[COLOR="Blue"]peter@cosmo:~$ iwconfig
lo no wireless extensions.

eth1 no wireless extensions.[/COLOR]

Network manager sees no wireless networks. And selecting "manual configuration" shows no entry for wireless.

However the dmesg log shows
[COLOR="Blue"][ 8.540000] eth0: RealTek RTL8139 at 0xe0954800, 00:0f:b0:4c:46:89, IRQ 17 [COLOR="Black"](router MAC address is correct)[/COLOR]
[ 8.540000] eth0: Identified 8139 chip type 'RTL-8101'[/COLOR]
while lspci shows
[COLOR="Blue"]02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)[/COLOR]

I tested the card this morning on a WinXP machine just to confirm it works.  It does.  And as I mentioned earlier, my Ubuntu is on a dual-boot w/ WinXP and the WinXP broadcomm wireless works, so I think we can rule out hardware problems.  So my original problems remain:
1) Broadcomm onboard wireless is glacially slow (however I should add, that there are very occasional bursts of normal functionality.  Maybe this is what I meant when I said in my O.P. that "I could swear it used to work")
2) Trying to override the onboard broadcomm using the Netgear WG511T card is coming up empty.
Note: I remain a noob, so if you have suggestions, please be explicit.   It'll help me a lot!  Thanks again.

---

### Post by Peter108 on 2007-08-14
P.S. Also tried blacklisting the *other* driver (8139too), but that just brought me back to square one: A bcm43xx driver and awful wireless performance.

---

### Post by Peter108 on 2007-08-14
Whoops.  Come to find out 8139too is a wired driver, not wireless.  FWIW, w/ card plugged in:

[COLOR="Blue"]peter@cosmo:~$ lspcmcia
Socket 0 Bridge: [yenta_cardbus] (bus ID: 0000:02:04.0)
CardBus card -- see "lspci" for more information
Socket 1 Bridge: [yenta_cardbus] (bus ID: 0000:02:04.1)[/COLOR]

Learning as I go,

---

### Post by kevdog on 2007-08-14
Can you summarize your problem in two sentences?? I read your original post, it was too long for me to follow and the subsequent posts are helping me.

---

### Post by Peter108 on 2007-08-14
[LIST=1]
[*]I experience very slow wireless response, using FF7.04 server, a Compaq R3000 laptop, onboard Broadcom wireless, (whose driver was installed using [How to: Broadcom Wireless cards - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=185174")), and Gnome Network Manager.
[*]As an alternative, I've tried blacklisting bcm43xx in /etc/modprobe.d/blacklist and installing a Netgear WG511T PCMCIA Cardbus card, but, as explained in greater detail elsewhere in this thread, that doesn't work, either. 
[/LIST]

Succinctly yours,:)

---

### Post by kevdog on 2007-08-14
Thanks for the explanation -- that was clear

As far as the onboard wireless with the Broadcom chipset, have you tried ndiswrapper as an alternative?  If you want to try this approach I can post specific instructions how to install, compile from source.

With the Netgear card, I dont know the chipset this card is using.  If you want to use this card instead we need to discover the chipset.  Its possible if you plug the card in and then do a 
lshw -C network, we can find this from what is posted.

Again Im confident a solution is possible, however what networking device do you want to try first?

---

### Post by Peter108 on 2007-08-14
Kevdog:

Thanks!   Tell you what: here's the output from lshw -C network.  Given what you see, is their a device/chipset that has proven more compatible?   If so, let's start with that one.   Otherwise, let's start with Broadcom. 

[COLOR="Blue"]peter@cosmo:~$ sudo lshw -C network
Password:
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth1
       version: 10
       serial: 00:0f:b0:4c:46:89
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.106 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:17

  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: iomemory:e0104000-e0105fff irq:11

  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=28 mingnt=10
       resources: iomemory:e0400000-e040ffff irq:16
peter@cosmo:~$[/COLOR]

---

### Post by bmartin on 2007-08-14
Here, [use this thread]("http://ubuntuforums.org/showthread.php?t=405990") to install the appropriate method for your WiFi chipset. It contains a graphical installer and does all the hard work for you.

I used to use the firmware on my BCM4318, but had problems on and off with connectivity; I'd randomly get disconnected. I switched to ndiswrapper and my problems went away.

---

### Post by Peter108 on 2007-08-14
Howdy bmartin: Ran through the process smoothly and without error, but my symptoms are now worse.  Whereas before Network Manager saw my wireless network and detected strong signal strength (but I suffered poor performance), now it sees no wireless network.   I.e., when I click the NM double-terminal icon, it shows only a wired network as an option, and does not even permit a manual configuration of a wireless network.  iwconfig eth0 returns "no such device".

My system is now behaving as it did when I had the Netgear WG511T card inserted--except that it isn't.   Do I need to somehow unmount the un-inserted card?

/var/log/messages shows this, interestingly:
Aug 14 17:01:16 cosmo kernel: [    6.170000] eth0: RealTek RTL8139 at 0xe084e800, 00:0f:b0:4c:46:89, IRQ 17

---

### Post by kevdog on 2007-08-14
Ok, lets start with the broadcom card.  

I dont know if you have installed ndiswrapper before, however if you have Ive included in the instructions how to remove an old version.  If you have not installed it, then just skip this part.

Also, (you might have done this), but lets blacklist the bcm43xx module right off the top:
```
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist
```

**[SIZE="4"]Ndiswrapper Uninstall Instructions[/SIZE]**
Ok before installing the new ndiswrapper packages we need to uninstall the old version completely. Dont worry if some of these commands dont do anything or seem not to work -- some may be repetitive.

```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo rmmod ndiswrapper
sudo /lib/modules/`uname -r`/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
sudo rm -rf /etc/ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```


**[SIZE="4"]Download, Compiling, Installing and Configuring Ndiswrapper from Source Files[/SIZE]**

If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

```

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


OK next we want to download the ndiswrapper source files (Reference URL = _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_)

We are grabbing ndiswrapper-1.48-rc1

```
cd ~
mkdir ndiswrapper
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz -O ~/ndiswrapper/ndiswrapper-1.48rc1.tar.gz 
cd ndiswrapper

```

Extract, compile, and install ndiswrapper
```
tar -zxvf ndiswrapper-1.48rc1.tar.gz
cd ndiswrapper-1.48rc1
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following:
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48rc1
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Window's wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running

---

### Post by bmartin on 2007-08-14
Um, nope. If it unplugs, simply unplug it and plug it back in and it should work.

I presume you installed the firmware. There's an ndiswrapper installer included in that program, too. Try that and see if you have better luck. You don't need to remove the firmware; the installer will blacklist the bcm43xx kernel module and remove it from memory. (The firmware installer, on the other hand, unblacklists the bcm43xx kernel module)

---

### Post by Peter108 on 2007-08-15
Kevdog:

I am following your instructions to install ndiswrapper.  I downloaded and extracted the targz file, but get the following when I run make distclean:
```

peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ make distclean
make -C driver clean
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.20-16-server/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make: *** [clean] Error 2
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ 
```

Indeed, under /lib/modules/2.6.20-16-server/ their is neither a file nor dir named 'build'. How do I proceed?  Thanks.

---

### Post by kevdog on 2007-08-15
Hmm, havent seen that error before and Ive had over 50 people follow these instructions.

Ok no big deal on the make distclean statement failing

What if you proceed with the make command???

---

### Post by Peter108 on 2007-08-15
Looks like I'm stopped in my tracks.  make produces pretty much same output as make distclean.

```
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ make
make -C driver
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.20-16-server/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make: *** [all] Error 2
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ 
```

---

### Post by kevdog on 2007-08-15
Hmmmm,
Ok did you install the kernel headers??

(Im googling around trying to find answers)

---

### Post by kevdog on 2007-08-15
Ok

/lib/modules/2.6.20-16-server/build directory should be a symbolic link

build should point to /usr/src/linux-headers-2.6.20-16-<?????>

In my setup ???? = generic
Since Im not using the server version I dont know if in /usr/src there should be a /usr/src/linux-headers-2.6.20-16-server directory

Again I would try installing the linux headers if not done so -- instructions in the long post above, and if this doesnt work I would create a build directory with symbolic link to directory listed above.

---

### Post by Peter108 on 2007-08-15
Yes, I built the headers.  Output below.  
Contents of /usr/src below.

Regarding "I would create a build directory with symbolic link to directory listed above."

I'm sorry to be such a dork, but I have some sort of cognitive block (I'm dead serious) using ln.  I always screw up source and target paths.  Can you provide me with the syntax?  I wouldn't ask if for me it weren't a high-risk proposition.  (Hey, I'm over 50; these things happen.)
 
```

peter@cosmo:/usr/src$ ls -al
total 16
drwxrwsr-x  4 root src  4096 2007-08-02 09:47 .
drwxr-xr-x 11 root root 4096 2007-08-02 09:41 ..
drwxr-xr-x 20 root root 4096 2007-08-02 09:47 linux-headers-2.6.20-16
drwxr-xr-x  4 root root 4096 2007-08-02 09:47 linux-headers-2.6.20-16-generic
```


```
peter@cosmo:~$ sudo aptitude install build-essential linux-headers- `uname -r`
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find package "2.6.20-16-server".  However, the following
packages contain "2.6.20-16-server" in their name:
  linux-image-2.6.20-16-server linux-image-2.6.20-16-server-bigiron linux-image-debug-2.6.20-16-server-bigiron 
  linux-image-debug-2.6.20-16-server linux-headers-2.6.20-16-server-bigiron linux-headers-2.6.20-16-server 
The following NEW packages will be automatically installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
The following packages have been kept back:
  opera 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
0 packages upgraded, 7 newly installed, 0 to remove and 1 not upgraded.
Need to get 667kB/8053kB of archives. After unpacking 33.7MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)' in the drive '/cdrom/' and press enter

Get:1 http://security.ubuntu.com feisty-security/main linux-libc-dev 2.6.20-16.29 [667kB]
Fetched 667kB in 55s (12.0kB/s)                                                                                        
Selecting previously deselected package linux-libc-dev.
(Reading database ... 95067 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.20-16.29_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up linux-libc-dev (2.6.20-16.29) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ..
```.

---

### Post by kevdog on 2007-08-15
****Hold on

linux-headers- `uname -r` --->>>> This is supposed to be 
sudo aptitude install linux-headers-`uname -r`

Just caught this -- no space

Try this above before doing what I typed below!!
*****Back

Try something like this:

First create the build directory with root priviledges

ln -s /usr/src/linux-<your kernel version> /lib/modules/<your kernel version>/build

So I would use


ln -s /usr/src/linux-linux-headers-2.6.20-16-generic /lib/modules/2.6.20-16-server/build

---

### Post by Peter108 on 2007-08-15
OK.  I reran the cmd:

```
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ sudo aptitude install linux-headers-`uname -r`
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  opera 
The following NEW packages will be installed:
  linux-headers-2.6.20-16-server 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 844kB of archives. After unpacking 7258kB will be used.
Writing extended state information... Done
Get:1 http://security.ubuntu.com feisty-security/main linux-headers-2.6.20-16-server 2.6.20-16.29 [844kB]
Fetched 844kB in 7s (113kB/s)                                                                                                
Selecting previously deselected package linux-headers-2.6.20-16-server.
(Reading database ... 96817 files and directories currently installed.)
Unpacking linux-headers-2.6.20-16-server (from .../linux-headers-2.6.20-16-server_2.6.20-16.29_i386.deb) ...
Setting up linux-headers-2.6.20-16-server (2.6.20-16.29) ...
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$
``` 

I have to leave for a meeting.  May not get back to this until much later today.   Do you suggest I back completely out of my ndiswrapper install-in-progress, or just resume by trying
to run make distclean?  Thanks, kevdog!!!

---

### Post by kevdog on 2007-08-15
Just resume at the distclean statement.  I think you should be good for now -- you havent broken anything yet!!:)

---

### Post by Peter108 on 2007-08-15
But still create the symlink first, right?  Otherwise, make distclean still bombs (Just reran it).  
["Going to a meeting" actually meant a teleconference, so I can multi-task with this stuff!]

---

### Post by kevdog on 2007-08-15
Again im not familar with the server version files.

Are the directories
/usr/src/xxxx-generic and xxxx-server the same?  If the look the same I would link the build directory to the server directory rather than the generic.  If server is empty link to generic.  Mine is linked to the generic.  

Sorry I really dont know the "actual difference" between the two.

---

### Post by Peter108 on 2007-08-15
Curses.  

Same result w/ make distclean, regardless of whether I symlink to /usr/src/linux-headers-2.6.20-16 or /usr/src/linux-headers-2.6.20-16-generic.   Jeez, I wonder if it's time to re-install using the desktop version.  This is my personal machine, so as long as I can get apache and subversion up and running, maybe that's the way to go.  

Gory details:

```
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$[COLOR="Red"] ls -al /lib/modules/2.6.20-16-server/build[/COLOR]
total 8
drwxr-xr-x 2 root root 4096 2007-08-15 10:15 .
drwxr-xr-x 5 root root 4096 2007-08-15 09:22 ..
[COLOR="Red"]lrwxrwxrwx 1 root root   32 2007-08-15 10:15 linux-headers-2.6.20-16 -> /usr/src/linux-headers-2.6.20-16[/COLOR]
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$[COLOR="Red"] ls -al /usr/src/linux-headers-2.6.20-16[/COLOR]
total 176
drwxr-xr-x 20 root root  4096 2007-08-02 09:47 .
drwxrwsr-x  5 root src   4096 2007-08-15 09:25 ..
drwxr-xr-x 27 root root  4096 2007-08-02 09:47 arch
drwxr-xr-x  2 root root  4096 2007-08-02 09:47 block
-rw-r--r--  1 root root 35898 2007-06-07 13:32 .config
drwxr-xr-x  2 root root  4096 2007-08-02 09:47 crypto
drwxr-xr-x  9 root root  4096 2007-08-02 09:47 debian
drwxr-xr-x 64 root root  4096 2007-08-02 09:47 drivers
drwxr-xr-x 63 root root  4096 2007-08-02 09:47 fs
drwxr-xr-x 43 root root  4096 2007-08-02 09:47 include
drwxr-xr-x  2 root root  4096 2007-08-02 09:47 init
drwxr-xr-x  2 root root  4096 2007-08-02 09:47 ipc
drwxr-xr-x  5 root root  4096 2007-08-02 09:47 kernel
drwxr-xr-x  5 root root  4096 2007-08-02 09:47 lib
-rw-r--r--  1 root root    13 2007-06-07 13:44 linux-headers.revision
-rw-r--r--  1 root root 50528 2007-04-12 10:15 Makefile
drwxr-xr-x  2 root root  4096 2007-08-02 09:47 mm
drwxr-xr-x 37 root root  4096 2007-08-02 09:47 net
drwxr-xr-x  9 root root  4096 2007-08-02 09:47 scripts
drwxr-xr-x  4 root root  4096 2007-08-02 09:47 security
drwxr-xr-x 17 root root  4096 2007-08-02 09:47 sound
drwxr-xr-x 13 root root  4096 2007-08-02 09:47 ubuntu
drwxr-xr-x  2 root root  4096 2007-08-02 09:47 usr
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ [COLOR="Red"]make distclean[/COLOR]
make -C driver clean
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.20-16-server/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make: *** [clean] Error 2
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ sudo ln -s /usr/src/linux-headers-2.6.20-16-generic /lib/modules/2.6.20-16-server/build
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ ls -al /lib/modules/2.6.20-16-server/build
total 8
drwxr-xr-x 2 root root 4096 2007-08-15 10:21 .
drwxr-xr-x 5 root root 4096 2007-08-15 09:22 ..
lrwxrwxrwx 1 root root   32 2007-08-15 10:15 linux-headers-2.6.20-16 -> /usr/src/linux-headers-2.6.20-16
lrwxrwxrwx 1 root root   40 2007-08-15 10:21 linux-headers-2.6.20-16-generic -> /usr/src/linux-headers-2.6.20-16-generic
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ sudo rm /lib/modules/2.6.20-16-server/build/linux-headers-2.6.20-16
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$[COLOR="Red"] ls -al /lib/modules/2.6.20-16-server/build[/COLOR]
total 8
drwxr-xr-x 2 root root 4096 2007-08-15 10:22 .
drwxr-xr-x 5 root root 4096 2007-08-15 09:22 ..
[COLOR="Red"]lrwxrwxrwx 1 root root   40 2007-08-15 10:21 linux-headers-2.6.20-16-generic -> /usr/src/linux-headers-2.6.20-16-generic[/COLOR]
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$  [COLOR="Red"]ls -al /usr/src/linux-headers-2.6.20-16-generic[/COLOR]
total 572
drwxr-xr-x 4 root root   4096 2007-08-02 09:47 .
drwxrwsr-x 5 root src    4096 2007-08-15 09:25 ..
lrwxrwxrwx 1 root root     31 2007-08-02 09:47 arch -> ../linux-headers-2.6.20-16/arch
lrwxrwxrwx 1 root root     32 2007-08-02 09:47 block -> ../linux-headers-2.6.20-16/block
-rw-r--r-- 1 root root  83217 2007-06-07 11:16 .config
lrwxrwxrwx 1 root root     33 2007-08-02 09:47 crypto -> ../linux-headers-2.6.20-16/crypto
lrwxrwxrwx 1 root root     34 2007-08-02 09:47 drivers -> ../linux-headers-2.6.20-16/drivers
lrwxrwxrwx 1 root root     29 2007-08-02 09:47 fs -> ../linux-headers-2.6.20-16/fs
drwxr-xr-x 4 root root   4096 2007-08-02 09:47 include
lrwxrwxrwx 1 root root     31 2007-08-02 09:47 init -> ../linux-headers-2.6.20-16/init
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 ipc -> ../linux-headers-2.6.20-16/ipc
lrwxrwxrwx 1 root root     33 2007-08-02 09:47 kernel -> ../linux-headers-2.6.20-16/kernel
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 lib -> ../linux-headers-2.6.20-16/lib
-rw-r--r-- 1 root root  50527 2007-06-07 13:59 Makefile
lrwxrwxrwx 1 root root     29 2007-08-02 09:47 mm -> ../linux-headers-2.6.20-16/mm
-rw-r--r-- 1 root root 414274 2007-06-07 13:56 Module.symvers
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 net -> ../linux-headers-2.6.20-16/net
drwxr-xr-x 9 root root   4096 2007-08-02 09:47 scripts
lrwxrwxrwx 1 root root     35 2007-08-02 09:47 security -> ../linux-headers-2.6.20-16/security
lrwxrwxrwx 1 root root     32 2007-08-02 09:47 sound -> ../linux-headers-2.6.20-16/sound
lrwxrwxrwx 1 root root     33 2007-08-02 09:47 ubuntu -> ../linux-headers-2.6.20-16/ubuntu
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 usr -> ../linux-headers-2.6.20-16/usr
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ [COLOR="Red"]make distclean[/COLOR]
make -C driver clean
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.20-16-server/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make: *** [clean] Error 2
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$  ls -al /usr/src/linux-headers-2.6.20-16
```

---

### Post by kevdog on 2007-08-15
No something must be wrong with the symbolic link

Ill touch back later gotta run

---

### Post by kevdog on 2007-08-15
OK, not sure what is wrong but the syntax for the ln statment is correct:

ln -s <targetdir> <symbolic link>
targetdir = actual existing directory
symlin = new linked virtual directory

So

ln -s /usr/src/linux-headers-2.6.20-16-generic /lib/modules/2.6.20-16-generic/build


Here is how mine is configured
```

kevin@Homer:/lib/modules/2.6.20-16-generic$ l[SIZE="3"]**s -la /lib/modules/2.6.20-16-generic/**[/SIZE]
total 1680
drwxr-xr-x  8 root root   4096 2007-08-05 23:11 .
drwxr-xr-x  9 root root   4096 2007-06-14 07:37 ..
lrwxrwxrwx  1 root root     40 2007-05-28 07:44 build -> /usr/src/linux-headers-2.6.20-16-generic
drwxr-xr-x  2 root root   4096 2007-07-30 21:00 extra
drwxr-xr-x  2 root root   4096 2007-06-09 07:44 initrd
drwxr-xr-x 11 root root   4096 2007-05-28 07:42 kernel
drwxr-xr-x  2 root root   4096 2007-06-29 07:40 madwifi
drwxr-xr-x  2 root root   4096 2007-08-05 23:11 misc
-rw-r--r--  1 root root 353964 2007-08-05 23:11 modules.alias
-rw-r--r--  1 root root     69 2007-08-05 23:11 modules.ccwmap
-rw-r--r--  1 root root 387451 2007-08-05 23:11 modules.dep
-rw-r--r--  1 root root    813 2007-08-05 23:11 modules.ieee1394map
-rw-r--r--  1 root root    806 2007-08-05 23:11 modules.inputmap
-rw-r--r--  1 root root  22147 2007-08-05 23:11 modules.isapnpmap
-rw-r--r--  1 root root     74 2007-08-05 23:11 modules.ofmap
-rw-r--r--  1 root root 265182 2007-08-05 23:11 modules.pcimap
-rw-r--r--  1 root root   1303 2007-08-05 23:11 modules.seriomap
-rw-r--r--  1 root root 157869 2007-08-05 23:11 modules.symbols
-rw-r--r--  1 root root 450879 2007-08-05 23:11 modules.usbmap
drwxr-xr-x  2 root root    360 2007-08-14 22:36 volatile

```

```
kevin@Homer:/usr/src/linux-headers-2.6.20-16-generic$ **[SIZE="3"]ls -la /usr/src/linux-headers-2.6.20-16-generic/[/SIZE]**
total 572
drwxr-xr-x 4 root root   4096 2007-06-09 07:43 .
drwxrwsr-x 7 root src    4096 2007-05-28 07:44 ..
lrwxrwxrwx 1 root root     31 2007-05-28 07:44 arch -> ../linux-headers-2.6.20-16/arch
lrwxrwxrwx 1 root root     32 2007-05-28 07:44 block -> ../linux-headers-2.6.20-16/block
-rw-r--r-- 1 root root  83217 2007-06-07 12:16 .config
lrwxrwxrwx 1 root root     33 2007-05-28 07:44 crypto -> ../linux-headers-2.6.20-16/crypto
lrwxrwxrwx 1 root root     34 2007-05-28 07:44 drivers -> ../linux-headers-2.6.20-16/drivers
lrwxrwxrwx 1 root root     29 2007-05-28 07:44 fs -> ../linux-headers-2.6.20-16/fs
drwxr-xr-x 4 root root   4096 2007-06-09 07:43 include
lrwxrwxrwx 1 root root     31 2007-05-28 07:44 init -> ../linux-headers-2.6.20-16/init
lrwxrwxrwx 1 root root     30 2007-05-28 07:44 ipc -> ../linux-headers-2.6.20-16/ipc
lrwxrwxrwx 1 root root     33 2007-05-28 07:44 kernel -> ../linux-headers-2.6.20-16/kernel
lrwxrwxrwx 1 root root     30 2007-05-28 07:44 lib -> ../linux-headers-2.6.20-16/lib
-rw-r--r-- 1 root root  50527 2007-06-07 14:59 Makefile
lrwxrwxrwx 1 root root     29 2007-05-28 07:44 mm -> ../linux-headers-2.6.20-16/mm
-rw-r--r-- 1 root root 414274 2007-06-07 14:56 Module.symvers
lrwxrwxrwx 1 root root     30 2007-05-28 07:44 net -> ../linux-headers-2.6.20-16/net
drwxr-xr-x 9 root root   4096 2007-06-09 07:43 scripts
lrwxrwxrwx 1 root root     35 2007-05-28 07:44 security -> ../linux-headers-2.6.20-16/security
lrwxrwxrwx 1 root root     32 2007-05-28 07:44 sound -> ../linux-headers-2.6.20-16/sound
lrwxrwxrwx 1 root root     33 2007-05-28 07:44 ubuntu -> ../linux-headers-2.6.20-16/ubuntu
lrwxrwxrwx 1 root root     30 2007-05-28 07:44 usr -> ../linux-headers-2.6.20-16/usr

```

---

### Post by kevdog on 2007-08-15
Ok I think I found the problem with your setup.

We are going to redo a few things here:

cd /lib/modules/2.6.20-16-server/build
rm linux-headers-2.6.20-16
rm linux-headers-2.6.20-16-generic
cd..
rmdir build

Now your present working directory should be /lib/modules/2.6.20-16-server

Try the following
ln -s /usr/src/linux-headers-2.6.20-16-generic build

I think the problem last time was that I had you create the build directory first, then make a symbolic link.  After further reading this was incorrect.  The build directory should not have existed, and the symbolic link made (which creates the build directory)

Hopefully this will work --- Pain in th A$$

---

### Post by Peter108 on 2007-08-15
Before I do that,  take I look at my versions of 

/lib/modules/2.6.20-16-generic/ and 
/usr/src/linux-headers-2.6.20-16-generic/

The content of our 'headers' dirs matches up, but the content of_ your _/lib/modules/2.6.20-16-generic/  does not equal  _my_ /lib/modules/2.6.20-16-generic/, which is empty but for a symlink.   The contents of your /lib/modules/2.6.20-16-generic/ maps to my /lib/modules/2.6.20-16-server.  Do we care, or do your latest instructions account for that.  I'm a little fogged at this point, so am not sure. 


```
peter@cosmo:/lib/modules/2.6.20-16-generic$ ls -la /lib/modules/2.6.20-16-generic/
total 8
drwxr-xr-x 2 root root 4096 2007-08-02 09:47 .
drwxr-xr-x 5 root root 4096 2007-08-02 11:35 ..
lrwxrwxrwx 1 root root   40 2007-08-02 09:47 build -> /usr/src/linux-headers-2.6.20-16-generic

```


```

peter@cosmo:/lib/modules/2.6.20-16-generic$ ls -la /usr/src/linux-headers-2.6.20-16-generic/
total 572
drwxr-xr-x 4 root root   4096 2007-08-02 09:47 .
drwxrwsr-x 5 root src    4096 2007-08-15 09:25 ..
lrwxrwxrwx 1 root root     31 2007-08-02 09:47 arch -> ../linux-headers-2.6.20-16/arch
lrwxrwxrwx 1 root root     32 2007-08-02 09:47 block -> ../linux-headers-2.6.20-16/block
-rw-r--r-- 1 root root  83217 2007-06-07 11:16 .config
lrwxrwxrwx 1 root root     33 2007-08-02 09:47 crypto -> ../linux-headers-2.6.20-16/crypto
lrwxrwxrwx 1 root root     34 2007-08-02 09:47 drivers -> ../linux-headers-2.6.20-16/drivers
lrwxrwxrwx 1 root root     29 2007-08-02 09:47 fs -> ../linux-headers-2.6.20-16/fs
drwxr-xr-x 4 root root   4096 2007-08-02 09:47 include
lrwxrwxrwx 1 root root     31 2007-08-02 09:47 init -> ../linux-headers-2.6.20-16/init
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 ipc -> ../linux-headers-2.6.20-16/ipc
lrwxrwxrwx 1 root root     33 2007-08-02 09:47 kernel -> ../linux-headers-2.6.20-16/kernel
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 lib -> ../linux-headers-2.6.20-16/lib
-rw-r--r-- 1 root root  50527 2007-06-07 13:59 Makefile
lrwxrwxrwx 1 root root     29 2007-08-02 09:47 mm -> ../linux-headers-2.6.20-16/mm
-rw-r--r-- 1 root root 414274 2007-06-07 13:56 Module.symvers
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 net -> ../linux-headers-2.6.20-16/net
drwxr-xr-x 9 root root   4096 2007-08-02 09:47 scripts
lrwxrwxrwx 1 root root     35 2007-08-02 09:47 security -> ../linux-headers-2.6.20-16/security
lrwxrwxrwx 1 root root     32 2007-08-02 09:47 sound -> ../linux-headers-2.6.20-16/sound
lrwxrwxrwx 1 root root     33 2007-08-02 09:47 ubuntu -> ../linux-headers-2.6.20-16/ubuntu
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 usr -> ../linux-headers-2.6.20-16/usr
peter@cosmo:/lib/modules/2.6.20-16-generic
```$

```
peter@cosmo:/lib/modules$ ls -al 2.6.20-16-server
total 1648
drwxr-xr-x  5 root root   4096 2007-08-15 09:22 .
drwxr-xr-x  5 root root   4096 2007-08-02 11:35 ..
drwxr-xr-x  2 root root   4096 2007-08-15 10:22 build
drwxr-xr-x  2 root root   4096 2007-08-02 11:35 initrd
drwxr-xr-x 11 root root   4096 2007-08-02 11:35 kernel
-rw-r--r--  1 root root 350590 2007-08-14 16:45 modules.alias
-rw-r--r--  1 root root     69 2007-08-14 16:45 modules.ccwmap
-rw-r--r--  1 root root 377855 2007-08-14 16:45 modules.dep
-rw-r--r--  1 root root    813 2007-08-14 16:45 modules.ieee1394map
-rw-r--r--  1 root root    806 2007-08-14 16:45 modules.inputmap
-rw-r--r--  1 root root  22147 2007-08-14 16:45 modules.isapnpmap
-rw-r--r--  1 root root     74 2007-08-14 16:45 modules.ofmap
-rw-r--r--  1 root root 262725 2007-08-14 16:45 modules.pcimap
-rw-r--r--  1 root root   1303 2007-08-14 16:45 modules.seriomap
-rw-r--r--  1 root root 152961 2007-08-14 16:45 modules.symbols
-rw-r--r--  1 root root 443820 2007-08-14 16:45 modules.usbmap
```

---

### Post by kevdog on 2007-08-15
Ok -- I have to look at this a few times to see what you mean -- its getting confusing

Bottom line at this point

your /lib/modules/2.6.20-16-server (almost) equals my /lib/modules/2.6.20-16-generic

And just to make it more complex my lib/modules/2.6.20-16-server directory is empty except for a misc directory

Ok just to clarify
When I type
```
uname -r
```

I get 2.6.20-16-generic

You get 2.6.20-16-server


So Im thinking your server directory should match my general directory

So lets fix a few things on your end:
```
cd /lib/modules/2.6.20-16-generic
rm build
```

```
cd /lib/modules/2.6.20-16-server
```

Ok my last question to you -- in the server directory I see a directory called build for you 
```
drwxr-xr-x  2 root root   4096 2007-08-15 10:22 build
```
Its 4096 in size.  What are the contents of this directory???
My build directory is simply a symbolic link that points to /usr/src/linux-headers-2.6.20-16-generic

Also what are the contents of your
/usr/src directory?

Hopefully this isnt too confusing, b/c Im starting to lose it!

---

### Post by Peter108 on 2007-08-15
```
peter@cosmo:/lib/modules/2.6.20-16-server$ ls -la build
total 8
drwxr-xr-x 2 root root 4096 2007-08-15 10:22 .
drwxr-xr-x 5 root root 4096 2007-08-15 09:22 ..
lrwxrwxrwx 1 root root   40 2007-08-15 10:21 linux-headers-2.6.20-16-generic -> /usr/src/linux-headers-2.6.20-16-generic
```


```
peter@cosmo:/usr/src$ ls -la
total 20
drwxrwsr-x  5 root src  4096 2007-08-15 09:25 .
drwxr-xr-x 11 root root 4096 2007-08-02 09:41 ..
drwxr-xr-x 20 root root 4096 2007-08-02 09:47 linux-headers-2.6.20-16
drwxr-xr-x  4 root root 4096 2007-08-02 09:47 linux-headers-2.6.20-16-generic
drwxr-xr-x  4 root root 4096 2007-08-15 09:25 linux-headers-2.6.20-16-server
```

I'm guessing you didn't want recursion on that second one:)

---

### Post by Peter108 on 2007-08-15
Oh, and per your instructions, I did get rid of build from /lib/modules/2.6.20-16-generic.

---

### Post by kevdog on 2007-08-15
Ok 

getting to the bottom of this

cd /lib/modules/2.6.20-16-server/build
rm linux-headers-2.6.20-16-generic
cd..
rmdir build

I need to make a symbolic link at this point but I dont know whether to link to 
/usr/src/linux-headers-2.6.20-16-server  or
/usr/src/linux-headers-2.6.20-16-generic

I do not have a /usr/src/linux-headers-2.6.20-16-server directory.


Is there any difference in these two directories? (my generic directories are full of symbolic links that point to 2.6.20-16)

---

### Post by Peter108 on 2007-08-15
Did the rm/rmdir, per your instructions.

Regarding

 "I need to make a symbolic link at this point but I dont know whether to link to
/usr/src/linux-headers-2.6.20-16-server or
/usr/src/linux-headers-2.6.20-16-generic"

on my machine, the two dirs have appear to have identical content. 


```
peter@cosmo:/usr/src$ ls -al [COLOR="Red"]**linux-headers-2.6.20-16-server**[/COLOR]
total 572
drwxr-xr-x 4 root root   4096 2007-08-15 09:25 .
drwxrwsr-x 5 root src    4096 2007-08-15 09:25 ..
lrwxrwxrwx 1 root root     31 2007-08-15 09:25 arch -> ../linux-headers-2.6.20-16/arch
lrwxrwxrwx 1 root root     32 2007-08-15 09:25 block -> ../linux-headers-2.6.20-16/block
-rw-r--r-- 1 root root  83281 2007-06-07 12:15 .config
lrwxrwxrwx 1 root root     33 2007-08-15 09:25 crypto -> ../linux-headers-2.6.20-16/crypto
lrwxrwxrwx 1 root root     34 2007-08-15 09:25 drivers -> ../linux-headers-2.6.20-16/drivers
lrwxrwxrwx 1 root root     29 2007-08-15 09:25 fs -> ../linux-headers-2.6.20-16/fs
drwxr-xr-x 4 root root   4096 2007-08-15 09:25 include
lrwxrwxrwx 1 root root     31 2007-08-15 09:25 init -> ../linux-headers-2.6.20-16/init
lrwxrwxrwx 1 root root     30 2007-08-15 09:25 ipc -> ../linux-headers-2.6.20-16/ipc
lrwxrwxrwx 1 root root     33 2007-08-15 09:25 kernel -> ../linux-headers-2.6.20-16/kernel
lrwxrwxrwx 1 root root     30 2007-08-15 09:25 lib -> ../linux-headers-2.6.20-16/lib
-rw-r--r-- 1 root root  50526 2007-06-07 14:11 Makefile
lrwxrwxrwx 1 root root     29 2007-08-15 09:25 mm -> ../linux-headers-2.6.20-16/mm
-rw-r--r-- 1 root root 414274 2007-06-07 14:08 Module.symvers
lrwxrwxrwx 1 root root     30 2007-08-15 09:25 net -> ../linux-headers-2.6.20-16/net
drwxr-xr-x 9 root root   4096 2007-08-15 09:25 scripts
lrwxrwxrwx 1 root root     35 2007-08-15 09:25 security -> ../linux-headers-2.6.20-16/security
lrwxrwxrwx 1 root root     32 2007-08-15 09:25 sound -> ../linux-headers-2.6.20-16/sound
lrwxrwxrwx 1 root root     33 2007-08-15 09:25 ubuntu -> ../linux-headers-2.6.20-16/ubuntu
lrwxrwxrwx 1 root root     30 2007-08-15 09:25 usr -> ../linux-headers-2.6.20-16/usr
```


```
peter@cosmo:/usr/src$ ls -al[COLOR="Red"]** linux-headers-2.6.20-16-generic**[/COLOR]
total 572
drwxr-xr-x 4 root root   4096 2007-08-02 09:47 .
drwxrwsr-x 5 root src    4096 2007-08-15 09:25 ..
lrwxrwxrwx 1 root root     31 2007-08-02 09:47 arch -> ../linux-headers-2.6.20-16/arch
lrwxrwxrwx 1 root root     32 2007-08-02 09:47 block -> ../linux-headers-2.6.20-16/block
-rw-r--r-- 1 root root  83217 2007-06-07 11:16 .config
lrwxrwxrwx 1 root root     33 2007-08-02 09:47 crypto -> ../linux-headers-2.6.20-16/crypto
lrwxrwxrwx 1 root root     34 2007-08-02 09:47 drivers -> ../linux-headers-2.6.20-16/drivers
lrwxrwxrwx 1 root root     29 2007-08-02 09:47 fs -> ../linux-headers-2.6.20-16/fs
drwxr-xr-x 4 root root   4096 2007-08-02 09:47 include
lrwxrwxrwx 1 root root     31 2007-08-02 09:47 init -> ../linux-headers-2.6.20-16/init
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 ipc -> ../linux-headers-2.6.20-16/ipc
lrwxrwxrwx 1 root root     33 2007-08-02 09:47 kernel -> ../linux-headers-2.6.20-16/kernel
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 lib -> ../linux-headers-2.6.20-16/lib
-rw-r--r-- 1 root root  50527 2007-06-07 13:59 Makefile
lrwxrwxrwx 1 root root     29 2007-08-02 09:47 mm -> ../linux-headers-2.6.20-16/mm
-rw-r--r-- 1 root root 414274 2007-06-07 13:56 Module.symvers
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 net -> ../linux-headers-2.6.20-16/net
drwxr-xr-x 9 root root   4096 2007-08-02 09:47 scripts
lrwxrwxrwx 1 root root     35 2007-08-02 09:47 security -> ../linux-headers-2.6.20-16/security
lrwxrwxrwx 1 root root     32 2007-08-02 09:47 sound -> ../linux-headers-2.6.20-16/sound
lrwxrwxrwx 1 root root     33 2007-08-02 09:47 ubuntu -> ../linux-headers-2.6.20-16/ubuntu
lrwxrwxrwx 1 root root     30 2007-08-02 09:47 usr -> ../linux-headers-2.6.20-16/usr
peter@cosmo:/usr/src$
```

---

### Post by kevdog on 2007-08-15
Well ok then lets try the following:

cd /lib/modules/2.6.20-16-server
ln -s /usr/src/linux-headers-2.6.20-16-server build

Hopefully that should do the trick
If you do a ls -la, hopefully build will point to the server directory.

---

### Post by Peter108 on 2007-08-15
A purtier sight I never did see!  However I did neglect to use sudo.  I see no permissions errors, so assume it's OK to continue.  What say you?  

```
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ [COLOR="Red"]make distclean[/COLOR]
make -C driver clean
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make -C utils clean
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
rm -f *~
rm -fr ndiswrapper-1.48rc1 ndiswrapper-1.48rc1.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make -C utils distclean
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
rm -f .\#*
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$
```

With gratitude,

---

### Post by kevdog on 2007-08-15
Really only need the sudo infront of the sudo make install statement.  Yea keep going -- I almost forgot what your original problem was.  We've been dealing with the path/symbolic link issue for so dang long, I lost sight of the forest through the trees.:)

---

### Post by Peter108 on 2007-08-15
OK, I made it through the install.  Next challenge: When I get to 
"Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:"

I get this:
```

peter@cosmo:~/driver$[COLOR="Red"] sudo ndiswrapper -i *****.inf[/COLOR]
installing ***** ...
couldn't open *****.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.
peter@cosmo:~/driver$ 

```

Here, FWIW, is everything that preceded it, starting w/ make distclean:

```
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$[COLOR="Red"] make distclean[/COLOR]
make -C driver clean
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make -C utils clean
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
rm -f *~
rm -fr ndiswrapper-1.48rc1 ndiswrapper-1.48rc1.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h built-in.o
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make -C utils distclean
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
rm -f .\#*
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ [COLOR="Red"]make[/COLOR]
make -C driver
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make -C /usr/src/linux-headers-2.6.20-16-server SUBDIRS=/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-server'
  LD      /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/built-in.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/crt.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/hal.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/iw_ndis.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/loader.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/ndis.o
/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/ndis.c: In function ‘NdisMFreeMapRegisters’:
/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/ndis.c:937: warning: cast to pointer from integer of different size
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/ntoskernel.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/ntoskernel_io.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/pe_linker.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/pnp.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/proc.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/rtl.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/wrapmem.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/wrapndis.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/wrapper.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/usb.o
  CC [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/divdi3.o
  LD [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/ndiswrapper.mod.o
  LD [M]  /home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-server'
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make -C utils
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ [COLOR="Red"]sudo make install[/COLOR]
Password:
make -C driver install
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make -C /usr/src/linux-headers-2.6.20-16-server SUBDIRS=/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-server'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-server'
echo /lib/modules/2.6.20-16-server/misc
/lib/modules/2.6.20-16-server/misc
mkdir -p /lib/modules/2.6.20-16-server/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-16-server/misc
/sbin/depmod -a 2.6.20-16-server -b /
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/driver'
make -C utils install
make[1]: Entering directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/peter/ndiswrapper/ndiswrapper-1.48rc1/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$ [COLOR="Red"]ndiswrapper -v[/COLOR]
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-server/misc/ndiswrapper.ko
version:        1.48rc1
vermagic:       2.6.20-16-server SMP mod_unload 686 
peter@cosmo:~/ndiswrapper/ndiswrapper-1.48rc1$[COLOR="Red"] cd ~[/COLOR]
peter@cosmo:~$[COLOR="Red"] mkdir driver[/COLOR]
peter@cosmo:~$[COLOR="Red"] cd driver[/COLOR]
peter@cosmo:~/driver$[COLOR="Red"] sudo ndiswrapper -i *****.inf[/COLOR]
installing ***** ...
couldn't open *****.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.
peter@cosmo:~/driver$
```

---

### Post by kevdog on 2007-08-15
Can you post your driver version, maybe in a zip file so I can try installing it on my machine??

Ive seen this damn error before, and I cant remember a workaround.  

Where did you get your driver?  Have you checked the ndiswrapper website for a possible alternative?

---

### Post by Peter108 on 2007-08-15
Well, again I have to plead noob.  Can you tell me where/how to find the driver/version.  

Meanwhile,  I'll check the website.  Also, did you notice this message in the make install:

```
NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
```

Part of the puzzle?

---

### Post by kevdog on 2007-08-15
Few things,

can you repost (with the broadcard card turned on)
lshw -C network
lspci -nn

Make sure that the /etc/ndiswrapper file is completely empty (sudo rm -R /etc/ndiwrapper/*)

Where did you get your drivers you were trying to install anyway?? From CD or download??

Dont know what to make about the Windows error message thing (for right now!)  I dont think you installed the windows drivers before (or did you)??? I think this message if meant for people upgrading the ndiswrapper version.

---

### Post by Peter108 on 2007-08-15
```
peter@cosmo:/windows$ [COLOR="Red"]lshw -C network[/COLOR]
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth1
       version: 10
       serial: 00:0f:b0:4c:46:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.106 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:17
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: iomemory:e0104000-e0105fff irq:11
peter@cosmo:/windows$[COLOR="Red"] lspci -nn[/COLOR]
00:00.0 Host bridge [0600]: nVidia Corporation nForce3 Host Bridge [10de:00d1] (rev a4)
00:01.0 ISA bridge [0601]: nVidia Corporation nForce3 LPC Bridge [10de:00d0] (rev a6)
00:01.1 SMBus [0c05]: nVidia Corporation nForce3 SMBus [10de:00d4] (rev a4)
00:02.0 USB Controller [0c03]: nVidia Corporation nForce3 USB 1.1 [10de:00d7] (rev a5)
00:02.1 USB Controller [0c03]: nVidia Corporation nForce3 USB 1.1 [10de:00d7] (rev a5)
00:02.2 USB Controller [0c03]: nVidia Corporation nForce3 USB 2.0 [10de:00d8] (rev a2)
00:06.0 Multimedia audio controller [0401]: nVidia Corporation nForce3 Audio [10de:00da] (rev a2)
00:06.1 Modem [0703]: nVidia Corporation nForce3 Audio [10de:00d9] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation nForce3 IDE [10de:00d5] (rev a5)
00:0a.0 PCI bridge [0604]: nVidia Corporation nForce3 PCI Bridge [10de:00dd] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation nForce3 AGP Bridge [10de:00d2] (rev a4)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 420 Go 32M] [10de:0179] (rev a3)
02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
02:04.0 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.1 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.2 System peripheral [0880]: Texas Instruments PCI1620 Firmware Loading Function [104c:8201] (rev 01)
peter@cosmo:/windows$ 
```

I cannot turn on my broadcomm switch anymore.  Nothing happens when I try.  That's part of the mess.  As is the fact that Network Manager doesn't even list my essid anymore or show wireless as an option for manual configuration.   

Regarding drivers, I began this journey by following the steps in [URL="http://ubuntuforums.org/showthread.php?t=185174"]Howto:Broadcom Wireless Cards
[/URL], (I just now recall) fetching the driver from the WinXP side of my dual-boot machine (the side whose Broadcom wireless works flawlessly, FYI).   Attached is a tar.gz containing 
[LIST]
[*]bcmwl5.sys (the driver) 
[*]wl_apsta.o (the firmware extracted and installed by fw-cutter)
[/LIST]

One other thing: When I began this thread,  my wireless network  was being recognized by Network Manager. And the signal was plenty strong.  It was only after following the advice (well-intentioned, of course) in post #14 of this thread and going through the steps in  [HOWTO: Broadcom 43xx based wireless cards the EASY way]("http://ubuntuforums.org/showthread.php?t=405990") (hardee har har) that things went completely to hell.  That's where you joined the fray.

---

### Post by kevdog on 2007-08-15
Do you have an installation disk with the windows xp drivers on them??

The drivers you posted are the bcm43xx drivers and are definitely the wrong ones.  The reason your card  isnt working or lights not on is b/c the drivers are not installed yet

---

### Post by Peter108 on 2007-08-15
The driver I'm running right now on the WinXP side of the machine is 
BCMWL5.SYS 
4.100.15.5 
10/12/2006

I don't believe I have the install disk, but I do have a copy of not only the above driver, but the newer version (which I just pulled off my Vista machine), BCMWL6.SYS.    I've copied them both into my home dir on the Ubuntu side.  And I can grab anything else I want/need out of the Windows partition (like BCMWL5.PNF and BCMWL5.inf)

Will one of these work?  If so, how do I install?  

[Update:  Turns out I have WinXP "recovery" disks, FWIW, plus of course my FF 7.04 server install disk]

---

### Post by kevdog on 2007-08-15
no vista drivers the winxp .sys and .inf files are good.  the bcmwl5 files. put them in the ~/driver directory and then install them as per the instructions:)

---

### Post by Peter108 on 2007-08-16
OK.  Getting closer.  Do I need to undo my mistake of issuing the literal command (duh)
```

ndiswrapper -i *****.inf

```
instead of 
```

ndiswrapper -i bcmwl5.inf
```

I did both, and now see

```
peter@cosmo:~/driver$ ndiswrapper -l
***** : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
peter@cosmo:~/driver$ 
```

IOW, do I need to get rid of that first entry before going forward?   I tried, with the following result:
```

peter@cosmo:~/driver$ sudo ndiswrapper -r  *****.inf
couldn't delete /etc/ndiswrapper/bcmwl5.inf: No such file or directory
```

---

### Post by kevdog on 2007-08-16
```
sudo rm -R /etc/ndiswrapper/*
```

Make sure the /etc/ndiswrapper directory is completely empty

Then begin at
sudo ndiswrapper -i  step

---

### Post by Peter108 on 2007-08-16
Here's what's in /etc/ndiswrapper.  Life gets tricky when your command target is a wildcard](*,)

```
peter@cosmo:~/driver$[COLOR="Red"] cd /etc/ndiswrapper[/COLOR]
peter@cosmo:/etc/ndiswrapper$[COLOR="Red"] ls -al[/COLOR]
total 16
drwxr-xr-x   4 root root 4096 2007-08-16 06:48 .
drwxr-xr-x 111 root root 4096 2007-08-16 06:45 ..
[COLOR="Red"]drwxr-xr-x   2 root root 4096 2007-08-15 15:26 *****
drwxr-xr-x   2 root root 4096 2007-08-16 06:48 bcmwl5[/COLOR]
peter@cosmo:/etc/ndiswrapper$ [COLOR="Red"]cd bcmwl5[/COLOR]
peter@cosmo:/etc/ndiswrapper/bcmwl5$[COLOR="Red"] ls -al[/COLOR]
total 1180
drwxr-xr-x 2 root root   4096 2007-08-16 06:48 .
drwxr-xr-x 4 root root   4096 2007-08-16 06:48 ..
-rw-r--r-- 1 root root    922 2007-08-16 06:48 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    922 2007-08-16 06:48 14E4:4311:1364:103C.5.conf
-rw-r--r-- 1 root root    922 2007-08-16 06:48 14E4:4311:1365:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 06:48 14E4:4311.5.conf -> 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    978 2007-08-16 06:48 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    978 2007-08-16 06:48 14E4:4312:1360:103C.5.conf
-rw-r--r-- 1 root root    978 2007-08-16 06:48 14E4:4312:1361:103C.5.conf
-rw-r--r-- 1 root root    978 2007-08-16 06:48 14E4:4312:1362:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 06:48 14E4:4312.5.conf -> 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 06:48 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 06:48 14E4:4318:1356:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 06:48 14E4:4318:1357:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 06:48 14E4:4318.5.conf -> 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    974 2007-08-16 06:48 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    974 2007-08-16 06:48 14E4:4319:1359:103C.5.conf
-rw-r--r-- 1 root root    974 2007-08-16 06:48 14E4:4319:135A:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 06:48 14E4:4319.5.conf -> 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 06:48 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    941 2007-08-16 06:48 14E4:4320:12F4:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 06:48 14E4:4320:12F8:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 06:48 14E4:4320:12FA:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 06:48 14E4:4320:12FB:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 06:48 14E4:4320.5.conf -> 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    974 2007-08-16 06:48 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root    974 2007-08-16 06:48 14E4:4324:12FC:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 06:48 14E4:4324.5.conf -> 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root 675862 2007-08-16 06:48 bcmwl5.inf
-rw-r--r-- 1 root root 429184 2007-08-16 06:48 bcmwl5.sys
```

---

### Post by kevdog on 2007-08-16
cd /etc/ndiswrapper

Hmm this could be challenging

cd *****
sudo rm *
cd ..
sudo rm -R bcmwl5

Now the hard part!!

sudo ndiswrapper -r *****

If that doesnt work (by making the /etc/ndiswrapper directory empty) try
sudo rmdir *****

Please post /etc/ndiswrapper after doing this if it doesnt work.

---

### Post by Peter108 on 2007-08-16
OK, I think we're good.   I went straight to the rm -R ***** (rather than trying ndiswrapper -r *****) b/c that dir was already empty.  I re-did ndiswrapper -i bcmwl5.inf and now see

```
peter@cosmo:~/driver$ [COLOR="Red"]ndiswrapper -l[/COLOR]
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
peter@cosmo:~/driver$ 
```

And here's what /etc/ndiswrapper looks like:

```
peter@cosmo:/etc/ndiswrapper$ [COLOR="Red"]ls -al[/COLOR]
total 12
drwxr-xr-x   3 root root 4096 2007-08-16 07:46 .
drwxr-xr-x 111 root root 4096 2007-08-16 06:45 ..
drwxr-xr-x   2 root root 4096 2007-08-16 07:46 bcmwl5
peter@cosmo:/etc/ndiswrapper$[COLOR="Red"] ls -al bcmwl5[/COLOR]
total 1180
drwxr-xr-x 2 root root   4096 2007-08-16 07:46 .
drwxr-xr-x 3 root root   4096 2007-08-16 07:46 ..
-rw-r--r-- 1 root root    922 2007-08-16 07:46 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    922 2007-08-16 07:46 14E4:4311:1364:103C.5.conf
-rw-r--r-- 1 root root    922 2007-08-16 07:46 14E4:4311:1365:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 07:46 14E4:4311.5.conf -> 14E4:4311:1363:103C.5.conf
-rw-r--r-- 1 root root    978 2007-08-16 07:46 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    978 2007-08-16 07:46 14E4:4312:1360:103C.5.conf
-rw-r--r-- 1 root root    978 2007-08-16 07:46 14E4:4312:1361:103C.5.conf
-rw-r--r-- 1 root root    978 2007-08-16 07:46 14E4:4312:1362:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 07:46 14E4:4312.5.conf -> 14E4:4312:135F:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 07:46 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 07:46 14E4:4318:1356:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 07:46 14E4:4318:1357:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 07:46 14E4:4318.5.conf -> 14E4:4318:1355:103C.5.conf
-rw-r--r-- 1 root root    974 2007-08-16 07:46 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    974 2007-08-16 07:46 14E4:4319:1359:103C.5.conf
-rw-r--r-- 1 root root    974 2007-08-16 07:46 14E4:4319:135A:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 07:46 14E4:4319.5.conf -> 14E4:4319:1358:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 07:46 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    941 2007-08-16 07:46 14E4:4320:12F4:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 07:46 14E4:4320:12F8:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 07:46 14E4:4320:12FA:103C.5.conf
-rw-r--r-- 1 root root    918 2007-08-16 07:46 14E4:4320:12FB:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 07:46 14E4:4320.5.conf -> 14E4:4320:00E7:0E11.5.conf
-rw-r--r-- 1 root root    974 2007-08-16 07:46 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root    974 2007-08-16 07:46 14E4:4324:12FC:103C.5.conf
lrwxrwxrwx 1 root root     26 2007-08-16 07:46 14E4:4324.5.conf -> 14E4:4324:12F9:103C.5.conf
-rw-r--r-- 1 root root 675862 2007-08-16 07:46 bcmwl5.inf
-rw-r--r-- 1 root root 429184 2007-08-16 07:46 bcmwl5.sys
peter@cosmo:/etc/ndiswrapper$
``` 

Have a conf call.  Back in 30 mins to continue.  I'm assuming I'm good to go.  Thanks!

---

### Post by kevdog on 2007-08-16
Keep going -- Im sure there will be more bumps in the road ahead!!!

---

### Post by bmartin on 2007-08-16
Try this: **sudo ndiswrapper -r '*****'**

I added a ***** driver on mine, then I used that command and it removed it :KS

Also do **sudo rm -r '/etc/ndiswrapper/*****'**

I tried that on my computer, too, and it had the desired effect.

---

### Post by Peter108 on 2007-08-16
dmesg shows a successful load of ndiswrapper, but should I be concerned about the last line?

```
[COLOR="Red"][48391.450000] ndiswrapper version 1.48rc1 loaded (smp=yes)[/COLOR]
[48391.490000] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[48391.490000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
[48391.490000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNK3] -> GSI 17 (level, low) -> IRQ 21
[48391.500000] ndiswrapper: using IRQ 21
[48391.990000] wlan0: ethernet device 00:90:4b:b7:e2:40 using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[48391.990000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[48391.990000] usbcore: registered new interface driver ndiswrapper
[48392.050000] ndiswrapper: changing interface name from 'wlan0' to 'eth0'
[48392.330000] [COLOR="Red"]ADDRCONF(NETDEV_UP): eth0: link is not ready[/COLOR]
peter@cosmo:~/driver$ 
```

---

### Post by bmartin on 2007-08-16
Yes, the last line is a problem, but the driver is installed correctly and it has recognized your card. This is usually the toughest step. Your best bet is to uninstall network-manager
```
sudo apt-get remove network-manager
```
and install [wifi-radar]("http://blakecmartin.googlepages.com/wifi-radar.html") or [wicd]("http://blakecmartin.googlepages.com/wicd.html"). My apologies if you already have one of them. I'm watching several threads and I don't really remember who did what.

---

### Post by kevdog on 2007-08-16
eth0 is usually your wired interface.  But I see the line: 

ndiswrapper: changing interface name from 'wlan0' to 'eth0'

For right now just keep following the instructions with the 
sudo ndiswrapper -m

We may need to modify the /etc/iftab device in order to associate the MAC address of your wireless card with wlan0 rather than eth0.

Keep following the instructions.

---

### Post by Peter108 on 2007-08-16
OK, will do.  But I didn't see your reply before blowing away Network Manager and installing wifi-radar.  Tried to configure it, but am confused.  Will return to the ndiswrapper commands and report back.

---

### Post by kevdog on 2007-08-16
With either of these tools - wifi, wicd, network manager -- if you dont have a working driver for you device down below, none of them are going to work.  I prefer wicd, but you have to configure things in the appropriate manner before you start jumping 2 steps ahead.

---

### Post by Peter108 on 2007-08-16
OK, I've executed the final step in your install instructions from post #16. 
```

sudo shutdown -r now
```

I've removed wifi-manager and installed wicd.  If it's good enough for you, it's good enough for me.   Where to from here?  Thanks!!!

---

### Post by Peter108 on 2007-08-16
Attached find current router wireless settings, w/ keys concealed.  

Wicd connects to my network and shows 81% signal strength.  Preferences show 

wpa supplicant driver = wext
wireless interface = eth0
wired interface = eth0

Still no functionality, though.  And pinging my router returns "Destination Host Unreachable"

---

### Post by Peter108 on 2007-08-16
Other diagnostics:
```
peter@cosmo:~/tmp$ [COLOR="Red"]lshw -C network[/COLOR]
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth1
       version: 10
       serial: 00:0f:b0:4c:46:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.106 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:17
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 03
       serial: 00:90:4b:b7:e2:40
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.48rc1+Broadcom,03/23/2006, 4.4 ip=192.168.0.102 latency=64 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:e0104000-e0105fff irq:21
peter@cosmo:~/tmp$[COLOR="Red"] lspci -nn[/COLOR]
00:00.0 Host bridge [0600]: nVidia Corporation nForce3 Host Bridge [10de:00d1] (rev a4)
00:01.0 ISA bridge [0601]: nVidia Corporation nForce3 LPC Bridge [10de:00d0] (rev a6)
00:01.1 SMBus [0c05]: nVidia Corporation nForce3 SMBus [10de:00d4] (rev a4)
00:02.0 USB Controller [0c03]: nVidia Corporation nForce3 USB 1.1 [10de:00d7] (rev a5)
00:02.1 USB Controller [0c03]: nVidia Corporation nForce3 USB 1.1 [10de:00d7] (rev a5)
00:02.2 USB Controller [0c03]: nVidia Corporation nForce3 USB 2.0 [10de:00d8] (rev a2)
00:06.0 Multimedia audio controller [0401]: nVidia Corporation nForce3 Audio [10de:00da] (rev a2)
00:06.1 Modem [0703]: nVidia Corporation nForce3 Audio [10de:00d9] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation nForce3 IDE [10de:00d5] (rev a5)
00:0a.0 PCI bridge [0604]: nVidia Corporation nForce3 PCI Bridge [10de:00dd] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation nForce3 AGP Bridge [10de:00d2] (rev a4)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 420 Go 32M] [10de:0179] (rev a3)
02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
02:04.0 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.1 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.2 System peripheral [0880]: Texas Instruments PCI1620 Firmware Loading Function [104c:8201] (rev 01)
peter@cosmo:~/tmp$ 
```

Here's /etc/iftab

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:90:4b:b7:e2:40 arp 1
eth1 mac 00:0f:b0:4c:46:89 arp 1


The eth1 MAC matches what my router displays as the "WAN" MAC address.
However, my router shows a different value both for the "wireless" and "LAN" MACs ( 00-0D-88-28-D7-94) than is shown above for eth0

---

### Post by kevdog on 2007-08-16
Edit your iftab file:

gksu gedit /etc/iftab

Whatever the MAC address is of your wired rtl card -- make that eth0.
Whatever the MAC address of your wireless card is -- make that wlan0.

Make sure that /etc/modprobe.d/ndiswrapper is alias wlan0 ndiswrapper (thats what the ndiswrapper -m command does).

Also make sure ndiswrapper is mentioned on one line in /etc/modules.

Reboot.

Then post the results of 
iwlist scan

Since you uninstalled network manager, the interface is going to be activated "automatically"
We will bring it up by hand at first, and then transition over to wicd (just to check for any errors).

Give me a chance to view the files you posted.

---

### Post by Peter108 on 2007-08-16
Glad I retried w/ sudo.  **Also, for iftab's wlan0 entry, I used the "serial" line from "lshw -C network".  I notice that "iwlist scan" reports a different value on the "Address" line?  Which is the correct value for iftab?**

Take 1:
```
peter@cosmo:~$ [COLOR="Red"]iwlist scan[/COLOR]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```

Take 2:
```
peter@cosmo:~$ [COLOR="Red"]sudo iwlist scan[/COLOR]
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0D:88:28:D7:94
                    ESSID:"xkred27"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

peter@cosmo:~$ 
```

[LIST]
[*]Confirmed wlan0 alias in /etc/modprobe.d/ndiswrapper
[*]After updating iftab and rebooting lost wired functionality
[*]Wireless also still not functioning
[*]Pinging the router from either wired/wireless returns "connect: Network is unreachable"
[*]But that little blue wireless light is on (and may have been on for some time, but I just noticed it)
[/LIST]

/etc/iftab:

```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.
# Following 2 lines are original entries prior to manual configuration
#eth0 mac 00:90:4b:b7:e2:40 arp 1
#eth1 mac 00:0f:b0:4c:46:89 arp 1
#
# Following are mods as per kevdog
# Wired: RTL-8139/8139C/8139C+ MAC address obtained from lshw
[COLOR="Red"]eth0 mac 00:0f:b0:4c:46:89 arp 1[/COLOR]
# Wireless: BCM4306 802.11b/g Wireless LAN Controller MAC address obtained from lshw
[COLOR="Red"]wlan0 mac 00:90:4b:b7:e2:40 arp 1[/COLOR]
```

---

### Post by kevdog on 2007-08-16
Couple of things

You cant run wired and wireless at the same time unless you configure the cards to be on different subnets.

The MAC addresses for you cards are correct -- you find them with lshw -C network

The address listed in iwlist scan is the MAC address of your router.

Comment out everything in the /etc/iftab file -- Im not sure what is going on.  It doesnt matter anyway.  Reboot  -- unhook the ethernet cable -- we are going strictly wireless

After reboot, determine the interface name (logical name) of the wireless card through lshw -C network

Make sure you can see the router through iwlist scan (or with use of sudo).
If router is successfully seen, ensure all encryption WEP/WPA is off (looks like it is from what you posted).
Then do the following

<in>=eth1 or eth0 or wlan0, etc. <<---depends what you found in lshw -C network as your logical name

sudo ifconfig <in> down
sudo ifconfig <in> up 
sudo iwconfig <in> essid "xkred27" mode Managed
sudo dhclient <in>

See if now you are connected to the router --- ie ping the routers ip address
ping xxx.xxx.xxx.xxx

---

### Post by Peter108 on 2007-08-16
Kevdog, FYI, I'm replying to your last post using Ubuntu 7.04, Firefox, and a [COLOR="Blue"]FUNCTIONING WIRELESS CONNECTION[/COLOR].  [COLOR="Red"]HOLY S**T!!![/COLOR]=D>

Details below.  What next? (That is, after I finish prostrating before my laptop)

```
peter@cosmo:~$ [COLOR="Red"]lshw -C network[/COLOR]
peter@cosmo:~$ sudo [COLOR="Red"]lshw -C network[/COLOR]
Password:
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:4c:46:89
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:17
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:b7:e2:40
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.48rc1+Broadcom,03/23/2006, 4.4 latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:e0104000-e0105fff irq:21
peter@cosmo:~$ [COLOR="Red"]sudo iwlist scan[/COLOR]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0D:88:28:D7:94
                    ESSID:"xkred27"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

peter@cosmo:~$ [COLOR="Red"]sudo ifconfig wlan0 down[/COLOR]
peter@cosmo:~$[COLOR="Red"] sudo ifconfig wlan0 up[/COLOR]
peter@cosmo:~$ [COLOR="Red"]sudo iwconfig wlan0 essid "xkred27" mode Managed[/COLOR]
peter@cosmo:~$[COLOR="Red"] sudo dhclient wlan0[/COLOR]
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:90:4b:b7:e2:40
Sending on   LPF/wlan0/00:90:4b:b7:e2:40
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.102 -- renewal in 236688 seconds.
peter@cosmo:~$[COLOR="Red"] ping -c 5 192.168.0.1[/COLOR]
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=255 time=12.6 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=255 time=1.51 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=255 time=1.33 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=255 time=1.45 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=255 time=2.84 ms

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 1.337/3.956/12.636/4.374 ms
```

---

### Post by kevdog on 2007-08-16
Glad you got it working - b/c from what you posted I dont know what to make??

```
 *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
```

What's all this DISABLED business??? Its working isn't it.  I guess there are something I dont understand??

Just for my curiosity, can you just verify that it doesnt say DISABLED when you are actually connected -- I think you have to bring the interface up (ie sudo ifconfig wlan0 up) for the DISABLED to go away.

Ok, you probably dont want to type all this crap everytime you want to get an internet connection (however save these commands in a file -- one day when the SH** hits the fan, you will have to rely on a manual connection -- trust me on this one).

Anyway you probably want to use wicd so things are done automatically!!

To release your DHCP address
sudo dhclient -r wlan0

I hope you have at least the 1.33 release of wicd.  
Again for the first time we are going to fire up wicd manually:
Hit alt-F2 and type in “/opt/wicd/gui.py” <----Dont need the quotes

When the GUI pops open, see if you can connect to you wireless network, also check the about box.  If you are running v 1.3.1 then we will upgrade to actually the developmental svn releases (thats what Im running).

Let me know if WICD is working for you.  You can set it up to run at boot time by doing the following
System->Preferences->Sessions
Create a new Session called wicd with the command /opt/wicd/gui.py.  Make sure tick box is enabled.

If something doesnt work with wicd, report back so we can upgrade to the svn sources.

---

### Post by Peter108 on 2007-08-16
DISABLED was before I did
peter@cosmo:~$ sudo ifconfig wlan0 down
peter@cosmo:~$ sudo ifconfig wlan0 up
peter@cosmo:~$ sudo iwconfig wlan0 essid "xkred27" mode Managed
peter@cosmo:~$ sudo dhclient wlan0

Right now, w/ a functioning connection I get
```
peter@cosmo:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:4c:46:89
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:17
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:b7:e2:40
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.48rc1+Broadcom,03/23/2006, 4.4 ip=192.168.0.102 latency=64 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:e0104000-e0105fff irq:21

```

Bring up wicd gives me

```
attempting to connect daemon...
success
starting...
refreshing...
disabling ip
disabling dns
no wired profiles found
1
ESSID : xkred27
making a new network entry...
disabling ip
disabling dns
0


```

The wicd main page lists two entries, one for xkred27 and another for "wired network".  However the "Connect" button for the wired network is greyed-out.   I need to git to an MD appointment, but can you tell me my next steps?  I'm thinking
[LIST=1]
[*]I should reboot to see what kind of connectivity I get on restart
[*]Get my wired connection working
[*]Get my wireless connection working w/ WEP
[/LIST]
Thoughts?

---

### Post by kevdog on 2007-08-16
Again, you can only run wired or wireless at one time.  Its probably greyed out since you booted without the network cable not in place??

Id go for WPA over WEP, but some of this is router dependent.  If you want to use WEP, select the arrow next to your wireless connection on the main page, then advanced settings, Use encryption, WEP, and then enter your hex key.  You can choose to start this connection at boot if you want or you can start it manually through the GUI.  

WICD is pretty self explanatory.  Just go through the menus and such.  You will be able to figure it out!!
WPA can be tricky, however with some work, its not too bad either!

---

### Post by imdano on 2007-08-16
The wired connect button is probably greyed out because you haven't made a wired profile yet.  Click the "Wired Network" expander, enter a name for the profile in the text box you see, press "add", and you should be all set.

---

### Post by Peter108 on 2007-08-17
imdano,

Thanks.  That was absolutely it.  Now the only remaining problem is getting the wireless to work w/ WEP encryption enabled.  On my router (a D-Link DI514), I'm given the option of 64/128 bit and HEX/ascii.  So I have four possilbe choices.  I don't know if wicd forces one choice, since when you check the use encryption box, the dropdown menu gives a choice of "WEP".  Not sure that it matter b/c with any of the four choices, I get the same result:  If you click connect, it jus hangs while "obtaining IP address."

If I disable WEP on the router, everything works fine.  Even if I "use encryption[WEP]" checked in wicd, as long as its disable on the router, wireless will work.  But of course I have me a totally unsecured network here, so there's unfinished business.  

Am running 1.3.1.  Does anyone know if upgrading to 1.3.3 would make a difference?

Thanks.  And particular, thanks to kevdog who gave generously of his time and expertise.

---

### Post by kevdog on 2007-08-17
Here try this, again Im defaulting back to command line (just for debugging purposes)

64bit WEP (5 character ASCII password) is associated with a 10 character hexkey

128bit WEP (13 character ASCII password) is with a 26 character hexkey

Some routers you type in the ascii key, and it generates the hex.  Others do not. 
Lets just start out with 64bit for right now, then go to 128bit if everything is working.

***Note key can be either in hex or ascii.  

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "xkred27" mode Managed

#Use **only** one of the following lines below - #1 for hex key, #2 for ASCII key - prepend s: to denote ASCII
sudo iwconfig key XXXXXXXXXX
sudo iwconfig key s:ASCII

sudo dhclient wlan0

---

### Post by Peter108 on 2007-08-17
Quick question:

Should I go into the router's web interface and enable 64 bit WEP first, or are these commands doing that?

---

### Post by kevdog on 2007-08-17
Gotta change the settings in the router first!

---

### Post by Peter108 on 2007-08-17
```
peter@cosmo:~$ sudo ifconfig wlan0 down
Password:
peter@cosmo:~$ sudo ifconfig wlan0 up
peter@cosmo:~$ sudo iwconfig wlan0 essid "xkred27" mode Managed
peter@cosmo:~$ sudo iwconfig key s:mykey
[COLOR="Red"]Error : unrecognised wireless request "s:mykey"[/COLOR]
peter@cosmo:~$ 
```

Router info attached.

---

### Post by kevdog on 2007-08-17
Sorry I typed the damn command wrong, this is the format:

sudo iwconfig wlan0 key XXXXXXXXXX
sudo iwconfig wlan0 key s:ASCII

---

### Post by Peter108 on 2007-08-17
Shoulda caught that one myself.

```
peter@cosmo:/etc/apache2$ [COLOR="Red"]sudo iwconfig wlan0 key s:xxxxx[/COLOR]
peter@cosmo:/etc/apache2$ 
peter@cosmo:/etc/apache2$[COLOR="Red"] sudo dhclient wlan0[/COLOR]
There is already a pid file /var/run/dhclient.pid with pid 27057
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:90:4b:b7:e2:40
Sending on   LPF/wlan0/00:90:4b:b7:e2:40
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.102 -- renewal in 225122 seconds.
peter@cosmo:/etc/apache2$[COLOR="Red"] ping -c 5 192.168.0.1[/COLOR]
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.106 icmp_seq=1 Destination Host Unreachable
From 192.168.0.106 icmp_seq=2 Destination Host Unreachable
From 192.168.0.106 icmp_seq=3 Destination Host Unreachable
From 192.168.0.106 icmp_seq=4 Destination Host Unreachable
From 192.168.0.106 icmp_seq=5 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 0 received, +5 errors, 100% packet loss, time 4002ms
, pipe 3
peter@cosmo:/etc/apache2$ 

```

---

### Post by kevdog on 2007-08-17
Question

Looking at your router settings

There is a box that says Network Authentication --- Disabled.  What are the choices for this??

Did you type in all the ASCII keys or just one and the router filled in the rest?

Since it looks like you are trying to use key #1 for the wep authentication try this:

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo killall dhclient dhclient3
sudo rm /var/run/dhclient.pid
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key [1] s:<ASCII password>
sudo dhclient wlan0
```

If this fails, change the router settings to hex, and enter 10 letter/number hex key and then use the following statement in the above
```

sudo iwconfig wlan0 key [1] <HEXKEY>
```

Im getting most of this stuff from:
```
man iwconfig
```

Also post:
route -n
/etc/resolv.conf

---

### Post by Peter108 on 2007-08-17
>There is a box that says Network Authentication --- Disabled. What are the choices for this??

Disabled
IEEE 802.1x
WPA-PSK
WPA

>Did you type in all the ASCII keys or just one and the router filled in the rest?

I typed them in, then selected the top one.   (FYI FWIW, if I change the "Key Type" from ASCII to HEX, I *believe* it just HEXifies the ASCII values)

>Since it looks like you are trying to use key #1 for the wep authentication try this:
Below are results from ASCII and HEX key attempts.
```
peter@cosmo:~$ sudo ifconfig wlan0 down
Password:
peter@cosmo:~$ [COLOR="Red"]sudo ifconfig wlan0 0.0.0.0[/COLOR]
peter@cosmo:~$ [COLOR="Red"]sudo killall dhclient dhclient3[/COLOR]
dhclient: no process killed
dhclient3: no process killed
peter@cosmo:~$ [COLOR="Red"]sudo rm /var/run/dhclient.pid[/COLOR]
peter@cosmo:~$ [COLOR="Red"]sudo ip route flush dev wlan0[/COLOR]
Nothing to flush.
peter@cosmo:~$ [COLOR="Red"]sudo ifconfig wlan0 up[/COLOR]
peter@cosmo:~$[COLOR="Red"] sudo iwconfig wlan0 mode Managed[/COLOR]
peter@cosmo:~$ [COLOR="Red"]sudo iwconfig wlan0 key [1] s:xxxxx[/COLOR]
peter@cosmo:~$ [COLOR="Red"]sudo dhclient wlan0[/COLOR]
There is already a pid file /var/run/dhclient.pid with pid 22714
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:90:4b:b7:e2:40
Sending on   LPF/wlan0/00:90:4b:b7:e2:40
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
send_packet: Network is down
Terminated

<[COLOR="Blue"]Take 2 after changing router settings from ASCII to HEX>[/COLOR]

peter@cosmo:~$ [COLOR="Red"]sudo ifconfig wlan0 down[/COLOR]
peter@cosmo:~$ [COLOR="Red"]sudo ifconfig wlan0 0.0.0.0[/COLOR]
peter@cosmo:~$ [COLOR="Red"]sudo killall dhclient dhclient3[/COLOR]
dhclient3: no process killed
peter@cosmo:~$ [COLOR="Red"]sudo rm /var/run/dhclient.pid[/COLOR]
peter@cosmo:~$ [COLOR="Red"]sudo ip route flush dev wlan0[/COLOR]
Nothing to flush.
peter@cosmo:~$[COLOR="Red"] sudo ifconfig wlan0 up[/COLOR]
peter@cosmo:~$[COLOR="Red"] sudo iwconfig wlan0 mode Managed[/COLOR]
peter@cosmo:~$ [COLOR="Red"]sudo iwconfig wlan0 key [1] nnnnnnnnnn[/COLOR]
peter@cosmo:~$[COLOR="Red"] sudo dhclient wlan0[/COLOR]
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:90:4b:b7:e2:40
Sending on   LPF/wlan0/00:90:4b:b7:e2:40
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
Trying recorded lease 192.168.0.102
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
peter@cosmo:~$ [COLOR="Red"]route -n[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 wlan0
peter@cosmo:~$ more[COLOR="Red"] /etc/resolv.conf[/COLOR]
nameserver 192.168.0.1

```

>Im getting most of this stuff from man iwconfig
I probably wouldn't (i.e., get it) from reading the man page, given my lack of foundational knowledge, but I certainly take your point and will be more proactive in educating myself.  I will begin man page when I return later this afternoon.

---

### Post by Peter108 on 2007-08-19
Would I be correct in assuming that this WEP key problem is due to some peculiarity with my router?  If so, I could try swapping it out.  It's an old 802.11b D-Link DI-514, and is about due anyway.  Thoughts?

Thanks.

---

