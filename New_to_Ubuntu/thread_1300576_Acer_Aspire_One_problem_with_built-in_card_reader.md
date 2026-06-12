---
title: "Acer Aspire One problem with built-in card reader"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by orbital on 2009-10-25
I'm having trouble getting Acer Aspire One built-in card reader to work. I'm trying to get it to read my xD card but with no success. When I put the card into the reader nothing happens, it doesn't mount at all.

I tried this also but with no success: [https://help.ubuntu.com/community/AspireOne110L#Card%20Readers](https://help.ubuntu.com/community/AspireOne110L#Card%20Readers)

Is there any ways to get the reader to work on my Aspire One? I'm using Ubuntu 9.04.

Thanks for any help.

---

### Post by nothingspecial on 2009-10-25
It works on my wifes aspire one if she starts the computer with the card inserted.

---

### Post by orbital on 2009-10-25
> **nothingspecial said:**
> It works on my wifes aspire one if she starts the computer with the card inserted.

I tried it but it didn't help. Same thing as before, no mount.

---

### Post by colmhopkins on 2009-10-25
Hi Orbital

This worked for me.  I am using Jaunty 9.04 and Acer Aspire One ZG5.  And have tried various solutions to fix the problem all to no avail .

It might add about 3 secs to boot up and some errors but works.

sudo gedit /boot/grub/menu.lst

where it first says ro quiet splash
e.g. kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=e843be20-ee17-4004-891e-8fc0f93ead46 ro quiet splash

Just added the following to the end of the line, save and reboot.

kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=e843be20-ee17-4004-891e-8fc0f93ead46 ro quiet splash pciehp.pciehp_force=1

:popcorn:

Colm

---

### Post by orbital on 2009-10-25
> **colmhopkins said:**
> Hi Orbital

This worked for me.  I am using Jaunty 9.04 and Acer Aspire One ZG5.  And have tried various solutions to fix the problem all to no avail .

It might add about 3 secs to boot up and some errors but works.

sudo gedit /boot/grub/menu.lst

where it first says ro quiet splash
e.g. kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=e843be20-ee17-4004-891e-8fc0f93ead46 ro quiet splash

Just added the following to the end of the line, save and reboot.

kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=e843be20-ee17-4004-891e-8fc0f93ead46 ro quiet splash pciehp.pciehp_force=1

:popcorn:

Colm

When I boot with this i get "Unknown boot option, ignoring pciehp..." notification just after the boot.

Any other ideas?

---

### Post by colmhopkins on 2009-10-25
Hi Orbital

Updated partners netbook and got same message as you.  Leave it with me and see can I find a solution.

Colm

---

### Post by LewRockwell on 2009-10-25
[http://ubuntuforums.org/showthread.php?t=1300716](http://ubuntuforums.org/showthread.php?t=1300716)

.

---

### Post by colmhopkins on 2009-10-25
Orbital 

Undo the changes made to the /boot/grub/menu.lst

type 
sudo gedit /etc/modules

enter the following line, save and reboot

pciehp pciehp_force=1

This worked on my partners acer, allowing hot swapping on boot sd card readers

Best of luck
Colm

---

### Post by colmhopkins on 2009-10-25
To LewRockwell

There is no one solution to the problem of sd card mounts on the acer aspire one.  I don't like as a new poster being told in caps and with little understanding what I should and shouldn't do.

"*** * * [B]_Please Edit First Post Title With "[SOLVED]" When It Is!_**
MANDATORY INFORMATION: make, model/build number, OSes, software, accessories
/customizations/modifications/peripherals/etc...and a DETAILED account of difficulties!"[/B]

Just trying to help those like myself who are having difficulties.

Your post would put me off replying and helping others again.

Colm

---

### Post by LewRockwell on 2009-11-01
> **colmhopkins said:**
> Your post would put me off replying and helping others again.

seriously?

well, we'll promptly return what you've paid to participate on the forums...

your check is in the mail...

{{sigh}}

.

---

### Post by teh603 on 2009-11-02
There's more'n one cause to the problem. Some AAOs have ROM BIOS issues that cause it. If an AAO is having trouble reading cards, its not necessarily the card's fault.

There's also a report that both AAO card readers stopped working under Karmic, so take that in mind as well.

---

### Post by LewRockwell on 2009-11-02
> **teh603 said:**
> There's more'n one cause to the problem. Some AAOs have ROM BIOS issues that cause it. If an AAO is having trouble reading cards, its not necessarily the card's fault.

There's also a report that both AAO card readers stopped working under Karmic, so take that in mind as well.

begin-fyi

the readers on those that have been on the tech bench work flawlessly under Windows XP

end-fyi

.

---

### Post by teh603 on 2009-11-02
> **LewRockwell said:**
> begin-fyi

the readers on those that have been on the tech bench work flawlessly under Windows XP

end-fyi

.Which makes me think its an issue with the ROMs, driver or abstraction layer. Not necessarily with the card itself. Otherwise it would always work perfectly with freshly bought cards, wouldn't it?

It isn't the first AAO BIOS issue, by the way. Or do you remember when the power manager was still freaking out because the BIOS was incorrectly reporting screen brightness?

---

