---
title: "Problem connecting to PPPoE network"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by zephyrus17 on 2007-10-30
I am using a Dell 1501 with a Broadcom 440x Wired Network Card. I am dual booting with Vista with Vista installed first.

I have tried "sudo pppoeconf", but that does not work. I have downloaded gnome_ppp, but I don't know my dial-up number as I was never asked for a phone number in Windows. My firefox just says that it cannot connect.

I don't really know what else to do.

Can someone help, please?

---

### Post by TheThinker on 2007-10-30
Please explain what exactly didn't work in PPPoEconf? Did it fail to detect your ethernet card? If nothing happens in the terminal, then you probably don't have PPPoEconf installed on your computer. Go to the Ubuntu repositories at [http://packages.ubuntu.com](http://packages.ubuntu.com) in a different computer and search for PPPoE under the correct version of Ubuntu you're running. Then, download the deb packages PPPoEconf and PPPoE, transfer them to your Ubuntu computer, and install them there. That should be very easy to do.

About you not knowing your dialup number, I'd call your internet service provider for technical support. They're more than willing to give you the correct dialup number for your area.

---

### Post by zephyrus17 on 2007-10-30
My apologies. Well, sudo pppoeconf did work. It detected 'eth0' and said 'triggered connection' or something. But, in Firefox, it wouldn't connect. All right, will call them and ask.

---

### Post by ggauche on 2007-10-30
Have you tried disabling Ipv6?

Type **about:config** in Firefox's address bar.
Scroll down to the line that starts with
**network.dns.disableIPv6** and double click to set it to **true.**

I found this in one of these forums and it worked for me - both in Gutsy and PCLinuxOS.
Maybe this will work for you.

---

### Post by zephyrus17 on 2007-10-30
I managed to fix it. Turns out it was a typo on my part. :)
But, still, thanks for all you help.

---

