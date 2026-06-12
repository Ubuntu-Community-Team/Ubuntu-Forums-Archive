---
title: "Pages Not Loadioing Properly"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by faron45 on 2009-01-17
I have had a major problem now for about the last 2-3 weeks that I've just been trying to deal with until I really had  time to bring it to all of you for help with.Well,now's the time.Now,if I were running windows [of any sort],I would conclude that I must have stumbled upon a virus of some sort.Or,possibly some sort of spyware [or something]. But,since I have no semblance [of any sort] of microsoft on my pc then I cannnot for the life of me figure out why my pc is behaving this way.My problem is trying to load web pages.

 For some reason,my web pages do not seem to want to load.Properly or entirely.Sometimes they will load.But,more often than not,I will have to try to load the same page [I have even seen it take more than 10 tries] several times before I can get it to load up properly [and usually the page will not even completely load ] .When the page does finally load,it will only load [I would say] about 99% of the page.[I say 99% because even when it  looks like it has loaded completely [I am informed] that the page is indeed still loading.Plus,upon scrolling to the bottom of the page I find that it stil  has not loaded my user name where it should be.

 PLEASE-does ANYONE have a clue as to what may be happening & how I might fix this ? PLEASE-[and,I will remind all of you-I am still basically just a beginning comp.user.So,again,PLEASE be patient with me.And,as always-thank you all very,VERY much for any & all help.And,yes,if my problem is resolved,I will indeed mark this post as "solved".Again,thank you all very,VERY much.

                                                                      Ever indebted to all of you,your friend,
                                                                                     faron45
                                                                                             aka; guitarfiend !!
        :guitar:

---

### Post by northern lights on 2009-01-17
Can you run```
ping google.com
```wait for around five results, hit Ctrl+Z and paste the output here?

---

### Post by faron45 on 2009-01-17
I can indeed run this.........Trying to figure out how to copy & paste the results though.For some reason,I don't seem to be able to copy & paste.One moment please.And,sorry for the delay !


Here we go...Again,sorry for the delay-
bobby@cybertek:~$ ping google.com
PING google.com (72.14.205.100) 56(84) bytes of data.
64 bytes from google.com (72.14.205.100): icmp_seq=1 ttl=238 time=135 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=2 ttl=238 time=147 ms
64 bytes from qb (72.14.205.100): icmp_seq=3 ttl=238 time=133 ms
64 bytes from qb (72.14.205.100): icmp_seq=4 ttl=238 time=132 ms
64 bytes from qb (72.14.205.100): icmp_seq=5 ttl=238 time=133 ms
64 bytes from qb (72.14.205.100): icmp_seq=6 ttl=238 time=132 ms
64 bytes from qb (72.14.205.100): icmp_seq=7 ttl=238 time=134 ms
64 bytes from qb (72.14.205.100): icmp_seq=8 ttl=238 time=147 ms

[1]+  Stopped                 ping google.com
bobby@cybertek:~$

---

### Post by Hendrixski on 2009-01-17
> **faron45 said:**
> I can indeed run this.........Trying to figure out how to copy & paste the results though.For some reason,I don't seem to be able to copy & paste.One moment please.And,sorry for the delay !

Shift + CTRL + C for copying from commandline

---

### Post by Hendrixski on 2009-01-17
> **faron45 said:**
> I can indeed run this.........Trying to figure out how to copy & paste the results though.For some reason,I don't seem to be able to copy & paste.One moment please.And,sorry for the delay !


Here we go...Again,sorry for the delay-
bobby@cybertek:~$ ping google.com
PING google.com (72.14.205.100) 56(84) bytes of data.
64 bytes from google.com (72.14.205.100): icmp_seq=1 ttl=238 time=135 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=2 ttl=238 time=147 ms
64 bytes from qb (72.14.205.100): icmp_seq=3 ttl=238 time=133 ms
64 bytes from qb (72.14.205.100): icmp_seq=4 ttl=238 time=132 ms
64 bytes from qb (72.14.205.100): icmp_seq=5 ttl=238 time=133 ms
64 bytes from qb (72.14.205.100): icmp_seq=6 ttl=238 time=132 ms
64 bytes from qb (72.14.205.100): icmp_seq=7 ttl=238 time=134 ms
64 bytes from qb (72.14.205.100): icmp_seq=8 ttl=238 time=147 ms

[1]+  Stopped                 ping google.com
bobby@cybertek:~$

Ah you updated the post while I was respond...
umm.  Looks like you can ping alright.  So... is it just firefox?  Maybe try installing Opera or Konqueror (however it's spelled... it's basically Safari for Linux).  See if they handle it differently?

---

### Post by northern lights on 2009-01-17
~130ms delay is reasonable, i.e. it's not an issue with your connection or ISP.

Have you tried a different browser? Just to determine whether it's a system or a browser issue. If it's an issue with Firefox, it can be fixed for sure, but let's narrow it down by using an alternative browser.

Run```
sudo apt-get update && sudo apt-get install seamonkey
```Subsequently open *Seamonkey*. Same problems?

---

### Post by albinootje on 2009-01-17
> **faron45 said:**
> 
 For some reason,my web pages do not seem to want to load.Properly or entirely.

There are websites to test your connection speed.

[http://www.my-speedtest.com/](http://www.my-speedtest.com/)
[http://www.dslreports.com/speedtest](http://www.dslreports.com/speedtest)

Did you recently install add-ons to Firefox ?
Is the connection also slow in web browsers like Midori, Galeon, Konqueror ?
Is installing software through Synaptic Package Manager also slow ?
What about torrent downloads and ftp downloads ?

---

### Post by unutbu on 2009-01-17
If you click System>Preferences>Network Proxy, do you have "Direct Connection" enabled? or are you using a proxy? 

If you are using a proxy, that might explain why you sometimes see an incomplete page even when your browser claims the page has been completely downloaded. It might be the case that the proxy cache is incomplete.

---

### Post by faron45 on 2009-01-17
Okay.........................Again,please be patient ! Thanks.Heh,heh.
unutbu-I can'ty seem to tell...BUT-I'm pretty sure proxy is being used as I have seen  a default xubuntu proxy listed before.......
Northern...again,thanks.Still installing seamonkey..........

Northern..okay-seamonkey installed...any way I can check this like we did with other ?

Northern-okay-seem to be having same issue.

---

### Post by Hendrixski on 2009-01-17
> **faron45 said:**
> Okay.........................Again,please be patient ! Thanks.Heh,heh.

Hurry up slowpoke  :P

Just kidding

---

### Post by unutbu on 2009-01-17
faron45, I forgot you are using Xubuntu... hence no gnome panel... hence no System>Pref>Network Proxy. I don't know my way around an Xubuntu system very well, so if others know how to do this properly, please chime in!

From googling, it appears proxys are setup in Xubuntu by defining the http_proxy environment variable. To test if you are using a proxy, how about try this:

At a terminal prompt type:
```

echo $http_proxy
```
I think this should return the address of your proxy server if you are indeed using one.

---

### Post by faron45 on 2009-01-17
Same issue...[Just in case you didn't see the above edit].

unutbu-doesn't look good.Results for that test are...
bobby@cybertek:~$ echo $http_proxy

bobby@cybertek:~$ 


****

---

### Post by faron45 on 2009-01-17
albinootje-Yes,I believe I havew indeed installed/updated firefox.And,yes-apparently connections are also slow with other browsers.Installing software through Synaptic is ffine.Torrent & ftp I know nothing about.

Have you all given up on me ??

---

### Post by albinootje on 2009-01-17
> **faron45 said:**
> albinootje-Yes,I believe I havew indeed installed/updated firefox.And,yes-apparently connections are also slow with other browsers.Installing software through Synaptic is ffine.Torrent & ftp I know nothing about.

Have you all given up on me ??

Can you provide the complete output of :
```

dmesg | tail -n50
ifconfig -a
ping -c10 62.108.1.66

```
Thanks.

---

### Post by faron45 on 2009-01-17
bobby@cybertek:~$ dmesg | tail -n50
[   55.309479] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   55.309500] PCI: setting IRQ 11 as level-triggered
[   55.309508] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   55.309577] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   55.978157] intel8x0_measure_ac97_clock: measured 54171 usecs
[   55.978176] intel8x0: clocking to 48000
[   61.731253] lp0: using parport0 (interrupt-driven).
[   61.958699] Adding 738948k swap on /dev/sda5.  Priority:-1 extents:1 across:738948k
[   62.702803] EXT3 FS on sda1, internal journal
[   65.497182] ip_tables: (C) 2000-2006 Netfilter Core Team
[   67.097851] No dock devices found.
[   71.073812] IBM machine detected. Enabling interrupts during APM calls.
[   71.073834] apm: BIOS not found.
[   72.298659] ppdev: user-space parallel port driver
[   72.659712] audit(1232211206.287:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4789 profile="/usr/sbin/cupsd" namespace="default"
[   79.725744] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   80.265377] usb 1-1: new full speed USB device using uhci_hcd and address 6
[   80.355862] Bluetooth: Core ver 2.11
[   80.358254] NET: Registered protocol family 31
[   80.358276] Bluetooth: HCI device and connection manager initialized
[   80.358291] Bluetooth: HCI socket layer initialized
[   80.389315] usb 1-1: device descriptor read/64, error -71
[   80.617145] usb 1-1: device descriptor read/64, error -71
[   80.737589] Bluetooth: L2CAP ver 2.9
[   80.737612] Bluetooth: L2CAP socket layer initialized
[   80.811519] Bluetooth: RFCOMM socket layer initialized
[   80.812417] Bluetooth: RFCOMM TTY layer initialized
[   80.812445] Bluetooth: RFCOMM ver 1.8
[   80.833048] usb 1-1: new full speed USB device using uhci_hcd and address 7
[   80.961045] usb 1-1: device descriptor read/64, error -71
[   81.188886] usb 1-1: device descriptor read/64, error -71
[   81.409579] usb 1-1: new full speed USB device using uhci_hcd and address 8
[   81.820473] usb 1-1: device not accepting address 8, error -71
[   81.932418] usb 1-1: new full speed USB device using uhci_hcd and address 9
[   82.267224] NET: Registered protocol family 17
[   82.344195] usb 1-1: device not accepting address 9, error -71
[   86.055141] NET: Registered protocol family 10
[   86.056985] lo: Disabled Privacy Extensions
[   88.269500] [drm] Initialized drm 1.1.0 20060810
[   88.283754] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   88.283792] PCI: setting IRQ 10 as level-triggered
[   88.283802] ACPI: PCI Interrupt 0000:00:01.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   88.283827] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   88.288786] [drm] Initialized i810 1.4.0 20030605 on minor 0
[   88.292269] mtrr: base(0xe8000000) is not aligned on a size(0x180000) boundary
[   88.309572] [drm] Using v1.4 init.
[   91.487348] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[   91.487363] 	driver to use reclaim_buffers_idlelocked() instead.
[   91.487369] 	I will go on reclaiming the buffers anyway.
[   96.164918] eth0: no IPv6 routers present
bobby@cybertek:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:7d:f8:77:ca  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:7dff:fef8:77ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33079081 (31.5 MB)  TX bytes:5454155 (5.2 MB)
          Interrupt:3 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40100 (39.1 KB)  TX bytes:40100 (39.1 KB)

