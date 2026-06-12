---
title: "Wireless and bluetooth help"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by kablack7 on 2008-06-01
Hey all

I have an HP Pavillion dv9000 with ubuntu 8.04. The wireless card is a Broadcom Corp BCM 4328 802.11a/b/g/n. The wireless light on the front is amber, which apparently means the wireless isn't working, or something.
I tried the guide [_here_]("http://ubuntuforums.org/showthread.php?t=405990"), which didn't work. Apparently this wireless chipset is not very compatible with ubuntu, and it is difficult to make it work. 
Has anyone got any ideas?

I also bought a small usb bluetooth adapter to use my bluetooth mouse. I tried the guide [_here_](http://ubuntuforums.org/showthread.php?t=586105), and that.... didn't work. haha. The adapter came with a driver cd, but of course they don't work with linux. I tried using the BlueMan app, but when I scan for bluetooth devices, it can't find my mouse. When I try to manually insert the bluetooth address of my mouse, it says that it is not supported.

Any ideas?

---

### Post by kablack7 on 2008-06-01
okay, update..

I managed to get the bluetooth mouse working, so don't worry about that. However, I'm still having problems with the wireless. I managed to install the proper NDISwrapper drivers for my wireless card, and it seems to be working. I can connect to my wireless network (which is WPA encrypted), but the internet doesn't work... despite being connected to the network, I cannot load any websites, nor can I send or receive any packets. The little wireless light on the front has turned to blue, which means it should be working...

Another thing, the network icon in the top bar somehow changed. When I click on it now, instead of showing me the option of using the wired or wireless connection, it simply says "manual configuration", and brings me to the network settings window... how can I change this back to the way it was?

---

### Post by kablack7 on 2008-06-02
bump?

---

### Post by kablack7 on 2008-06-03
bump...?

---

### Post by vexingmodstwo on 2008-06-03
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

This should be the first place you go if you have a Broadcom wireless card.

Are there moderators here?  That tutorial should be a permanent link in this section.

---

### Post by kablack7 on 2008-06-03
Well, if you had read my first post, you might have realized that I have already tried the guides online. The guide you posted is actually the one that allowed me to install the drivers properly, but now I have a different problem.

Once again, I have got the drivers installed, and I can connect to a wireless network... however when I do connect, I cannot load any webpages, nor can I do anything on the internet. So something is still amiss.

---

### Post by vexingmodstwo on 2008-06-03
> **kablack7 said:**
> Well, if you had read my first post, you might have realized that I have already tried the guides online, and the guide you posted a link to does not have instructions for my particular wireless card (the Broadcom BCM4328 ). 

Once again, I have got the drivers installed, and I can connect to a wireless network... however when I do connect, I cannot load any webpages, nor can I do anything on the internet. So something is still amiss.

The question about the link wasn't directed at you, sorry for the confusion.

I wasn't sure if you'd gone through this particular tutorial so I wanted to make sure you had.

Your card is listed in that tutorial, btw.  You need to follow the steps in 2b.

I was in the same boat after going through that How To.  I've suggested using wifiradar (and manually configuring the connection) instead of the network manager that comes with the distro.

---

### Post by vexingmodstwo on 2008-06-03
> **kablack7 said:**
> Well, if you had read my first post, you might have realized that I have already tried the guides online. The guide you posted is actually the one that allowed me to install the drivers properly, but now I have a different problem.

Once again, I have got the drivers installed, and I can connect to a wireless network... however when I do connect, I cannot load any webpages, nor can I do anything on the internet. So something is still amiss.

If you can, find out what the default gateway address is for the router.

Manually enter that into the profile for the wireless connection in the network manager.  You might be having a problem with the DHCP stuff that others, including myself, had.

---

### Post by kablack7 on 2008-06-03
Is there a way to do this without having to manually configure my connection depending on the router? I don't want to have to do that, this is a laptop, and if i'm visiting home or at a friends place and want to be able to connect to the wireless network, i don't want to have to go through a whole involved process just to connect to the internet.

---

### Post by vexingmodstwo on 2008-06-03
> **kablack7 said:**
> Is there a way to do this without having to manually configure my connection depending on the router? I don't want to have to do that, this is a laptop, and if i'm visiting home or at a friends place and want to be able to connect to the wireless network, i don't want to have to go through a whole involved process just to connect to the internet.

Try forcing the connection first.  If that works, you can worry about going to other places later.  If it doesn't work, you won't be able to get it to work anywhere right now because the issue hasn't been fixed for your particular situation.

Make sense?

---

