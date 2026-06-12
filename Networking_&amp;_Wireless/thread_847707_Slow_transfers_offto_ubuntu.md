---
title: "Slow transfers off/to ubuntu"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by nry on 2008-07-02
Hi

Setup a file server for myself and used ubuntu, managed to get samba installed fine etc and everything the way I wanted.

Problem im having now is the best transfer rates I get are (based on what vista tells me in the transfer window) connected via gigabit

Write: 8-10mb/s
Read: 10-13mb/s

Now this is with samba, over apache2 its lower read speeds

I head read alot of threads on this same thing but no  real solutions that work for me...

I don't currently have any more computers so im stuck with laptop and file server for testing.
Is a high performance laptop so should be able to handle some decent file transfer speeds.
The file server spec:
AMD XP 2000
1GB PC3200 ram
Gigabit pci card (tried both netgear card (used realtek chip) and a dlink card)
System drive is a 2.5" IDE 80 gb 4200rpm
Storage drive is a 3.5" SATA Western Digital green power 1tb
Thats connected to a 4 port pci sata card using sil3114

Basically I need to achieve write speeds of atleast 15mb/s and read speeds of a minimum!! 20mb/s due to hosting hd movies for soon to be built htpc

Tried ipref....
Ubuntu side
```
root@nas:~# iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.9 port 5001 connected with 192.168.1.5 port 52622
[  4]  0.0-10.0 sec    350 MBytes    294 Mbits/sec
root@nas:~# iperf -c 192.168.1.5
------------------------------------------------------------
Client connecting to 192.168.1.5, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.9 port 44770 connected with 192.168.1.5 port 5001
[  3]  0.0-10.0 sec    445 MBytes    373 Mbits/sec
root@nas:~#

```

Windows side
```

C:\>iperf.exe -c nas
------------------------------------------------------------
Client connecting to nas, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[368] local 192.168.1.5 port 52622 connected with 192.168.1.9 port 5001
[ ID] Interval       Transfer     Bandwidth
[368]  0.0-10.0 sec   350 MBytes   293 Mbits/sec

C:\>iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[144] local 192.168.1.5 port 5001 connected with 192.168.1.9 port 44770
[ ID] Interval       Transfer     Bandwidth
[144]  0.0-10.0 sec   445 MBytes   372 Mbits/sec

```

Based on that shouldn't the network allow for atleast around 30mb/s?

hdparm result
```

root@nas:~# hdparm -Tt /dev/sda1

/dev/sda1:
 Timing cached reads:   402 MB in  2.00 seconds = 200.99 MB/sec
 Timing buffered disk reads:  206 MB in  3.02 seconds =  68.16 MB/sec
root@nas:~#

```


Don't really know what else to do, bit lost here.
Going to give ftp a try as well see if I get anywhere with that but im expecting about the same.

Also tried the netdump makes no difference at all

Also when i first set this all up I could write to the ide drive at about 30mb/s now im lucky to get 8mb/s

---

