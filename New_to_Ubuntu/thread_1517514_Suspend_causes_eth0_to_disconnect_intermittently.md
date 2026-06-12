---
title: "Suspend causes eth0 to disconnect intermittently"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-06-25
When my computer suspends and later resumes, sometimes eth0 disconnects and becomes unavailable. I have to reboot to be able to reconnect to the Internet.

As the title says, this is intermittent; sometimes the computer resumes with eth0 connecting fine.

This happens on my computer (Lucid 10.04 64-bit) and my wife's computer (Lucid 10.04 32-bit).

Any ideas how to prevent the eth0 from becoming unavailable?

---

### Post by regala on 2010-06-25
> **Paddy Landau said:**
> When my computer suspends and later resumes, sometimes eth0 disconnects and becomes unavailable. I have to reboot to be able to reconnect to the Internet.

As the title says, this is intermittent; sometimes the computer resumes with eth0 connecting fine.

This happens on my computer (Lucid 10.04 64-bit) and my wife's computer (Lucid 10.04 32-bit).

Any ideas how to prevent the eth0 from becoming unavailable?

how about reporting a bug on Launchpad ?

---

### Post by Paddy Landau on 2010-06-25
> **regala said:**
> how about reporting a bug on Launchpad ?
Thanks for the idea. I should have searched Launchpad first.

It's already been reported:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509239](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509239)

I've added my vote and my voice.

In the meantime, I'd love to find a workaround!

---

### Post by Paddy Landau on 2010-08-04
I contacted Canonical about this (paid support).

Canonical says that it's [bug 605045]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/605045").

---

### Post by Paddy Landau on 2010-08-06
Canonical has given me a work-around for this.

[LIST=1]
[*]Install WICD (System > Administration > Synaptic Package Manager; install wicd).
[*]Uninstall network manager (mark for complete removal network-manager and network-manager-gnome).
[*]Reboot.
[/LIST]

---

### Post by DaveRaj on 2010-08-13
Doing this left my network disconnected on reboot. You need to add a new step:

2.5) make sure /etc/network/interfaces contains the lines 

auto eth0
iface eth0 inet dhcp

---

### Post by Paddy Landau on 2010-08-13
Interesting. I didn't touch that file at all.

I've gone back to using network-manager, because wicd disabled Samba and I have no workaround for it.

---

### Post by DaveRaj on 2010-08-13
I don't know enough about how wicd or network-manager work. I guess using one of these means that you shouldn't need to manually enter values in /etc/network/interfaces. So maybe I should have spent more time playing around with wicd before manually configuring things. 

Regarding switching back to network-manager from wicd and samba. I've also had samba problems, but I think this is more related to the transition from traditional init.d scripts to upstart and dependencies not being met. For example see [https://bugs.launchpad.net/ubuntu/lucid/+source/upstart/+bug/494141](https://bugs.launchpad.net/ubuntu/lucid/+source/upstart/+bug/494141) for discussion about dependencies between cups and samba. 

Overall the upgrade to lucid has caused me lots of little intermittent problems :(.

---

### Post by Paddy Landau on 2010-08-14
Hmm, I don't know anywhere near enough about network-manager or wicd to be able to comment on what you said. I had a look at the bug but I can't see whether it has anything to do with wicd.

I had the Samba problem only on wicd. As soon as I reverted to network-manager, the problem solved itself.

> **DaveRaj said:**
> Overall the upgrade to lucid has caused me lots of little intermittent problems :(.
True, me too, and that's to be expected I think. Computers are still awfully primitive. Still, it's better than the enormous problems that I used to get upgrading the various versions of Windows. Let's hope that over the coming years, Canonical gets Ubuntu's upgrades smoother and smoother (as, I understand, has Windows, though I've still had big problems with it).

---

