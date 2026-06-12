---
title: "No Internet Connection on new Ubuntu install (I'm a newbie)"
date: 2005-12-03
forum: Networking &amp; Wireless
---

### Post by phenix777 on 2005-12-03
I have installed Ubuntu on an old machine of mine in the interest of learning linux and all of the associated good things that go along with it.  The install went fine, however, the network connection does not work (to my LAN or the internet).

I followed the network troubleshooting thread and came up with the following information:

emil@ubuntu:~$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD, link ok


emil@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:50:BA:B0:06:97
          inet6 addr: fe80::250:baff:feb0:697/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:695 dropped:552 overruns:695 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xd000


So, it seems to me that though my ethernet card is installed into the system it is not able to connect with my router and get an IP address; hence the RX errors noted above.

I did dl the most recent driver but have no idea how to compile and install it (I 've spent many hours scouring the internet for instructions).

Again, it's an older computer (2001) and the NIC is a DF-538TX.  The router is a late model Dlink.

I am brand new to linux with almost no frame of reference (it's rather different than winxp I'm begining to find out).  Any help would be much appreciated.  Thanks a lot.

---

### Post by bissej on 2005-12-03
hello. i'm another newbie having a similar problem. i was running 5.04 with no problems, but i upgraded to breezy yesterday and now my ethernet connection is screwed up. it works sometimes but goes out every few minutes, and eventually comes back but sometimes takes awhile. i checked ifconfig, and i also have lots of RX packet errors, so it seems my problem is similar to the previous one. any ideas?
thanks.

---

### Post by mips on 2005-12-03
[QUOTE=phenix777]
          RX packets:0 errors:695 dropped:552 overruns:695 frame:0
[/QUOTE]

**overruns:**
This basically says how many times the LAN card was was unable to handle the incoming data to a hardware buffer because the input rate is higher than it can handle.
**dropped:**
Indicates packets dropped due to a full queue/buffer.

Manually set the cards speed and duplex to 10Mb/s & half-duplex. Do the same on the router side and lets see if it makes a difference.

Also try a static IP instead of using dhcp.

I think your card uses the Realtek 8139 chipset. Does the correct driver load ?

---

### Post by phenix777 on 2005-12-03
Thanks so much for your help.

Unfortunately, I cannot figure out how to set me ethernet card to 10 Mb/s and half-duplex.

I have set the router to 10 Mb/s.

Could you please advise?  Thanks a lot.

---

### Post by bissej on 2005-12-03
hi. thanks for the help. my problem might be slightly different, as my dropped number is 0. here are the numbers i get:

RX packets:25696 errors:360 dropped:0 overruns:1 frame:363

and when i ping when it is down, i get this:

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=1 Destination Host Unreachable
From 192.168.0.2 icmp_seq=2 Destination Host Unreachable
From 192.168.0.2 icmp_seq=3 Destination Host Unreachable


--- 192.168.0.1 ping statistics ---
6 packets transmitted, 0 received, +5 errors, 100% packet loss, time 5000ms
, pipe 3

when it is down, the router's URL ([http://192.168.0.1/](http://192.168.0.1/)) won't open.
thanks.

---

### Post by daniel_teixeira on 2005-12-03
having the same problem here with my acer 1691 laptop. With the previous version 5.04 it was just plug and play. Now i can seem to be able to use the ethernet card.

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=phenix777]Thanks so much for your help.

Unfortunately, I cannot figure out how to set me ethernet card to 10 Mb/s and half-duplex.

I have set the router to 10 Mb/s.

Could you please advise?  Thanks a lot.[/QUOTE]
I am not 100% sure, but I think
```

$ sudo ifconfig eth0 media 10baseT

```
will set your NIC to 10Mpbs.

---

### Post by mips on 2005-12-04
Frame errors indicate a hardware problem/CRC/Collisions.

In the above cases I think it might be more related to a software driver issue of sorts seeing you all worked under hoary.