---

### Post by albinootje on 2009-01-17
> **faron45 said:**
> 
[   79.725744] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1


Thanks. ifconfig does not show any errors, neither does dmesg.
Can you (still) post the output of :
```

ping -c10 62.108.1.65

```

---

### Post by faron45 on 2009-01-17
bobby@cybertek:~$ ping -c10 62.108.1.65
PING 62.108.1.65 (62.108.1.65) 56(84) bytes of data.
64 bytes from 62.108.1.65: icmp_seq=1 ttl=239 time=213 ms
64 bytes from 62.108.1.65: icmp_seq=2 ttl=239 time=210 ms
64 bytes from 62.108.1.65: icmp_seq=3 ttl=239 time=209 ms
64 bytes from 62.108.1.65: icmp_seq=4 ttl=239 time=205 ms
64 bytes from 62.108.1.65: icmp_seq=5 ttl=239 time=207 ms
64 bytes from 62.108.1.65: icmp_seq=6 ttl=239 time=209 ms
64 bytes from 62.108.1.65: icmp_seq=7 ttl=239 time=208 ms
64 bytes from 62.108.1.65: icmp_seq=8 ttl=239 time=207 ms
64 bytes from 62.108.1.65: icmp_seq=9 ttl=239 time=207 ms
64 bytes from 62.108.1.65: icmp_seq=10 ttl=239 time=209 ms

