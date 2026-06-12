---
title: "Xubuntu and Netgear wg111v2 usb: It doesn't work, but why? It should, right?"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by Genecks on 2007-06-01
Alright, I was using Kubuntu the other day, and the netgear wg111v2 wireless USB was working on the operating system. I didn't have to mess with ndiswrapper or any other configuration. It was pretty much plug and play.

However, I recently instlaled Xubuntu on an older computer, which has Windows 2000. I know the netgear wg11v2 usb works on it, because I've used it on the Windows operating system. However, when I partitioned the HD, installed Xubuntu, and played with Xubuntu, I couldn't get the netgear usb to work. I don't know why it wasn't working. I figured it would work, because it worked on Kubuntu.

Could it be that Xubuntu and Kubuntu don't have the same presets? In other words, I _need_ to setup Xubuntu to use the wireless usb, while I don't need to set it up for Kubuntu.

Does anyone know about this problem?

I decided that perhaps I need to install the driver and more for Xubuntu. Do I?

Well, I tried anyway, and it said ndiswrapper wasn't installed. I thought, "Huh?"
Anyway, I decided to use sudo apt-get install ndiswrapper
It worked, but then I restarted for things to take effect
I type in "ndiswrapper"
It said..

> Error: no versions of ndiswrapper found!

Apparently, I'm coming across some problems. I'm not too sure why, though.

If there is something else I could try, I was looking for an option to connect to the Internet in Xubuntu. In other words, on Kubuntu, there is a system bar part near the taskbar. I couldn't find the same thing in Xubuntu. I figured if I could find that, I could make it look for the linksys connection. In Kubuntu, it looks like a tiny, tiny barchart. I'm looking for that same thing in Xubuntu. Is it there?

---