I'll do some searching and see what i can come up with.

---

### Post by mips on 2005-12-04
[http://www.ubuntuforums.org/showthread.php?t=92921&highlight=8139](http://www.ubuntuforums.org/showthread.php?t=92921&highlight=8139)
[http://ubuntuforums.org/showthread.php?p=510858](http://ubuntuforums.org/showthread.php?p=510858)
[http://www.ussg.iu.edu/hypermail/linux/kernel/0502.0/1404.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0502.0/1404.html)
[http://www.scyld.com/rtl8139.html](http://www.scyld.com/rtl8139.html)

See if any of the above helps and let us know.

---

### Post by bissej on 2005-12-04
hello. i'm still having problems. my case might be different, as i'm using a desktop & not a laptop with wireless. i found some post about changing the sleep time on the boot script, but i don't know where that boot script is. might that help? if so, where is that script located? otherwise, i'm  at a loss for what to do and really frustrated. itgoes down every few minutes, and stays down for about a minute. 
thanks.

---

### Post by mips on 2005-12-04
/boot/grub/menu.lst

Make a backup to the same directory before you edit the file. worse case scenario is you wont be able to boot.

---

### Post by bissej on 2005-12-04
hey. thanks again for all your help. i guess it's not the boot script that i want. i read what i pasted below in a previous post, and i was looking for that particular script related to the sleep time. however, i'm not sure if this is really relevant to the problems that i am having. do you have any other ideas of what it could be? it goes down every few minutes, and i cannot even ping my ISP. and then it comes back and works for another few minutes, and then goes down again. 
thanks so much.


------------------------------------------------------------------


The version for Hoary, I just checked, had a "sleep 20" command before the "pppd call speedtch" one that tries to make the connection. While the more recent version for Breezy tells the computer to "sleep" for only 10 seconds.
In my case, this seems to be more than half the times not enough. And when I increase the value to bigger "sleep" times I can then always get a connection.
Therefore, I think that the solution for anyone who has problems getting a connection is just a question of finding out how much time is enough for you to wait before trying to connect to your ISP.
At least that's how it works for me.

In case anyone has doubts about what I'm talking about, this is the line in question (in bold) in the boot script:


#!/bin/bash
modprobe ppp_generic
modprobe pppoatm
modprobe br2684
count=0
while [[ $count -lt 40 ]]
do
sync=$(dmesg | grep 'ADSL line is up')
if [ ! -z "$sync" ]
then
br2684ctl -b -c 0 -a VP.VC
sleep 3
ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up
sleep 10 <- THIS ONE (TRY INCREASING THE VALUE IN THIS LINE TO MORE SECONDS)
pppd call speedtch
exit 0
fi
sleep 1
let "count += 1"
done
echo "The Speedtouch firmware didn't load"

---

### Post by bissej on 2005-12-06
i solved my internet connection problem, and i thought i'd post it in case it might help others. when i upgraded from hoary to breezy, my connection became really sporadic, going on and off frequently. i was using a serial cable instead of an ethernet cable, which had worked fine under hoary. however, it appears this was the problem, and with a better cable my connection seems to be working fine. so for whatever reason, hardware which worked fine with hoary might not be good enough for breezy, and others might want to consider this if having trouble after an upgrade.

---

### Post by mips on 2005-12-06
[QUOTE=bissej]i solved my internet connection problem, and i thought i'd post it in case it might help others. when i upgraded from hoary to breezy, my connection became really sporadic, going on and off frequently. **i was using a serial cable instead of an ethernet cable, which had worked fine under hoary.** however, it appears this was the problem, and with a better cable my connection seems to be working fine. so for whatever reason, hardware which worked fine with hoary might not be good enough for breezy, and others might want to consider this if having trouble after an upgrade.[/QUOTE]

Consider your self lucky it did work ;) The specs on a serial cable are nowhere near that of an ethernet cable. Did you just crimp RJ-45 connectors onto the serial cable ?

---

