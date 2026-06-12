---
title: "wireless very slow since 9.04"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by vallvi on 2009-05-16
I'm sorry to start a new thread on this, but I really can't find an answer on the others. Since installing 9.04, my internet connection is many times slower than it used to be. My other ubuntu computer (8.04) in the network is doing ok, so I don't dear to upgrade that one. I've done speedtests, tried different browsers, but it's consistently and substantially slower. I'm using a wireless card (realtrack) and alinksys router. 

What's happening? What can I do? Please help!

Thnx!

Below are the iwconfig and ifconfig, in case that helps
henk@henk-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:90:4C:91:00:01   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=68/100  Signal level:-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

henk@henk-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:8d:ec:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1042 (1.0 KB)  TX bytes:1042 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:08:a1:9d:a2:c1  
          inet addr:172.26.3.2  Bcast:172.26.3.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe9d:a2c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26223574 (26.2 MB)  TX bytes:2098102 (2.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-08-A1-9D-A2-C1-32-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by linux6994 on 2009-05-16
Simple things to try:

1.Try changing the wireless channel to a different one on your linksys, you have 11 channels to choose from perhaps 1,6, or 11 for best channel separation. Channel 6 is default out of the box and is the one most cluttered since folks do not often change it.

I realize that upgrading would not of changed your channel but try it anyway.

2. Try to reseat the wireless card. Ensure that you have powered off your PC and then unplug your card and plug it back in once again.

3. If you are in a residential area with many wireless networks are you sure you are connected to your linksys router and not a further one away? I would change the linksys router name on the router to something less generic so you can more easily identify it. Just an idea.

If you connect direct to the router how is the overall performance? I know it will be quicker but you will realize if there is a substantial difference.


Good Luck.

---

### Post by kpkeerthi on 2009-05-16
Also try [disabling IPv6]("http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html")

---

### Post by stillious on 2009-05-20
Hi vallvi

I see that the rate of your wireless card is set to 1mb/s.

If you open up a terminal and type the following:

```
sudo iwconfig wlan0 rate 54MB
/etc/init.d/networking restart
```

See if that makes any difference for you ):P

---

### Post by vallvi on 2009-05-23
Thanks, everybody for the suggestions. But none of them worked. I did everything that everybody suggested, but no change to my speed. I'm still down to a miserable 20 KB per sec, according to different speed tests on the Internet. The Windows machine in the same network has 100 KB per sec (which is also slow, but that's because I live in a place where Internet in general is slow. 

I would like to get at least up to the speed of the Windows machine. Any other suggestions to solve my problem? I'd hate to have to go back to Windows. On Ubuntu 8.04, I had 100 KB per sec, but when I changed to 9.04, a ew weeks ago it dropped to one fifth.

Thanks so much for any help anyone can give

---

### Post by PatrickVogeli on 2009-05-23
try: 

sudo iwconfig wlan0 rate 5.5M 

and DON'T do the networking restart, let's see if it makes a difference

---

### Post by vallvi on 2009-05-23
Yes, that seemed to work. Thanks, Patrick!
But after I restart the computer, I'm back to the old slow speed. How do I make this lasting??

---

### Post by unutbu on 2009-05-23
vallvi, open a terminal and type
```

gksu gedit /etc/network/interfaces
```

This will pull up an editor with root privileges so you can edit the system file
/etc/network/interfaces. 

Look for a stanza that begins with
```

auto wlan0
```

Include in that stanza
```

wireless-rate 5.5M
```

Save and exit gedit. See if it works after reboot.

---

### Post by PatrickVogeli on 2009-05-23
You wouldn't do what unutbu says, since there's nothing in /etc/network/interfaces about the interfaces anymore.

What I'd do:

gksudo gedit /etc/rc.local and put iwconfig wlan0 rate 5.5M before exit 0

---

### Post by vallvi on 2009-05-24
Thanks Patrick. You did it again! 
I've no idea what I did and why I had to do it, but it works.
Moltes gracias!

---

### Post by geirknappen on 2009-06-13
run      gksudo gedit /etc/rc.local      in terminal

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


And do this?:

#!/bin/sh -e
#
# rc.local iwconfig wlan0 rate 5.5M
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


Is that correrct?

---

### Post by Azrael3000 on 2009-06-13
No you would do this:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iwconfig wlan0 rate 5.5M

exit 0

```

All lines with a # in front are comments.

---

### Post by geirknappen on 2009-06-13
Thanks.

---

### Post by 3rdalbum on 2009-06-13
Try experimenting with the number; on one of my wireless cards I get the best speed when set to 11MB/s, and on another I get the best speed from 24MB/s.

---

### Post by myotis on 2009-06-20
can I jump in on this thread.

I have the same problem that file transers between my Thinkpad and NAS are running at 2Mb/s with a 54Mb transfer speed available.

Unlike the OP my iwconfig says

Bit Rate: 54Mb/s 

I have tried the solution here and it makes no difference, but given that iwconfig is already reporting 54Mb/s does that suggest the issue is elsewhere.

Having said that, do I no to activate the rc.local script somehow - rebooting or uncommenting any of the lines currently commented out.

Many thanks,

Graham

---

### Post by Mechmechie on 2009-06-25
Thanks for the newb level help on this. Just a btw,if i put the speed above 24m it get reset to 1m.
Is this as it should be? Thanks:D

---

### Post by k1001001 on 2009-07-02
> **Azrael3000 said:**
> No you would do this:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iwconfig wlan0 rate 5.5M

exit 0

```

All lines with a # in front are comments.
I had the same problem with differing speeds between Windows and Ubuntu, and this solved it for me as well. Thanks!

---

### Post by umaxtu on 2009-07-25
Just a quick comment: I had the same problem and the fix mentioned in this thread worked **partially **but in the interest of whatever is causing this fixed i must mention that when watching the network usage in the system monitor I noticed that one second my wifi would be running full boar and the next only doing a handful of bytes a second which throws off the average considerably. This behavior was consistent (and still is but not anywhere near as bad) until I set my wifi card's rate at 12 mb/s

I hope this helps the problem get permanently fixed.
 **EDIT: Updating to the latest kernel version now 2.6.28-14 combined with setting the rate to 12mb completely fixed the problem for me**

---

