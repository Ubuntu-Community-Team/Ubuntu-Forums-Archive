---
title: "Torrent issues"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by nLpPyXR on 2013-10-23
Hello everyone, let me start by saying I'm not a spammer nor a bot, just a barely computer-literate recent convert to the wonders of Ubuntu and Linux in general.

Here's the deal: I don't have a router, just a regular SB5102 Cable Modem by Motorola hooked directly to my PC, I have completely disabled the firewall (and checked via sudo ufw status verbose) and I can download and browse perfectly fine through Firefox.

The thing is, for some reason, all my torrents appear to be seeding, yet there are no peers, as in, Transmission 2.82 says "0 peers of 0 peers connected", and when I go to Trans' settings no matter what port I try, they all seem to be closed by default.

My Lubuntu version is 13.10, and I'd be more than happy to provide any additional info. Please help me! I'm on a private tracker and not seeding for days can really put a dent on one's ratio.

---

### Post by nLpPyXR on 2013-10-26
I'm sorry for bumping this but I've been to Transmission's own Forum and their IRC channel in Freenode and no one has been able to help me; and given the fact that utorrent was working perfectly a few days ago when I was still running Windows, this has got to be something specifically related to Lubuntu.

I'm on the verge of switching back to XP just because I can't seed and the private trackers I'm in might ban me; a shame because I really do love Ubuntu and LXDE... please, HELP ME!

---

### Post by leclerc65 on 2013-10-26
[QUOTE=nLpPyXR]
I'm on the verge of switching back to XP...
[/QUOTE]
Oh no ! 
Consider kTorrent instead.

---

### Post by Allavona on 2013-10-26
Agreed with leclerc65. Ktorrent is quite possibly the best Linux torrent program out there. Hit the settings and configure away. Keep in mind that uTorrent runs in WINE.

---

### Post by nLpPyXR on 2013-10-26
> **leclerc65 said:**
> Oh no ! 
Consider kTorrent instead.

> **Allavona said:**
> Agreed with leclerc65. Ktorrent is quite possibly the best Linux torrent program out there. Hit the settings and configure away. Keep in mind that uTorrent runs in WINE.

but isn't kTorrent a KDE-exclusive? remember I'm running Lubuntu here

---

### Post by warp99 on 2013-10-26
Open a terminal and type the following:

```
:~$ sudo iptables -L
```

If there are chains listed flush them out:

```
:~$ sudo iptables -F
```

Now see if the ports are available.

---

### Post by nLpPyXR on 2013-10-26
> **warp99 said:**
> Open a terminal and type the following:

```
:~$ sudo iptables -L
```

If there are chains listed flush them out:

```
:~$ sudo iptables -F
```

Now see if the ports are available.

I got "CHAIN Input" "Chain Forward" and "Chain Output" all with "policy ACCEPT"

I typed sudo iptables -F and nothing happened. Tested the ports and Transmission... same problems...

Btw, to those that suggested kTorrent or qBitTorrent, I just got done trying them out and they have the same problems, so I'm positive it's something on Lubuntu acting up.

---

### Post by warp99 on 2013-10-26
if iptables shows no chains then the ports are not blocked as UFW is only a graphic front end for iptables. The problem is somewhere else. Use a port checking tool like this:

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

It may be that your ISP is blocking certain ports that torrent users frequent.

---

### Post by nLpPyXR on 2013-10-27
> **warp99 said:**
> if iptables shows no chains then the ports are not blocked as UFW is only a graphic front end for iptables. The problem is somewhere else. Use a port checking tool like this:

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)

It may be that your ISP is blocking certain ports that torrent users frequent.

While that's possible, I find it quite unlikely due to the fact that everything was working fine just a few days ago when I was still on win XP running uTorrent. There's just something different about Lubuntu 13.10 that leaves me unable to seed. Of course, I'd assume I can't seed because of my listening ports closed, but why are they closed now all of a sudden when they weren't before? what makes Lubuntu incapable of doing whatever windows and utorrent were doing that allowed me to seed normally?

---

### Post by warp99 on 2013-10-27
Another way is to open Transmission, pick the port you want to use then issue the following command:

```
sudo netstat -tulpn
```

The port should show it being used by Transmission.

---

### Post by nLpPyXR on 2013-10-27
nope, there's a port being used by Transmission but it's a different one.

---

### Post by warp99 on 2013-10-27
Do you have random ports picked in the settings? If so un-check this.

---

### Post by nLpPyXR on 2013-10-27
nope, it's un-checked

---

### Post by warp99 on 2013-10-27
Choose a port above 49000 in Transmission (example 49999) and exit from the program using "Quit" on the menu bar then restart. Check with the "sudo netstat -tulpn" to see if that port was taken by Transmission. Check again with "sudo iptables -L" that no chains exist. Everything should be working at that point.

---

### Post by nLpPyXR on 2013-10-27
followed your instructions step by step and still got the same issues. Thanks for all the help but I think I'm gonna try a different distro like Peppermint or LXLE, possibly PCLinuxOS-LXDE and/or Zorin OS Lite.

If all those fail... there's always Win XP.

---

### Post by leclerc65 on 2013-10-27
> **nLpPyXR said:**
> but isn't kTorrent a KDE-exclusive? remember I'm running Lubuntu here
It just installs tons of extra packages, so what ? I have kTorrent in Mint Maya Mate.

---

### Post by nLpPyXR on 2013-11-02
My apologies and sincere grattitude to everyone who tried to help me and offered suggestions, be it here, or in the Ubuntu IRC channel over at Freenode.

Turns out, my ISP decided to change everyone's IP addresses to dynamic ones by default, so without calling them and asking to get a static IP (which comes with every port open by default) there's just nothing you can do, regardless of wether or not you have a router.

---

