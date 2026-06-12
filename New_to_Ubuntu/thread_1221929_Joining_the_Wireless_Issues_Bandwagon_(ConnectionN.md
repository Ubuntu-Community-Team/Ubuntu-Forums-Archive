---
title: "Joining the Wireless Issues Bandwagon (Connection/No Internet)"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by Wataru8675 on 2009-07-24
I've done a search of the forums and tried sifting through all the wireless problems, but haven't seen anything relevant to my issue.

My wireless this morning seemed to connect just fine (the little bars up there were all green and happy and it was all like, "Connection Established, Little Brother!!") so I tried to go on the internet, but after waiting for about a minute and a half, it timed out.  I couldn't log into Pidgin either.  I'm on my ethernet right now and, obviously, it's working just dandy.  But is there a way to do something like on Windows XP/Vista where there was a "Repair Wireless" option or something like that?  Maybe a few command lines?

Speaking of command lines, I don't know if they'll be any help here, but these are my outputs that have been commonly asked for:

sudo iwlist scanning
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:18:F2:5A
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=67/100  Signal level=-58 dBm  
                    Extra: Last beacon: 24ms ago
          Cell 02 - Address: 02:81:6D:6B:0E:80
                    ESSID:"print server 1F9C6D"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=67/100  Signal level=-60 dBm  
                    Extra: Last beacon: 184ms ago

pan0      Interface doesn't support scanning.
```


iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:18:F2:5A   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=75/100  Signal level=-54 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:219  Invalid misc:0   Missed beacon:1

pan0      no wireless extensions.

```


ifconfig
```
eth0      Link encap:Ethernet  HWaddr 08:00:46:c8:f8:25  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fec8:f825/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5007 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5506422 (5.5 MB)  TX bytes:687034 (687.0 KB)

eth1      Link encap:Ethernet  HWaddr 00:0e:35:0d:35:67  
          inet6 addr: fe80::20e:35ff:fe0d:3567/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:194890 (194.8 KB)  TX bytes:79687 (79.6 KB)
          Interrupt:9 Base address:0xe000 Memory:d0201000-d0201fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1287 (1.2 KB)  TX bytes:1287 (1.2 KB)
```


UPDATE:  My dad has wireless internet in the other room, and now I can't connect at all...
UPDATE2:  It says I need to enter a WEP password...but I'm on an unsecured wireless network... >_>

---

### Post by Hospadar on 2009-07-24
Well, you're definately not connected to the wireless in the first place.  If you were you'd see an "inet addr" in the ifconfig for your wifi.

I might suggest a couple things:
1) try changing the essid of the router (in the router's config).  Maybe your neighbour has a router that's also called "linksys"  Unlikely, but i've seen this kind of problem in dorms and apartments.
ager packages are in the apt cache so we can re-install them later without an internet connection.

2) try connecting manually, you might need to disable/kill network manager to be able to do this, the whole process might look something like:
```
killall nm-applet #kill network manager
sudo ifdown eth1
sudo iwconfig eth1 essid "linksys" #if you change the router's essid, you'll have to change this
sudo iwconfig #just make sure at this point that eth1 has the right essid
sudo ifup eth1
ifconfig #see if eth1 has an ip address now ("inet addr")

```Obviously this is not a permanent solution, but it might give you some more insight into the problem
Make sure there's no password on the router for these instructions to work

---

### Post by Wataru8675 on 2009-07-24
> **Hospadar said:**
> Well, you're definately not connected to the wireless in the first place.  If you were you'd see an "inet addr" in the ifconfig for your wifi.

I might suggest a couple things:
1) try changing the essid of the router (in the router's config).  Maybe your neighbour has a router that's also called "linksys"  Unlikely, but i've seen this kind of problem in dorms and apartments.
ager packages are in the apt cache so we can re-install them later without an internet connection.

2) try connecting manually, you might need to disable/kill network manager to be able to do this, the whole process might look something like:
```
killall nm-applet #kill network manager
sudo ifdown eth1
sudo iwconfig eth1 essid "linksys" #if you change the router's essid, you'll have to change this
sudo iwconfig #just make sure at this point that eth1 has the right essid
sudo ifup eth1
ifconfig #see if eth1 has an ip address now ("inet addr")

```Obviously this is not a permanent solution, but it might give you some more insight into the problem
Make sure there's no password on the router for these instructions to work

Will the first option disrupt any currently connected computers?  My dad's working from home in the other room, so I don't want him to lose Internet.

EDIT:  The second option, I got through until this
```
kyle@Kyle-laptop:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
```
What in Jolly Joseph does that mean?

---

### Post by Wataru8675 on 2009-07-24
Desperation bump. ><

---

### Post by LowSky on 2009-07-24
unplug router, wait a minute, replug in router wait for connection to re-establish and you might be fine

let us know

---

### Post by Wataru8675 on 2009-07-24
> **LowSky said:**
> unplug router, wait a minute, replug in router wait for connection to re-establish and you might be fine

let us know

Nothin'.  Same thing's happening, wireless tries to connect for about a minute to my linksys network, then for some reason tries to connect to a neighbor's network or something, one that I've never seen nor used.  It isn't ours, though, because it's labeled "Qwest4880" and we have Comcast.  I have the only computer in the house (of 3) that can't connect to the wifi, so it has to be something with the computer and not the router.

I'm sorry if you're getting frustrated with me spamming this, but...I'm at a complete and utter loss here.

EDIT:  I'm gonna go with the AP Comp Sci motto..."If all else fails...reboot."  I'll edit with results.

RESULTS:  I can't believe that actually worked. -______-;  Must have just been a slight error when it booted up this morning...  Sorry to bother you all. ^^;;;

---

### Post by lsouth on 2009-07-24
Dude!  Maybe you can tell me how to do magic on mine! lol

Lee

---

