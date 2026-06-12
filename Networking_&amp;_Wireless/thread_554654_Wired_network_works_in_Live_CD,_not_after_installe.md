---
title: "Wired network works in Live CD, not after installed"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by daveerickson on 2007-09-19
This is very strange, and to start things off, this isn't on my PC, it is on a friends who I recommended to make the switch from XP. He tried the live cd and it worked, now installed...nothing. I have no idea where to start. Any help would be appreciated. Thanks!:)

---

### Post by kevdog on 2007-09-19
This happens sometimes.  Please give us more details about your wired card

lspci -nn
lshw -C network

---

### Post by daveerickson on 2007-09-19
I will forward these instructions on to him and post the response. Thanks for the quick reply.

---

### Post by daveerickson on 2007-09-20
Well bad news. My friend called MSI, the manufacture of his MB, and they said linux drivers don't exist. So, he reinstalled XP! I will have to talk to him some more and get him back on track. That sucks that this happened. I don't understand what the live cd does to setup wired networking that a full install does...:confused:

Wish me luck.

---

### Post by winhamwr on 2007-11-20
I also had networking working find on the Live CD and on my first bootup. It was broken my second boot, so I just rebooted and it worked. Then I rebooted a few hours later and now it's not working again. I'm kind of at a loss for why it would just work, not work, work and not work. Is there a way to return to the "auto detect" settings?

I'm running a Marvell 88E8053 ethernet card (onboard my mobo). 

What should I do to start troubleshooting this problem? 

thanks
-wes

---

