---
title: "Intel 3945ABG: *frustrating* to no end"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by Zorael on 2007-08-23
**- Intro, skip if TLDR**
I have an Acer laptop with a built-in Intel 3945ABG chipset. I used to run Ubuntu until about a month ago when I had to send the entire machine to service as the motherboard broke down. Up until then I hadn't experienced any real issues with Ubuntu at all. When I got it back, I thought I'd try out Kubuntu (as I already had gotten a peek at Xubuntu on another laptop), but then the madness ensued.

The one and *only* way I could get Kubuntu to connect to my wireless network was to set up the router to use DHCP, so that KNetworkManager could connect to it without breaking its "roaming mode", or whatever it's called. I usually have my networks set up with static IPs, but I figured it an acceptable workaround - until it turns out the connection dies about 10 minutes after establishing it. Noteworthy is that I *cannot* reconnect once I've connected and then lost connection.

I searched the forums only to find a gazillion posts about the 3945 chipset, some stretching back into 2006, all with their own solutions to their own problems. Many couldn't get (K/X)Ubuntu to find the card/chipset itself, which obviously isn't the issue I'm experiencing. Others recommended to try ndiswrapper, which I had limited (read: no) success with. A popular workaround was to get rid of KNetworkManager and network-manager in favor of wicd, so I tried that.

wicd in itself is awesome, and seems to be able to connect even with a static IP provided, but something - the driver? - still falls short.


**- Issue!**
**The *only* way I can connect to networks is to set wicd up to *not* automatically connect to my home network, and instead load it upon getting into KDE and then clicking Connect.** Anything else results in it pausing at "Obtaining IP address" for ages, then failing to connect. I only have one try. If I successfully connect through wicd after startup, then hit disconnect and refresh, it can no longer see any networks. At that point, an 'iwlist eth1 scan' says either "No scan results" or "Interface doesn't support scanning". If I wish to reconnect at that point - or switch networks - I have to reboot to catch that one golden first connection attempt again.


**- stuff**
```
zorael@azrael:~$ lspci | grep 3945
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

zorael@azrael:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 12
       serial: 00:a0:d1:a0:ec:6b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:cc000000-cc003fff ioport:3000-30ff irq:16
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@07:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:6e:39:9a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.0.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:ce000000-ce000fff irq:19
```

**When working:**
```
zorael@azrael:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"LappskoleB"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:1F:68:EB
          Bit Rate:11 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=71/100  Signal level=-65 dBm  Noise level=-66 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:798   Missed beacon:0

zorael@azrael:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:11:95:1F:68:EB
                    ESSID:"LappskoleB"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=67/100  Signal level=-66 dBm  Noise level=-66 dBm
                    Extra: Last beacon: 180ms ago

```

**When borked:**
```
zorael@azrael:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"LappskoleB"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:11:95:1F:68:EB
          Bit Rate:11 Mb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1162   Missed beacon:0

zorael@azrael:~$ iwlist eth1 scan
eth1      No scan results

zorael@azrael:~$ iwlist eth1 scan
eth1      Interface doesn't support scanning.

zorael@azrael:~$ iwlist eth1 scan
eth1      No scan results
```

Even when borked, it is correctly set up through ifconfig and iwconfig; it just doesn't see any available networks. And if I enter a "hidden ESSID", it still can't/won't connect. ifdown and then ifup doesn't help, disabling and then reenabling the wireless radio through the switch on the front of the machine doesn't help, nor does biting one's nails. It *seems* to be set up correctly in every way imaginable, but it doesn't do anything.



I've tried Kubuntu 7.04, Ubuntu 7.04 Live CD and Kubuntu Gusty Tribe 3, all with the same problem. And it worked prior to sending it in for repair, where they replaced the motherboard! The chipset itself isn't broken, as it works flawlessly in XP (I dualboot).


Is it possible I have some new, garbage, non-linux compatible firmware?

---

### Post by odin1965 on 2007-08-24
I have similar problems, beginning around the 1st week of August with my Dell with 3945. I have been trying to find an answer, see thread below

