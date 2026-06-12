---
title: "Ethernet cards' killer Ubuntu"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by dunadar on 2007-06-29
Hello everybody,

I'm just translating a message posted a few months ago at Ubuntu-es (the spanish-speaking community) by me. I couldn't obtain a reply, nor found any related information searching the web, so I hope you can help me with this mistery...

I recently formatted a friends PC, and installed WIndowsXP and Ubuntu 6.06 on it. The PC had an ethernet card which has traditionally provided the internet connection, working properly.

Here at home, I have a cable connection with a cable-modem that automatically configures ethernet device using DHCP (totally automatic... in fact, I get once WXP infected by Blaster only 3 seconds past the first boot after installing the OS :P)

When booting up with Ubuntu, I could see it didn't configure connection parameters correctly, so I returned to Windows and it failed too. The device is recognized in both OSs, it is working, sending and receiving packets, but it fails with DHCP config. So I supposed the ethernet card was broken, and bought another one.

The new card was working perfectly with WindowsXP, but when I reboot Ubuntu for testing it the card failed with the same symptoms as in the beginning (many DHCP Discover, no DHCP Offers). And the worst part is that this new ethernet card has never worked again :S


My conclusion is "Ubuntu hates this computer", but I'm open to other opinions :P
I will always be thankful if you can help me, giving a clue, suggesting what the problem can be, or revealing the final solution... because even my linux-geek friends can't explain this.

dunadar.

---

### Post by stchman on 2007-06-29
> **dunadar said:**
> Hello everybody,

I'm just translating a message posted a few months ago at Ubuntu-es (the spanish-speaking community) by me. I couldn't obtain a reply, nor found any related information searching the web, so I hope you can help me with this mistery...

I recently formatted a friends PC, and installed WIndowsXP and Ubuntu 6.06 on it. The PC had an ethernet card which has traditionally provided the internet connection, working properly.

Here at home, I have a cable connection with a cable-modem that automatically configures ethernet device using DHCP (totally automatic... in fact, I get once WXP infected by Blaster only 3 seconds past the first boot after installing the OS :P)

When booting up with Ubuntu, I could see it didn't configure connection parameters correctly, so I returned to Windows and it failed too. The device is recognized in both OSs, it is working, sending and receiving packets, but it fails with DHCP config. So I supposed the ethernet card was broken, and bought another one.

The new card was working perfectly with WindowsXP, but when I reboot Ubuntu for testing it the card failed with the same symptoms as in the beginning (many DHCP Discover, no DHCP Offers). And the worst part is that this new ethernet card has never worked again :S


My conclusion is "Ubuntu hates this computer", but I'm open to other opinions :P
I will always be thankful if you can help me, giving a clue, suggesting what the problem can be, or revealing the final solution... because even my linux-geek friends can't explain this.

dunadar.

So you are saying that Ubuntu is rendering ethernet cards non functional?  I have never heard that?

In Ubuntu give us an lspci and post the output here.  I am surprised, Ubuntu supports pretty much every ethernet card out there.

---

### Post by dunadar on 2007-06-29
Oops, sorry for not putting the proper info...

lspci returns:

00.01.0 PCI bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01) 
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev10)

I'm handcopying this, so I only put here the involved line and other refering the mobo.
As I previously said, it has killed two different cards, so I'm starting to think it could be a problem with the motherboard (but I have no idea what the problem can be). Tomorrow I'm going to try with a third card, after replacing 6.10 with the most recent Feisty Fawn, and pluging it onto another PCI slot... I hope it not to die :(

Nevertheless, I still need all the help you can give to me, because Murphy never fails and I must finish with the PC in a pair of days hehehe

(I don't know the english word for 'pringao'... it is more or less a person that always pays for other's errors or makes their work due to its lack of personality)

---

