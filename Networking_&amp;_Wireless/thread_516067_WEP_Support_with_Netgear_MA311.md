---
title: "WEP Support with Netgear MA311"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by cchase on 2007-08-02
I have a Netgear MA311 card with the Prism 2.5 Wavelan chipset.  I am running Dapper Drake 6.06.01.  My Router is a Linksys WRT54G.

I am able to connect to the network via my router without encrytion just fine.  When I add a WEP encryption I lose all connection.  I have also tried a WPA but I just don't know enough about it plus I have three other PC's that are connected to it via my WEP.

I have tried using Network Manager (after removing all info from the interfaces file).  I have tried entering the key via the GUI, via the interfaces file and via iwconfig.  I tried it with and without dashes.  I have my settings for an open authentication.  I even tried a passphrase and even tried a 64 bit encryption.

Here are my iwconfig settings:

cchase@Kitchen:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"CCHASE"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.432 GHz  Access Point: xx:xx:xx:xx:xx:xx
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=92/92  Signal level=-8 dBm  Noise level=-149 dBm
          Rx invalid nwid:0  Rx invalid crypt:131  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I have my encryption turned off in this example but normally it would all be the same except the encryption key would be listed.  The "Rx invalid crypt" is normally in the 4-400's.

Here are my ifconfig settings:

cchase@Kitchen:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:09:5B:2F:FF:8D
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe2f:ff8d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5140 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6076830 (5.7 MiB)  TX bytes:1036380 (1012.0 KiB)
          Interrupt:5 Memory:df9fe000-df9fefff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

I have literally spent weeks trying to figure out this problem.  I read a post about blacklisting (what I think are drivers) but it was for Kubuntu.  Fortunately because of all this research I have learned much about Ubuntu.  I feel like I have done my due-dillegence before I broke down to ask for help.  Does anyone have any idea?  Help!!!

---

### Post by kentpend on 2007-08-02
I too am having the same issue, only my card is a WPN311 from Netgear, and I'm on Feisty.

As far as I can tell, a possible solution is to force the router to use open key authentication, not shared or even auto.  Unfortunately, I haven't been able to test it because the option for "open key" does not seem to exist in my router's settings (firmware issue maybe?).

Incidentally, is there any reason you aren't using WPA?  I'm only trying to get WEP to work as that's what the wireless setup supports by default; I'll probably work on WPA soon.

---

### Post by cchase on 2007-08-02
I figured that the router authentication could be a problem but I can't seem to find any documentation on it.  I am using WEP because I know nothing about WPA and how it works so I am trying to work on one problem at a time.

BTW I bought a book called Ubuntu Hacks on Amazon and it helped a bunch.  If you are new too, I recommend it.  Unfortunately, there is nothing to help me in this situation.  Good luck

---

### Post by cchase on 2007-08-10
I never could find a solution so I am now just running a MAC filter and not broadcasting my SSID.  I suppose that none of my neighbors will be trying to hack my network.  I really don't have much to hack anyway.

---

### Post by ecco_loco on 2007-08-10
I have that card and router -and I use wep -spent long weeks tying to get WPA to work -it won't

Sortof a n00b but I'll post anything I can-

root@sloop:~# iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"hackme"  Nickname:"bingo"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:0F:66:37:83:FF   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:0FEF-005-FB   Security mode:open
          Power Management:off
          Link Quality=50/92  Signal level=-62 dBm  Noise level=-146 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13  Invalid misc:0   Missed beacon:0

root@sloop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:5B:41:4F:12  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe41:4f12/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12668170 (12.0 MiB)  TX bytes:3988055 (3.8 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

I had issues -so I got wifi radar and was able to configure -keep the security open and i always enter the hexidecimal

good luck

lshw -C network
root@sloop:~# lshw -C network
  *-network               
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 01
       serial: 00:09:5b:41:4f:12
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.3.6 ip=192.168.1.11 latency=32 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:e6000000-e6000fff irq:11

---

