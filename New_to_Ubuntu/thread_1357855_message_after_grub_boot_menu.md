---
title: "message after grub boot menu"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by jnmjr on 2009-12-17
I'm using Ubuntu 9.10 with grub2. When UBU begins to boot I get a black screen with, VGA=792 is deprecated. Use set GFX payload=1024x768x24, 1024x768 Before Linux command instead. After this UBU loads fine. What does it mean and how do I fix it. THX.:confused:

---

### Post by drs305 on 2009-12-17
It probably means that you have "vga=792" on the *GRUB_CMDLINE_LINUX_DEFAULT=* line of /etc/default/grub. As noted in the message, the "vga=" mode is deprecated now, which means it isn't the *preferred*  way to accomplish things. As you have seen, GRUB 2 will work fine leaving things unchanged.

What G2 is suggesting is to make /etc/default/grub look like this:

> 
GRUB_GFXMODE=1024x768x24,1024x768
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Note: Make the two GRUB_CMDLINE... lines look like what you currently have, minus the "vga=792" entry.

You would edit the file as root with any text editor, after making a back up, such as:
```

sudo cp /etc/default/grub /etc/default/grub.old
gksu gedit /etc/default/grub
```
After you make the changes, save the file, then update the menu with:
```

sudo update-grub

```

---

### Post by jnmjr on 2009-12-17
:biggrin:Thank you DRS305. Worked perfect.

---

### Post by drs305 on 2009-12-17
> **jnmjr said:**
> :biggrin:Thank you DRS305. Worked perfect.

:-) 

I'll put a note about this in my Grub 2 Basics post when I get a bit of time.

Edit: Done

---

### Post by epeneto on 2010-10-14
Kubuntu Lucid 10.04. Same message, same problem. SOLVED. Thanks so much.:guitar:
   Greetings from Spain.   Mismo menaje, mismo problema. SOLUCIONADO. Muchísimas gracias

                                                  =D>=D>=D>=D>=D>

---

