---
title: "Wired Internet Woes (BCOM 359xx)"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by mp4215 on 2007-09-25
The internet on my desktop has suddenly stopped working. It was fine then my roommate uses the ethernet cord to plug in his laptop for a while, then back into my desktop. At this point it stops working. I have searched the forums and tried many different things to make it work or see what the problem is. I have done ipconfig, ifup & ifdown, dhclient, mii-tool, ethtool, etc. None of these have fixed the problem or helped me figure out the problem. 

A few of these commands and others were run in a script that is tarred and attached to this post. I have also tried shutting down my computer and doing a cold boot. I have tried different ethernet cords and cards, different ports on the router. My roommates computer gets the internet just fine. 

My computer is running 7.04 as its only OS.

Any ideas?

---

### Post by scrooge_74 on 2007-09-25
check what you have in /etc/network/interfases

maybe reset that file and put everything back to auto, example

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

It helped me a while back with my wireless broadcom

---

### Post by mp4215 on 2007-09-25
I just checked and all seems well in that file.

Is there any way that card failed yet still somehow detects the link?

---

### Post by mp4215 on 2007-09-26
Does anyone think I should try doing a reinstall?

---

### Post by noob12 on 2007-09-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/140813](https://bugs.launchpad.net/ubuntu/+bug/140813) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				May be related to that bug.  Reporter indicates manually reloading may workaround the issue. Try that.
```

sudo ifdown eth2
sudo modprobe -r 3c59x
sudo modprobe 3c59x
sudo ifup eth2

```

This assumes you have entries for eth2 in your /etc/network/interfaces file.

Also: response on the bug suggests trying Gutsy (pre-release).

---

### Post by mp4215 on 2007-09-26
I tried those commands and they did not work.

---

### Post by scrooge_74 on 2007-09-27
> **mp4215 said:**
> Does anyone think I should try doing a reinstall?

In some instances using 7.04 gives troubles, maybe a earlier version could do the trick for you

---

