---
title: "compiling madwifi after install"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by drumkitcat on 2007-03-06
Hi,
I've just done a fresh install of Ubuntu Edgy 6.1 on my Toshiba Satellite laptop, which has both a built in wired ethernet connection, and an Atheros AR5112 wireless card. 

After dinking with this for some time last week, I've done a fresh install.. 

I've also installed madwifi from Symantic Package Manager, and Network Manager from the Add/Remove area.

My question is this - having installed madwifi from Symantic, do I need to do any additional configuring in the terminal, or should it be ready to go as is? (as is = after doing a reboot)

If it does require any additional configuring (like compiling the madwifi driver?)  can someone please post the commands to do this?

Currently, my laptop runs great with the wired ethernet connection, and it does correctly identify my Atheros wireless card, but I haven't attempted to use it alone as yet since doing the fresh re-installation of Edgy. (time constraints last couple of days)

Thanks in advance, and look forward to hearing from anyone!

---

### Post by drumkitcat on 2007-03-06
bump

---

### Post by netztier on 2007-03-06
> **drumkitcat said:**
> Hi,
If it does require any additional configuring (like compiling the madwifi driver?)  can someone please post the commands to do this?


Before going down the "build your own driver" road, I'd first try installing the **linux-restricted-modules** package which includes madwifi drivers. You'll find a lot of *linux-restricted-modules-<some kernel-version>* modules listed in Synaptic. The version you'll finally install has to match the installed version of *linux-image-<kernel version>* or things won't work. Pick the "meta package" **linux-restricted-modules-generic** (-k7 if you have an AMD processor). This should then auto-select the version that matches your kernel.

And while you're at it, install **network-manager** and **network-manager-gnome** too; they will let you configure wireless connectivity from the Gnome menu. On my HP nc6000 with the same Atheros-based mini-PCI card, this worked out-of-the-box, WPA and WPA2 included.
[COLOR="Red"](bah.. forget this section. I should've read your original posting more precisely. You have network-manager already installed, sorry.)[/COLOR]

best regards

Marc


PS: be wary if you have installed nVidia drivers from their website. linux-restricted-modules bring ubuntu's package of nvidia's drivers and they will conflict.

---

### Post by drumkitcat on 2007-03-06
Thanks, I'll check on those.  My processor is an Intel Celeron so there shouldn't be any conflicts.

thanks though for your reply!!

---

