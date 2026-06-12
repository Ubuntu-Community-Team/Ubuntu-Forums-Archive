---
title: "Ubuntu is killing my LAN... bios doesnt even see it"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by pashintSudoNewb on 2009-01-19
ok, first let me say that if this is a common bug/problem, im REALLY sorry for wasting anyones time. in my own defense, my google fu is pretty strong lol...

ok, the problem... I now have a dual boot sys : xp, ububntu 8.10, and i left 30 gigs or so for another distro to play with, or bsd, havent decided yet... anyways.... it appears that when i shut down ubuntu, im losing the LAN there. the ONLY resolution so far has been the old cmos jumper, but until i do that, xp cant see the nic, linux cant, and the options for it are even gone from my bios (sorry i dont have the prereq info about the board, bios, etc. handy) My next next step is t reboot to ubuntu, see if its seeing the nic now (which i  have a gut feeling it will) and then reboot from there, which i see no reason why i wont end up opening the case to reset the cmos. i wanted to at least get this posted before starting that oh so fun journey, so all seriousness, thank you in advance, and i cant wait to dig into this distro. thanks again....

---

### Post by jrusso2 on 2009-01-19
How do you know its not a hardware problem with your nic?  What nic are you running anyway?

---

### Post by fuzzyk.k on 2009-01-19
yeah am with hardware problem

---

### Post by pashintSudoNewb on 2009-01-19
I was sorta joking in the title guys, sorry if any of that came off wrong. ok, im sorta with you on the hardware thing, just if nothing else, something in ubuntu is triggering it, cause going into and coming out of windows doesnt cause the problem; make that cause the problem to make itself visable ;) As for the NIC, windows shows it as "VIA compatible Fast Ethernet Adapter" (sorry, im actually fairly proficient with computers, and am totally comfortable on one, my first was a vic20 if that helps lol... i just feel super uneducated with unix/linux and this is a hell of a curveball to get immediately after install)And as far as hardware goes, this is a box i built 2 years ago or so, and have gone through a bunch since, and mainly used my laptop recently, so i honestly dont remember the specs on the stuff, but just lemme know what you need, even if it requires me dling sisoft sandra or something, and ill post it here... thanks again!

---

### Post by pashintSudoNewb on 2009-01-19
just an update, im about to flash my bios, as it appears there was a bios update released a couple years ago taht MAY fix it... but i still think the community, or the linux community as a whole, would find this very interesting. i know  the responses i got said "hardware problem" but it a problem that windows doesnt cause, ubuntu does... its not about blame, literally. Anyways, ill let u know if the flash helps, and any feedback is appreciated...

---

### Post by pashintSudoNewb on 2009-02-04
ok... im gonna asume youre using an ecs p4mpro800-m2 ver? (look at your physical mb, it clearly states it) and were going to flash your bios using amiwin or amidos. If it didnt work, or more specifically, rendered your keyboard apperently unusable, heres what happened. you flashed with not the newest bios, but the one prior, and/or with the wrong MB ver numbers bios. what i did was leave the keyboard unplugged on boot, than after the boot load, plug it in (i think it has to be a usb kb to work) and edit your menu.lst (i forget the directory, i think its /etc/grub/menu.lst, i may totally be wroong though) and change the default boot option to windows if you have a dual boot machine. from win u can reflash with the correct bios, though in amiwin mine said the bios id and the rom id didnt match, so i had to force it to flash regardless (its just a checkbox). that fiixed the prob completly, keyboard works again, and im not losing lan coming out of ubuntu. btw, u can get lan back when that happens by resetting your cmos jumper. hope this was helpful...

---

