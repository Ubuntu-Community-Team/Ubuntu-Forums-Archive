---
title: "Turning on Linux box slows network"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by hbj on 2007-10-05
Hi,

I have set up an Ubuntu box running Dapper.  Samba was working fine and shares could be browsed from the Windows machines on the network.  We have Windows 2000 Small Business as a domain controller.  Everything was working fine until I decided to try to join the Ubuntu box to the domain using Samba and winbind.  This seemed to work but I started getting complaints that the  LAN was unbearably slow, particularly while trying to copy files from the domain controller to desktop Windows machines.  For example, five minutes to open a couple MB file.

I can't figure out any reason why joining  the Linux machine to the domain would slow down the LAN but that is the complaint.  If we shut down the Linux box, network speeds immediately return  to normal.

The current fix is to shut down the Linux machine during the day so that people can get their work done, but there must be a way to track down the problem.  Ethereal captures don't seem to shw anything particularly strange, but then again, I'm a novice at Ethereal.

Any advice to things to check to try to fix this problem would be greatly appreciated.

Heath

---

### Post by Alex1200GS on 2007-10-05
I'm a novice too, but I suspect that the samba settings on the linux box are to blame and that is the first place I'd look. Also, skim through /var/log/messages and dmesg|tail for something juicy.

Alex

---

### Post by El Rogueo on 2007-10-05
> **hbj said:**
> Hi,
I can't figure out any reason why joining  the Linux machine to the domain would slow down the LAN but that is the complaint.  If we shut down the Linux box, network speeds immediately return  to normal.

Quick question- what exactly does the linux box /do/ on the network? Or is it just he presence of the thing that causes the slowdown?

Aside from that, just two upgrade comments:

If you're using Ethereal, upgrade to Wireshark, which I find easy to understand even when you have no idea what's going on, particularly in the THERE'S A LOT OF NEW MESSAGES POPPING UP function~ 

you don't have to know what they are to recognize a traffic spike, heh.

Secondly, is there a reason you have opted not to upgrade either to Edgy or Feisty? Gutsy is coming out soon anyway, but I would still recommend that you upgrade your distro for the sake of ensuring it's not a problem that's been phased out by time and testing.

have you tried connecting the machine to another network and seeing if a similar reaction is observed? That way you would know if it was just the machine or instead /the interaction/ between the network and the machine that was suspect. If you narrow it down to the machine then you know it's a settings issue, probably with samba or something

hope that helps :-k

---

### Post by hbj on 2007-10-05
One thing strange I noticed - on the domain controller, when I go to Active Directory Users and Computers/phoenix-web  and check the Properties, it shows:

Computer name (pre-Windows 2000): phoenix-web
DNS name: localhost

I'm wondering if the "Dns name: localhost" is causing problems somehow.  No matter what I do, I can't get this to show up as the hostname of the ubuntu box.  Could this be part of the problem?  My Samba settings:

[global]
security = ads
netbios name = PHOENIX-WEB
realm = COMPANY.COM
password server = PHOENIXDC
workgroup = PHOENIX
idmap uid = 2000-10000000
idmap gid = 2000-10000000
winbind separator = +
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
template homedir = /home/%D/%U
template shell = /bin/bash
client use spnego = yes
domain master = no
local master = no
preferred master = no
os level = 0
server string = %t SERVER
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = No
panic action = /usr/share/samba/panic-action %d
socket options = TCP_NODELAY
wins support = no
wins server = 10.124.0.1

---

### Post by hbj on 2007-10-05
The computer acts as a mail filter and vpn and ssh access point connecting to the outside world.  I've left it at Dapper because it's the LTS version which I thought would be better in a coprorate environment.  If there are improvements to Samba AD integration in later versions of Ubuntu I don't really see why upgrading to Feisty would be a problem if it is necessary.

---

### Post by El Rogueo on 2007-10-05
> **hbj said:**
> The computer acts as a mail filter and vpn and ssh access point connecting to the outside world.  I've left it at Dapper because it's the LTS version which I thought would be better in a coprorate environment.  If there are improvements to Samba AD integration in later versions of Ubuntu I don't really see why upgrading to Feisty would be a problem if it is necessary.

No, I see what you mean about LTS, I forgot it was a corporate environment, that's probably the safe bet.

I can see why the slowdown if it's a mail filter, but it's preventing people from downloading things quickly also?

Any wireshark/ethereal reports of interest?

your samba settings look okay, but I'm not exactly a samba wizard so I can't be sure

localhost? as in the loopback address? That's odd. Well, when you connect the machine to the network and everything slows down, does the machine still do what it's meant to regardless?

Whether it's the source of the slowdown or not that certainly looks wrong to me. I'll do some more research and get back to you.

---

### Post by El Rogueo on 2007-10-05
> **Alex1200GS said:**
> skim through /var/log/messages and dmesg|tail for something juicy. Alex

Did this turn up anything?

---

### Post by hbj on 2007-10-05
/var/log/messages doesn't show anything strange.

It still seems to show a network slowdown even if I turn off samba, ftp and postfix services.  Still have a slow network until I turn off the computer alltogether.  So it seems to be some kind of strange AD interaction with the domain controller since it became a problem after I joined the computer to the domain.  Checking wireshark now.

---

### Post by hbj on 2007-10-10
Problem fixed - it was a dying network switch.  Plugging in the network cable from the Ubuntu box to the switch locked up the whole network.  Replaced the switch, everything works fine.

---

