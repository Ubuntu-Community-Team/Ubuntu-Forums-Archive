---
title: "Lubuntu splash screen gone update."
date: 2010-10-29
forum: New to Ubuntu
---

### Post by John Phang on 2010-10-29
Lately i've updated my lubuntu 10.10 after a restart my splash screen gone, but why?

can anyone help me please. :)

---

### Post by Gaygerbil on 2010-10-30
Bump I get the same thing with Lubuntu and Ubuntu Netbook remix on my netbook, after like a week or two of usage the splash screen magically disappears on boot.

It still shows however on shutdown. Anyone else getting this? And anyone know why this would happen?

---

### Post by mr_luksom on 2010-11-01
I'm pretty sure you can toggle it by hitting ESC when booting/shutting down.

If you are seeing text instead of a splash, then that will work.

---

### Post by John Phang on 2010-11-21
Sorry to reply late, i've tried what you said by hitting esc while booting/shutting but it won't work, do you have any other way to fix it please?

---

### Post by cavalier911 on 2010-11-21
Open /boot/grub/grub.cfg with a text editor.
Scroll down to where you see something similar to this:
```
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos9)'
	search --no-floppy --fs-uuid --set 1c4adc10-a208-4373-b842-9851a8421da7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1c4adc10-a208-4373-b842-9851a8421da7 ro  quiet **_splash_**
	initrd	/boot/initrd.img-2.6.35-22-generic
}
```

Verify **splash** is there at the end of linux line.

---

### Post by John Phang on 2010-11-22
Pardon, but which is the text editor for lubuntu 10.10?

---

### Post by Cpierce on 2010-11-22
I believe it is Leafpad

---

### Post by John Phang on 2010-11-24
I've check my /boot/grub/grub.cfg nd the **splash** word is there if i'm not mistaken.. and i'm so sorry to reply you late... here is the file i attach, i attach this file because i scare i didn't check well... Please help me to check it for the second time please...

PS: I'm so sorry with my english.. and i would like to thank you for helping me out... ;)

---

