---
title: "Wireless working on Ubuntu, but not Kubuntu (Gutsy)"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by Spudgun79 on 2008-03-09
Hi, I'm hoping someone can help as I'm a bit stuck.  I'm relatively new to the Linux world, but I am a tinkerer and so enoying the experience, apart from this!

I installed Ubuntu Gutsy on my laptop and was able to get the wireless working just fine with the restricted drivers.  Its a PCMCIA Linksys WPC54G version 3. I recently installed the kde desktop (Kubuntu) to try it out via the Synaptic Package Manager.  I now have both Gnome and KDE installed and can switch between the two.

However I'm having an issue where the wireless refuses to work on Kubuntu.  If I log straight into Kubuntu straight from boot the wireless refuses to work.  From trial and error I've got as far as getting it to find the router with some tinkering which I need to repeat every time, but it refuses to find an ip address and will not allow me to connect to the net.

Just to make things interesting though, if I log into Ubuntu, log out and then into Kubuntu, the wireless then works fine!  I'd like to be able to go straight into Kubuntu and for it to just work like it does in Ubuntu from boot.

I don't know if this is relevant, but the device is listed as 'eth1' and not 'wlan*x*', but its the same in Ubuntu as well and that works.

Any ideas?

---

### Post by jakejas on 2008-03-09
I seem to remember having the same problem when I first installed the KDE packages. If i'm remembering right, you might have to install the restricted drivers manager for KDE. I'm pretty new to Linux as well, so take this with a grain of salt, but I think that might be the problem. Good Luck!

---

### Post by Spudgun79 on 2008-03-11
Thanks for the help, I couldn't quite get it to work, but you pointed me in the right direction so thanks! :)

However, since I liked the look and feel of Kubuntu I downloaded the ISO, wiped the laptop and installed from scratch and after that it worked pretty much straight away.  I do remember reading in my research something about you can only have gnome or KDE network managers at any one time so there may have been some conflict there.  Anyhow its sorted now.

---