[http://ubuntuforums.org/showthread.php?t=525152](http://ubuntuforums.org/showthread.php?t=525152)

[http://ubuntuforums.org/showthread.php?t=530352](http://ubuntuforums.org/showthread.php?t=530352)

Is it possible that an upgrade to the 3945 firmware was performed around this time? I can't find any mention of firmware except in my output from 'lshw -C network' which shows, driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0, the same as yours does.

I have been researching here as well as at the ipw3945 project at sourceforge and the network manager mailing list, but as yet have no solution. Mine worked PERFECT up until the first week of August. Now I can occasionally connect to the WPA network at work after much friggin around, but can never duplicate the connection. At home, I have removed all encryption from my router and network manager occasionally connects but says I have o signal strength.

---

### Post by Zorael on 2007-08-25
In a sense, it feels better to know I'm not alone. :>

I posted it as a [bug in Launchpad](https://bugs.launchpad.net/ubuntu/+bug/134515), not sure if it'll get attention anytime soon, but we can hope.


Bump 'cause we're desperate!

---

### Post by Zorael on 2007-08-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/134515](https://bugs.launchpad.net/ubuntu/+bug/134515) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				<empty post to include the launchpad url in the entry field>

---

### Post by Zorael on 2007-08-27
I've made "some" progress.


First off, I scrapped network-manager and knetworkmanager in favor of wicd, and I've never since looked back.

Secondly, while I still only have one shot at connecting, but *now* I can reset it without having to restart the machine.


Now, off the top of my head, the ritual to restore after it's broken down (with likely some irrelevant, unneeded and redundant steps):

1) Open wicd
2) Disconnect the network to be safe (with the button)
3) Close wicd
3) Do 'sudo modprobe -r ipw3945 && sudo modprobe ipw3945' in a terminal (mayhaps just one modprobe ipw3945 call does the trick, I'm not knowledgeable enough to know)
4) Open wicd again, hit refresh
5) At this point, it discovers my essids again 90% of the time, if not I return to step 2, rinse and repeat
6) Hit connect and pray.


That'd be the discovery part. I've had shaky luck of being able to reconnect, with a success rate of ~20% or less.

Sometimes, if I do it the DHCP way, it just freezes at Obtaining IP address.
Other times, both with DHCP and with a static ip, it connects and reports a 0% signal.
Further other times, it connects and reports a valid signal, but only one ping request goes through before the connection dies. (I usually run a 'ping 192.168.0.1' in another terminal so I know if I succeeded.)

Wicd doesn't seem to want to connect successfully (or at least, not give the UI feedback that it is trying) if you haven't hit disconnect since your last attempt, and often if you haven't restarted the program itself. So a lot of opening/closing involved.


Better than nothing, I guess. :) This way I can keep at it and eventually get it back in shape without the constant reboots. But it's still about as broken; what if the connection breaks down when I'm not there to give an effort to beat it back into shape?

---

### Post by dumbmatter on 2007-08-28
i think this somehow might be related to the type of router you have.  i have the same problem as you with my router, most of the time it won't connect, and when it does, it will eventually drop the connection.

but i can connect to my neighbor's unprotected wireless every time.  hasn't failed yet.

---

### Post by Zorael on 2007-08-28
Mayhaps.

From where my machine sits, I'm in the range of two networks - mine and my neighbor's. When the interface ceases to cooperate, I can detect no networks. Once I unload and reload the module, I can once again detect both.

If my router in some way screws up the release process, causing the interface to "hang", then yes - perhaps another router would do the trick. However, I've tried with three routers so far though with no difference, so the probability grows ever smaller. Also, mind, it works without flaws in Windows - and I had no issues in Linux with the chipset on my earlier motherboard, before I got it replaced.

edit: Further, it's not only a matter of being able to successfully connect; while certainly a big issue, I'm also concerned with the interface breaking down on me after it has lost connection. When in its broken state, it's very, very uncooperative. Even with WEP disabled I can't connect to anything.

---

