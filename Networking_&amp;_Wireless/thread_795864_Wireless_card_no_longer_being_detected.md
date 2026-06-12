---
title: "Wireless card no longer being detected"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by hobbitboy60 on 2008-05-15
hello i am using Ubuntu 7.10 and have never had any problems with the detection of my wireless card.

but a day ago i turned my computer on only to find that my card is not detected and i have no clue how to fix this.

is there a way to replace the system files and not my own files because it took days to fully configure my system and i would hate to have to reinstall Ubuntu.

any help is appreciated

thanks in advance

---

### Post by EXCiD3 on 2008-05-15
What wireless card do you have?

---

### Post by Ayuthia on 2008-05-15
Are you able to see your wireless card when you do lspci -nn in the Terminal?  If so, can you post your lshw -C network?

Also, do you have another operating system installed on this computer?  If so, does your wireless work on it?

---

### Post by hobbitboy60 on 2008-05-15
ok all i have about my card is that it is a linksys wireless-G PCI card

but it worked when i first installed ubuntu so cant i get the networking files and replace them or should i reinstall

the card works on Windows vista

---

### Post by Ayuthia on 2008-05-16
> **hobbitboy60 said:**
> ok all i have about my card is that it is a linksys wireless-G PCI card

but it worked when i first installed ubuntu so cant i get the networking files and replace them or should i reinstall

the card works on Windows vista
When you say that if you could get the networking files, does that mean that you are using ndiswrapper?  If so, does typing:
```
sudo modprobe ndiswrapper
```in the Terminal get it working again?

---

### Post by hobbitboy60 on 2008-05-16
this is nice.....

i logged in so i could do some of the terminal test and i messed around with all of the internet settings and after redoing my connection settings 5 times it works....

only now the signal strength says im at 0% even though im connected

---

### Post by hal10000 on 2008-05-16
I had the same problem on my pc after upgrading to hardy. My wireless PCI-card (Netgear MA 311) wasn't working anymore. Ipreviously used the orinoco driver for this card and figures out, that this card was deactivated in the new kernel on hardy, so i had to compile a new kernel from the sources.

Maybe if your card uses the same driver you have to compile a new kernel. Good luck.

---

