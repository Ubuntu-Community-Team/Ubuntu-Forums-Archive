---
title: "CUPS Network access broken in Hardy"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by drpaul on 2008-07-10
I got no response in the General Forum. Hope I hit pay dirt here. :)

After some recent Hardy upgrades, the access to the ipp printer I had set up in CUPS is broken. The printer is connected locally [USB], and I can print locally.

The CUPS interface page reports

"Unable to get printer status (Forbidden)!"

for the printer set up as ipp: interface. Other machines [Windows] can't see it, although they can ping my Hardy machine. It used to work [Gutsy and right after upgrade, I think]. Something is certainly wrong as CUPS can't sense the printer status.

Any ideas are truly welcome. I have messed around a little with cupsd.conf but have had no affect.

TIA

Paul

---

### Post by drpaul on 2008-07-11
Doesn't look like I'm getting any response here, either.

After starting my computer yesterday, I decided [based on some old thread reading] to install gnome-cups-manager. I opened it and it was working [my network printer]. Don't really know what fixed it, but it works now.

:confused:

que sera

Paul

---

### Post by jpv on 2008-07-14
Per [http://lists.netisland.net/archives/plug/plug-2008-06/msg00075.html](http://lists.netisland.net/archives/plug/plug-2008-06/msg00075.html) I'm printing to CUPS printers from W2K and XP.  That's a lot easier than my old way with Samba; when it works. :-/

It stopped working again, sort of, too.  Note my issue is not wireless related, but this was the best thread I was able to find...

XP2 and Linux all continue to work fine over IPP, as does the LaserJet4 on CUPS on Debian.  But the OfficeJet K-60 on Ubuntu Hardy (workstation) simply stopped working from W2K Pro only, around Friday (2008-07-11).  I did some Ubuntu updates [1], but none of them jump out at me as the cause.  (But...  There was a kernel update...  And I have not rebooted into an older kernels to test, as it's a pain to reboot that machine again so soon.)

I completely purged all the CUPS and HP stuff I could find on the Ubuntu machine, and reinstalled.  AFAICT, the sticking point is W2K --> Ubuntu Hardy latest.  All other combinations work e.g., W2K --> Debian, XP --> Ubuntu, Ubuntu --> anything.  Note the W2K is in VMware VM but I've tried a variety of versions of it trying to rule out changes (or more likely corruption) on the W2K side.  None worked.  And up until Friday or so, everything was just fine.

The symptoms are as follows:

1) Printing to Ubuntu (IPP) from W2K Pro just stopped working.  The local W2K queue built up, but CUPS showed no jobs and nothing printed.  Printing from XP2 and/or Ubuntu (local or remote) was unaffected.

2) Deleting and reinstalling all CUPS/HP software on the Ubuntu side had no effect.  (Not surprising but I'd wanted to do that anyway.)

3) Deleting all printers and "related ports" on the W2K side worked.  But...

4) Attempting to re-add the printer fails with "Could not connect to the printer.  You either entered a printer name that was incorrect or the specified printer is no longer connected to the server.  Click help for more information."  Browsing to the identical URL in FF works as expected and also as expected the Event Log is utterly and completely useless (as always).  Googling for this generic message has also thus far been useless.  Lots of hits, nothing relevant.

