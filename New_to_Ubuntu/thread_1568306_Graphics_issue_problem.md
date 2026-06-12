---
title: "Graphics issue problem"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by nikhilnair12 on 2010-09-05
I have insalled ubuntu 10.04 64 bit version. I am using Acer aspire 5738 laptop. Upon installation all visual effects were working fine. But the brightness key(from the keyboard fn+ arrow key) doesnt appear to change the screen brightness. So i edited grub after a lot of search and i resolved the problem. But now i couldnt enable the visual effects (Normal and Extra). What to do?

---

### Post by jtarin on 2010-09-05
> So i edited grub after a lot of search and i resolved the problem. It could be worthwhile to include exactly what you did?

---

### Post by nikhilnair12 on 2010-09-05
sudo gedit /etc/default/grub
changed bottom line to this
GRUB_CMDLINE_LINUX="nomodeset acpi_backlight=vendor"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
 save and sudo update-grub
I then rebooted.

---

### Post by jtarin on 2010-09-05
Well to be honest your not pushing the biggest 3D card available in that laptop and that model is known for exactly this problem. As you can see by editing Grub that is a problem in kernel configuration when try to achieve a balance between you "video card/kernel/and your desires to have the most effects you can have". There seem to be more ability in Kubuntu to adjust these effect....not 100% sure as I usually turn them off as they get in my way.The method you have used for brightness is the most popular now, but now you have to balance that against effects full-on.

---

### Post by nikhilnair12 on 2010-09-07
I m ready to sacrifice the brightness key function but i need my visual effects to work properly. Can i do anything on that

---

### Post by jtarin on 2010-09-07
> **nikhilnair12 said:**
> I m ready to sacrifice the brightness key function but i need my visual effects to work properly. Can i do anything on thatWhat visual effects specifically are you referring to? I'm thinking Compiz!

---

