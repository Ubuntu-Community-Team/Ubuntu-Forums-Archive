---
title: "Can't switch to static ip addresses"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by sonicsmooth on 2007-10-30
7.10 gutsy

I'm trying to set up a home server so I need static ip addresses from my wireless belkin router.

The router's DHCP function does not allow static leases; that is, I can't assign a specific IP address to an incoming MAC address.

Therefore I'd like to turn off the DHCP function in the router and turn on static ip in my PC.

However, whether I try it through the gui or through the /etc/network/interfaces file, and restart the networking service, my ifconfig eth0 shows no IP address, and there is NO routing table when I type netstat -rn.  When I try pinging the router 192.168.1.1 it says network unreachable.

in this case my interfaces file looks like this:
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

where 192.168.1.1 is the router, and I'm trying to get my PC to be 192.168.1.2

Interestingly, even when I turn off the DHCP function, my *other* machine (a laptop), which still has the old IP address assigned, still works, and that's how I'm able to re-enable the DHCP function in the router (through its web interface).

When I turn dhcp back on and re-establish the connection, it all works fine.

Any idea what is going on?  This is the simplest thing and absolutely can't get this and about 50 other "simple" things to work on my f*ing machine.  I'm about to explode I'm so frustrated.

thanks
Michael

PS 
* My dvd rom won't mount (some 0x54 error), I've tried changing the cable, changing the controller, changing the IDE channel, etc.  It will mount CDs (both data and music) but not DVDs.  I have *all* the libdvdcss2 and libdvdread stuff installed ad nauseum, and all my soft links work fine.

*NFS doesn't seem to work NO MATTER how many times I try mounting it, In the rare cases it does work it's v e r y   s l o w

*xine doesn't read my chanels.conf and therefore won't watch DVB, even though it used to when it was out of the box.

*xine won't play .ts files even though it used to when it was out of the box, 

* I can never figure out which of the 30 different codecs, demuxes, driver, etc., I should use with what type of video file.  Why can't mplayer just figure it out?  I hate mplayer.  What idiot decided it's a good idea to force the user to pick from 30 different codecs? WTF?

*sound doesn't work straight with my extigy (only through some apps, but not by default, even though I've enabled usb-audio as default) , 

* mythbuntu seems to only half work.I can access absolutely NO content, read any directories, find any audio files, watch any TV channels (analog or digital), even though i know all the drivers work and I can sometimes get SOME functionality from the command line tools. *snip*

...I don't know if this is typical or if my machine is cursed.  I'm about to go back to Windows.

---

### Post by wieman01 on 2007-10-30
First of all, please edit your post and remove compromising sections such as the one ending with "F...". You'll get in trouble otherwise, although we all understand your frustration.

Could it be that another computer is claiming "192.168.1.2" and therefore the router won't let you connect?

What is the output of:
> sudo ifdown -v eth0
> sudo ifup -v eth0
> ifconfig

---

