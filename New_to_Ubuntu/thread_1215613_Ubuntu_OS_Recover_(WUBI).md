---
title: "Ubuntu OS Recover (WUBI)"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by SPARTAN-118 on 2009-07-17
Hi guys, 

I'm in a bad mood 'cuz I screwed up Ubuntu.

I have a dual-boot configuration with Windows. With the program StartUp-Manager, I managed to make it so Ubuntu can no longer boot; now, when I select Ubuntu, it just goes back to the OS select menu (I think, the bootloader menu?).

How can I recover Ubuntu via the LiveCD? I'm a total n00b at Terminal, the only thing I pretty much know how to do is install software (sudo apt-get install...)

Really, just because Ubuntu is so customizable and "Open Source" makes me think it's okay to mess around with it.
But when Ubuntu is your main OS and Windows is your backup OS, it's not good to screw it up.
Especially when you have Windows Vista.

Oh, yeah, and, while Windows has a much more "cluttered" and complex interface, at least it takes everything at face value, unlike Ubuntu, which has the "truth that lies within the truth".

SPARTAN-118

---

### Post by earthpigg on 2009-07-17
> **SPARTAN-118 said:**
> 
I have a dual-boot configuration with Windows. With the program StartUp-Manager, I managed to make it so Ubuntu can no longer boot; now, when I select Ubuntu, it just goes back to the OS select menu (I think, the bootloader menu?).


hi,

have you tried selecting a different kernel from the list at the menu you describe?

couple downsides of wubi that you will have to deal with while doing this:
-cannot simply boot from a live CD to see your ubuntu install, since it is within windows.
-instead of the standard linux boot loader (GRUB), it uses the windows boot manager.

i've never used wubi, so wont be of much help if selecting a different kernel can't help you out....

...but one of the first things *I* would try is popping that live CD in with windows running and explore my options there. can you see the ubuntu filesystem *_at all_* from within windows, either with the live cd or without?

---

### Post by SPARTAN-118 on 2009-07-17
Well, right now I'm on my dad's computer. On mine, I have the LiveCD running. 

I booted up the LiveCD, and there is no "recover" option.

However, the advantage of having a WUBI install is that you can access your files from Windows even if you are using the LiveCD, and, like you said, the boot drives and everything are in Windows.

So, what portion of the boot_menu.lst or whatever it uses to boot says what kernel it uses?

In StartUp-Manager, I selected "Windows Vista (Loader)".

How do I edit the boot menu.list/lst/whatever so that it says to boot up from the Ubuntu 9.04 kernel? If I can just edit that part, so that it boots from Ubuntu, instead of booting the loader, I'm certain I can fix my system.

Thank you, 
SPARTAN-118.

EDIT: I forgot to mention, I'm trying to use gedit in the LiveCD to edit boot_menu.lst.

---

### Post by earthpigg on 2009-07-17
as i understand it, wubi uses the MS Windows bootloader and not grub.... meaning that you can do all the modifications in the world to /boot/grub/menu.lst either manually, or by using startup manager.

either way, it wont change anything for the better and may (as you have seen) break things.

this is what the Windows bootloader looks like:
[IMG]http://www.dedoimedo.com/images/computers/wubi-bootloader.jpg[/IMG]

this is what GRUB (GRand Universal Bootloader), the most common Linux bootloader and the one used by true dual-boot ubuntu installs, looks like:
[IMG]http://thegabfather.files.wordpress.com/2008/09/grub4kt.jpg[/IMG]

StartUp-Manager is an outstanding tool to fiddle with GRUB, the bootloader used by Ubuntu....

...but you gotta use windows tools to play with the windows bootloader, and linux tools to play with the linux bootloader.


> Oh, yeah, and, while Windows has a much more "cluttered" and complex interface, at least it takes everything at face value, unlike Ubuntu, which has the "truth that lies within the truth".

entering your password - aside from when you first turn the computer on - is claiming root privileges.

'root privileges' is another way of saying 'turn god-mode on'.

you can do anything, and the system assumes that -- since you are God -- you have naturally done your homework and are incapable of making mistakes.

---

### Post by SPARTAN-118 on 2009-07-17
"The system assumes - since you are God - that you have done your homework and are incapable of mistakes".

Guess that's why I'm in the Beginner Talk forum, huh? ;)

Anyway, problem solved, and yes, I now know that I use the Windows bootloader, not GRUB.

My problem was that (thanks to raymondhenson, I fully understand it now) I had selected the default OS to Windows Vista (Loader), which made it loop back to the bootloader.

Replacing menu.lst with the backup - which I assume StartUp-Manager created automatically - fixed this, and reset the default value to "0", or Ubuntu 9.04.

So, yeah, problem solved.

Can someone please close this?

Thanks, 
SPARTAN-118

---

### Post by raymondh on 2009-07-17
> **SPARTAN-118 said:**
> "The system assumes - since you are God - that you have done your homework and are incapable of mistakes".

Guess that's why I'm in the Beginner Talk forum, huh? ;)

Anyway, problem solved, and yes, I now know that I use the Windows bootloader, not GRUB.

My problem was that (thanks to raymondhenson, I fully understand it now) I had selected the default OS to Windows Vista (Loader), which made it loop back to the bootloader.

Replacing menu.lst with the backup - which I assume StartUp-Manager created automatically - fixed this, and reset the default value to "0", or Ubuntu 9.04.

So, yeah, problem solved.

Can someone please close this?

Thanks, 
SPARTAN-118

To mark your thread solved ... go to your first post > edit > advanced > type SOLVED in front of your thread Title > save.

Happy Ubuntu-ing ;)

---

### Post by SPARTAN-118 on 2009-07-19
thnx raymond. 

srry 4 spelling, using psp.

SPARTAN-118

---

