---
title: "my xorg log"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by Someone uk on 2010-09-11
i keep getting blank screens in ubuntu
> (WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

can anyone suggest a way i can fix this?

i have a nvidia 8600m gt
driver version 256.53 (i have had the same problem with earlier drivers)
ubuntu 10.04 64bit

---

### Post by cavh on 2010-09-11
If you can get to a GNOME desktop, can you click on Administration, Hardware Drivers and follow the prompts from there?

---

### Post by Someone uk on 2010-09-11
i have already tried deactivating them and reactivating them but i still had the same problem when i did

---

### Post by Rubi1200 on 2010-09-11
Does booting with the nomodeset parameter make any difference?

---

### Post by JohnHeikkila on 2010-09-11
When you boot, press Esc or hold Shift to get to the GRUB menu. There select a recovery mode, and select "root console" when the recovery menu starts. It may take a while.
When you're in the console, do "sudo dkpg-reconfigure xserver-xorg" and then "sudo nvidia-xconfg". After this, reboot.

---

### Post by Someone uk on 2010-09-12
i seem to get this now:
(WW) Sep 12 12:22:59 NVIDIA(0): WAIT (2, 6, 0x8000, 0xdfff2fff, 0x00002c8c)

---

### Post by JohnHeikkila on 2010-09-12
(WW) means Warning, so as long as it doesn't return any errors and you can see the screen, you'll be fine.
When it tells you the "low graphics mode", there should be an option to start in a console mode. Select that, and try those commands I told you the last post, then type "sudo killall Xorg" and this should restart Xorg.

---

### Post by Someone uk on 2010-09-12
well it's kinda back to square 1 with me because i still get blank screens but no report in the Xorg log now :(

---

### Post by Someone uk on 2010-09-12
> **Someone uk said:**
> i seem to get this now:
(WW) Sep 12 12:22:59 NVIDIA(0): WAIT (2, 6, 0x8000, 0xdfff2fff, 0x00002c8c)

(WW) Sep 12 23:03:55 NVIDIA(0): WAIT (2, 6, 0x8000, 0xdfff2fff, 0x0000ca30)
just got this
this is the last entry i had in my xorg.0.old and it was the last entry then as well so i assume it is somewhat related to my problem

---

### Post by absolutezero1287 on 2010-09-12
I have a related issue. I get the following error every boot. 
```

$ cat /var/log/Xorg.0.log | grep EE
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

```

I had the same error when I was using archlinux. I had to get the install script from the nvidia website. It blacklisted certain modules. If I recall correctly it blacklisted the nouveau module.

---

