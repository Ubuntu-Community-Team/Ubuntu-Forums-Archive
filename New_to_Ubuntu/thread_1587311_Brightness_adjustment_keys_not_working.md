---
title: "Brightness adjustment keys not working"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Rekenber on 2010-10-03
I have a NEO VIvid V3153 Laptop, and have installed Kubuntu (works fine), Fedora (works fine too).

Since I have switched to Ubuntu (and overall I can say that I am having a great time), the keys won't work.

I was Fn+F7 (Increase) and +F8 (decrease).

What should I do?

---

### Post by Hippytaff on 2010-10-03
I don't particularly know much about this but have you tried bind-keys

**System menu** -> **Preferences** -> **Keyboard Shortcuts**

---

### Post by Jesus_Valdez on 2010-10-03
Can you change the brightness using other methods (such as the applet)?

---

### Post by Rekenber on 2010-10-04
Applet?

And I don't know which application does this. I tried smartdimmer but failed, init_nvclock() fail

I installed kubuntu before, and it worked there.

---

### Post by Mark Phelps on 2010-10-04
One possibility is that with the newer kernels, the info for these keys is not being detected anymore.  I found that to be true for a tablet PC whose bezel keys have not been detected since 8.04.

To see if the key press is being detected, install and run xev.

When you run it, put the mouse inside the box and press the key in question.  You should see a bunch of info scroll by in the window. IF you do, the keypress is being detected.  IF you don't, there's really nothing much you can do because the kernel isn't even seeing the keypress.

---

### Post by emoguitarist06 on 2010-10-04
For me Asus 1201N this worked for me


[B]gksudo /etc/default/grub

change the line that says "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" to read "GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux acpi_brightness=vendor splash"" instead.

Save and then "sudo update-grub2"

Reboot.[/B]

---

### Post by Rekenber on 2010-10-05
I tried to adjust brightness using the applet (Power management) and I was successful WHILE ON AC POWER.

Is there a way to dim it while on battery power?

---

### Post by Griffiss on 2010-10-06
I had a similar problem, and eventually found a workaround, though not a full solution, by using the following command:
```
sudo setpci -s 00:02.0 F4.B=e0
```
where B=x can be set with values from 00 to FF in hexadecimal notation which corresponds from complete blackness to full brightness. And 00:02.0 is the address of my VGA controller given by the command
```
lspci
```
Discussion of my problem can be found here, with links to the fix in post #15: [http://ubuntuforums.org/showthread.php?t=1588980](http://ubuntuforums.org/showthread.php?t=1588980)

---

### Post by Rekenber on 2010-11-05
Working since upgraded to 10.10

CHEERS! :D

---

