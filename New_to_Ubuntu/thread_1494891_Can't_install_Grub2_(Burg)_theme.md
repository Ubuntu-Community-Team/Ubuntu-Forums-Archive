---
title: "Can't install Grub2 (Burg) theme"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by steigerjb on 2010-05-27
I am trying to install [http://shafin.deviantart.com/#/d2lcgm0]("http://shafin.deviantart.com/#/d2lcgm0")

I have following the person's instructions:

> **Here is how to instal BURG:**
Add ppa:bean123ch/burg to software sources
sudo apt-get install burg burg-themes

**To use this theme:**
Extract the tarball to /boot/burg/themes
sudo update-burg
While booting in the grub screen, press 't'
In the theme selection menu, select radiance or Radiance Text.

This is the Radiance Text version, I recommend editing /boot/burg/burg.cfg and making the menu entry names short for better presentation

I got as far as "While booting in the grub screen, press 't'". I am not sure what they mean by "while booting in the grub screen", but I pressed 't' after the dell boot screen and the grub2 screen (when it had the flashing _ thing.) Nothing happened. It just booted to the same old grub2 screen. I tried a couple times. Even the last time I pressed t like 20 time trying to get into the theme selection menu before the grub2 screen showed.

what am I doing wrong?

---

### Post by steigerjb on 2010-06-01
nobody knows?

---

### Post by Ozymandias_117 on 2010-06-01
I'm about to reboot to test, but I bet you need to hold shift while booting to get to the GRUB menu, THEN press 't'

---

### Post by steigerjb on 2010-06-04
> **Ozymandias_117 said:**
> I'm about to reboot to test, but I bet you need to hold shift while booting to get to the GRUB menu, THEN press 't'

shift didnt do anything for me

---

### Post by gecka on 2010-12-06
same problem here, t does nothing

---

### Post by Jechem on 2011-01-21
try F2 key

---

