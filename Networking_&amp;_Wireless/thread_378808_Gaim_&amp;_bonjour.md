---
title: "Gaim &amp; bonjour"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by threespacemen on 2007-03-07
I've been trying to use Bonjour on my LAN using Gaim 2.0.0 Beta 6 - I've "set up" a Bonjour account, however when it tries to connect, I get the following error message:

"Unable to establish connection with the local mDNS server. Is it running?"

I've been reading up on zeroconf, avahi and bonjour, and trying to increase my understanding of multicast DNS, however I can't seem to figure out why I keep getting this error. I have a Windows PC with Miranda (the stand-alone iChat version from [http://xurble.org/projects/iChatMiranda](http://xurble.org/projects/iChatMiranda)) and Windows Bonjour running on the LAN to test, but my ubuntu machine doesn't show up as a user on it. 

I've installed just about every non-lib avahi package I can find in the repos, on both this box and on an ubuntu domain controller on the LAN, and I've also opened UDP port 5353 in both directions (even using Firestarter, because it had me doubting my iptables skills), but still nothing. So much for this zeroconf, eh...? Anyone got any ideas?

Bonjour looks like a great, simple concept for intra-LAN communication, as users don't have to go through the rigmarole of establishing accounts, etc, however it'd be great if I could get it to work...

(as an aside - occasionally it *does* seem to work in Gaim; at least, now for periods of about 10 minutes at a time I don't get the "unable to connect" error, and then it inevitably returns, but still don't show up in the Win client...)

---

### Post by spd106 on 2007-03-08
I tried following the instructions in this thread a while back, but it was rather unstable and crashed often. 
[http://ubuntuforums.org/showthread.php?t=287911](http://ubuntuforums.org/showthread.php?t=287911)

Unfortunately It doesn't look like bonjour support will be better integrated through using avahi any time soon.

I've read that gajim has better avahi support.

---

### Post by killfire on 2007-03-09
that probably means the avahi daemon is not started.... find the initscript and start it (sorry on gentoo machine so I don't know the exact path)

---

### Post by threespacemen on 2007-03-11
Aha! Thanks for that. For some reason the initscript doesn't start avahi-daemon, but I'll have to look into fixing that later. Started /usr/sbin/avahi-daemon manually, and now it looks like bonjour is working nicely in Gaim. 

However... I can't see any of the Win32 lan clients in the user list, and they can't see me. They (using Miranda) can see each other no troubles at all. Could quite likely be a firewall issue, so some more tinkering is probably in order...

---

### Post by huygens on 2007-06-20
> **threespacemen said:**
> Aha! Thanks for that. For some reason the initscript doesn't start avahi-daemon, but I'll have to look into fixing that later. Started /usr/sbin/avahi-daemon manually, and now it looks like bonjour is working nicely in Gaim.

Yes, there is a file that prevent avahi to be started by the init script. You have to modify /etc/default/avahi-daemon, you will find a variable that is set by default to 0. Set it to 1, and you should be able to start avahi upon boot. ([see this blog post for more information on Avahi]("http://www.berthon.eu/ice_and_fire/?p=110"))


> **threespacemen said:**
>  However... I can't see any of the Win32 lan clients in the user list, and they can't see me. They (using Miranda) can see each other no troubles at all. Could quite likely be a firewall issue, so some more tinkering is probably in order...

It must be a firewall problem. I do not have a firewall on both Ubuntu and Windows (I'm behind my firewall/router, so there is no need for one on each machine), and I can chat with Pidgin/Avahi on Ubuntu and Pidgin/Bonjour on Windows. They see each other.
If Gaim does not offer you any longer the possibility to create Bonjour account. You should probably build Gaim or Pidgin (the new name for Gaim) by hand and enabling it. There is a [pretty easy guide to enable Avahi on Pidgin]("http://www.berthon.eu/ice_and_fire/?p=100").

---

