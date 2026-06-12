---
title: "Issues with default route"
date: 2005-05-05
forum: Networking &amp; Wireless
---

### Post by Tyr_7BE on 2005-05-05
So my school provides pretty decent Wireless G coverage to the parts of the campus I frequent. I bought a D-LINK AirPlus DWL-G650 PCMCIA card so I could get in on the wireless thing with my laptop.  I've used the card in the past with Windows and it's worked just fine.

I plugged the card into the side of the laptop, and issued a "sudo ifconfig ath0 up". The device roared to life, and I saw a bunch of flashing lights. So now that the card is active, I try to connect to the wireless network.

Using a PHP script I found on the net (can't remember where), I was able to extract the commands used to connect to a wireless network.

"sudo iwlist ath0 scan" returned the following:

```
  
conor@conor-lt:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:01:F4:ED:1A:4B
                    ESSID:"uw-wireless"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:01:F4:ED:1B:F5
                    ESSID:"uw-wireless"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:01:F4:ED:1B:D5
                    ESSID:"uw-wireless"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100

```


I next issued a "sudo iwconfig ath0 essid uw-wireless key off". That appeared to work fine. It printed nothing, and now "iwconfig ath0" returns the following:

```

conor@conor-lt:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"uw-wireless"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:01:F4:ED:1B:D5
          Bit Rate:11 Mb/s  Tx-Power:50 dBm  Sensitivity=0/3
          Retry:off  RTS thr:off  Fragment thr:off
          Power Management:off
          Link Quality=31/94  Signal level=-64 dBm  Noise level=-95 dBm
          Rx invalid nwid:5704  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed beacon:0

```


The following is the ouput of "sudo dhclient ath0":

```

conor@conor-lt:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit url_removed.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:0f:3d:52:0f:f6
Sending on  LPF/ath0/00:0f:3d:52:0f:f6
Sending on  Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 129.97.192.1
bound to 129.97.192.166 -- renewal in 464 seconds.

```

So it's definitely talking to the network.

Now at this point, under windows, I go to [www.laptop.uwaterloo.ca](www.laptop.uwaterloo.ca), which redirects me to a sign-in page and I sign on using my username and password. Unfortunately, under Linux, epiphany gives me a host not found.

Furthermore, here are the results of me attempting to ping several addresses:

```

conor@conor-lt:~$ ping 129.97.192.166
PING 129.97.192.166 (129.97.192.166) 56(84) bytes of data.
64 bytes from 129.97.192.166: icmp_seq=1 ttl=64 time=0.053 ms
64 bytes from 129.97.192.166: icmp_seq=2 ttl=64 time=0.065 ms
64 bytes from 129.97.192.166: icmp_seq=3 ttl=64 time=0.047 ms
64 bytes from 129.97.192.166: icmp_seq=4 ttl=64 time=0.066 ms
64 bytes from 129.97.192.166: icmp_seq=5 ttl=64 time=0.048 ms

--- 129.97.192.166 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 0.047/0.055/0.066/0.012 ms



conor@conor-lt:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.065 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.067 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.048 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.057 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.047 ms

--- 127.0.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.047/0.056/0.067/0.012 ms



conor@conor-lt:~$ ping 129.97.192.165
connect: Network is unreachable

conor@conor-lt:~$ ping 129.97.192.164
connect: Network is unreachable

conor@conor-lt:~$ ping 129.97.192.163
connect: Network is unreachable

conor@conor-lt:~$ ping 129.97.192.167
connect: Network is unreachable

conor@conor-lt:~$ ping 129.97.192.168
connect: Network is unreachable

conor@conor-lt:~$ ping 129.97.192.169
connect: Network is unreachable

```


If I open up a browser and navigate to 129.97.192.166, I get my local apache2 default web server. So it bound itself to 129.97.192.166 and now that points at localhost. The actual network appears to be unreachable.

It seems that direct operations on the AirPlus Card work (ie, iwconfig worked fine, dhclient showed me talking happily to the network), but things like ping and browsing that aren't specifically directed at the ath0 device fail.


Am I missing a step here? It seems that device ath0 is capable of talking to the wireless network, but as far as my laptop is concerned it has no active network interfaces.

Of particular interest is the line in "iwconfig ath0" after I've connected and obtained a DHCP lease. "Rx invalid nwid" is a huge number. Does this mean that my laptop is rejecting incoming packets from the network?

Ubuntu Hoary, Compaq Presario 2500, D-Link AirPlus DWL-G650 PCMCIA Wireless Card.


Addendum:

I've tried posting this thread on other forums, and here's what we got so far.

I first perform the following steps: I issue a "sudo ifconfig ath0 up" followed by "sudo iwconfig ath0 essid uw-wireless key off".  I then issue a "sudo dhclient ath0" which appears to be successful, and as soon as that's done, I type "sudo ifconfig ath0 down".

Now if I issue an "iwconfig ath0", it still shows my card as being connected to the wireless network.

Now I do the following: I type "sudo ifconfig ath0 up", and as fast as I can I issue a "route -n".  Before route is even finished printing to the screen, I hit the "up" key to get my most recent command and press enter.  Here's the output:

```

conor@conor-lt:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
129.97.192.0    0.0.0.0         255.255.255.0   U     0      0        0 ath0
conor@conor-lt:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
conor@conor-lt:~$

```

So the routing tables are populated for a split second, and then for whatever reason the entry disappears.  Most of the time, my routing tables are blank like this (unless I'm on a wired network and able to get internet).

Contents of /etc/resolv.conf:
```

search uwaterloo.ca
nameserver 129.97.192.1

```

Can anyone provide ANY clue as to why this is happening?

---

### Post by Gowator on 2005-05-05
Im not sure but mine sets the default route twice with eth0 and ath0

to get it working I need to 

```
route del default gw
```
which deletes the last one... then i delete both and add specifically or not ...

have you tried manually adding it 
```
route add default gw 129.97.192.166 ath0
```

---

### Post by Tyr_7BE on 2005-05-05
I just tried it with the syntax you specified.

```

conor@conor-lt:~$ sudo route add default gw 129.97.192.76 ath0
conor@conor-lt:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         129.97.192.76   0.0.0.0         UG    0      0        0 ath0
conor@conor-lt:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
conor@conor-lt:~$ 

```

Same situation.  It immediately flushes the routing tables when ath0 is being used.

Right now, I'm plugged in to the same school network using a network cable.  Everything works great.

```

conor@conor-lt:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
129.97.83.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         129.97.83.1     0.0.0.0         UG    0      0        0 eth1
conor@conor-lt:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
129.97.83.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         129.97.83.1     0.0.0.0         UG    0      0        0 eth1
conor@conor-lt:~$

```

So my routes are persistant when we use eth1 (wired).

```

conor@conor-lt:~$ cat /etc/resolv.conf
search uwaterloo.ca
nameserver 129.97.83.1
conor@conor-lt:~$

```

So it all looks good, and works perfect.  When I use ath0, /etc/resolv.conf is updated accordingly, and the ONLY difference I see is that the routing tables are flushed when using ath0.

This happens when I manually configure using iwconfig and ifconfig, and also when I use System->Administration->Networking.  I choose to Activate ath0, a little window pops up telling me it's activating, and then all appears successful.  However, I immediately switch to a terminal, and.......

```

conor@conor-lt:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
129.97.192.0    0.0.0.0         255.255.255.0   U     0      0        0 ath0
0.0.0.0         129.97.192.1    0.0.0.0         UG    0      0        0 ath0

conor@conor-lt:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

conor@conor-lt:~$ cat /etc/resolv.conf
search uwaterloo.ca
nameserver 129.97.192.1

conor@conor-lt:~$

```

So in theory I have a valid route to the network for a total of 0.5 seconds.

Computers :(

---

### Post by Gowator on 2005-05-05
looks OK but you don't actually have a default...  

if you add it manually does it persist or dissapear too?

---

### Post by Tyr_7BE on 2005-05-05
When I add it manually it disappears almost right away, just like it does when network autoconfig programs do it for me.

Could I need to define ath0 as a valid interface somewhere?  I didn't have the card inserted when I installed Hoary...I just popped it in for the first time a few days ago.  Is there any additional configuration that needs to be performed?

---

### Post by Tyr_7BE on 2005-05-06
Solved!!  Coming atcha from my wireless network!

A long time ago I installed NetworkManager in an effort to simplify my wireless experience. Well it didn't work so I just left it on there.  Yesterday I noticed a bunch of strange error messages coming from NetworkManager, so I removed it with apt-get.  Today I come in to school, connect, and the route stays!!

Thanks for your suggestions all.

---

