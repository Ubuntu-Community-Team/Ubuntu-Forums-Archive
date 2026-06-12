---
title: "Linksys LNE100TX NIC seems to be locking up my PC"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by hillrunr on 2007-02-10
I've been trying to find an NIC to replace one which I believe may have simply been malfunctioning. The Linksys LNE100TX card came highly recommended by many people, including those at a computer service store who are the only ones I know locally who will be willing to professionally look at a Linux box (for quite a price unfortunately).

When I got my LNE100TX card home, I put it in my PC and, as I was told it would be autodetected, just started up my PC to see what would happen. All went well. I started up Firefox and was online at Google. I tried to go to a site other than Google and one page got loaded. I moved around a bit on it and then my PC froze. I restarted, loaded Google, visited the same page, and the PC froze before it was even half loaded. I've tried several other things and the only time the PC freezes is when I'm accessing the internet. It seems like the network card is causing the PC to freeze every time I try to do anything online.

Anyone ever see this before? Any idea why this could be happening? I'm so close to seeing the finish line at this point, it's frustrating that I can't take this final step and have a fully functioning Linux desktop!

---

### Post by gradedcheese on 2007-02-10
That seems like a hardware problem to me.  Take a look at your previous boot's dmesg log:

sudo gunzip /var/log/dmesg.1.gz
less /var/log/dmesg.1

and scroll to the end, see if there are any messages about errors with the network card (or anything else suspicious).  'q' gets you out of 'less'.  You could also try putting the card in a different PCI slot.

---

### Post by hillrunr on 2007-02-11
Thanks for the help. I didn't find any dmesg.1.gz file but I did see dmesg. Taking a look at that, I did see some strange messages about a CD-ROM, so I disconnected both my CD-ROM and CD-RW drives. I moved my network card to another slot and removed unnecessary hardware such as an old modem that I wouldn't need if I could get the network card working. I restarted, checked the dmesg file and didn't see anything that looked like an error message anywhere in the file. I then started Firefox. Google began loading, about half of the Google banner came up, then the PC froze.

Is there anything specifically I should be looking for in this file?

Again, thanks for the help. I know there is light at the end of this tunnel. I'm so close!

---

### Post by RJARRRPCGP on 2007-08-22
Is your PCI bus overclocked? Sounds like PCI bus corruption if you're also getting IDE-related errors.

---

