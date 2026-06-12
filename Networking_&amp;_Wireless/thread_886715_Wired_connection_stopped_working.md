---
title: "Wired connection stopped working"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by CooLMaNxxx on 2008-08-11
Dear ubuntuforums users,

I have been lurking around for a while, reading support requests and learning a bit here and there.

Yesterday I rebooted and unfortunately my wired connection simply stopped working.

I am running latest generic kernel (2.6.24-19) on hardy.

Understandably this is less than what is necessary for you to help me troubleshoot the problem, so here's a bit more:

lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: xx:xx:xx:xx:xx:xx
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL2 driverversion=1.0.40.2 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair
```

(note: previously this has shown *-network DISABLED
to enable I used 'ifconfig eth0 up')

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:dbfc0000-dc000000 

```
dhclient eth0:
```
Listening on LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   LPF/eth0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

dhclient gives the _same_ result when the cable is plugged in and when it is out.

I get no lights whatsoever from the built in network card, but my second boot (windows xp) lights are up and everything is working (as you can see; because I am writing from it).


I will appreciate any help.

Thank you!

---

### Post by Sterkarm on 2008-08-11
hmmm, im having fairly simmler problems


both my cards refuse to work in xp as well thoguh :(

was just going to sujest a few fixes but i do belive they shouldent effect your card..

oh well. gd luck with it

---

### Post by Iowan on 2008-08-11
Post results of **ifconfig** and contents of **/etc/network/interfaces**.

---

### Post by Trollslayer on 2008-08-11
I have had a similar problem with cable broadband - the modem will only makea DHCP offer once and needs to be power cycled for each request.

---

### Post by CooLMaNxxx on 2008-08-11
> **Sterkarm said:**
> hmmm, im having fairly simmler problems


both my cards refuse to work in xp as well thoguh :(

was just going to sujest a few fixes but i do belive they shouldent effect your card..

oh well. gd luck with it

Sounds like your cards are the problem, that is not my case.

Thank you.

> **Iowan said:**
> Post results of **ifconfig** and contents of **/etc/network/interfaces**.

I posted ifconfig (I discarded the lo device).

/etc/network/interfaces has only 2 lines regarding the lo device.


Any ideas?

(it worked before!!)

---

### Post by CooLMaNxxx on 2008-08-11
By the way,

What really bothers me is that non of the network card LEDs is on.

I believe that if I find a way to turn them on, and hence establish a connection between the computer and the router I will be able to solve the problem easily.

Unfortunately I am unable to do that, you have any ideas?

---

### Post by CooLMaNxxx on 2008-08-11
bump :\

---

### Post by CooLMaNxxx on 2008-08-11
Ok, I solved the problem.

Apparently the only way to re-activate the device after using Windows XP is to shut down the computer.
If I reboot after using the device in Ubuntu I do not have any problems.

My guess is the Windows driver has some booting mechanism Linux does not implement.

---

