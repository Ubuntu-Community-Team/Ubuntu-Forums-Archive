---
title: "[SOLVED] Conceding Wireless is Difficult in Ubuntu Hardy"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by jwferk on 2008-09-09
I am conceding that I will probably never get my Atheros (Netgear WG311) wireless card to connect to the Netgear WGR614 router.  Better said, that I will never get an IP address out of the router.

I have WindowsXP on one hard disk and Ubuntu Hardy on the second.  This is a Dell Intel dual core x86_64 configuration.  The wireless works fine after a Windows boot.  Both boots work flawlessly with a wired connection.  The remote computer (WindowsXP) in my wife's second floor office also works flawlessly via wireless.  That computer is 40 ft by a straight line from the router.  This computer is 6 ft away from the router.  It's not that I particularly need the wireless connection here; its been the challenge of trying to get it to work for the last 6 month.

I've tried to configure the wireless using the native Hardy network tool to no avail.  ndiswrapper does not solve the problem.   The wireless does not work with ndiswrapper if I deactivate the Atheros HAL module and Atheros 802.11 support module that comes with Hardy.    Madwifi does not solve the problem.  ath_pci and ath_hal are both loaded in the kernel module.  WICD does not solve the problem in any scenario.

Right now the output from **lshw -C network** is:

[I]*-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:11:11:d2:4b:a2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5751-v3.23a ip=192.168.1.3 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
 
 *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wifi0
       version: 01
       serial: 00:14:6c:30:1d:45
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g[/I]

**iwconfig** is shown below and indicates everything is OK.

[I]lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"homeoffice"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:4D:96:DA   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-YYYY-5B   Security mode:restricted
          Power Management:off
          Link Quality=35/70  Signal level=-58 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]
[B]
ifup[/B] indicates:
[I]
ifup: interface ath0 already configured[/I]

If I run **Network Tools **I am showing eth0 working.  HOWEVER, the output from Network Tools Configure for eth0 is

[I]The interface does not exist
Check that it is correctly typed and that it is correctly supported by your system.[/I]

This is the same output I get if I try to configure ath0.

Network tools also lists 3 wireless interfaces including
[I]
ath0
wifi0 [/I]

and 

*aht0:avahi*

each of which is preceded by the notation of "unknown interface"

The **Network Tools** output for each interface are

[I]Network device:	eth0
Hardware address:	00:11:11:d2:4b:a2
IP address:	192.168.1.3
Netmask:	255.255.255.0
Broadcast:	192.168.1.255
Multicast:	Enabled
MTU:	1500
Link speed:	not available
State:	Active
Transmitted packets:	13041
Transmission errors:	0
Received packets:	11808
Reception errors:	0
Collisions:	0

Network device:	wifi0
Hardware address:	not available
IP address:	not available
Netmask:	not available
Broadcast:	not available
Multicast:	not available
MTU:	not available
Link speed:	not available
State:	not available
Transmitted packets:	329
Transmission errors:	0
Received packets:	19815
Reception errors:	0
Collisions:	0

Network device:	ath0
Hardware address:	not available
IP address:	not available
Netmask:	not available
Broadcast:	not available
Multicast:	not available
MTU:	not available
Link speed:	not available
State:	not available
Transmitted packets:	89
Transmission errors:	0
Received packets:	0
Reception errors:	0
Collisions:	0

Network device:	ath0:avahi
Hardware address:	00:14:6c:30:1d:45
IP address:	169.254.3.74
Netmask:	255.255.0.0
Broadcast:	169.254.255.255
Multicast:	Enabled
MTU:	1500
Link speed:	54 Mbps
State:	Active
Transmitted packets:	89
Transmission errors:	0
Received packets:	0
Reception errors:	0
Collisions:	0[/I]


So - while **lshw -C network** thinks ath0 is up and running, network tools thinks ath0:avahi is working but not ath0.

I don't understand why Network Tools is treating the logical "wifi0" as a separate interface nor where ath0:avahi originates.

I've worked through multiple suggestions from the forums as well as doing all the checks at the Ubuntu wireless troublshooting page.

Any thoughts other than I should give up?

Bye and bye - I have Suse 11 on a Sony Vaio laptop and it works fine with wireless.  I have had Suse 10.3 on this computer prior to switching to Hardy and the wireless also worked great.

---

### Post by cybrsaylr on 2008-09-09
I've been having the same wireless problems with Hardy since an update a couple weeks ago.
Prior to that update, wireless ran great on my Toshiba laptop. 
Been trying all kinds of fixes since and still can't get wireless back.

---

### Post by hawksbill on 2008-09-10
I checked on madwifi's website and depending on the revision of your card it may or may not be compatible with the driver. 

[http://madwifi.org/wiki/Compatibility/Netgear](http://madwifi.org/wiki/Compatibility/Netgear)

I'm not sure what aht0:avahi is.

When using madwifi the default under ifconfig -a should show ath0 wifi0 and your wired network cards. If the aht0:avahi interface is invalid it may be because the driver is in conflict. In such case you could try blacklisting the module, reboot, then see if this helps or remove the module and try the ndis wrapper. If ndis is your route just make sure the madwifi module is removed to prevent conflicting information being passed.

I am no expert here just a few things I picked up along the way. Hope this helps.

---

### Post by mcld on 2008-09-10
I'm facing very similar problems to you - very similar iwconfig output etc. (Except I have no ethernet on my system.)

I know that "avahi" is a service for zeroconf networking (see [thread]("http://ubuntuforums.org/showthread.php?t=525149") or [wiki]("https://help.ubuntu.com/community/HowToZeroconf")).

I tried deactivating avahi as follows: went into System->Services and untick avahi-daemon aka "Multicast DNS Service Discovery" (despite the warning shown). I also followed some advice I found somewhere and added the line "AVAHI_DAEMON_START=0" to the file /etc/default/avahi-daemon  , which is supposed to prevent the avahi service from loading. HOWEVER, even if I do all this and reboot, I still see an entry for "ath0:avahi" in ifconfig.

Can anyone help us? :)

