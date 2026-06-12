---
title: "Post-up action with Network Manager?"
date: 2014-09-24
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2014-09-24
For some 7 years now I've been using the **/etc/network/interfaces** file to configure my network connections, and disabling **Network Manager** by having the single word "exit" in the /etc/default/NetworkManager and /etc/default/NetworkManagerDispatcher files to stop them from installing automagically at boot time.

For almost that long, I've been launching an **iptables-restore** action as a post-up command in the interfaces file, to configure my firewall as soon as the network is available.

Now that I'm in the process of moving from 12.04.5 to 14.04.1 by way of a clean install on a totally separate drive, it seems like a good time to join the 21st century and use Network Manager to handle everything more easily. However my searching through the forum here and also via Google hasn't turned up any help on doing so. It looks as if a rather complicated script may be necessary to take the place of that single line in the eth0 stanza of my interfaces file!

Can anyone steer me to a reference somewhere that will make this as painless as NM is supposed to be? Thanks!

---

### Post by JKyleOKC on 2014-09-26
bump

---

### Post by tgalati4 on 2014-09-26
It can be a difficult transition for some.

First, you need to understand that networkmanager has gotten better, but also more complicated.  The easiest thing to do is let nm do the work.

Make sure your /etc/network/interfaces file is minimal:

Comment out everything else!

> tgalati4@Mint14-Extensa ~ $ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


Don't modify your /etc/resolv.conf file for DNS servers--no matter how deep the urge to do so.  If you feel you must modify a file, then modify this one:

> 
tgalati4@Mint14-Extensa /etc/resolvconf/resolv.conf.d $ cat tail

# OpenDNS Fallback (configured by Linux Mint in /etc/resolvconf/resolv.conf.d/tail).
nameserver 8.8.8.8
nameserver 8.8.4.4

nameserver 208.67.222.222
nameserver 208.67.220.220



Finally, you need to bring up the nm graphical dialog:  Right-Click on the network icon and click on "Edit Connections"  or Control Center -> Network.

You need to add a profile--a storage container that will hold your network settings.  It could be "Home", "Work", "Vacation Home", etc.  It needs to reflect the physical location of your network, because that is the profile that you will use whenever you are in that physical location.  If  you have a laptop that you lug from "Home" to "Work" then it should automatically connect to each one with correct credentials--BUT, you must set them up before hand.

Add your network information in the dialog box.  Add appropriate IP entries in your /etc/hosts files for static devices (like printers) that you frequently connect to.

Reboot and you should be connected.

The key is not to add or modify the standard network configuration files that you have used for 30 years.

---

### Post by JKyleOKC on 2014-09-26
> **tgalati4 said:**
> You need to add a profile--a storage container that will hold your network settings.  It could be "Home", "Work", "Vacation Home", etc.  It needs to reflect the physical location of your network, because that is the profile that you will use whenever you are in that physical location.  If  you have a laptop that you lug from "Home" to "Work" then it should automatically connect to each one with correct credentials--BUT, you must set them up before hand.

Add your network information in the dialog box.  Add appropriate IP entries in your /etc/hosts files for static devices (like printers) that you frequently connect to.

Reboot and you should be connected.

The key is not to add or modify the standard network configuration files that you have used for 30 years.I'm not having a problem getting connected; the /etc/network/interfaces file only has the stanzas for "lo" and I've not made any change there from the initial clean install of 14.04.1. In fact, I'm posting this from the new installation.

My problem is duplicating the action of the "post-up" command in the old system, and the man pages for NetworkManager are leaving me more than slightly confused. Here's what the old system has: ```
iface eth0 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	**post-up iptables-restore < /etc/iptables.up.rules**
auto eth0
```The line in bold is there to restore my iptables rule set immediately upon bringing up the LAN interface.

What I'm looking for is a way to achieve that same result in the new system. Looking at "man NetworkManager" I find this: > NetworkManager will execute scripts in the /etc/NetworkManager/dispatcher.d directory in alphabetical order in response to  network events.This is the only hint I've found so far; it suggests that I might write a bash script that verifies that (1) the interface is "eth0" and (2) the action is "up," and then executes the "iptables-restore < /etc/iptables.up.rules" command followed by "exit 0." Does this sound like the right way to tackle the situation?

Since this is a desktop/server installation which will never be roaming, and has only one user, would a profile actually be needed?

I'm also having a few other problems getting my local mail server to work properly but that's material for another thread...

Thanks for the response!

---

### Post by JKyleOKC on 2014-09-27
With nothing much to lose since this is a clean install and the previous system remains fully intact, I decided to try such a script -- and it appears to have worked. Here's the script itself:```
#! /bin/bash
#  Script to set iptables whenever eth0 comes up
#  file is /etc/network/if-up.d/001SetFirewall
#  By Jim Kyle - 26 Sept 2014

