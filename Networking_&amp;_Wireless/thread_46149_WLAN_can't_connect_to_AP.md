---
title: "WLAN can't connect to AP"
date: 2005-07-03
forum: Networking &amp; Wireless
---

### Post by bodiddlie on 2005-07-03
I've been trying to get my Netgear wg511t (out of the box my rear end) pcmcia card to connect to my wireless AP all night.  I followed the instructions in this link:

[http://www.ubuntuforums.org/showthread.php?t=38972&highlight=wg511t](http://www.ubuntuforums.org/showthread.php?t=38972&highlight=wg511t)

and got the card detected and showing up in the network configuration applet.  First thing I ran into was that if I tried to activate the card in the applet after entering my WEP key, the system hung up.  Total complete lock up.  So I rebooted and did it without the key.  No hang up, but no connection either.  So I routed around the forums and tried using iwconfig and changed some lines in /etc/network/interfaces.  But still nothing.  Here's some output.

#iwlist ath0 scan

ath0   Scan completed :
  Cell 01 - Address 00:80:C8:1D:AB:6B
  ESSID:"default"
  Mode:Master
  Frequency:2.437 GHz  (Channel 6)
  Quality=54/94  Signal level=-41 dBm  Noise level=-95 dBm
  Encryption key:off
  Bit RAte: 1 Mb/s
  Bit Rate: 2Mb/s
  Bit Rate: 5Mb/s
  Bit Rate: 11Mb/s
  Bit Rate: 22Mb/s
  Extra:bcn_int:100


#iwconfig

lo   no wireless extensions

ath0    IEEE 802.11g  ESSID:"default"
           Mode:Managed  Frequency:2.437 GHz  Access Point: 00:80:C8:1D:AB:6B
           Bit Rate:1 Mb/s  Tx-Power:50 dBm  Sensitivity=0/3
           Retry:off  RTS thr:off  Fragment thr:off
           Power Management:off
           Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
           Rx invalid nwid:21  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0  Missed beacon:0

sit0     no wireless extensions


#cat /etc/network/interfaces

<removed comments>
auto lo
iface lo inet loopback

iface ath0 inet dhcp
wireless_mode managed
wireless_essid default

wireless_channel 6

auto ath0


If anyone has any ideas your help would be greatly appreciated.

---

### Post by spd106 on 2005-07-03
Hi, it's good that the nic has associated with the AP. That's often half the battle. 

Unfortunately I'm not sure what's going wrong. Does ifconfig show that you have an ip address? If not check the AP is set to handle dhcp requests. Also make sure your AP isn't blocking requests ie no ip addresses available or wrong mac control lists.

An obvious question, but have you tried ifup ath0?

Good luck

---

### Post by bodiddlie on 2005-07-03
ifconfig doesn't have show an ip.  Here's the output:

#ifconfig

ath0  Link encap:Ethernet  HWaddr 00:0F:B5:AF:33:B1
         inet6 addr: fe80:20f:b5ff:feaf:33b1/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
         RX packets:52  errors:4758  dropped:0 overruns:0 frame:4758
         TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:199
         RX bytes:17236 (16.8 KiB)  TX bytes: 41760 (40.7 KiB)
         Interrupt:9  Memory:c49e000-c49f0000

<lo stuff removed>

I pulled up the status pages on my router and it shows a wireless pc connected with a mac of 00:0F:B5:AF:33:B1.  Exactly what my card shows me in ifconfig.  Just nothing going on the system itself.  Weird.

---

### Post by spd106 on 2005-07-03
Have you seen this thread? interesting and there are some things you could try.

[http://www.ubuntuforums.org/showthread.php?t=32370](http://www.ubuntuforums.org/showthread.php?t=32370)

I remember someone had trouble with ipv6, and managed to disable it somehow. That might be your problem, or maybe I am just clutching at straws.

what about manually setting your ip address?

---

### Post by bodiddlie on 2005-07-03
I issued a sudo ifdown -a to bring the card down, then issued sudo ifup -a and the system hung completely.  Hmmmm.  Changing to static ip didn't do anything either.  

#cat /etc/network/interfaces

<trim comments and lo stuff>

iface ath0 inet static
wireless_mode managed
wireless_essid default
wireless_channel 6
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1

auto ath0

---

### Post by bodiddlie on 2005-07-03
Well, now it's connected but I still can't access anything.  When I run iwconfig it shows the signal at 55/94.  But if I try to ping any of my other machines or router I get "network is unreachable".  Also, if I run sudo dhclient (oh yeah, I switched everything back to dhcp) it says no DHCPOFFERS received.  Argh.

---

### Post by bodiddlie on 2005-07-04
Okay, I disabled IPv6 and still nothing.  Reading some more in the forums I noticed that someone mentioned trying to ping the loopback at 127.0.0.1 to verify that tcp/ip isn't dead.  Doing that gives me this:

#ping 127.0.0.1
connect:  Network is unreachable

So it seems that maybe it's not just the wireless.  The card is detected and both lights (this is a netgear wg511t) are blinking in tandem.  My router shows the laptop in the DHCP table and has an ip assigned to it.  However, ifconfig doesn't show said ID.  I've tried ifdown -a followed by ifup -a but that hangs the laptop.  iwconfig shows it as connected and receiving a signal.  I'm stumped.  Any ideas anyone?

---

### Post by bodiddlie on 2005-07-04
After leaving the system alone for a little while I came back and issued another ifconfig.  This time it gives me an ip address.  However pinging the loopback still doesn't work but it at least tries now.  Now I just get destination host unreachable.

---

### Post by spd106 on 2005-07-05
Hi, It's very weird that the loopback doesn't work. Do you have some kind of firewall running?  I've never come accross this before so i'm not sure how to re-enable 127.0.0.1.

Perhaps a file has been corrupted somewhere. Dare I say reinstall ubuntu?

---

### Post by bodiddlie on 2005-07-05
No firewall and I've reinstalled twice now.  Hmmmph.

---

