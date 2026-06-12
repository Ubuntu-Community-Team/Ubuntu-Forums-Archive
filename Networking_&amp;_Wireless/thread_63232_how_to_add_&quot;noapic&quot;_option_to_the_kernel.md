---
title: "how to add &quot;noapic&quot; option to the kernel?"
date: 2005-09-07
forum: Networking &amp; Wireless
---

### Post by orrego on 2005-09-07
i know you need to add it to /boot/grup/menu.lst
but how?

i do not find any doc on this.

I need to do this as it is how i can get my network card to work properly on ubuntu.

thanks for any hint.

greetings from Santiago, Chile.

---

### Post by adwait on 2005-09-07
When grub appears during start up, you can press 'e' and edit the kernel options (or is it 'a', I can't remember, read whatever it says at the bottom of the GRUB screen).

---

### Post by mlomker on 2005-09-07
You can edit the /boot/grub/menu.lst file using **vim** from the command line.  You'll see a number of **kernel** commands in there and you just add the command to the end of the line.

---

### Post by aveline on 2005-09-07
[QUOTE=mlomker]You can edit the /boot/grub/menu.lst file using **vim** from the command line.  You'll see a number of **kernel** commands in there and you just add the command to the end of the line.[/QUOTE]
 gah! vim??? LOL no ty... hehe hm if you want a simpler editor do:

sudo gedit /boot/grub/menu.lst

on the line where the KERNEL is at the end put:

... noapic nolapic (last command may not be necessary but if it is just put it after your noapic)

---

### Post by skoal on 2005-09-07
orrego, your kernel option in /boot/grub/menu.lst would look like this:

kernel          /vmlinuz-2.6.12.5-050905 root=/dev/sda3 ro quiet splash **pci=noacpi**

* That option will turn of IRQ routing and PCI scanning by ACPI...

Other options which might interest you are "acpi=x", where x is one of the following:

off - disable ACPI
noirq - do not use ACPI to route IRQ's

When grub first boots up, press ESC, hilite the kernel you want, and press "e" as adwait mentioned.  Then you just append those options to the end (as shown above).  You can do it this way first, which will _not_ be permanent - just to test it out.  If that seems to work for you, then edit /boot/grub/menu.lst and add that entry there to make it persist on subsequent reboots.

\\//_

---

### Post by az on 2005-09-07
Actually, you want to add it to you default kernle options:

## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

So, put it at the end of that last line.  Yes, it is commented, but that is what update-grub will use to reconstruct your new menu.list every time it is called.  As it is, if you get a security update or bugfis for the grub package, or install a new kernel, your menu.list will be rewritten. 

Then run 
sudo update-grub

---

