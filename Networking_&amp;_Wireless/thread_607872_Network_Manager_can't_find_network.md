---
title: "Network Manager can't find network"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by Scragglygoat on 2007-11-09
Hi everyone, I am having some problems with my wireless, and I'm hoping thatsomeone out there has a solution. I see alot of other posts here about similar things, with a variety of suggestions. I've just spent the whole day trying to learn enough to get it going but the problem is I am a complete novice and am having to do a lot of reading for even the most simple things. Here is the tale: 

I have an IBM x30 Thinkpad with Windows XP SP2 installed, and I have just added Ubuntu 7.10, using it to partition the disk for the install. The install was flawless, and everything worked out of the box - the smile on my face was miles wide! I can boot XP or Ubuntu, and almost everything seems to work. 

Unfortunately the network suddenly stopped working. It may have been following a system suspend, I'm not sure. Now Network Manager cannot "see" any wireless networks (but XP has no trouble with it.) I have tried rebooting, and editing /etc/default/acpi-support so it reads MODULES="ipw3945" and rebooting as suggested by meldroc here: [http://ubuntuforums.org/archive/index.php/t-332361.html](http://ubuntuforums.org/archive/index.php/t-332361.html) but I've changed it back as that didn't fix it for me. I have tried commenting out several lines in /etc/network/interfaces and rebooting as suggested here: [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-45c7dcb29a13372e1da1221b5ed499d981ea7ec6](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ#head-45c7dcb29a13372e1da1221b5ed499d981ea7ec6) but as that didn't fix it I have undone that again now. 

My network card is a mini pci Intel Corporation PRO/Wireless 2915ABG, and before installing Ubuntu I installed this card myself, and had to run a program that came with it in DOS to edit the BIOS to get around IBM's over-eager censorship. This seemed to go OK eventually (the X30 has no floppy drive, so it took some fiddling) and the card seemed to work fine. As I say, it also worked initially with Ubuntu, which makes me puzzled - there must be a simple way to sort it out, mustn't there? 

I must say that Ubuntu was so far ahead of Windows in my book until this - it just seemed to work amazingly well, in contrast to the woes of some users trying to upgrade to Vista. I guess nothing is completely pain free :-) 

If you can help, would you please bear in mind that I really am just starting with Linux? I have had it for a few days - less than a week and even editing read-only files was difficult!

---

### Post by Scragglygoat on 2007-11-11
Hmmm... I've now found that my system has stopped picking up USB memory sticks when I put them in... I think perhaps I need to pause on the Linux thing and spend a little time on some tutorials before I try again. I don't want to give up on it because when it all works it looks great! 

Back soon...

---

