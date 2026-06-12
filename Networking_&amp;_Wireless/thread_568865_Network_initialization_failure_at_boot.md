---
title: "Network initialization failure at boot"
date: 2007-10-06
forum: Networking &amp; Wireless
---

### Post by shanen on 2007-10-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/133374](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/133374) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Personal background is that I'm moderately experienced with Ubuntu. I've been using it for a couple of years on a number of machines, mostly IBMs.

Problem background is that I installed Ubuntu on a Sharp notebook a few weeks ago and the network fails to initialize the connection when the machine boots. The installation seemed to go completely smoothly from a 7.04 CD, but after booting the machine is not connected to the LAN. If I right-click on the network icon and disable networking, then right-click again and enable networking, it will connect. Sometimes I have to do that more than once. My feeling is that I have to give it a little time to fully disable the network before trying to enable it. Once it is connected, there is no problem after that.

I've looked at the main log files, but don't see anything that is apparently related to a network failure to initialize. However, I could be looking at the wrong files, or maybe I'm not recognizing what I should be looking for.

Diagnostic hints? Fixes?

(Hopefully the problem will go away when I upgrade to Gutsy.)

P.S. The Launchpad URL below seems to be a very close match, but it is marked as a duplicate of another bug that does not really seem to match the problem I'm seeing.

---

### Post by noob12 on 2007-10-06
Can you post these:
```

lspci -nn

sudo lshw -C network

cat /etc/network/interfaces

```

Are you using Network Manager?   My recommendation for laptops (and also in that launchpad bug thread) is that you remove all of the entries from /etc/network/interfaces except the first stanza for loopback (lo).  Keep that.  See if this helps.

---

