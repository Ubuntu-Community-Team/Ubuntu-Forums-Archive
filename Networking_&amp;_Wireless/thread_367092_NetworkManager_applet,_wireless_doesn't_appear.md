---
title: "NetworkManager applet, wireless doesn't appear"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by marktechey on 2007-02-21
While using NetworkManager Applet 0.6.4, it says I'm not connected to the internet, even though I'm connected, and can browse the web, like I'm doing now. When I click on it, only the wired network shows up. How can I fix this?

---

### Post by AlcoJaguar on 2007-02-21
If it's a pcmcia card you can just pop it out and put it back in, it network-manager should catch it before it enables with the stock network tool with Ubuntu. If you can't do that, open up your networks under system->admin, deselect your wireless card as active, edit the properties, uncheck enable this card, and restart. When you log in next it should detect the card with network-manager (I had the same problem, this is how I fixed it on my laptop).

---

### Post by marktechey on 2007-02-22
Thanks for the reply, I tried it, and it didn't work

---

### Post by marktechey on 2007-02-22
Never mind, I got it to work now, i just didn't disable everything.

---

### Post by adamstorm on 2007-02-22
AlcoJaguar, that worked for me perfectly! THANKS! I've been trying to get this thing to work for two days now. I'm surprised that hasn't shown up in any howto guides that I read. (I read a lot of them)

Cheers!

---

