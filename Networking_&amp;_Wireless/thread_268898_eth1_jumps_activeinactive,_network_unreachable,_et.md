---
title: "eth1 jumps active/inactive, network unreachable, etc"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by UnknownVariable on 2006-09-30
Bit of a linux newbie here. Originally I was going to start off with a different distro, but found out I was biting off more than I could chew. I thought back to my old Ubuntu account I had and figured I'd try this out again.

I'll start off with some of the info from the console:

```
[FONT="Lucida Console"]alexander@alex-laptop:~$ ping 192.168.2.1
connect: Network is unreachable[/FONT]
```

```
[FONT="Lucida Console"]alexander@alex-laptop:~$ iwconfig
lo      no wireless extensions

eth0    no wireless extensions

eth1    IEEE 802.11b/g  ESSID:"starport_wireless"  Nickname:"Broadcom 4318"
        Mode:Managed  Access Point: Invalid  Bit Rate=1 Mb/s
        RTS thr:off  Fragment thr:off
        Link Quality:0  Signal level:0  Noise level:0
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries:0 Invalid misc:0  Missed beacon:0

sit0    no wireless extensions[/FONT]
```

```
[FONT="Lucida Console"]alexander@alex-laptop:~$ ifconfig
etho0   Link encap:Ethernet  HWaddr 00:E0:B8:99:E1:94
        UP BROADCAST MULTICAST  MTU:1500  Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
        Interrupt:177

lo      Link encap:Local Loopback
        inet addr:127.0.0.1  Mask: 255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:299 errors:0 dropped:0 overruns:0 frame:0
        TX packets:299 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:22220 (21.6 KiB)  TX bytes:22220 (21.6 Kib)[/FONT]
```

In System -> Administration -> Networking, this is what I see: In the connections tab, there's three entries. The first is Wireless connection, which says "The interface eth1 is not active," followed by Ethernet connection, which is eth0 and active, and lastly Modem connection, ppp0, not configured, which is alright, as I don't plan on using a phone line anyway. :D 

My wireless connection properties are all set correctly, and when I click activate, it shows a progress bar bouncing back and forth for a while (I'd say about four full minutes) before it disappears and my wireless connection reads active. I'm unable to view any webpages at all, and if I close and reopen my Network Settings box, my wireless connection again reads that it's not active.

I'm running on a Gateway MX6124 laptop, and the wireless card which is built into it is a Broadcom AirForce 54g Wireless Network Adapter. I'm also going to be using a Marvell Yukon Ethernet Controller for my direct internet connections during class, so I have a feeling I'll need to tinker with those settings as well. I haven't tried it out yet, however. I do have drivers for both of these devices on a CD ROM, though they're meant for Windows, so I'm not sure how I'd go about importing those if I need to for any reason.

As previously mentioned, I'm a linux newbie, so I've got no clue what's going on here. I do have a lot of computer experience however (webmaster, etc, yadda yadda) so don't hesitate with computer terms. :D I know to look something up if I'm not sure what it means.

Thanks for any and all help. :)

[SIZE="1"]Note - I was going to make a similar post in the newbie forum area, but I figured I'd post here, since this forum area is more specific to my need.[/SIZE]

---

