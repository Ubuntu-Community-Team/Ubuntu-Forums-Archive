---
title: "RTL8187b wireless still not connecting on 8.10"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by jgmillr1 on 2008-11-02
Hi all,

I've been using the hacked drivers generously provided by datanorth this year but have anxiously waited for my rtl8187b network card to be fully supported as promised with the 2.6.27 kernel in 8.10.

After updating to 8.10, the wireless card detects my wireless network but is still unable to connect. I went as far as disabling the WEP encryption on my router but the wireless connection manager on the laptop continued to ask me for a WEP key!? 

I booted the live 8.10 CD and it had the same behavior, so this doesn't seem to be due to an issue stemming from the upgrade from 8.04.

I'm not sure why the wlan skips over wlan0 and is using wlan1. I also haven't seen the "wmaster0" device before.

I'm clearly missing something here but I'm stumped at the moment. Any help would be greatly appreciated. Below is the output showing the states and conditions of the network devices on the laptop for reference. Thanks in advance.

jgmillr1@carrie-laptop:~$ lsmod | grep 8187
rtl8187                53120  0 
mac80211              216820  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               32392  2 rtl8187,mac80211
usbcore               148848  4 rtl8187,ehci_hcd,uhci_hcd

dmesg | tail
[ 5335.785358] wlan1: authenticate with AP 00:18:01:eb:06:d5
[ 5335.949234] wlan1: authenticate with AP 00:18:01:eb:06:d5
[ 5336.148029] wlan1: authenticate with AP 00:18:01:eb:06:d5
[ 5336.348028] wlan1: authenticate with AP 00:18:01:eb:06:d5
[ 5336.548028] wlan1: authentication with AP 00:18:01:eb:06:d5 timed out
[ 5348.565362] wlan1: authenticate with AP 00:18:01:eb:06:d5
[ 5348.764031] wlan1: authenticate with AP 00:18:01:eb:06:d5
[ 5348.964037] wlan1: authenticate with AP 00:18:01:eb:06:d5
[ 5349.164031] wlan1: authentication with AP 00:18:01:eb:06:d5 timed out
[ 5357.930981] wlan1: authenticate with AP 00:18:01:eb:06:d5
[ 5358.128027] wlan1: authenticate with AP 00:18:01:eb:06:d5
[ 5358.328025] wlan1: authenticate with AP 00:18:01:eb:06:d5
[ 5358.528021] wlan1: authentication with AP 00:18:01:eb:06:d5 timed out

jgmillr1@carrie-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:96:7a:a3  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe96:7aa3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3045931 (3.0 MB)  TX bytes:341727 (341.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20600 (20.6 KB)  TX bytes:20600 (20.6 KB)

wlan1     Link encap:Ethernet  HWaddr 00:16:44:91:92:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-91-92-5C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jgmillr1@carrie-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"GW1S1"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

jgmillr1@carrie-laptop:~$ lsusb
Bus 007 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Hugo Oliveira on 2008-11-03
I have the same problem in the 8.04 with the hacked drivers it works, and after the update for the 8.10 I can't make it work.

---

### Post by paul555 on 2008-11-03
Same problem here :(

---

### Post by lotocone on 2008-11-04
Like others, I've had the 8187b runaround. The Ubuntu project had made me a bit complacent and I didn't check before buying my Toshiba A200 1V0 - I took it for granted that it would just work like pretty much everthing has since Dapper. I messed around for a few months before giving up on wireless given that the word was that Intrepid would support 8187b.  

Here's what happened...

I did an online upgrade from Hardy to Intrepid after which the the wireless discovered my Access Point with no problem; but I couldn't even ping it, let alone get a connection.

So I burned a CD and did a fresh install and that fixed it, but I had no range. I tried one or two things to fix that but with no real success. Then I installed Wicd and removed Network Manager and Bingo!

Go here for a howto...

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I hope that works for others.

Paul
England
(raining)

---

