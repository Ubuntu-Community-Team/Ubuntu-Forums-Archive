---
title: "Unable to get Atheros AR5212 wireless card to connect to network."
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by newtoubu on 2007-04-20
I have just done a fresh install of Feisty 7.04 in the hope that it would solve my wireless woes, having had no luck with Edgy Eft despite many hours of trying.

I am running a Dell Inspiron laptop with a Netgear WG511T PCI wireless card, Atheros AR5212 chipset, and trying to connect to a Netgear router (128 bit WEP security). When i go into System>Administration>Network and go to the properties of Wireless connection (interface ath0) i am presented with a list of wireless access points in the drop down for the ESSID. I have done endless reading on the forums and tried various solutions but nothing has yet worked so i have now purposely gone back to square one (fresh install) with the hopes that someone will find it easier this way to help me out. I am currently using a Windows PC to browse the internet and the laptop is set up right beside it.

In the network settings Wireless connection has a '-' in the box beside it and has roaming mode enabled. Wired connection has a tick in the box beside it and Modem connection also has a '-'.

Terminal: ifconfig results

ath0   Link encap:Ethernet HWaddr 00:09:5B:E9:34:FC
          UP BROADCAST RUNNING MULTICAST MTY:1500 Metric:1
          [etc]

eth0  Link encap:Ethernet HWaddr 00:11:43:41:70:87
          UP BROADCAST RUNNING MULTICAST MTY:1500 Metric:1
          [etc]

eth0:avah Link encap:Ethernet HWaddr 00:11:43:41:70:87
                  UP BROADCAST RUNNING MULTICAST MTY:1500 Metric:1
                  [etc]

lo     Link encap:Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr:  ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTY:16436 Metric:1
       [etc]

wifi0  Link encap:UNSPEC HWaddr 00-09-5B-E9-34[.....]
         UP BROADCAST RUNNING MULTICAST MTY:1500 Metric:1
        [etc]

**iwconfig results**

lo                 no wireless extensions.

eth0            no wireless extensions.

wifi0            no wireless extensions.

ath0            IEEE 802.11g  ESSID: " "   Nickname: " "
                   Mode:Managed Frequency:2.437 Ghz Access Point: Not-Associated
                   [etc]

I'd really appreciate any assistance and would be more than happy to provide whatever information may be of help.

I am relatively new to Linux having only made the plunge this year so pardon any very basic questions.

---

