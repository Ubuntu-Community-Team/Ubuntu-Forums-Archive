---
title: "Ubuntu won't recognize my WLAN"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by stickman51 on 2008-12-14
Sorry; I've asked this before, got some answers but nothing in more than a day so I hope it is ok to ask again.....getting kind of desperate.

When I boot into Vista, I'm online instantly, via my Wireless Local Area Network. When I boot into Linux Ubuntu 8.10, I can't.

ONCE it did; I (somehow) found all WLANS and clicked my own, entered my 10-digit WLAN security code and was in. Not now. I'm using a brand new eMachines laptop. If I could find where to make the WLANs show up I should be ok. Can somebody please help out this nooooby?

---

### Post by The Cog on 2008-12-14
Can you start by posting the output from these commands:
> lspci
ifconfig
iwconfig

---

### Post by stickman51 on 2008-12-14
> **The Cog said:**
> Can you start by posting the output from these commands:

Thank you Cog; I only got Ubuntu yesterday so don't even know how to INPUT that; can we go back one more step please? Once I'm logged in, where do I go? I see the desktop with taskbar at the top.

---

### Post by jamesrfla on 2008-12-14
Applications>Accessories>Terminal top left corner

---

### Post by The Cog on 2008-12-14
OK. Launch a terminal from the start menu. I think it's Applications->Accessories->Terminal. Copy and paste each of those commands into the terminal and press Enter after each one. Don't use Ctrl-V to paste, use a mouse right-click and choose paste from the menu.

Then you can drag the mouse over all the console text, right-click and choose copy. Paste it into a reply here. 

FYI, lspci lists all the PCI cards and their make/model. ifconfig says what interfaces are in the system, and iwconfig lists the wireless properties of any wireless interfaces found. It's all part of figuring out what you've got and to what extent it is working.

---

### Post by stickman51 on 2008-12-14
Thanks, James; if you mean Applications | Accessories | Terminal, sure; got that.
So there I have: (my username is kenlaninga)
kenlaninga@ubuntu:~$ (and black flashing cursor)
so I entered those 3:
lspci
ifconfig
iwconfig 
with "Enter" after each one, and got a load of text after each one. After the final one, the iwconfig, I got:
lo    no wireless connection
eth0  no wireless connection
pan0  no wireless connection

and then the first prompt again.

But it DID work once. And it DOES show them in Vista.

---

### Post by stickman51 on 2008-12-14
Then you can drag the mouse over all the console text, right-click and choose copy. Paste it into a reply here. 

But, I cannot paste it all for you, Cog; that 'puter is not online; that's the whole problem; I hope what I showed you is enough for you but I can type more if you need it; I'm using a different 'puter for this chat.

MORE............ I copied and pasted ALL the text into a text editor document and saved it on the desktop, inserted a flash drive, dragged it to that drive; moved the drive to the Vista computer, but sadly Vista said the folder was empty. It isn't. Too bad. I had hoped to be able to show you ALL the text.

STILL MORE............ found a way to get all the text into the Vista machine so now I CAN show it all to you here IF YOU want it...........

---

