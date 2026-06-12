---
title: "Lubuntu Mini ISO Network Functionality"
date: 2017-06-03
forum: Networking &amp; Wireless
---

### Post by lash5402 on 2017-06-03
Recently, I started playing with Mini Lubuntu ISOs for computers with low memory and storage space. I am doing this in my spare time for fun to learn and fiddle around with a Linux OS. I was able to install Lubuntu 16.04 mini to an ASUS Eee PC 1000HA with ease. My problem now is how do I install program packages, manually, without a web connection? How can I prep a Mini ISO disc that has network functionality added to it so if I ever need to use it on another machine it will install the network devices automatically during the install? Or at least have the packages on disc so I can install the packages from disc. The funny thing is during the install it used my network devices to download the latest packages without any issue. It wasn't until the install was done that I noticed I couldn't use my network devices.

---

### Post by Bucky Ball on 2017-06-04
If you are talking about an ethernet cable, just plug it in. It should work just fine 'out of the box' without you doing anything. Have you tried? If it's not working, see the command further in the post.

As for wireless, that would depend on the wireless card. If you click on the Network icon in the taskbar, if you have one, do you see any available wireless networks? You say your internet is not working, so probably not, but if yes, then your wireless is already working, you just haven't connected to an available network. If not, we would need to work on getting the card working.

You don't store the drivers for wireless on a disk or USB somewhere. Just install them if they're not already there then the wireless will 'just work', regardless of what network you're trying to connect to, when you want to use it. Or you can switch of networking until you do want to use it.

You don't mention whether you are talking about wireless or cable or both, though. Please give us the output of this command in a terminal.

```
sudo lshw -C network
```

That will give us basic info on what you have in the box re. networking.

---

### Post by howefield on 2017-06-04
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by lash5402 on 2017-06-05
Both wireless and ethernet. I do not see a network icon in the taskbar. Remember I installed with a Mini ISO. I could use a regular desktop disc but I wanted to play with installing packages manually without a network connection so I can learn how to do that with Linux systems. I've tried searching online but I never find any of the info I am looking for, just people with similar questions that never get answered Lol.

*-network DISABLED
description: Ethernet interface
product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
Vendor: Qualcomm Atheros
version: b0
*-network DISABLED
description: Wireless interface
product: AR242x / AR542x Wireless Network Adapter ( PCI-E )
vendor: Qualcomm Atheros
version: 01

So, after putting in the command you gave me, it looks like they are there and it can see them but how do I turn them on?

---

### Post by lash5402 on 2017-06-07
Anyone?

---

### Post by Bucky Ball on 2017-06-07
Nothing here sorry, but my post will bump your thread to the top of the list again.

You have no driver for either ethernet or wireless, odd, and without an internet connection of some kind, not sure how you'd get them unless they're in the kernel already. As they're not loading, guessing they're not, which is also odd as these devices have been around for some time.

You may need access to a machine that is online to download the drivers. Thinking it would be the athk5 or athk9, not sure which, and hopefully someone can confirm. I'm looking around now for info on those devices.

Hopefully one of the wireless experts here can help some more and you might consider posting the output of the wirelessinfo script (see my signature, first line, second link) as a precursor and to save time if they do.

PS: You have the mini Lubuntu, but say you have no network icon in the taskbar. So you do have a desktop environment and a taskbar? If you right click on the taskbar does it give you the option to add the network manager? I'm not familiar with Lubuntu and not familiar with getting connected via the terminal, so ... my support potential is limited here.

---