--- 62.108.1.65 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9005ms
rtt min/avg/max/mdev = 205.973/208.918/213.424/1.964 ms

---

### Post by albinootje on 2009-01-17
> **faron45 said:**
> bobby@cybertek:~$ ping -c10 62.108.1.65
PING 62.108.1.65 (62.108.1.65) 56(84) bytes of data.
64 bytes from 62.108.1.65: icmp_seq=1 ttl=239 time=213 ms
---- cut for brevity ----
--- 62.108.1.65 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9005ms
rtt min/avg/max/mdev = 205.973/208.918/213.424/1.964 ms

That's slowish, see below for mine, but at least you don't have any packet loss with it.

> 
$ ping -c10 62.108.1.66
PING 62.108.1.66 (62.108.1.66) 56(84) bytes of data.
64 bytes from 62.108.1.66: icmp_seq=1 ttl=246 time=38.9 ms
64 bytes from 62.108.1.66: icmp_seq=2 ttl=246 time=97.3 ms
64 bytes from 62.108.1.66: icmp_seq=3 ttl=246 time=48.2 ms
64 bytes from 62.108.1.66: icmp_seq=4 ttl=246 time=9.43 ms
64 bytes from 62.108.1.66: icmp_seq=5 ttl=246 time=9.78 ms
64 bytes from 62.108.1.66: icmp_seq=6 ttl=246 time=35.2 ms
64 bytes from 62.108.1.66: icmp_seq=7 ttl=246 time=9.27 ms
64 bytes from 62.108.1.66: icmp_seq=8 ttl=246 time=31.5 ms
64 bytes from 62.108.1.66: icmp_seq=9 ttl=246 time=31.1 ms
64 bytes from 62.108.1.66: icmp_seq=10 ttl=246 time=44.9 ms

