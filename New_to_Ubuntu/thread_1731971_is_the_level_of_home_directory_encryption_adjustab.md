---
title: "is the level of home directory encryption adjustable?"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by nutpants on 2011-04-17
is the level of home directory encryption adjustable?
i have a netbook a Toshiba nb100. not its not the fastest thing out there
but its fast enough for a lot fo what i need a netbook for
 but being a netbook i would like to encrypt the home directory. 
but when i do it goes slower that i can stand.
its nice and quick with out encryption.. ( it is is just that much faster then encrypted)

can i adjust the level of encryption so that i get some speed back but still block out the average computer tech genius. i can use a a container encryption for anything that i seriously need to encrypt 

thanks for any info..

nutz

---

### Post by deconstrained on 2011-04-17
The "average computer tech genius" would probably perform a [cold boot attack]("http://en.wikipedia.org/wiki/Cold_boot_attack") (kill the power, put in a livedisk, obtain a core dump and extract the encryption key from the image of the memory). That's if he/she obtained your computer while it was running. So even if you use encryption you need to set your BIOS password, so that it's much more difficult for an attacker to get to your memory's contents; it would then require physically removing the memory or opening the laptop and clearing the CMOS, and because laptop memory can get really warm, the data in the DIMMS would dissipate faster, so the DIMMS would have to be removed and put on ice fast.

Unfortunately, since built-in encryption instructions are still a pretty new feature in processors and you're using older hardware, filesystem encryption is going to slow down your I/O no matter what. However, you might have better luck (and it would probably be more secure) to back up your data, LuksFormat your home partition, and then set up your home filesystem on the encrypted partition. That way you'll have plenty more options for encryption and hashing algorithms to choose from. I recommend aes-xts-plain and sha256; that will be pretty secure and none too slow.

Good luck!

---

