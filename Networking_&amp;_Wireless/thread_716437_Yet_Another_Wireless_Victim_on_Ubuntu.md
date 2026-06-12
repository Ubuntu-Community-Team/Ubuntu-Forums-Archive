---
title: "Yet Another Wireless Victim on Ubuntu"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by surrealimage on 2008-03-05
First thank you for reading the post. I am very enthu to join the increasing Ubuntu users.

On the Sony NR110E laptop I got, I tried to use Windows Vista. Like everybody says, it sucks a big time. Then I tried to get Ubuntu and installed with Dual Boot.

Except for wireless everything seems to be fine.

First my driver did not work. As everyone suggested I went ndiswrapper route and installed the ndiswrapper. Now I am able to see the networks in the dropdown box of Admin--> Network. But it did not work.

Mine was WPA so I tried the thread [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) It did not work.

Then I made  the network unsecured and tried using the steps in this thread for unencrypted networks. It also did not work. 
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

I request someone to help me so that it motivates me to use Ubuntu.

---

### Post by surrealimage on 2008-03-05
Hi friends,
Request you to have a look into my issue.

---

### Post by nutz on 2008-03-05
Lets get started by having you run these two commands and post the result of lspci.

```
sudo update-pciids
```

Then run this one and post the result...

```
lspci
```

---

### Post by surrealimage on 2008-03-06
lspci result

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


---

### Post by nutz on 2008-03-06
It looks like you are in the same situation as me. It looks like you have an Atheros AR5007 based card. I know this isn't what you want to hear but at this time there is no way to make this card work. Those who have gotten it to work have said it doesn't work very well and it only works under 32 bit. Check out this link...

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

---

### Post by surrealimage on 2008-03-06
Umm. I checked the link. Not very +ve. Does it mean that we may expect a firmware upgrade soon? I could not figure this out.

Without wireless I cannot probably use Ubuntu :-(

---

### Post by nutz on 2008-03-06
To sum it up it means there is no legit driver for that card yet. You can try some of the methods others have used but they only work with 32 bit. And even then they don't work very well...

I got it to work under 32 bit but only with the security disabled. And an unsecured wireless network is unacceptable to me.

---

### Post by surrealimage on 2008-03-06
Me too. I dont want an unsecured connection. Thank you for your help.

---

### Post by hexion on 2008-03-06
Another victim here...

Brand new Compaq Presario A910EM and cannot use the wireless card at all :(

Followed the steps in that link and got it recognized but it detects "Unknown Computer" nets, and of course doesn't work at all.

Anyone tried with ndiswrapper??? I cannot since I can't find windows xp drivers for this card :(

---

### Post by nutz on 2008-03-06
> **hexion said:**
> Another victim here...

Brand new Compaq Presario A910EM and cannot use the wireless card at all :(

Followed the steps in that link and got it recognized but it detects "Unknown Computer" nets, and of course doesn't work at all.

Anyone tried with ndiswrapper??? I cannot since I can't find windows xp drivers for this card :(

I may not be a guru but I busted my balls with this card for 2 weeks and at this time it just doesn't work. I got it to work briefly but only with security disabled and only under 32 bit, it would also constantly disconnect.

---

### Post by raiwo on 2008-03-06
for atheros card see: [http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)

---

### Post by surrealimage on 2008-03-06
I know that this is unrelated to the Kernel and superb GNome...but Ubuntu has to get drivers support more aggressively than the way it is now. For a newbie, this is a real nightmare....

---

### Post by surrealimage on 2008-03-07
I dont know exactly what I did new this time
But this worked using the instructions at [http://ubuntuforums.org/showpost.php?p=3868406&postcount=48](http://ubuntuforums.org/showpost.php?p=3868406&postcount=48)

In between I tried [http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877) but I think I might have overwritten these drivers with those in the above post. 

Thanks to Chalewa. This is my 4th day with Ubuntu and I was almost about to give up. Your post helped me.

---

### Post by nutz on 2008-03-07
I am happy to be proven wrong. Perhaps I will give it another try myself.

---

### Post by surrealimage on 2008-03-07
nutz, I think the reboot sequence after installing the drivers seems to be key. First I rebooted switching off the wifi switch then another reboot switching on.

One more thing I did different today was made my wifi unsecure first. Made it work then switched to WPA/AES. It worked like charm.

All the best.

---

### Post by nutz on 2008-03-07
> **surrealimage said:**
> nutz, I think the reboot sequence after installing the drivers seems to be key. First I rebooted switching off the wifi switch then another reboot switching on.

One more thing I did different today was made my wifi unsecure first. Made it work then switched to WPA/AES. It worked like charm.

All the best.

Just for clarification are you running 64 bit?

---

### Post by Capsid84 on 2008-03-07
You could always setup you router with MAC Address filtering and have a strong admin name and password. That would provide you with some security without having an encryption.

---

### Post by nutz on 2008-03-07
> **Capsid84 said:**
> You could always setup you router with MAC Address filtering and have a strong admin name and password. That would provide you with some security without having an encryption.

While MAC filtering will stop them from making a connection to the router it does not encrypt data being set to the endpoints. Without any encryption a user could simply sniff your traffic in the same manner as they would on a broadcast network. So when you enter that password on your favourite website it flows over the air in plain text form that is effortless to read. This is why the use of public hotspots that are unencrypted enable the ever popular gmail hack. On a secured network that uses encryption the gmail hack is not possible.

---

### Post by nutz on 2008-03-07
Since someone sent me a private message in response to my last post I will explain further.

Without security on the physical layer of the network such as WPA your
only other option is data level security. This is exactly what https
does when you go to a banking website or another site like that. https
provides a data level security that is designed to prevent captured
traffic from being easily read. Any site that does not use https or
something similar in function is unsecured and unless the physical layer
of the network protects the data it can be easily read.

---

### Post by hexion on 2008-03-07
I will copy here another post I sent in other thread since I didn't have response there and this is a better place for it :)


> And would you know by a chance where to find the proper windows drivers?

My laptop came with **crappy** windows vista and I can't find windows xp drivers (which I suppose are the one used with ndiswrapper)

Thanks

---

### Post by Miljet on 2008-03-07
I had been fighting the same problem for weeks and just found the post listed below. The fix is extremely simple. Look at the post and follow the directions carefully.

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