--- 62.108.1.66 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9001ms
rtt min/avg/max/mdev = 9.278/35.593/97.326/24.798 ms


---

### Post by faron45 on 2009-01-17
Thanks much albinootje.I guess everybody else has given up on me.Darnit !

---

### Post by albinootje on 2009-01-17
Can you post the output of :
```

sudo mii-tool -v eth0
cat /etc/resolv.conf
set|grep -i proxy

```

---

### Post by faron45 on 2009-01-17
Okee-dokee...here ya go...
~$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD, link ok
bobby@cybertek:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4601
#
### END INFO

search domain_not_set.invalid


nameserver 192.168.1.1
nameserver 68.238.64.12


bobby@cybertek:~$ set|grep -i proxy

---

### Post by albinootje on 2009-01-17
[QUOTE=faron45;6567711]
Thank you. What gives a ping to your router ?
```

ping -c10 192.168.1.1

```

---

### Post by faron45 on 2009-01-17
Hmmmmmmm.Let's see..
~$ ping -c10 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.755 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.766 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.710 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.715 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.748 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=0.686 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=0.759 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=0.714 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=0.681 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=0.772 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9000ms
rtt min/avg/max/mdev = 0.681/0.730/0.772/0.043 ms

---

### Post by albinootje on 2009-01-17
> **faron45 said:**
> 
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=0.772 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9000ms
rtt min/avg/max/mdev = 0.681/0.730/0.772/0.043 ms

Looks good!
Did you try those speedtest websites ?

---

### Post by faron45 on 2009-01-17
> **albinootje said:**
> Looks good!
Did you try those speedtest websites ?

I did not.I thought I did that earlier actually.Hmmmmmmmm.You gettin' tired yet ? I may have to give up for awhile.Been at this for hours now.But,if you still have any ideas,I'l stick with it.

---

### Post by albinootje on 2009-01-17
> **faron45 said:**
> I did not.I thought I did that earlier actually.Hmmmmmmmm.You gettin' tired yet ? I may have to give up for awhile.Been at this for hours now.But,if you still have any ideas,I'l stick with it.

I hope some other people have ideas to find out why your internet connection is so slow in Ubuntu.

Would you mind trying with the OpenDNS nameservers ?
[http://neeocis.wordpress.com/2008/05/04/opendns-in-ubuntu/](http://neeocis.wordpress.com/2008/05/04/opendns-in-ubuntu/)

---

### Post by faron45 on 2009-01-17
Hmmmmmmmmm.I don't know.Should I ? Hmmmmmmmmmmmmm.

---

### Post by albinootje on 2009-01-17
> **faron45 said:**
> Hmmmmmmmmm.I don't know.Should I ? Hmmmmmmmmmmmmm.

It's easy to use it temporarily, and it's easy to go back to your 192.168.1.1 as primary nameserver later on.

---

### Post by faron45 on 2009-01-17
I'll give it a try.But,I'm givin' up for the day I think.....Thanks for all your help & feel free to email me if you come up with anything else.Again,thanks very,very much.

---