5) Fiddling with TCP settings in /etc/sysctl.conf per 
[http://ubuntuforums.org/showthread.php?t=796194&highlight=IPP](http://ubuntuforums.org/showthread.php?t=796194&highlight=IPP) and [http://ubuntuforums.org/showpost.php?p=5211755&postcount=58](http://ubuntuforums.org/showpost.php?p=5211755&postcount=58)
and the suggestion above did not help me.

So, after killing way too many hours on the issue over the weekend, I gave up.  I moved the LaserJet off the parallel port on the Debian server and on to a JetDirect card, which I'd been meaning to do anyway.  Then I moved the OfficeJet from Ubuntu to Debian, and now it all works.

I suspect something in the most recent kernel update did it, so I'm posting all of this in an attempt to provide details and clues for anyone else in the same boat.


_______________________________
[1] Aptitude logs:
	Aptitude 0.4.9: log report
	Mon, Jul  7 2008 15:30:11 -0400
	
	IMPORTANT: this log only lists intended actions; actions which fail due to
	dpkg problems may not be completed.
	
	Will install 16 packages, and remove 0 packages.
	1810kB of disk space will be used
	===============================================================================
	[HOLD, DEPENDENCIES] linux-image-generic
	[HOLD, DEPENDENCIES] linux-restricted-modules-common
	[HOLD, DEPENDENCIES] linux-restricted-modules-generic
	[HOLD, DEPENDENCIES] mytharchive-data
	[INSTALL, DEPENDENCIES] libsilc-1.1-2
	[HOLD] linux-generic
	[HOLD] linux-headers-generic
	[UPGRADE] libpurple0 1:2.4.1-1ubuntu2 -> 1:2.4.3-0ubuntu1~hardy1
	[UPGRADE] mytharchive 0.21.0+fixes16838-0ubuntu2 -> 0.21.0+fixes16838-0ubuntu2.1
	[UPGRADE] mythbrowser 0.21.0+fixes16838-0ubuntu2 -> 0.21.0+fixes16838-0ubuntu2.1
	[UPGRADE] mythbuntu-control-centre 0.27-0ubuntu1 -> 0.28-0ubuntu1~hardy2
	[UPGRADE] mythcontrols 0.21.0+fixes16838-0ubuntu2 -> 0.21.0+fixes16838-0ubuntu2.1
	[UPGRADE] mythflix 0.21.0+fixes16838-0ubuntu2 -> 0.21.0+fixes16838-0ubuntu2.1
	[UPGRADE] mythgallery 0.21.0+fixes16838-0ubuntu2 -> 0.21.0+fixes16838-0ubuntu2.1
	[UPGRADE] mythgame 0.21.0+fixes16838-0ubuntu2 -> 0.21.0+fixes16838-0ubuntu2.1
	[UPGRADE] mythmusic 0.21.0+fixes16838-0ubuntu2 -> 0.21.0+fixes16838-0ubuntu2.1
	[UPGRADE] mythnews 0.21.0+fixes16838-0ubuntu2 -> 0.21.0+fixes16838-0ubuntu2.1
	[UPGRADE] mythvideo 0.21.0+fixes16838-0ubuntu2 -> 0.21.0+fixes16838-0ubuntu2.1
	[UPGRADE] mythweather 0.21.0+fixes16838-0ubuntu2 -> 0.21.0+fixes16838-0ubuntu2.1
	[UPGRADE] pidgin 1:2.4.1-1ubuntu2 -> 1:2.4.3-0ubuntu1~hardy1
	[UPGRADE] pidgin-data 1:2.4.1-1ubuntu2 -> 1:2.4.3-0ubuntu1~hardy1
	[UPGRADE] tomboy 0.10.1-1 -> 0.10.2-0ubuntu1
	===============================================================================
	
	Log complete.
	Thu, Jul 10 2008 17:58:06 -0400
	
	IMPORTANT: this log only lists intended actions; actions which fail due to
	dpkg problems may not be completed.
	
	Will install 19 packages, and remove 0 packages.
	195MB of disk space will be used
	===============================================================================
	[INSTALL, DEPENDENCIES] libdns35
	[INSTALL, DEPENDENCIES] linux-headers-2.6.24-19
	[INSTALL, DEPENDENCIES] linux-headers-2.6.24-19-generic
	[INSTALL] linux-image-2.6.24-19-generic
	[INSTALL] linux-restricted-modules-2.6.24-19-generic
	[INSTALL] linux-ubuntu-modules-2.6.24-19-generic
	[UPGRADE] bind9-host 1:9.4.2-10 -> 1:9.4.2-10ubuntu0.1
	[UPGRADE] dnsutils 1:9.4.2-10 -> 1:9.4.2-10ubuntu0.1
	[UPGRADE] libbind9-30 1:9.4.2-10 -> 1:9.4.2-10ubuntu0.1
	[UPGRADE] libisc32 1:9.4.2-10 -> 1:9.4.2-10ubuntu0.1
	[UPGRADE] libisccc30 1:9.4.2-10 -> 1:9.4.2-10ubuntu0.1
	[UPGRADE] libisccfg30 1:9.4.2-10 -> 1:9.4.2-10ubuntu0.1
	[UPGRADE] liblwres30 1:9.4.2-10 -> 1:9.4.2-10ubuntu0.1
	[UPGRADE] linux-generic 2.6.24.18.20 -> 2.6.24.19.21
	[UPGRADE] linux-headers-generic 2.6.24.18.20 -> 2.6.24.19.21
	[UPGRADE] linux-image-generic 2.6.24.18.20 -> 2.6.24.19.21
	[UPGRADE] linux-restricted-modules-common 2.6.24.13-19.42 -> 2.6.24.13-19.44
	[UPGRADE] linux-restricted-modules-generic 2.6.24.18.20 -> 2.6.24.19.21
	[UPGRADE] mytharchive-data 0.21.0+fixes16838-0ubuntu2 -> 0.21.0+fixes16838-0ubuntu2.1
	===============================================================================
	
	Log complete.

>>>>>	reboot   system boot  2.6.24-19-generi Thu Jul 10 18:41 - 03:15 (3+08:34) <<<<<

---

### Post by drpaul on 2008-07-14
How are you managing the printers on the Ubuntu machine? They are connected to that one, right?

I can't check all of your various conditions, but if others on the local network can access the ipp printer, then you might look at the way permissions have been set up. Can you ping the Ubuntu machine from the W2K system?

Sounds like a very hairy problem.

Paul

---

### Post by jpv on 2008-07-15
> **drpaul said:**
> How are you managing the printers on the Ubuntu machine? They are connected to that one, right?

There was a printer on an Ubuntu machine and another on a Debian Etch machine.  I was managing the one on Ubuntu via CUPS (localhost), Admin, Printing (Sys-Cfg-printing and also Gnome CUPS manager (OLD)).  None had any useful effect on the problem, but all worked fine otherwise.


> **drpaul said:**
> I can't check all of your various conditions, but if others on the local network can access the ipp printer, then you might look at the way permissions have been set up. Can you ping the Ubuntu machine from the W2K system?

Yes, everything works as expected except that connecting to the printer on the Ubuntu machine via IPP (W2K HTTP) or printing to same fails **from W2K only**.  Connecting to CUPS via Firefox (e.g. to copy the URI) works fine.  Printing to that printer from XP2 or Ubuntu also works fine.

My guess is that it's a bad interaction between a recent Ubuntu Kernel update and W2K Windows "networking" and/or TCP/IP.  But that is just a guess and I've worked around the problem by moving everything to Debian, which Just Works.

---

### Post by drpaul on 2008-07-15
It's frustrating that bugs like this don't get very much attention.

It's probably more trouble than it's worth, but it would be interesting to try the printer on the Ubuntu machine and install gnome-cups-manager. It's what cured my dilemma [different from yours presumably].

Paul

---

### Post by jpv on 2008-07-15
> **drpaul said:**
> [It] would be interesting to try the printer on the Ubuntu machine and install gnome-cups-manager. It's what cured my dilemma [different from yours presumably].

But I *did* that.  Above "5) Fiddling with [...] and the suggestion above [about using gnome-cups-manager] did not help me." and "I was managing [...] and also Gnome CUPS manager (OLD))".  Obviously I wasn't quite clear enough...  It didn't help though. :-(

---

