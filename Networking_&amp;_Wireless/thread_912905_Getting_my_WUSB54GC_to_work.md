---
title: "Getting my WUSB54GC to work"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by Aizawa on 2008-09-07
I'm still very new to Linux, so I'm sorry if the solution to this problem is rather obvious.

Up to now I've used Fedora 8 & 9, and I've had no problems getting my WUSB54GC to work.

Now in Ubuntu, I installed ndiswrapper, successfully installed the windows driver for my card. "ndiswrapper -l" shows the driver and the device, so it should work.

Now, in Fedora, there was only the network setting GUI (If that's what you call those things) "Gnome Network Manager". That program is installed on Ubuntu, apparently, but it's not the same version.. May not be an older/newer, it's just not the same thing.

Anyhow, in System>Administration I have Network and Network Tools. I seriously don't understand what the Network Tools thing is, other then that I can ping from it. Anyhow, in the network settings thing, I've entered the encryption passwords and all that, it's all right, but my card just wont work. I mean, it's installed, linux knows about it, I've entered all the information, but no, it just wont work. Please, if anyone sees the solution, do tell! :)

---

### Post by Aizawa on 2008-09-07
I'm bumping this since I've yet to find a solution.. Please?

---

### Post by hajk on 2008-09-07
Several possibilities to solve your problem:

1. Does it show an alternate driver, like ssb, when you run the "sudo ndiswrapper -l" command? In that case you should ensure that the ndiswrapper module is loaded before that alternate driver.

2. In a standard install the network-manager applet should handle your wireless connections, no need to mess with other configurations.

3. You don't need ndiswrapper if you install a recent kernel, like 2.6.26 from backports, since it has the rt73usb module for your wireless adapter. You also need to install the firmware from Ralink.

---

### Post by Aizawa on 2008-09-13
1. Nope!
2. Um. Oh. Oops?
3. I.. Don't know how to see what kernel I have.

---

