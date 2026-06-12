---
title: "iwconfig works but /etc/network/interfaces doesn't (sort of)"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by dennis1200 on 2006-12-21
I have a Broadcom 4318 card, (it works w/ ndiswrapper). However, the computer never connects correctly on boot up. etc/network/interfaces is configured correctly, but it only works if I load it after boot using:

```
sudo /etc/init.d/networking restart
```
OR
```
sudo iwconfig eth1 key open XXXXX
```
(followed by sudo dhclient)
Then it connects.

On boot it either connects to an unsecured network in the area or hangs trying to get connected to a secured network specified in interfaces (if there aren't any unsecured ones around).

Here's my interfaces file:
```
auto lo
iface lo inet loopback

#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid XXXX
wireless-key open XXXXX

```

There's no point using wired - I'm 2 floors up from the hub.

The fact that restarting the networking service after boot works seems to indicate that /etc/network/interfaces is written right. Agh! What's the deal? ](*,)

I currently wrote 
```
/etc/init.d/networking restart
``` into rc.local, but that's kind of a cheap hack. I want the real deal.

Otherwise: Super Kudos to Ubuntu! Once printing is fully working, I will free /dev/hda1 from its oppressor, because Ubuntu is incredible!

---

### Post by bernied on 2006-12-21
I had a similar problem with wpa - the problem was that the interface was being brought up before it had finished associating with the access point. The solution was to add a 'pre-up sleep 2' (that's literally wait 2 secs) line to the interfaces entry, something like this:
```
iface eth1 inet dhcp
pre-up wpa_supplicant --lots-of-wpa-gubbins--
pre-up sleep 2
```
I don't know how this applies to your setup where the init script does the association as well - worth a try anyway.

---

### Post by dennis1200 on 2006-12-22
I put in a "pre-up sleep 3" after the "iface" line, but to no avail. Are there other things I should pre-up as well?

In terms of the init script - isn't that what's running on boot when the OS is "configuring network interfaces"? Should I fiddle with that? I'll post it here:

```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          networking
# Required-Start:    mountvirtfs ifupdown $local_fs
# Default-Start:     S
# Default-Stop:      0 6
### END INIT INFO

PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

[ -x /sbin/ifup ] || exit 0

. /lib/lsb/init-functions


case "$1" in
start)
	log_action_begin_msg "Configuring network interfaces"
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
	if [ "$VERBOSE" != no ]; then
	    if ifup -a; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	else
	    if ifup -a >/dev/null 2>&1; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	fi
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
	;;

stop)
	if sed -n 's/^[^ ]* \([^ ]*\) \([^ ]*\) .*$/\2/p' /proc/mounts | 
		grep -qE '^(nfs[1234]?|smbfs|ncp|ncpfs|coda|cifs)$'; then
	    log_warning_msg "not deconfiguring network interfaces: network shares still mounted."
	    exit 0
	fi

	log_action_begin_msg "Deconfiguring network interfaces"
	if [ "$VERBOSE" != no ]; then
	    if ifdown -a --exclude=lo; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	else
	    if ifdown -a --exclude=lo >/dev/null 2>/dev/null; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	fi
	;;

force-reload|restart)
	log_action_begin_msg "Reconfiguring network interfaces"
	ifdown -a --exclude=lo || true
	if ifup -a --exclude=lo; then
	    log_action_end_msg $?
	else
	    log_action_end_msg $?
	fi
	;;

*)
	echo "Usage: /etc/init.d/networking {start|stop|restart|force-reload}"
	exit 1
	;;
esac

exit 0


```

I'm no script writer, so it's a bit jibbery to me, but when I run it in a terminal, it specifically uses the latter section on "reconfiguring network interfaces". Of course, on boot it is running the first section "Configuring network interfaces" - I assume I'd have to tweak that one if anything.

---

### Post by bernied on 2006-12-23
I believe the key is the 'ifup -a' command, mentioned several times:
```
]start)
	log_action_begin_msg "Configuring network interfaces"
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
	if [ "$VERBOSE" != no ]; then
	    if **ifup -a**; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	else
	    if **ifup -a** >/dev/null 2>&1; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	fi
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
	;;

```so there are two cases, when $VERBOSE is set or not, in each 'ifup -a' is run. ifup takes its parameters from the interfaces file, so its that file that you should change. I also think it's a bad idea in general to change that script, as it will get reset with any update of the init system, or of networking, whereas the configuration file will not. There should be something you can do with interfaces. You could make it run another script using the pre-up command.

Another thing you could try is to shift the order of the init scripts, so that the networking one runs later. That involves changing the number of the symlinks in the /etc/rc.d/rc._/files (I might have the location a bit wrong, look for directories with rc.0 (shutdown), rc.1 (single user), rc.2 (normal login - I think), the rest are not used (again, I think).

---

### Post by bernied on 2006-12-23
So the file that is run is /etc/rcS.d/S40networking which is a symlink to /etc/init.d/networking

But read /etc/rcS.d/README before you change the order.

I've just re-read your last post, I think the pre-up sleep needs to go after the two wireless commands, not before.

---

### Post by bernied on 2006-12-23
I just saw something a bit weird on [another post]("http://www.ubuntuforums.org/showthread.php?t=241565") that might help:
```
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "******"
pre-up iwconfig ra0 mode Managed
```That 'turn it on, turn it off, turn it on, turn it off' malarky seems a bit bizarre to me, like flicking a light switch on and off a few times to show it who's boss. But might be worth a try for you.

---

### Post by dennis1200 on 2006-12-25
In response to the last several posts (thanks for your interest and help!)

> I've just re-read your last post, I think the pre-up sleep needs to go after the two wireless commands, not before.

pre-up sleep still didn't work after relocating it to after the 2 wireless commands (i.e. to the end of the interface entry). It does wait the 3 seconds, but to no effect.

> Another thing you could try is to shift the order of the init scripts, so that the networking one runs later

I tried various SXX combos, from the current S40 (at which point networking *should* be available, according to the rcS.d README), up through S89 (second to last item in rcS.d - before **S90console-screen.sh**


And the pre-up up/down/up/down thing also failed. Even trying mode open and mode managed (I believe my card needs the open mode, or at least always has for a proper WEP connection). I have not, however, tried the up/down lines with a boot order of S89. I might as well try S95 while I'm at it, though. I'll let you know what happens.

---

### Post by dennis1200 on 2006-12-26
No luck with S95 either. I'm thinking I'll just disable on boot and stick in a line in rc.local, much as I hate to do it :rolleyes: . Anyone have any other ideas? Thanks for all the help you've given me already.

---

### Post by dennis1200 on 2006-12-26
I just thought of something - runlevels. I forget how the 1-6, 0, S work. But sysv-rc-conf shows networking as running in runlevel 0 and S. Anything I should be changing there?

---

### Post by bernied on 2006-12-26
I'm pretty sure that S is a common startup. This stuff is always run at startup. Level 0 is shutdown, that's why most of the links start with K (kill). Level 1 is single user (root), level 2 is default with desktop (I think). The rest are duplicates of 2 (again I think). You can use these for whatever you want. There might be something special about 6.

There's a thing called the Debian Policy Manual, which details this stuff. [This bit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit) discusses the rc system. I'm pretty sure that Ubuntu (which was originally based on Debian) adopted this stuff and hasn't messed with it.

---

### Post by bernied on 2006-12-26
After reading that myself, maybe it's rubbish. Maybe [this](http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-custombootscripts) is more relevant, especially the last line  of section 2.4.3.

---

### Post by linuxa on 2006-12-29
I've been having similar problems with my wireless recently as well.

All I did was change the essid from the router, and the /etc/network/interfaces file no longer takes after the essid is corrected, I'm having to use:

[I]sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key open <password>
sudo iwconfig wlan0 essid <essid>
sudo ifconfig wlan0 up
sudo ifup wlan0[/I]

and it only works if I drop the wirelss prefix in the interfaces file (essid instead of wireless-essid). 

Kind of freaks me out that a simple change like this would totally ruin the way the network is suppose to be brought up.

In regard to the runlevel, AFAIK, ubuntu **doesn't** adopt Debian's runlevel policy. You can try setting the run level to text mode, you'll find it still boots to gui. The only way to change to text mode on boot (haven't yet figured out how to change to the other runlevel options :p) seem to come from deleting the shortcut to kdm or gdm from within /etc/rc.d.

---

### Post by bscook on 2007-01-03
i've begun to experience a similar problem with a WIRED network on my pc.  basically, network active at bootup, but if i go into a terminal and enter "sudo /etc/init.d/networking restart" everything works fine.

it was working up unitl about a week ago.  i haven't directly changed any network settings since then, but maybe one of the automatic updates?

anyway i'll keep fooling around and post if i come up with anything...

---

### Post by bscook on 2007-01-03
i tried all suggestions in previous posts.
pre-up suggestions (ifconfig up, wait 2, etc) either at the top of the list following iface line, or at the bottom of the list.  makes no diff. tried delays of 2,3,5,10,12 seconds to no avail.  

thanks for the suggestion of putting in the cheat in rc.local ... that seems to workaround the problem...

---

### Post by dennis1200 on 2007-01-03
So I've just gotten back to my home away from home after winter break, and can confirm this with 2 networks (both WEP-encrypted). What the network does, despite a correctly written interfaces file, is automatically connects to an unsecured network (at home there wasn't one, which is why it was hanging). So here, in Chi-town, there is an unsecured network, which gets a connection on boot, meaning no hang time, and the rc.local restart command gets me connected to my WEP network. Still, none of the above solutions (pre-ups and whatnot) do anything. Is there another boot file for networking which I should tinker with?

---

### Post by bernied on 2007-01-03
a few more (lame) ideas:
- remove the interface completely from the interfaces file - just comment out all the lines with it in. If it still comes up on boot then you know that something else is involved. If it doesn't come up on boot, write a short script that brings it up (networking restart won't do it once it's removed from interfaces) the right way.
- look in the files in /var/log especially messages (also maybe syslog and dmesg)
- look for other configuration files, especially if they're called wireless, probably somewhere in /etc and sub-directories

I'm certain there's a simple explanation for this disobedient behaviour, but i'm stumped.

---

### Post by dennis1200 on 2007-01-04
Well, before getting into too many of your solutions, I did peek at dmesg output, which showed some interesting stuff. First, and I've known this for a while, ndiswrapper boot entries in dmesg show wlan0, though my interface is eth1 (iftab is eth1, and ndiswrapper alias is also eth1). this doesn't seem to have posed any problems, but who knows.

However, here I wouldn't be surprised if this were a problem - ipv6. After having detected all the hardware, there are two entries near the very end of dmesg output (5th to last and last).

```
[17179603.668000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[17179603.668000] cpu_init done, current fid 0xa, vid 0x4
[17179608.888000] ppdev: user-space parallel port driver
[17179609.848000] apm: BIOS not found.
[17179611.748000] eth1: no IPv6 routers present
[17179612.740000] ip_tables: (C) 2000-2002 Netfilter core team
[17179612.768000] Netfilter messages via NETLINK v0.30.
[17179612.828000] ip_conntrack version 2.4 (3575 buckets, 28600 max) - 232 bytes per conntrack
[17179626.200000] eth1: no IPv6 routers present
dennis@dennis-laptop:~$ dmesg

```

Think that *that* means anything? I'll also try some of the other suggestions.

---

### Post by sonasi on 2007-01-12
I too was having the restart networking after boot to get my wireless working.

See [http://ubuntuforums.org/showthread.php?p=2004543#post2004543]("http://ubuntuforums.org/showthread.php?p=2004543#post2004543")
for the fix that I found.

---

### Post by bernied on 2007-01-12
genius

---

### Post by dennis1200 on 2007-01-13
But how would I use this fix for WEP, instead of WPA? Nice to know at least that the problem isn't just me.

---

### Post by sonasi on 2007-01-13
I don't think this fix would help at all for WEP.  As far as I know wpa_supplicant has nothing to do with WEP.  When I used to use WEP, I never had any problems or needed to restart networking.  My bad for assuming everyone was wrestling with WPA/WPA2.  Sorry.

---

