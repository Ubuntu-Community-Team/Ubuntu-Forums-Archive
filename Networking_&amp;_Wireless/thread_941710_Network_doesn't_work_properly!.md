---
title: "Network doesn't work properly!"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by yct1234 on 2008-10-08
Hi all,

My network card (only one on my computer) doesnt work properly! I can connect to the internet and download all the packages right after the installation but after a shut down, it wouldn't connect! Network manager shows connected but all IPs are 0.0.0.0 . That's using roaming mode. Manual config to DHCP doesn't help as well. I realised that if I boot up into ubuntu, then restart the computer, the network works! Guessing that the network adapter isn't properly activated on a clean boot...

I've checked the /etc/network/interfaces file oft mentioned on the many pages i've searched for and the 'auto eth0' line is there! i've now messed up the interfaces file and now ubuntu gets stuck right after the login screen.

1) How can I solve the network problem? Everything else works beautifully except for this network problem!! I've tried static, DHCP, roaming but it's still the same!

2) How do i go about editing the /etc/network/interfaces file form the recovery console? I've reinstalled ubuntu a few times now cause of this problem and have already downloaded all the extra packages for it...

Thanks! I'm going mad from this problem!!

---

### Post by Iowan on 2008-10-08
First, try **less /etc/network/interfaces** (or use **cat** instead of **less**).  This should list the file to see if there are any obvious errors.  I like **nano** as an editor - commands are listed at bottom of screen.

When you changed modes from roaming to static or DHCP... did you restart networking afterward (**/etc/init.d/networking restart**)?

---

### Post by yct1234 on 2008-10-10
> **Iowan said:**
> First, try **less /etc/network/interfaces** (or use **cat** instead of **less**).  This should list the file to see if there are any obvious errors.  I like **nano** as an editor - commands are listed at bottom of screen.

When you changed modes from roaming to static or DHCP... did you restart networking afterward (**/etc/init.d/networking restart**)?

Hi,

My /etc/network/interfaces is:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

I did the restart and it worked, but after a full shut down and full boot up, it stopped working again! My ifconfig shows an IP address that shouldn't be there. Since I'm connecting through a Linksys router/switch, the IP should be 192.168.1.x, but it became 169.x.x.x. (Last three x are actual numbers in ifconfig)

It's really frustrating that it's just the network that's not working. It seems that there's network connection when I used the recovery console.

What did I do wrong in my config?? :confused: Thanks!

---

### Post by hyper_ch on 2008-10-10
I discovered a few days ago WICD - it's a great replacement for the default network manager. You might want to check it out. Before I used WICD I also worked directly on the /etc/network/interfaces file but now I have no reason anymore: [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by Iowan on 2008-10-10
The 169.x.x.x address sounds like avahi kicking in - usually meaning DHCP failed to issue an address.  I still haven't seen a good reason why (or repeatable solution).

---

### Post by lswb on 2008-10-10
Network Mangler -oops, I mean Network Manager- as shipped with 8.04, unlike any other linux networking software I have ever seen, does not use /etc/network/interfaces and in fact iface entries in /etc/network/interfaces can cause NM to stop working altogether with that interface.

The default /etc/network/interfaces file in hardy with Network Manager installed has only these 2 lines:

```

auto lo
iface lo inet loopback

```

Try changing your /etc/network/interfaces back to this, set Network Manager to defaults (roaming) and see if works OK again. You may want to try logging out & in and/or rebooting after making the changes.

---