if [[ "$IFACE" == "eth0" ]] ; then
#   if [[ "$MODE" == "start" ]] ; then
        iptables-restore < /etc/iptables.up.rules;
        logger -p syslog.notice -i Loaded iptables rules when "$IFACE" came up;
#   fi
fi

exit 0

```It's stored as /etc/network/if-up.d/001SetFirewall with permissions of ```
-rwx--x--x 1 root root 363 Sep 26 20:06 001SetFirewall*
```

As per the man page for Network Manager, certain scripts run automagically in response to events, and one of those acts as a wrapper to the  /etc/network/if-up.d scripts.

Here's the result from syslog after restarting the system:> Sep 27 10:27:33 mehitabel NetworkManager[798]: <info> Activation (eth0) successful, device activated.
Sep 27 10:27:33 mehitabel dbus[410]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep 27 10:27:33 mehitabel dbus[410]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 27 10:27:33 mehitabel kernel: [   12.660693] vboxpci: IOMMU not found (not registered)
Sep 27 10:27:33 mehitabel kernel: [   12.719845] ip_tables: (C) 2000-2006 Netfilter Core Team
Sep 27 10:27:33 mehitabel kernel: [   12.728005] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
**Sep 27 10:27:33 mehitabel logger[1212]: Loaded iptables rules when eth0 came up**


It's a bit more complex than the old way, but does seem to have a certain elegance about it. I'm marking the thread as solved with this post, in case someone else has a similar problem in future. Thanks again to **tgalati4** for a response!

---

### Post by tgalati4 on 2014-09-27
Normally one would use *gufw* and *ufw* to set up the firewall.  The *ufw* scripts will start  automatically.  Since they are front-ends to *iptables*, you should get the same functionality as your post-up script.

Regarding your original question, you could allow NetworkManager to use your interfaces file, so your old settings should still work:

> tgalati4@Mint14-Extensa /etc/NetworkManager $ cat NetworkManager.conf 
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:XX:D3:ED:XX:1E,00:00:XX:3C:76:XX,

[ifupdown]
**managed=false**


As usual, there are several ways to accomplish the same thing in Linux.

---

### Post by ian-weisser on 2014-09-27
> **JKyleOKC said:**
> #  file is /etc/network/if-up.d/001SetFirewall

Yes, NM does use the ifup and ifdown hook folders in /etc/network for pre-up, post-up, pre-down, and post-down actions.

That's how I start my firewall, too.
That's also how I start my laptop backup script, which tests for the correct LAN before starting. And how I kill it, if it's still running when I disconnect from that LAN.

---

### Post by JKyleOKC on 2014-09-27
> **tgalati4 said:**
> Normally one would use *gufw* and *ufw* to set up the firewall.  The *ufw* scripts will start  automatically.  Since they are front-ends to *iptables*, **you should get the same functionality** as your post-up script.I've investigated the *ufw* approach extensively, and came to the conclusion that it could not handle the pinhole for my private FTP server (necessary to support my data recovery business) easily. Coming from a RedHat-based background I've not found ufw to be "uncomplicated" in comparison to straight editing of the iptables rule set, although I agree that it's a quite good starter package for newcomers.

I considered your second suggestion of changing the "managed" line but felt a bit cautious that it might open up a can of worms aka unexpected side effects; the script seemed much more direct. Thanks for the discussion though; it got me considering other alternatives and may even open my eyes to whatever is going wrong with my *postfix* configuration (which currently tries to fill /var/log/mail.err with repeated error messages about SASL)...

---

### Post by tgalati4 on 2014-09-27
I agree, the GUI's can't handle complex configurations.  Unfortunately, try to remove the GUI's and you end up breaking the distribution.  Try removing networkmanager from your system and see how far you get.

---

