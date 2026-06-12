---
title: "Speedtouch refuses to work"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by bunced on 2005-06-21
I have converted several of my friends to Linux. 1 of them in particular has a speedtouch modem. I have got everything except this modem working. I have followed all the instructions at [http://www.ubuntuforums.org/showthread.php?t=5879](http://www.ubuntuforums.org/showthread.php?t=5879) - except it is not working!

When I plug in the modem, /var/log/messages says:

```
Jun 16 17:58:22 localhost gconfd (chris-8860): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 16 17:58:22 localhost gconfd (chris-8860): Resolved address "xml:readwrite:/home/chris/.gconf" to a writable configuration source at position 1
Jun 16 17:58:22 localhost gconfd (chris-8860): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 16 17:58:23 localhost kernel: NET: Registered protocol family 10
Jun 16 17:58:23 localhost kernel: Disabled Privacy Extensions on device c02f0500(lo)
Jun 16 17:58:23 localhost kernel: IPv6 over IPv4 tunneling driver
Jun 16 17:58:30 localhost gconfd (chris-8860): Resolved address "xml:readwrite:/home/chris/.gconf" to a writable configuration source at position 0
Jun 16 17:59:32 localhost kernel: DSL line goes down
Jun 16 17:59:32 localhost kernel: ADSL line is down
Jun 16 17:59:47 localhost kernel: ADSL line is up (576 Kib/s down | 288 Kib/s up)
``` 
This seems to suggest that the connection is working, but Firefox won't find it, and the PC won't PING. I have also tried copying DNS settings over from Windows, but still to no avail.

Any help would be much appreciated

David

---

### Post by bunced on 2005-06-26
I know this is wrong, but I really could do with an answer

BUMP

Sorry,
David

---

### Post by darrell on 2005-06-26
David,

/var/log/messages should report something like:


```
Jun 26 21:28:15 localhost kernel: usb 3-2: new full speed USB device using uhci_hcd and address 4
```
... the modem has been plugged in


```
Jun 26 21:28:42 localhost modem_run[12998]: [monitoring report] ADSL link went up
Jun 26 21:28:53 localhost modem_run[12947]: ADSL synchronization has been obtained
Jun 26 21:28:53 localhost modem_run[12947]: ADSL line is up (2272 kbit/s down | 288 kbit/s up)
Jun 26 21:28:58 localhost pppd[13014]: Plugin pppoatm.so loaded.
Jun 26 21:28:58 localhost pppd[13014]: PPPoATM plugin_init
Jun 26 21:28:58 localhost pppd[13014]: Plugin pppoatm.so loaded.
Jun 26 21:28:58 localhost pppd[13014]: PPPoATM plugin_init
Jun 26 21:28:58 localhost pppd[13014]: PPPoATM setdevname - remove unwanted options
Jun 26 21:28:58 localhost pppd[13014]: PPPoATM setdevname_pppoatm - SUCCESS:0.38 

```
...the link has been established


```
Jun 26 21:29:31 localhost pppd[13015]: Connect: ppp0 <--> 0.38
Jun 26 21:29:35 localhost pppd[13015]: CHAP authentication succeeded
Jun 26 21:29:35 localhost pppd[13015]: local  IP address 80.229.150.88
Jun 26 21:29:35 localhost pppd[13015]: remote IP address 195.166.128.53
Jun 26 21:29:35 localhost pppd[13015]: primary   DNS address 212.159.13.49
Jun 26 21:29:35 localhost pppd[13015]: secondary DNS address 212.159.13.50
```
...logged on to ISP and got IP address/DNS servers


You don't seem to be getting this far. Please repost with all your /var/log/messages output from the time you plug the modem in. 

Darrell

---

### Post by bunced on 2005-06-27
I'm sure this is all that happens, but I will check again tonight.

Thanks so far
David

---

### Post by darrell on 2005-06-27
Right then,

Things Speedtouch have changed a bit in Hoary (or more correctly in the 2.6.10 kernel).

It should be simpler - the Speedtouch kernel module seems to have been enhanced so that it no longer needs the "speedtouch" user space stuff at all. All you need to get your modem up is some firmware (and libatm which is in Ubuntu main and on the Hoary cd, but not, AFAIK,  installed by default.)

However, you lose some things by not installing the speedtouch user-space package - ie, the example /etc/ppp/peers/ script to actually get connected to your ISP, and the running of this script automatically through hotplug.

Unfortunately, if you do install the speedtouch user-space package, you don't automatically get this functionality back, because the provided hotplug script doesn't work with the latest version of everyones favorite firmware package [http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012k_all.deb](http://ftp.linux.it/pub/People/md/warez/speedtouch-firmware_0.3012k_all.deb) - this is because the firmware filenames have changed. These are hardcoded in the hotplug script so it thinks there is no firmware and so exits with an error. Meanwhile the kernel has loaded the firmware, brought the line, and the system is just waiting for a pppd to connect...

The hotplug script can be changed (actually just need to comment out most of it) but why install a package which we don't need anymore? 

There is a good Ubuntu howto at  [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) but this doesn't give us back the hotplug functionality to automatically connect to the ISP. 

So, I've created a HOWTO which includes hotplug connection to the ISP without the speedtouch package, and I will submit this to the forum as soon as I've tested it - hopefully within the hour if it all goes ok.

I'll also test the idea of getting the modem up and running with nothing but a Hoary cd and the firmware which shipped with the modem - this would remove the catch 22 of needing a net connection to get on the net... (unfortunately, the HOWTO will still be on the net ](*,) 

Darrell

---

### Post by darrell on 2005-06-27
version 1 of my speedtouch howto is now posted: [http://ubuntuforums.org/showthread.php?t=44763](http://ubuntuforums.org/showthread.php?t=44763)

---

### Post by bunced on 2005-06-29
OK - I have followed all the steps. However, when I plug in, it doesn't connect. When I run 'pppd call adslscript' it loads the modules but it won't log onto the ISP. Am I just being dense?

P.S Thanks for the tutorial, darrell

P.P.S Sorry this is vague but I am trying to help my friend over the telephone

---

### Post by darrell on 2005-06-30
[QUOTE=bunced]OK - I have followed all the steps. However, when I plug in, it doesn't connect. When I run 'pppd call adslscript' it loads the modules but it won't log onto the ISP. Am I just being dense?

P.S Thanks for the tutorial, darrell

P.P.S Sorry this is vague but I am trying to help my friend over the telephone[/QUOTE]

Questions:

1. Does the log show the adsl line synchronising?

Assuming it does:

2. Is the module pppoatm loaded - check with
```
lsmod | grep pppoatm
```

(I've been told that this module should not need to be loaded manually, but at least on my Hoary installation, it does not load automatically and needs to be loaded manually as in the HOWTO.)

3. Does the log show any pppd processes starting up? if not, /var/log/syslog might show more information on errors. You might need to add the line
```
verbose
```
somewhere in /etc/ppp/peers/adslscript to get more feedback from the system. 

If there is no mention of pppd in the /var/log/messages output, it's probably failing due to some misconfiguration in the adslscript or elsewhere.

It is difficult trying to analyse this third hand - your friend's /var/log/messages and /var/log/syslog output would be very useful. 

BTW I've updated the HOWTO, after some feedback, to simplify it. The main changes are:

To forget about trying to delay the pppd launch in the hotplug script until the line comes up - it seems to work better if we just let pppd try immediately and fail a couple of times (it tries 10 times by default, I think). It is also much simpler this way - always a good thing. I've also found out that if the hotplug script is named the same as the kernel module (ie speedtch) the .usermap hotplug file is not needed.

The adslscript file is now based on an example script shipped with ppp - changing a couple of lines in this should be less error-prone than creating a whole new one with copy/paste as I had it before.

Bear with me, I'm learning all this as well.

---

### Post by bunced on 2005-07-07
Will try!

---

### Post by gary_emms on 2005-07-07
Try the instructions at [http://linux-usb.sourceforge.net/speedtouch](http://linux-usb.sourceforge.net/speedtouch). They've got instructions for Hoary and it works fine.
Gaz ;-)

---

