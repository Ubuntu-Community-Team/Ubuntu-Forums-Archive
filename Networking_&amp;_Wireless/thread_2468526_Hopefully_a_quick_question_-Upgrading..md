---
title: "Hopefully a quick question -Upgrading."
date: 2021-11-02
forum: Networking &amp; Wireless
---

### Post by 77_GCSX on 2021-11-02
[SIZE=3][FONT=times new roman]The system = Dell Optiplex 3010 (I know, it's old BUT it works), all stock/OEM except a 1 TB SSD 8 gb ram

I am currently running 16.04 lts and would like to upgrade to 20.04. I had tried this once before but backed out due to a NIC issue. I want to fully try this again.

The question is: Does the integrated NIC = [COLOR=#000000]RealTek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06) work "out of the box" with 20.04? Will I be able to upgrade and have an internet connection or will I need to do some updating of the driver?

Thank You![/COLOR][/FONT][/SIZE]

---

### Post by hk42 on 2021-11-02
Using 20.04 this is the result of sudo lspci:
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
It worked "out of the box"
I don't know for (rev06)
You should be able to test it from the live USB before installing anything.

---

### Post by T6&amp;sfpER35% on 2021-11-02
as hk42 pointed out , it should work. 
the question is,how do you want to upgrade? fresh install with iso image or somehow else?
iv'e read somewhere that its not a good idea to skip versions with a upgrade ,meaning one should upgrade to 18.xxx and then to 20.04.xx

[https://askubuntu.com/questions/1263794/how-to-upgrade-from-ubuntu-16-04-lts-to-20-04-in-virtual-machine]("https://askubuntu.com/questions/1263794/how-to-upgrade-from-ubuntu-16-04-lts-to-20-04-in-virtual-machine")
[https://ubuntu-mate.community/t/upgrade-path-from-16-04-20-04/21625]("https://ubuntu-mate.community/t/upgrade-path-from-16-04-20-04/21625")

edit : found [this](https://askubuntu.com/questions/1186854/realtek-ethernet-driver-issue-network-unclaimed-ubuntu-18-04) and [this](https://forums.linuxmint.com/viewtopic.php?t=295124) when searched around a bit.
might be of help

---

### Post by 77_GCSX on 2021-11-02
> **hk42 said:**
> Using 20.04 this is the result of sudo lspci:
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
It worked "out of the box"
I don't know for (rev06)
_**You should be able to test it from the live USB before installing anything**_.


Well now this is cool. I knew you could boot using the USB but not testing the NIC of the PC it's plugged into. I'll give it a try and report back (not real soon but soon).

Thank You.

---

### Post by 77_GCSX on 2021-11-02
> **3nd said:**
> as hk42 pointed out , it should work. 
the question is,how do you want to upgrade? fresh install with iso image or somehow else?
_**iv'e read somewhere that its not a good idea to skip versions with a upgrade ,meaning one should upgrade to 18.xxx and then to 20.04.xx**_

[https://askubuntu.com/questions/1263794/how-to-upgrade-from-ubuntu-16-04-lts-to-20-04-in-virtual-machine](https://askubuntu.com/questions/1263794/how-to-upgrade-from-ubuntu-16-04-lts-to-20-04-in-virtual-machine)
[https://ubuntu-mate.community/t/upgrade-path-from-16-04-20-04/21625](https://ubuntu-mate.community/t/upgrade-path-from-16-04-20-04/21625)

edit : found [this]("https://askubuntu.com/questions/1186854/realtek-ethernet-driver-issue-network-unclaimed-ubuntu-18-04") and [this]("https://forums.linuxmint.com/viewtopic.php?t=295124") when searched around a bit

That was going to be my next question. I'll test it out with the USB and if it works I'll give it a try. If not then I'll do the step by step upgrade.

BTW: Thanks for those links. I'm always up for learning how to fix problems, especially network.

Thank You.

---

### Post by TheFu on 2021-11-02
I wouldn't upgrade that far.  When I moved from 16.04 --> 18.04, it was 2.5 hours and some things broke.  Lots of cruft was left behind and I'll always wonder if some old library is being used and causing issues.

A fresh install is 15 minutes, then you'll know it is a fresh system.  I wish I'd done a fresh install now. BTW, the system where I did this is the main NFS server for the house, running jellyfin, plex, calibra, and inside a VM, nextcloud with about 20 addons for it. I get the entire "I don't want to reinstall everything or lose my data". That's why we do daily, versioned, backups.  I'm planning to move to 20.04 soon on that physical machine. It has a new NVMe SSD that just needs a firmware update before I make the 20.04 fresh install. It also has over 40TB of storage, so I have a little fear of data loss, but I'm fairly good at knowing where things are being installed which I wasn't for about the first 3 yrs using Linux.  I'll be pre-setting up all the storage (partitions, LVM) in the way I want on the SSD, so the installer will just need to be told which partitions/LVs to be used for the specific needs (*do something else* install option for storage).

As for the networking, I also had a rev 0c version of that NIC. Eventually, it had so many dropped packets that I disabled it and dropped in a $10 crappy Maxell NIC bought around 2007. Recently retired that motherboard for a new system - with Intel i210 NIC and added a 4-port Intel 82575GB NIC to have some VMs with better security using PCIe passthru for VMs. If you are worried about NIC support, $25 for a well-supported Intel GigE NIC is a great investment. Things "just work". Be careful with 2.5Gbps NICs.  In theory, those should be fine, but ... if you search these forums, you'll see some people got stuck and ended up buying a $25 older, Intel NIC. I know the i211 are well supported too.  The Intel v-217 seems to have some issues and if it isn't clear, I avoid Realtek NICs completely.

OTOH, realtek is the most popular NIC on motherboards and most of the time, they just work.

---

### Post by 77_GCSX on 2021-11-02
@ TheFu (and everyone else)

I REALLY appreciate all the input. I forgot to mention that my reason for Upgrading was just to do the upgrade and turn the PC into a Plex server. I've used Ubuntu Desktop before as a Plex server and it worked great.

I think what I'll do is: First try the 20.04 Live USB and see how things go. If there are issues then I'll try a Live USB of 18.04. If THAT still causes issues then I'll fall back to my alternate plan - Make my Windows PC the Plex server and then work on the upgrades on the 16.04 PC.

**ACTUALLY** A fresh install sounds decent. I do have yet another spare PC just sitting collecting dust. I could do the fresh install on that. However, the only network access that one would have is a Netgear A6100 USB wifi adapter which I have seen as having some issues as well BUT: If I were to do a fresh install on this AND have the 6100 plugged in already, does this adapter "work out of the box"? If it does I may just go this route.

---

### Post by TheFu on 2021-11-02
You don't need to loose most settings.  Just be certain to backup the specific files, not everything, just the ones used by the specific programs (like Plex), then do a basic install and restore that backup data back EXACTLY where it was before.  Again, don't just grab everything in /etc/, since many of those will use new settings and different userids after a fresh install.  For plex, you probably just want /var/lib/plex*  which would be smart to make a different storage volume (not part of the default / partition).  Then when plex starts, it will see all that data (assuming you have the plex username-userid-groupid on the new system correct for those files).  Also, put all the media storage back where it was and you should be golden, at least for plex.  The same idea applies to most other programs.

If your current system doesn't have /var/lib separate from / (partitioning), then everything under /var will be wiped.

That old computer may be a great idea - or not. Hard to say.  If your playback devices use plex transcoding, it could be a bad idea.  I just switched from a dual Core pentium to a 6 core Ryzen a few weeks ago for my Plex/mpd/calibre/nextcloud/wallabag/jellyfin/nfs server. Because is it a pure server and I seldom use it with a monitor connected, I don't really know how much faster is "feels". The NFS stuff is a little faster, but that's because the NIC changed.  I don't really do transcoding on that machine. I tried to move some of my video editing and commercial removal stuff to it, but strange dependency issues are breaking that effort.  For a few days last week, even my simple perl scripts for tv scheduling and recording were broke due to mismatched libraries. Eventually, I traced it back to some libraries in /usr/local/lib/perl5 ... by removing those compiled libraries, nearly everything started working again.  I also added perlbrew and use a newer install of perl for my personal needs, which is probably where the odd /usr/local/lib/perl5 problem originated.  Manually installed perl stuff (I've been a perl developer for 25 yrs) that would only happen to someone like me was the issue. I doubt anyone else would get into the same issue during a CPU upgrade and OS migration.  Plus, to get the iGPU in the Ryzen working, I'm running a very new kernel on that system with an OS that doesn't have it.

I'd say to avoid all use of wifi for computers in your home.

---

