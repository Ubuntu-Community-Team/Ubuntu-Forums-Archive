---
title: "wireless issue - new to ubuntu"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by orengolan on 2007-03-04
Hello Ubunu community!

i am new to Linux and Ubuntu,I installed Ubuntu on my desktop machine.
I have Windows on one harddrive and ubuntu on the other one.
My problem - I can't connect to the internet. I have a wireless PCI interface -
Atheros AR5005G 802.11abg NIC.
When I switch to the windows OS I can connect without any issues.

my hardware specs: [http://www.prosoa.com/hardware.html](http://www.prosoa.com/hardware.html)
router model: D-Link DI-514

At the bottom of this post I attached of the Connection tab in the networking GUI, just to make sure that everything is ok there.
"prosoa" is my network and I disabled the encryption on my router, so i left the password field empty.
the dhcp is enabled on the router.

I noticed that the DNS tab (in the Networking GUI) was 192.168.1.1 so i canged it to 192.168.0.1 (my router).

I was trying to find the answer on the forums but nothing helped,
here are a few of the commands I typed:

oren@oren-desktop:~$ sudo iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"prosoa"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


oren@oren-desktop:~$ sudo ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:E6:AC:DF  
          inet6 addr: fe80::211:95ff:fee6:acdf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:0C:6E:3E:61:8D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-E6-AC-DF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17633 errors:0 dropped:0 overruns:0 frame:76597
          TX packets:17106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1386861 (1.3 MiB)  TX bytes:842603 (822.8 KiB)
          Interrupt:217 Memory:e0b20000-e0b30000



Thanks in advance!

Oren


The connection tab in the Networking GUI:

[IMG]http://www.prosoa.com/network.gif[/IMG]

---

### Post by FurryNemesis on 2007-03-04
Have you tried ra0 in the configuration option of the network manager? I was able to connect like that.

---

### Post by orengolan on 2007-03-04
what is ra0 and how can I try it?

---

### Post by orengolan on 2007-03-06
anyone else?

---

### Post by gradedcheese on 2007-03-07
"ath0" is the correct name, ra0 would be for a Ralink card, you have Atheros so ath0...

> 
I noticed that the DNS tab (in the Networking GUI) was 192.168.1.1 so i canged it to 192.168.0.1 (my router).


The DNS info should have DNS servers in it, not anything to do with the router ;)  Here's an example of what DNS settings look like (if you want to use opendns)

```

search opendns.com
nameserver 208.67.222.222
nameserver 208.67.220.220

```

You can (with sudo) edit /etc/resolv.conf to look like that, or put those settings in the DNS tab in the GUI.  Now about your card:
- it's supported in Linux and you have the driver loaded
- it didn't associate to your AP

Open up the terminal and try to scan:

```

iwlist ath scan

```

Your router should show up there.  If it does, try manually associating like this:

```

sudo iwconfig ath0 essid prosoa

```

Now run iwconfig to make sure you're associated:

```

iwconfig ath0

```

looks OK?  Then ask the router for an address:

```

sudo killall dhclient
sudo dhclient ath0

```

got an address?  DNS is configured correctly (see my first comment)?  Then fire up Firefox and see if you're online...

Now, you can go ahead and use the GUI to configure this, or just edit /etc/network/interfaces if you don't mind doing that (it's easier for me to explain via the forum).  The file should contain lines like:

```

auto ath0
iface ath0 inet dhcp
wireless-essid prosoa
#wireless-key your_key_goes_here_when_you_want_wep

```

(lines starting with '#' are comments, remove the '#' and enter a WEP key if you wish...)

---

### Post by orengolan on 2007-03-09
One note - I enabled my WEP on the router because COX communication (my ISP) blamed me for downloading illigal application from the internet, probably by someone that connected to my wirless!)

I reinstalled the ubuntu (because of other issues i had, 
and now the DNS shows 3 addresses - 
68.6.16.30
68.6.16.25
68.6.16.30

Search domains:
sd.cox.net

ok, i followed your steps:

**the scan was ok, i see my router - **

iwlist ath0 scan

ESSID:"ProSoa"
Mode:Master
Frequency:2.437 GHz (Channel 6)
Quality=43/94  Signal level=-52 dBm  Noise level=-95 dBm
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Extra:bcn_int=100
   
**I manually associate the router but when I run iwconfig ath0 it is still ;Not-Associated' - **

oren@oren-desktop:~$ sudo iwconfig ath0 essid prosoa
oren@oren-desktop:~$ sudo iwconfig ath0
ath0      IEEE 802.11g  ESSID:"prosoa"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:6964-6C65-68   Security mode:restricted
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


any ideas?

---

### Post by orengolan on 2007-03-10
I am not sure what happend.
after restarting my router the issue was resolved.


thanks for the help,
My Linux journey has begun!

---

