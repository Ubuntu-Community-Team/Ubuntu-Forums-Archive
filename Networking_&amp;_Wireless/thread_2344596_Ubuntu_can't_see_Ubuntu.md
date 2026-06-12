---
title: "Ubuntu can't see Ubuntu"
date: 2016-11-26
forum: Networking &amp; Wireless
---

### Post by FerryGnu on 2016-11-26
14LTS x64 on Master PC
Wired Ethernet fixed IP
14LTS x86 Remote PC (about 12" away)

I can use Remmina on the Master and desktop sharing on The Remote and all good.

Nautilus **cannot** see the Remote - but - it can see a win7-pro laptop and the USB-flash-drive in the router.

What do I need to do to allow me to send files to the Remote?

Bit of a newbie to Ubuntu, so please keep it simple for me. :)

---

### Post by TheFu on 2016-11-26
First, you need to setup some type of **name resolution** so the machines can find each other. In the Unix/internet world, there are 3 normal methods for this:
a) DNS - most complicated, most flexible, most hacked. ;)
b) /etc/hosts - simple and always works. Easy when just a few machines and all have static IPs
c) Avahi - uses the most CPU ... {hostname}.local

As for file sharing, Linux can support many, many, different protocols.  Typically, unix-to-unix sharing on the same LAN is done using NFS.  If you want to share over the internet AND on the LAN, then something based on ssh is typically used, so scp, sftp, sshfs.  And if you want to share with Windows on the same LAN, then CIFS is the normal protocol as implemented by samba.  You can run all of these as you like and each has a place.  All require *name resolution* be solved first.

The most versatile and easiest to configure is to setup ssh on each Ubuntu machine, then use an sftp client from any other machine you are on to connect to the "server."  Windows has sftp/scp clients - filezilla and winscp are typically used. For stock ssh, putty is normally used on Windows.  ssh clients are built-into pretty much every Unix-like OS, including linux.  

Hope this helps.  You can find how-tos for these lots of places online. I try to stick with official Ubuntu versions of the instructions. help.ubuntu.com.

So after you do a little research and decide which type of name resolution you want on your network, we'd be happy to help.  

I use /etc/hosts and NFS, ssh, and samba on my network. Mainly use NFS inside the LAN and ssh/sftp/scp/sshfs over the internet.  Only use samba from Windows clients.

---

### Post by FerryGnu on 2016-11-27
Thanks TheFu,

Being at the pointy end of learning Ubuntu/Linux et al, I'll go for simple. I only need transfers between two Ubuntu PCs, the Remote is for the Home Theater. I am familiar with puTTY so will give that a try.

The Home Theater has been running on windows Vista for a while, but recently (finally) I made the jump to Ubuntu for my main PC, so now swapping everything over to Ubuntu. Damned msoft screwed up Vista updates back in June and still have not fixed it so it was hogging more and more of the CPU and unstoppable. Did not take me long to decide on Ubuntu for the the HT. As part of your name suggests, I say fu to msoft. :D

---

### Post by TheFu on 2016-11-27
Ok - if you want simple and only have a few machines, then 
* setup static IPs for each system - or use DHCP reservations. Reservations are handy for portable devices so they work correctly outside your home network, but still act like static IPs when at home. [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) - my attempt to explain it.
* Put each of the static IPs for all the devices on your home network into all the /etc/hosts files on **every** machine.  This is how IP works.  Only MSFT "broadcasts" their machines on the network saying "I'm here, I'm here, I'm here" all the time. This was their trade-off to make SMB work for small businesses (and really not a bad idea for the small scale).  That doesn't scale and doesn't go across subnets. No other OS does that anymore; other OSes follow standards for IP networking. Getting this stuff into the Windows "hosts" file is a little tricky, but possible. Run an editor as "Administrator." There isn't any way that I know to modify stock Android devices this way. They need to be rooted, to my knowledge. Same probably applies to chromebooks. You can attempt to use hostname.local and see if that works for each of your Linux machines. If it does, that means Avahi is enabled, but you get to add ".local" to their names for IP/name resolution.
* I'm still using a few Win7 VMs for media center, Quicken, Visio and video editing. Haven't found reasonable alternatives for my needs in those areas yet.  Tried to get MythTV working a few times years ago, but my tuners weren't supported then.  Now all my tuners are supported, but here (USA) we have to pay for schedule data and MSFT's is free. Plus I need a few Windows applications still, from time to time, so at least 1 Windows VM is needed anyway.  Besides that, I'm Linux or BSD or Unix.

Putty won't work until you install openssh-server on all the systems. While you are at it, .... 
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) - secure your ssh stuff
[http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh) - learn more things that ssh can do.
For file transfers, putty really isn't the way I'd go on Windows.  WinSCP is.  Don't forget to tweak the transfer settings to speed things up a little.

Oh and don't be too tied to only Ubuntu. Look at different Linux distros and servers.  They are all very similar.  The GUI is just another program. It is NOT the OS.  We can swap out the GUI in just a few minutes with relatively tiny risks.  Canonical has been drastically changing the default GUI on us the last few years. Rather than learn their new GUI all the time, I run a minimal GUI and use the same commands that have worked since 1993-ish.  Plus those commands work on Linux servers that don't have any GUI.

---

### Post by FerryGnu on 2016-11-30
Thanks for going to all that detail. Very much appreciated. 

Sorry for the confusion, I only mentioned that I could see windows devices to indicate I could see stuff on the current network like the USB-drive in the router and the old HT machine before I set it up with Ubuntu.

All the PCs in the house are now Ubuntu. Well, except two tablets that will not run it, but that's OK they never had access to the network anyway, just the internet and blocked from the network by the router (dd-wrt). I no longer need to access windows devices as I can use sneaker-net if I need to go back for anything.

I understand about Ubuntu being the the front end, but want to stay with it across all PCs for ease of use for other family members. 

Currently I am getting around the files issue with sneaker net, but when that HT-PC is back in the lounge it is behind the TV and not easily accessible and that's why I'd like file transfer access to it. Remmina is working fine to manipulate that PC, but has no file handling.

Looks like I will just have to use SSH on everything then. Thanks for the links on securing it.

---

### Post by TheFu on 2016-11-30
"seeing on the network" is vague.  Which protocols are being used?  TCP/IP don't broadcast "I'm here, I'm here, I'm here."  Some protocols do, usually those came from MSFT.  Unix protocols don't work that way - it doesn't scale.  In a small, home, network, avahi is a workaround for IP services.  I don't use it - when it first came out, there were issues, like 100% CPU use.  Doubt that is still an issue, but I'm old and have a method that works.  

If you use sftp:// in the URL for nautilus,  it will probably work. Don't know. I use NFS for most internal transfers and sftp only when remote and with a different tool than nautilus/filezilla.

If you are running dd-wrt - 2 comments:
a) check that it is patched. Lots of bugs in dd-wrt which can be bad.
b) it supports internal DNS and dhcp reservations. That would be an easy way to centralize all your device IP management. You'd be able to use names to access any of the machines that way.

---

