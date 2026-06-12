---
title: "Separate NAS or Server required?"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-03
Hi,

I've recently started with Ubuntu 8.10 on a Packard Bell Core2Duo with 2x1TB hard drive and 4096MB RAM.

Up to now I've been running Windows XP on the desktop/laptop, a Linux based NAS (IB4220 which was pre-configured for me) and hosting my web/ftp with a provider.

Three problems make me what to change:
1. The new desktop, mentioned above, comes with Vista. Upgrade to a multilanguage version costs over 100 Euros, upgrade to Office over 500 so I decided to go for Linux on the main PC.

2. FTP and webspace are getting out of hand. Plus I want to use CMS that needs PHP 5 (provider only gives PHP 4 at the moment). Some of my clients also require a more secure ftp (e.g. ftp over SSH).

3. My CD player broke so I'm thinking "media centre". The NAS is full of MP3/flv files anyway.

So the first question is; can I move my FTP and possibly web hosting in-house?
I've got about 600MB of ftp data but not a high traffic. I've connected my Fritzbox to dynDNS and can get an ftp or webserver running on the Ubuntu 8.10 home/desktop. However the NAS doens't allow ftp over SSH and doesn't seem configurable enough to be secure.

The next question is: if I move FTP and web in-house. Do I try to get them running on the desktop as some kind of background sevice or do I buy a very low cost computer (thinking <150 Euro ebay) as a server and strip the NAS hard disks out to install them in the server. If I get a second computer I'd probably like to access it by remote console only from the desktop to save buying a monitor and keyboard.

I want the server to be fairly secure and have RAID1 to avoid data-loss.

Appreciate any thoughts...


Richard

---

### Post by handy on 2009-03-03
If you move your ftp & web server in house, you will want to ensure the security of your LAN.

I don't know if you are aware of [*_IPCop_*]("http://www.ipcop.org/")?  I use it as a firewall, proxy, anti-virus, privoxy & some other services.  It is a tiny specialised Linux installation that is mature, runs headless & is observed & configured via a very slick web browser GUI. IPCop is also easy to install.

IPCop needs little CPU power, I am running mine on a PIII 650Mhz / 256Mb of RAM, that I got for $5- at the local rubbish dump.  A PII is better as they use even less electricity, as far as using new hardware is concerned, the Intel Atom based MiniITX boards work brilliantly & of course use little electricity, they are also very cheap.

I also use [*_FreeNAS_*]("http://www.freenas.org/") on a headless machine, it may or may not be worth your investigation, as it too is a very specialised & tiny installation (FreeBSD this time).  FreeNAS, too, is easy to install & configure, it also has an incredibly slick browser based client side GUI.

As far as RAID-1 is concerned, just remember that RAID is not a safe backup.  

Not even RAID-1, as you can be backing up corruption & not even know about it until it is far too late.

You are better off backing up onto some form of removable drive.  If the data is important then two separate removable drives.  

At a small legal firm who's IT I managed, I set up a system where there were three HDD's for backup, the Server had a drive drawer for ease of installation & removal of a backup drive.  

A drive was used last thing each afternoon to clone the entire Server drive, which included both system & data. 

Two drives were used in a leap frog fashion - day on day off; then the third drive was used only on Fridays.  I created this system in the hope that if something was going wrong that did not get picked up on one day or the next or the next or the next, that surely we would know by the end of the week.

Once, in a 10 year period of using this system the circumstances were such, that we nearly lost the lot. Fortunately the data was salvageable but it was costly to my customer, as a lot of recovery work had to be done by the staff for the 5 days of lost work.  

This shouldn't have happened, it was solely due to the fact that the boss solicitor (who is a technical child) did not pass on the warnings that Ghost was giving him each time he did the backup, before he went home at night.

He & the other 7 staff had all been educated to write down anything that ever happened which was different & pass it on to me.

The boss legal eagle apparently thought himself beyond that, his thinking cost him thousands of dollars & caused him & all of his staff a great deal of stress.

---

### Post by RichardCL on 2009-03-05
Thanks for the tips. I'd heard of freeNAS but not yet IPcop.

My router does have a firewall with port restriction (Fritzbox) but I'm not sure how reliable it is.

I'm backing up the RAID1 every week to one of two external USB drives. I collect all the important data as an uncompressed zip file stored by date so lots of redundancy. I don't bother backing up the operating system since I'm always thinking "I must reinstall the OS with new options". I just collect the sitemap from ftp and the favourites from firefox.

I looked at junkyard pcs but the cost of upgrading to SATA for the two hard disks and adding WLAN looks to be more than the cost of the Atom you recommend. I think I'll go for an Atom PC without harddisks and then implant the two 1TB hard disks from the NAS.

---

