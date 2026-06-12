---
title: "Netgear WG511 v2 PCMCIA wireless card trouble"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by Jack Bonner on 2009-08-11
I really need a hand on this one,i'm trying to set this damn wireless card up for someone. I've tried various things from other threads and websites, but none of them seem to work. It's the dreaded Chinese version of the card. One site called for me to take the drivers from the Windows install disk, but they don't seem to exist. All I can find are .dlls and setup.exe, autorun.exe and the like. The drivers aren't where the site said they'd be. Next I tried something from these forums, using cabextract to remove the drivers from the installer taken from the Netgear website. That doesn't work either, stating the "No valid cabinets found" error. So what can I do? Can someone give me a step by step guide for this card version and this Distro version. (9.04). I'm quite surprised, even setting up my wireless card on Arch was easier than this.

Cheers in advance for any advice.

---

### Post by Jack Bonner on 2009-08-11
Update, I just did an lspci

```
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

```

So at least is recognises it's there. However the lights on the card aren't lit up. I still can't figure out how to get these damn drivers

---

### Post by mapes12 on 2009-08-11
Hello Jack

I guess you have looked at these?

[http://ubuntuforums.org/archive/index.php/t-208088.html](http://ubuntuforums.org/archive/index.php/t-208088.html)

[http://www.google.co.uk/search?hl=en&q=Marvell+Technology+Group+Ltd.+88w8335+](http://www.google.co.uk/search?hl=en&q=Marvell+Technology+Group+Ltd.+88w8335+)

I have had so many problems with wifi cards on different machines that I just don't bother pulling my hair out any more but bite the bullet and get a cheap one that works straight out of the box. Just fitted one of these PCI cards into my test machine. Works a treat: [http://www.linuxemporium.co.uk/products/wireless/#pidR26940](http://www.linuxemporium.co.uk/products/wireless/#pidR26940)

The vendor says that it's tested and working in 8.04 and 8.10. It also works faultlessly in 9.04 cos that's what I'm running.

Mark - Sunny Staffs

---

### Post by Jack Bonner on 2009-08-12
> **mapes12 said:**
> Hello Jack

I guess you have looked at these?

[http://ubuntuforums.org/archive/index.php/t-208088.html](http://ubuntuforums.org/archive/index.php/t-208088.html)

[http://www.google.co.uk/search?hl=en&q=Marvell+Technology+Group+Ltd.+88w8335+](http://www.google.co.uk/search?hl=en&q=Marvell+Technology+Group+Ltd.+88w8335+)

I have had so many problems with wifi cards on different machines that I just don't bother pulling my hair out any more but bite the bullet and get a cheap one that works straight out of the box. Just fitted one of these PCI cards into my test machine. Works a treat: [http://www.linuxemporium.co.uk/products/wireless/#pidR26940](http://www.linuxemporium.co.uk/products/wireless/#pidR26940)

The vendor says that it's tested and working in 8.04 and 8.10. It also works faultlessly in 9.04 cos that's what I'm running.

Mark - Sunny Staffs

Thanks muchly! I combined things from the above links to get the card working. it now lights up, and detects wireless networks. However it won't connect to them. I have a WPA password right so i'm a little befuddled as to why it won't connect

---

### Post by mapes12 on 2009-08-12
> I have a WPA password right so i'm a little befuddled as to why it won't connectIn Network Manger there's a drop down list about how your password is accepted e.g. hexidecimal, ascii etc. Try them all. I found it gibberish but the hexidecimal option worked for me. I have a BTHomeHub.

---

### Post by Jack Bonner on 2009-08-14
Okay, it's still not working but I have more information now. I re-installed network-manager (I use WICD on my personal Arch machine) and now the card won't light up or find anything. I find this really odd. It never connected under WICD, which is why I tried to switch back.

---

### Post by Jack Bonner on 2009-08-14
> **Jack Bonner said:**
> Okay, it's still not working but I have more information now. I re-installed network-manager (I use WICD on my personal Arch machine) and now the card won't light up or find anything. I find this really odd. It never connected under WICD, which is why I tried to switch back.

Switching back to WICD brings back the card and network discovery. How does that work?

---

