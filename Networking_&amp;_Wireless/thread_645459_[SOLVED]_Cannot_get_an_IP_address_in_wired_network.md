---
title: "[SOLVED] Cannot get an IP address in wired network"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by Prodromoi on 2007-12-20
This has been driving me nuts...

I've recently set up three machines with Ubuntu 7.10 (desktop).  Two work perfectly, one doesn't.  The one that isn't behaving is a 64-bit install whereas the other two are i386 installs - although I don't know if this is significant.

The misbehaving machine will *not* see the router (wired, not wireless) or the internet.  When looking at the IP (using /sbin/ifconfig) I found that a program called avahi always allocates it 169.254.7.100 as the IP.  The router is supposed to dish out DHCP addresses of 192.168.x.x The two other Linux boxes get the correct IP as does the WinXP box on the same network.

I've done much searching of this forum and the net in general and found a lot of mention of avahi (and problems with it) but not been able to work out the solution.  I am a Linux newbie so a lot of what I've read goes over my head...!

Just to eliminate the obvious, I have:
Checked that the network cable works.
Checked that the socket on the router works.
Installed a different network card to make sure it's not a faulty network card.

I can't find an obvious way of amending the avahi settings.  I have tried a few obvious things like preventing it from starting using the 'Services' program, and even editing the /etc/default/avahi-daemon file to prevent avahi starting.  Neither option actually prevents avahi from starting on boot up though!

Can any please give me some newbie-friendly help here?

Can I change settings within avahi so that it doesn't over-rule the IP allocated by the router?
Do I actually need avahi running, and if not, how to disable it?
Or do I have to live with the weird IP that it sets and find some way for the router to see the machine?

Thanks in advance,
Al

---

### Post by Prodromoi on 2007-12-20
Right... I've been trying to sort this out all day and I'm a bit closer, but still not there.

According to the good folks on the #avahi IRC channel, what I've described isn't a problem with avahi, but with my DHCP settings.  So I've been trying to sort those out...

My i386 installs have "roaming enabled" as their default network connections and both are fine.  The 64-bit install also defaulted to that... but it isn't working.

I changed it (using System > Admin > Network) to DHCP.  Still nothing.

I changed it to a static IP address and gave that info to the router to allocate a static IP address to a machine of the appropriate name.  Still the same problem.  I  can't even ping the router.

Current network settings are:
IP address 192.168.1.6
Subnet mask 255.255.255.0
Gateway address 192.168.1.1

Running ethtool indicates that the network card is running and recognised (if I'm reading the output correctly).

If anyone can help get my settings sorted out, that would be great...

---

### Post by Prodromoi on 2007-12-20
(Bump, 'cos the thread has a new title now...)

---

### Post by danwood76 on 2007-12-20
Do you have green lights on the router and network card indicating a full connection?

regards,
Danny

---

### Post by Prodromoi on 2007-12-20
> **danwood76 said:**
> Do you have green lights on the router and network card indicating a full connection?

regards,
Danny

For the other three machines on the network (including the one I'm typing on now), yes.  On the port that the 64-bit machine is plugged into, the light is not lit.  (There's no light on the network card to indicate either way, alas.)

However, I tried a working machine in the same router port; all was OK.  I tried a PCI network card instead of the motherboard's on-board LAN card; still no sign of life.

---

### Post by danwood76 on 2007-12-20
it sounds like you may have a duff cable. have you tried other cables?

---

### Post by Prodromoi on 2007-12-20
Yep, tried that.  Grabbed one of the cables from one of the other machines which is working fine.

---

### Post by NilsE on 2007-12-20
Just for the heck of it do a  

sudo dhclient  

In a terminal and see if it resolves. If it does not it may give you more errors to look into.

Normally I resolve with no problem but every once in awhile I have to do this.

---

### Post by Prodromoi on 2007-12-20
> **NilsE said:**
> Just for the heck of it do a  

sudo dhclient  

In a terminal and see if it resolves. If it does not it may give you more errors to look into.

Normally I resolve with no problem but every once in awhile I have to do this.


OK, just tried that.  No success I'm afraid.  Got the response (after four failed attempts to discover) of "No DHCPOFFERS received".

The router has DHCP enabled and it's working for the other three machines - and a static IP address manually input for the troublesome one.

---

### Post by danwood76 on 2007-12-20
It must be a driver problem.
Try recompiling the latest driver making sure you have the 64 bit version.

Out of interest if you put the 32 bit live CD in does it get network access?

---

### Post by Prodromoi on 2007-12-20
That's a good idea about trying the 32-bit LIve CD, thanks... I'll try that now.

However, I have no idea how I'd go about recompiling any drivers!

---

### Post by oceanfree17 on 2007-12-20
Hi,

Apart from the 64 bit installation being the clearest difference, had that 64bit install machine XP on it before Ubuntu?

Whatever I did to XP, before my move to Ubuntu, stopped funcitonal 64bit installs? Once I got used to Ubu and finally removed XP - networking issues were gone!

Maybe a stab in the dark ... and Happy Holidays!!!!!!!!!!!!!!!!!!!!

---

### Post by Prodromoi on 2007-12-20
At last... the problem is solved!  And to say that the solution defies logic (well, to me anyway) seems an understatement.

In desperation I went back into the motherboard BIOS to see what I could tinker with.  The onboard LAN was - of course - enabled.  However, I thought I'd try and see what happened enabling the "boot from LAN" option as well might do.  Not that I expected anything different really...

Blow me if it didn't fix the problem!  I got a nice green light on the modem, and things started happening.  I've disabled the static IP and the machine is now happily seeing the router and the internet using the "roaming enabled" network setting.

Only taken me two days to figure the damn thing out!

The suggestions helped however.  Everything eliminated gets you closer to the answer...

---

