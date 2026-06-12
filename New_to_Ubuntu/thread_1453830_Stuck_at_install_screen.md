---
title: "Stuck at install screen"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by munkey pooo on 2010-04-13
I'm using a Windows XP PC

I downloaded Ubuntu. Burned the .iso file. Checked the md5sum thing, that was fine.

The cd boots and I get the language choices and I can press enter on enligsh.

At the install screen I can move up and down with the arrow keys but cant press enter on any of the options apart from "boot from first hard disk"

Ive tried removing "quiet splash --", adding "noapic nolapic", "acpi=off", "irqpoll", "lapic pci=routeirq" and "hpet=disable". None of these make any difference when I hit enter on either "try Ubuntu without any change to your computer" or "install Ubuntu"

How can I get Ubuntu to install?

Computer specs 
System Manufacturer: AOpen
BIOS: Phoenix - AwardBIOS v6.00PG
Processor: AMD Athlon XP 3000+ 2.09 GHz
Memory: 1024MB RAM

---

### Post by undecim on 2010-04-13
If you don't touch anything at all and allow the 30 second timer to reach 0, it will load the "Try" option automatically. From there, you can try Ubuntu and there is also an Install icon on the desktop if you want to install.

---

### Post by Don1500 on 2010-04-13
It sometimes takes longer than you expect to start the "Try" feature. Either do what undecim said and just wait for the timeout or hit enter and wait, it could take 30 sec sometimes.

---

### Post by igelman on 2010-04-13
i strongly agree with these posters and is something i would do if i was in the same position as you, monkey poo. But i also recommend trying a VM (virtual machine) which is almost like a virtual computer. Very cool stuff. Sun microsystems makes a free one 
( [http://www.sun.com/software/products/virtualbox/](http://www.sun.com/software/products/virtualbox/) ) No need to worry about "try ubuntu" if you take this path.

---

### Post by kakashi_hatake on 2010-04-13
hello, I'm very new to ubuntu but i remember installing and it completely froze for two hours. it installed fine though after that. the computer i used was very slow so that might affect it.

---

### Post by munkey pooo on 2010-04-20
It was a bad burn onto the CD. I burned the CD on my newer laptop that's running vista and that CD worked. 

Seeing as you cant select "check CD for defects" at the install screen, the way to know if it was a good burn is to put the CD in while you're logged in and a Ubuntu menu will pop up. When I did this with the bad CD burn, an error message would pop up instead.

---

