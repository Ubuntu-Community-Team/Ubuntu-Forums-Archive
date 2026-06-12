---
title: "Haven't yet got Atheros 5212 to work on HP nc4010 laptop"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by stanh on 2007-02-01
Trying for a week to get wireless working.  This card worked on XP.  I have installed Edgy.  When that didn't work I installed Dapper.  Still no luck. The linksys router is on channel 6.  I have no trouble connecting to it with my wireless PDA.

I think I'm close but must be missing something.

There is a blue led on the laptop that is on when the wireless card is working in XP.
This light is not on in Ubuntu.
I suspect the card is not active, at least not transmitting.

Here's some of my settings and results. 

Network Settings shows ath0 is active.

sudo lshw -businfo shows:
pci@00:09.0   ath0        network        AR5212 802.11abg NIC


stan@ubuntu1:~$ sudo lshw -C network
  *-network:0
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 9
       bus info: pci@00:09.0
       logical name: ath0
       version: 01
       serial: 00:0f:20:95:7e:8f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11
       resources: iomemory:98080000-9808ffff irq:5

Then I run sudo ifconfig ath0 up
and finally
sudo iwlist ath0

The results are:

stan@ubuntu1:~$ sudo iwlist ath0 scan
ath0      Failed to read scan data : Resource temporarily unavailable

My iwconfig:

stan@ubuntu1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ath0      IEEE 802.11  ESSID:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:66:53:20:0B
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and ifconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ath0      IEEE 802.11  ESSID:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:66:53:20:0B
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

stan@ubuntu1:~$
stan@ubuntu1:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:20:95:7E:8F
          inet6 addr: fe80::20f:20ff:fe95:7e8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:eedc0000-eedd0000

eth0      Link encap:Ethernet  HWaddr 00:0D:9D:91:31:F8
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe91:31f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3448 errors:0 dropped:0 overruns:0 frame:2
          TX packets:2932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3833065 (3.6 MiB)  TX bytes:390094 (380.9 KiB)
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5827 (5.6 KiB)  TX bytes:5827 (5.6 KiB)

---

### Post by spd106 on 2007-02-01
Have you seen this page? [http://madwifi.org/wiki/Compatibility#HP](http://madwifi.org/wiki/Compatibility#HP)

---

### Post by stanh on 2007-02-01
Yes I saw that.  I don't have any button to turn the wifi on/off.  I'll investigate using kernel 2.6.16.

I have also tried Fedora 6, same problem.  I just like Ubuntu so much better.  I haven't yet downloaded and compiled from Madwifi.  Maybe I'll try that.  I did it for Fedora and didn't work with it.  But I haven't tried it yet with either Dapper or Edgy, was hoping I could use the Madwifi drivers that came with them.

I suppose it's possible that this card just won't work with this laptop.  It did work with XP.  

I also tried to use ndiswrapper and that didn't help either.  

Anyway thanks for the response and I'll keep looking.

Stan

---

### Post by stanh on 2007-02-01
Finally...after 1 week.  Problem solved.  I'm connected.  Don't have WEP working yet but I finally have wireless working.

Here's what I found buried on the MADWIFI site.  Seems on some mini-pci cards, pin 13 can cause the radio to be stuck off. Put some tape over the pin and Bingo, it works. This link has some pictures of the pin location.  My card looked a little different, didn't have all the foils shown but I figured it out.

This may not work for your card but it it worth looking into.

[http://madwifi.org/wiki/UserDocs/MiniPCI?format=txt](http://madwifi.org/wiki/UserDocs/MiniPCI?format=txt)

I'm sending this reply.....wireless!!

---

