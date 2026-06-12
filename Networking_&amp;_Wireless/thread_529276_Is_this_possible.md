---
title: "Is this possible?"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by samh_08 on 2007-08-19
is it possible to take the dell wireless mini pci card out of my dell inspiron 6400 and replace it with a different mini pci card? really need help on this one, please let me know...thanks

---

### Post by spartan777 on 2007-08-19
I don't see why not.

---

### Post by samh_08 on 2007-08-19
well does anyone know which card would work, or what i need to look for. all i know is that i need a atheros chipset. i ordered a wireless pc card but i guess they dont work on the inspiron 6400. let me know..thanks

---

### Post by lsutiger on 2007-08-19
you could try and get the one you have now to work. What chipset does it have?
type :
lspci | grep controller
and post the output

---

### Post by samh_08 on 2007-08-19
here is what i got when i typed that in. getting the pc card the i bought to work is out of the question because i doesnt even fit into the stupid MINI-PCI express card slot that my dell has. this is why i was wondering if i can take the internal card as shown below and replace it with another atheros chipset card and still have everything work normal. please set me straight. thanks


sam@sam-laptop:~$ lspci | grep controller
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0b:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

---

### Post by lsutiger on 2007-08-19
I have the same exact card. [Follow this link]("http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html") and follow the directions.
If that doesn't work, [this will definitely work]("http://ubuntu1501.blogspot.com/2007/05/another-way-to-get-wi-fi-on-dell-1501.html"), but you will only have 11Mbps speed 

The first guide is very simple (even with pictures), the second is pretty easy, but no pizaaz!

---

### Post by lsutiger on 2007-08-19
PS - BTW, the wireless card is listed as a mini pci, but it is actually a Mini PCI-E..I even called dell tech support on that and told them that they needed to change it in the description. The two cards are of different size.
The tech argued with me...but there is no way on this earth you could fit a mini pci card into the slot :)

---

### Post by samh_08 on 2007-08-19
no no no..i think we're on a different page. i got the card working its just that i want a different card. im sick of the broadcom dell card and i want a card to replace it that has an atheros chipset. does that clear things up a bit?

---

### Post by lsutiger on 2007-08-19
Sorry for the quick reply...jumped the gun
[Here's what I got from a google]("http://www.google.com/search?q=atheros%20wireless&rlz=1L1GGXD&hl=en-US")
And the answer is, yes you can swap the card. Will it work? Maybe, with that chipset, most probably.

---

