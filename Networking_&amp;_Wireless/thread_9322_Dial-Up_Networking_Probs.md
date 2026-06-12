---
title: "Dial-Up Networking Probs"
date: 2004-12-27
forum: Networking &amp; Wireless
---

### Post by SandManMattSH on 2004-12-27
Sorry if this has been postes tons of times before, I just don't know where else to put it.  I'm having a bit of a dilemna tho.  I just installed Ubuntu, and got it set up (without a hitch).
I have used linux before, but only for a few hours (barely know anything), so for the sake of explanation, treat me like a newb.
Anyway, here is my problem:
[list=1]
[*]I need to get online on my Ubuntu machine to download updates as well as drivers and software.
[*]None of my other computers have CD burners, and I don't have a home network.
[*]My Ubuntu machine is dual-boot and also had Windows XP on it.
[*]I have an iPod that *could* be used to transfer files, but that would require a program like gtkpod, which would need to be downloaded.  Odd paradox, eh?
[*]I have the install CDs for the x86, PPC, and AMD64 editions of Woody readily available.  And I also have the LiveCD for x86.
[*]I tried setting up a dial-up connection by going to Computer > System Configuration > Networking > Add, and then filling out all of the requested information correctly.  The only thing I wasn't sure of was the "Modem Port".
[*]I then tried to connect by clicking the "Activate" button and it wouldn't connect.
[*]I went back in and tried various different "Modem Port"s.  It still wouldn't work.  I went into the "Device Manager" and pulled up the info on my modem card and tried practically everything I saw.  Still, no luck....
[/list

Anyway, this is where it stands.  For further clarification, lemme just state a few more things:
[list]
[*]When I clicked the "Activate" button all that happened was the checkbox in the "Active" menu checked for about 1-2 seconds and then unchecked.  Other than that, I noticed no change.
[*]I am using the x86 version of Woody (2.6.8.1-3-386).
[*]The modem card is a "HSF 56k Data/Fax/Voice/Spkp Modem" by Conexant.  And it is connected via a PCI slot.

---

### Post by muzzy on 2004-12-27
[QUOTE=SandManMattSH]
[*]The modem card is a "HSF 56k Data/Fax/Voice/Spkp Modem" by Conexant.  And it is connected via a PCI slot.[/QUOTE]
And this is the problem...  :mrgreen: 
HSF mean softmodem and it's dedicated for windoze. There are drivers for this modem, but... You will have to pay $14.95 for this or use free version, limited to 14.4Kbps data :mrgreen: 
Anyway, [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

---

