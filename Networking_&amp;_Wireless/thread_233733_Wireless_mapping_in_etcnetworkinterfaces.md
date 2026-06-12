---
title: "Wireless mapping in /etc/network/interfaces"
date: 2006-08-10
forum: Networking &amp; Wireless
---

### Post by n7tzg on 2006-08-10
Hi all,

I read in the man pages that there is a way to map multiple ap's with different settings on my wireless card.  Has anyone done this?  Any examples?  The man pages were less than clear to me.

Rob

---

### Post by wieman01 on 2006-08-10
Mmm... Seems I don't understand the question. Willing to help but what exactly do you mean by mapping **"multiple ap's with different settings on my wireless card"**? Can you outline your problem / question a bit further?

---

### Post by bensexson on 2006-08-10
I asked this question a while ago in this thread: [http://www.ubuntuforums.org/showthread.php?t=139519](http://www.ubuntuforums.org/showthread.php?t=139519)  Unfortunately got no answers.  Lets hope someone answers this time.

---

### Post by n7tzg on 2006-08-28
Ok, here is my exact problem:

I have a work wireless network over which I have no control.  It has both MAC address and WEP security.

My home system has MAC address security.  Both have different SSID's and hardware addresses.  

My question is how do I configure /etc/network/interfaces to automatically recognize the system I am connecting with?  I currently have a copy of interfaces that works for home, and one that works for work, but I have to swap them and start the network interface when I go to the other location.

Rob

---

### Post by cam_tram on 2007-03-13
You can try wifi-radar

---

