---
title: "Not sure if I have a problem or dont understand..."
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by fedoraboy on 2008-10-02
Okay, I am a long time linux/unix user, but a newbie for ubuntu.

I am seeing what I think is weird stuff happening during a boot of a newly installed ubuntu desktop.  Note: I also have an ubuntu server installed and I don't see it going on there.

The details:
It seems like networking isn't starting when I think it should.  In fact, a good portion of the rc scripts have run by the time networking comes up.  I created an /etc/init.d/testnet script that pings a local host on the network, does an ifconfig -a and attempts to resolve an external host -- just to see if networking is ... well ... working.

I then symlinked it in all over the place so I could see where the network actually comes up.

For example: here is my /etc/rc5.d directory:
K20apmd
K20exim4
K20hotkey-setup
K20ixbiff
K20ntop
K20rsync
K99laptop-mode
README
S01policykit
S01testnet
S05vbesave
S10acpid
S10sysklogd
S10xserver-xorg-input-wacom
S11klogd
S12dbus
S16ssh
S17portmap
S18avahi-daemon
S19autofs
S20apport
S20cupsys
S20gdomap
S20nfs-common
S20nfs-kernel-server
S20nvidia-kernel
S20powernowd
S20samba
S20smartmontools
S20xinetd
S21sendmail
S22ntpdate
S23ntp
S24aatestnet
S24dhcdbd
S24eetestnet
S24hal
S24testnet
S25bluetooth
S25pulseaudio
S30cfsd
S30gdm
S50testnet
S89anacron
S89atd
S89cron
S98usplash
S99acpi-support
S99rc.local
S99rmnologin
S99testnet
S99timidity

The first testnet that works is S24testnet -- after hal starts.  

So my questions:
Is that really where networking is coming together?  Or is there some backgrounded process early on that is just finishing?

This is as simple of a network connection as you can get.  It is a wired ethernet with a static IP.  I would think it would come up with the first ifconfig.

---

### Post by Iowan on 2008-10-02
I usually start a little further down the pipe. You mentioned that after the machine boots, **ifconfig -a** looks kosher? Contents of **/etc/network/interfaces** verify that eth0 is configured as desired?

I'm a bit confused by what you mean: > I also have an ubuntu server installed and I don't see it going on there.

---

### Post by fedoraboy on 2008-10-02
ifconfig -a gives expected results....  but networking doesnt work.  I.e, unable to ping a host on the local network.

I notice it in several startup scripts.

I have one startup script that attempts to do ntpdate towards a time server.  The dns lookup for it times out.  If I replace it with a hard IP, the ntpdate times out.

what I mean by "I dont see it on my ubuntu server" is that I have a second system with the ubuntu server edition.  On that system, networking actually works.  Both do ntpdate with rcN.d/S22ntpdate.  And the server has much fewer processes starting, 

...I am mostly trying to figure out if the ubuntu desktop normally works this way... or if I have boned something along the way.

---

### Post by Iowan on 2008-10-03
Post **/etc/network/interfaces**.

---

### Post by fedoraboy on 2008-10-03
Okay, I solved it.  (By "I solved it" I am pretty much copping out and almost lying.  What I really mean is: "I narrowed it down enough to get around it.")  But I'll post the summary here for future googlers.

The problem is either the tulip ethernet driver, a hardware issue with my old cranky hardware or some oddity with ubuntu and this card.  I've not had the problem in the past (Fedora 7 previously on this box) but F7 is a little out of date, so it could be that the current version of fedora is busted too.

Anyway, I went to the big box of semi broken stuff in the attic and fished out another card that would trigger a different driver.  Low and behold, the issue goes away.

The tulip card always did come up, but it seemed like it took a minute or more.  During that time, it was configured correctly (according to ifconfig) but got TX errors.  If you looked at the switch end, there was no carrier at all during this time.

I had also done other tweaks, like turning of ipv6 and turning off source address verification -- and both of these made the card come up faster... but still was gosh darn slow.

...but it works now.

---

