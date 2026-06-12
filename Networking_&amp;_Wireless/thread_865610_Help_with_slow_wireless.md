---
title: "Help with slow wireless"
date: 2008-07-20
forum: Networking &amp; Wireless
---

### Post by ctijacob on 2008-07-20
Hi guys, new to the forum and trying to get this laptop that was given to me running on Linux.. I've been battling a few problems over the past few days, the largest being my wireless.

First of all, I have an Acer Aspire 5050 with the Atheros 5007EG chipset. I couldn't get it working in Ubuntu 8.04 (64-bit), so I tried it on Fedora 9 (32 bit) and I did get it working, but not very well. It was extremely slow, with ping time in the 20,000's.. With the help from scottro I did have it working pretty well following the directions here:

[http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007)

Well, after I had the wireless fixed I had to try to get my graphics drivers working because Fedora doesn't support the ATI chipset and I ended up screwing up X.. so yeah, I decided that I'd rather fight the wireless battle in Ubuntu than the graphics battle in Fedora.

So here I am: I reinstalled Ubuntu 8.04 (64-bit) and following the link above I managed to get my wireless working.. but it's still very slow. The thing that seemed to work for Fedora was cleaning Madwifi cruft, but I don't have any old ndiswrapper or Madwifi on this install because I started on that page when I installed. I experimented with the ndiswrapper method, but it worked about the same and I had to re-run the make install every reboot. So I reverted back to the more reliable Madwifi.. I disabled IPv6, seeming to help route speeds some, but this is still really bad..

Here's some ping results:

jacob@jacob-laptop:~$ ping yahoo.com
PING yahoo.com (68.180.206.184) 56(84) bytes of data.
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=1 ttl=51 time=843 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=2 ttl=51 time=1208 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=3 ttl=51 time=815 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=4 ttl=51 time=141 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=5 ttl=51 time=6040 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=6 ttl=51 time=5580 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=7 ttl=51 time=4694 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=8 ttl=51 time=3758 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=9 ttl=51 time=4356 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=10 ttl=51 time=3653 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=11 ttl=51 time=2878 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=12 ttl=51 time=111 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=13 ttl=51 time=1498 ms
64 bytes from w2.rc.vip.sp1.yahoo.com (68.180.206.184): icmp_seq=14 ttl=51 time=596 ms

--- yahoo.com ping statistics ---
14 packets transmitted, 14 received, 0% packet loss, time 18028ms
rtt min/avg/max/mdev = 111.794/2584.178/6040.425/2006.994 ms, pipe 7

PING google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from 64.233.167.99: icmp_seq=1 ttl=243 time=3254 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=2 ttl=243 time=7245 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=3 ttl=243 time=9549 ms
64 bytes from 64.233.167.99: icmp_seq=4 ttl=243 time=12624 ms

--- google.com ping statistics ---
7 packets transmitted, 4 received, 42% packet loss, time 78282ms
rtt min/avg/max/mdev = 3254.106/8168.496/12624.535/3419.342 ms, pipe 4

Heres my iwlist:
jacob@jacob-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:2A:62:D8:FE   
          Bit Rate=54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-52 dBm  Noise level=-96 dBm
          Rx invalid nwid:19621  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any thoughts? If there's any other info that may be helpful.. let me know.

---

### Post by beren.olvar on 2008-07-20
Well, so you have your wireless card working with madwifi drivers.
the problem is that those drivers are not working propperly for 64-bit kernels, so you either reintall with 32-bit, or you can black list ath_pci and reinstall ndiswrapper.

You have to load the drivers for 64-bit win xp located at the acer website. i got those working flawlessly with the version 5.3
Sometimes they fail, but make install is not needed, you just have to load ndiswrapper module again by doing

sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper

cheers!!

---

### Post by ctijacob on 2008-07-21
Thanks for the advice, I ended up retrying the ndiswrapper. It worked for a couple boots, but then it wouldn't connect and I had to do the 

```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```

on every boot.. to avoid this little inconvenience I did

```
sudo gedit /etc/init.d/wicd
``` 

and put those entries into the file after the bash line so that it looks like this:

```
#!/bin/bash
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
if [[ $1 = "start" ]]
then
	echo "Stopping any running daemons..."
	killall daemon.py 2> /dev/null
	echo "Starting wicd daemon..."
	/opt/wicd/daemon.py 2> /dev/null
fi

if [[ $1 = "stop" ]]
then
	echo "Stopping wicd daemon..."
	killall daemon.py 2> /dev/null
fi
```

Which appears to avoid the problem altogether. Do you see any problems with this resolution?

---

### Post by beren.olvar on 2008-07-21
That should work when you reboot...
but idk what happens when you hibernate/suspend
is wicd restarted? if so, i may use your script also lol :P

---

