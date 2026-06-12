---
title: "How to apply settings?"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by RadhikaM on 2011-08-10
I'm attempting to change the brightness of my screen, but when I press Overview or Close, it goes back to the original settings. What do I press to make the settings stay?

---

### Post by madjr on 2011-08-10
> **RadhikaM said:**
> I'm attempting to change the brightness of my screen, but when I press Overview or Close, it goes back to the original settings. What do I press to make the settings stay?

is this a laptop or desktop?

and what version of xubuntu?

---

### Post by RadhikaM on 2011-08-10
> **madjr said:**
> is this a laptop or desktop?

and what version of xubuntu?

It's a laptop, and the latest version? Is that 11.04?

---

### Post by Toz on 2011-08-10
> **RadhikaM said:**
> I'm attempting to change the brightness of my screen, but when I press Overview or Close, it goes back to the original settings. What do I press to make the settings stay?

If you're talking about the Brightness Setting in the Power Manager module, then that setting has never worked for me either. I'm guessing your Fn brightness keys aren't working. What make/model of laptop do you have?

Have you tried any kernel parameters (see: [https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")), specifically the parameters:
[LIST]
[*]acpi_osi=Linux
[*]acpi_osi=
[*]acpi_osi=\"Linux\"
[*]acpi_backlight=vendor
[*]acpi_osi=Linux acpi_backlight=vendor
[/LIST]

---

### Post by RadhikaM on 2011-08-10
> **Toz said:**
> If you're talking about the Brightness Setting in the Power Manager module, then that setting has never worked for me either. I'm guessing your Fn brightness keys aren't working. What make/model of laptop do you have?

Have you tried any kernel parameters (see: [https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2#Editing the GRUB 2 Menu During Boot")), specifically the parameters:
[LIST]
[*]acpi_osi=Linux
[*]acpi_osi=
[*]acpi_osi=\"Linux\"
[*]acpi_backlight=vendor
[*]acpi_osi=Linux acpi_backlight=vendor
[/LIST]


I have a Compaq Presario CQ60, and the keys aren't working. I'll try the parameters when I reboot.

---

### Post by madjr on 2011-08-10
> **RadhikaM said:**
> I have a Compaq Presario CQ60, and the keys aren't working. I'll try the parameters when I reboot.

lots of models with the CQ60.

do you know what video card(s) does it have?

---

