---
title: "Ubuntu 9.04 Install woes"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by URGettingADull on 2009-07-17
I am attempting to install jaunty on a pIII 1 ghz 384mb ram that dual boots win 98 and currently edgy.  The problem that i am currently having is when i attempt to install from a burned disc the two load screens come up and when the bar fills on the second (splash?) screen the screen gives me a white cursor for a few flashes and then black, with a dead keyboard.  I have run memtest and diskcheck everything works fine.  the BIOS is rev A11.  I tried a geforce 4100 pci graphics card after reading about one person who solved this problem because their integrated graphics mem was like 1mb, same as mine, but to no avail, and it would give a black screen for edgy too so i had to uninstall it
.
plzhalp !

---

### Post by Temposs on 2009-07-17
You might want to try installing by way of the Alternative CD, which is text only. This way, you won't have any problems with your graphics card while trying to install. Here's a link:

[http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate](http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate)

Make sure you download this one:
[http://ftp.wayne.edu/linux_distributions/ubuntu/9.04/ubuntu-9.04-alternate-i386.iso](http://ftp.wayne.edu/linux_distributions/ubuntu/9.04/ubuntu-9.04-alternate-i386.iso)

or by way of bit torrent:
[http://releases.ubuntu.com/9.04/ubuntu-9.04-alternate-i386.iso.torrent](http://releases.ubuntu.com/9.04/ubuntu-9.04-alternate-i386.iso.torrent)

---

### Post by presence1960 on 2009-07-17
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

scroll down to section with F4. Try safe graphics mode or alternate text based installer as Temposs suggests. One of these should work for you.

---

### Post by misswham on 2009-07-17
I had a problem when I upgraded from 8.04 to 8.10 my screen went blank and i just installed over it with 9.04 from a disk and it downloaded but when I went to change the resolution to the correct one I got a blank screen so i just went back to 8.04.  It might be better to go back to what works.  Now I upgraded to 9.04 on my laptop and the only problem I have there is my audio doesnt work at all.

---

### Post by URGettingADull on 2009-07-19
Thanks, the alternate installer worked for me, but now Jaunty will not load.  IT gave me a blank screen at first, then i re installed the graphics card and i got a busy cursor that froze.  Did some searching on the matter, but didn;t find anything that was quite the same as this...

---

### Post by URGettingADull on 2009-07-19
also kb is dead

---

### Post by ugm6hr on 2009-07-19
Press escape at bootup and enter recovery mode.

Does this work?  Can you login at the Terminal there?

If yes, then the problem is a graphics card / GUI / Xorg issue.

---

### Post by URGettingADull on 2009-07-19
discovered the problem while trying to use the safe mode with networking, i was trying to install the driver for my graphics card and the netwroking mode kept giving me a device problem in address 801, which is my wireless-g PCI card.  So after uninstalling it ubuntu booted up first time, still having troube installingthe driver though.

edit: installed proprietary driver, not sure what to do about the network card though, i can't hot swap it, and if i install it the system won't boot up, any ideas?

---

### Post by URGettingADull on 2009-07-21
bump 

i have used the ndiswrapper on the windoze driver and tried the proprietary linux driver found on SMC's website.  Its the realtek 8185 chipset that is supposed to work "out of the box" according to ubuntu's website, when in fact it does quite the opposite and clobbers the OS.  I have tried installing without ethernet hooked up to try to force it to use the wireless network card to no avail.  

please someone stop me from going back to XP just because of a stupid wireless card...

](*,)X3.

---

### Post by ex-wirecutter on 2009-07-21
[

QUOTE=misswham;7634274]I had a problem when I upgraded from 8.04 to 8.10 my screen went blank and i just installed over it with 9.04 from a disk and it downloaded but when I went to change the resolution to the correct one I got a blank screen so i just went back to 8.04.  It might be better to go back to what works.  Now I upgraded to 9.04 on my laptop and the only problem I have there is my audio doesnt work at all.[/QUOTE]
I had the same problem with audio on my laptop, tried all the advice on this forum but still no luck . If you find a solution would you post it please ?

---

