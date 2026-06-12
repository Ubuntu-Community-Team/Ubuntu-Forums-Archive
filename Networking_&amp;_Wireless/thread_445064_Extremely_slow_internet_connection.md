---
title: "Extremely slow internet connection"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by Jakko on 2007-05-15
Hey!

I just installed Xubuntu 7.04 on an Asus Terminator barebone.
The computer is connected to the internet through a regular router over ethernet.
The integrated networkcard on the SIS 651 mainboard was giving me problems so I ended up using a standard PCI networkcard.

The problem I have is that the speed of the connection is far below what it should be.
Plugging the same ethernet cable in other machines, gives me a good connection speed. (close to 10 Mbit) but plugging the ethernet in the linux box is 40Kbyte max, but sometimes as low as 1 Kbyte.

What can you do to check whether networkcard is installed properly, and whether the network settings are correct?
How can I get a normal network speed on my linux box?

Regards


Jakko

---

### Post by Kobalt on 2007-05-15
Can you post the output of the command lines 
```
lspci
iwconfig
```

---

### Post by ezrollers on 2007-05-15
the standard answer seems to be to blacklist ipv6

add:

blacklist ipv6

to /etc/modprobe.d/blacklist

Alas it doesn't make one iota of difference for me

it might do for you though

---

### Post by Jakko on 2007-05-21
Thanks guys for the replies.
In the end the problem was the ethernet pci card.
Something was wrong with it, and when I put it in a windows machine the windows machine started freezing up and networking didn't work at all.
Replaced the pci card and now everything is ok.

:KS

---

