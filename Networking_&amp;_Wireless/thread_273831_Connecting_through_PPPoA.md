---
title: "Connecting through PPPoA?"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by F3nr1L on 2006-10-08
I have just recently gotten Ubuntu(Decided to wait for the CD because my burner is broken). I was trying to configure my connection, but it seems that my ISP will only let me through PPPoA, rather than PPPoE. I wondered if there was any easy fix to this, or any fix at all.

For reference, I have an Actiontec GT701-WG modem, and my connection is ADSL through Ethernet.

---

### Post by jwbirdsong on 2006-10-09
I use that exact same router and a default install of Ubuntu..(both Edgy and Dapper)
 You just need to set the router up for PPPoA and Ubuntu will connect just fine...no changes necessary to Ubuntu  (at least for me on two diff boxes; with 4 diffreent cards.. 2 wireless and 2 ethernet cabled.....All work just great.

There **ARE** _some_ wireless issues with Ubuntu...if possible get networking working with "wired" first.

Disregard that last part..I didn't catch the last part of your post.

---

### Post by F3nr1L on 2006-10-10
The modem is set up for pppoa. It is just, I don't know how to configure it in the network option on ubuntu. I have gotten the number and login information, but I don't know what to do on the tab with "autodetect" on it.(I had to switch over to windows and the name escapes me at the minute.) Having Ubuntu and not being able to do much of anything is quite stressful.

---

### Post by mips on 2006-10-10
You have a router. Let the router handle the PPPoA & authentication stuff. Rather configure your router than ubuntu.

If your router is properly setup you dont need to do anything in ubuntu except enable dhcp.

---

### Post by F3nr1L on 2006-10-10
It is set up properly, at least it must be because I can connect on windows. Eth0 is enabled and set to dhcp..is that what you mean?

Edit: also, I found out my network card is a VIA Rhine II, if that helps. Perhaps I don't have a driver for it?

---

### Post by mips on 2006-10-12
If your router is properly setup to do pppoa and it has the login parameter then you only have to configure ubuntu for dhcp. You do not configure pppoa or authentication in ubuntu.

I have no idea how your windows is setup so I cannot comment.

---