---

### Post by hawksbill on 2008-09-10
Ah thanks for the clarification on that. I also found this thread which may help.

[http://ubuntuforums.org/showthread.php?p=5375548](http://ubuntuforums.org/showthread.php?p=5375548)

---

### Post by fewjr on 2008-10-01
jwferk said> Any thoughts other than I should give up?



I do have one thought for you my friend. I have an Atheros chipset and had a heck of a time getting it to connect in Hardy. I tried everything I could by searching this forum, google and asking questions. To make a long story short....I did a fresh install of hardy to get me back to the start. I am not sure how bad I had screwed things up, so I thought that was best. After that, what had fixed my problem was running my router in wpa instead of wep. I have had my network running wep for along time before now. wpa is more secure anyway, so if you are running wep, give wpa a try. All those things I tried and the frustration were starting to tick me off. I could not connect in wep no matter what I did. As soon as I switched to wpa and changed my families windows computers to connect to it, I came back to the Ubuntu box and it connected right away. Here is a link to my post that never got answered:

[http://ubuntuforums.org/showthread.php?t=927123](http://ubuntuforums.org/showthread.php?t=927123)

Here is a link I followed through with to try to help myself:

[http://ubuntuforums.org/showthread.php?t=929486](http://ubuntuforums.org/showthread.php?t=929486)

DapperMe17 tried to help me and I would say he did because he made me think. Let me know if this helps.

Regards,
fewjr

---

### Post by jwferk on 2008-10-21
fewjr:

Thanks much for the hint on WPA.  This has helped somewhat and I've gotten things down to a single issue.

1 - I crashed the router and reconfigured it for WPA;
2 - the Windows desktop upstairs worked immediately - no issues in connecting to the reconfigured router;
3 - I run both Windows and Open Suse 11.0 on a Sony Viao laptop.  Both of these connected immediately;
4 - I have Windows and Ubuntu on separate hard drives on this computer.  The Windows side connected immediately to the router;  I couldn't get Ubuntu to connect. Same issues as before;
5 - I trashed the existing Ubuntu install and reformatted the Ubuntu drive;
6 - For the fun of it, I loaded Mandriva 2009 running KDE4 as a trial.  It took all of 23 seconds to connect the wireless to the router under Mandriva;
7 - I trashed the Mandriva install and reloaded Ubuntu Hardy;  At the first boot, there were four network interfaces under Network Tools including lo, eth0 (there is a hardwire card in the box as well as the wireless), ath0 and wifi0 which is the logical to ath0;  Everything connected up immediately including the wireless.  That was the first time it ever worked.
8 - unfortunately, when I re-booted a second time, a ghost interface (avahi-ath0) was now listed under along with lo, eth0, wifi0 and ath0.  The wireless no longer worked.

The good news is that I can get the wireless to consistently work at re-boot if I go to the Network GUI tool and re-enter the WPA passphrase every time I re-boot.  The bad news is that at re-boot, the ghost interface (avahi-ath0) always appears first.  It goes away after I re-enter the pass phrase for WPA.

So - the problem is (1) specific to Ubuntu (which continues to be frustrating as this is clearly a bug in the program) and (2) is localized to the appearance of the ghost interface (avahi-ath0).  Turning off the Multicast DNS service and disabling any bluetooth services (as suggested elsewhere) does not fix the issue. 

I've tried using ndiswrapper but that doesn't fix the issue.  I'm currently using the atheros non free drivers and the ath_pci kernel module.

I understand the avahi function is associated with  the Local Zeroconference functions but I'm not sophisticated enough to sort out what part of that is causing the bug.

Anyway, this is getting closer to a solution but still needs some work.

Bye and bye - I'm sending this via wireless.

Cheers

---

### Post by jwferk on 2008-10-23
This solution has now worked for my Netgear WGR614 router with a Netgear wireless Atheros AR5212/AR/5213 processor.  The driver is the native madwifi that comes with the linux non-free package.  The kernel is 2.6.24-21-generic

1- At the suggestion of fewjr, I reset my router configuration from WEP to WPA.  That allowed me to finally get a connection to the wireless using the Network tool under System > Admin.

2 - to get rid of the ghost interface (avahi-ath0) that was coming up each time I re-booted, I deleted the file named "avahi-autoipd" using Synaptic.

(this should be done at your own risk as I am not sophisticated enough with Ubuntu to know what else this affects.  So far, after 5 re-boots, I have encountered no problems).

3 - the last problem I was having dealt with the Network tool which wanted to re-write the WPA passphrase at re-boot.  It kept copying itself so I would have two identical passphrases strung together (no idea why that was happening).

4 - I installed widc as the wireless manager, set it WPA encryption and selected MADWIFI as the driver preference.

So far, I have re-booted 5 times to see how stable things are.  They are working.

---

