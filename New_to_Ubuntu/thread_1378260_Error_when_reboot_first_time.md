---
title: "Error when reboot first time"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by lyltln on 2010-01-11
Hello people

Im new to all this Ubuntu thing. I did a format on my laptop and install Ubuntu. Works very nice , but when i reboot i get msg Can`t find NTLDR press ctrl+ alt +del. Any ideas how to fix this. Thank you

---

### Post by Miljet on 2010-01-11
I'm afraid that we will need more information to be able to help you.

What version Ubuntu did you install?

You said that you did a format. Did you install as dual-boot with Windows? Or did you install Ubuntu to the entire disk? Or did you install Ubuntu from within Windows using WUBI?

The NTLDR file that it is complaining about not finding is the loader file for Windows.

---

### Post by kenox on 2010-01-11
Did you install from the live cd? And now you cant reboot to the newly installed system? 
The live cd boots to a completely different system... and only on reboot will the newly installed system be used (although both look the same)..

Do you have more than one hard disk?
Did you get any error during install? Some "GRUB" or Bootloader.... stuff?

As Miljet said NTLDR is the Windows Bootloader.

---

### Post by anand_30 on 2010-01-11
> **lyltln said:**
> Hello people

Im new to all this Ubuntu thing. I did a format on my laptop and install Ubuntu. Works very nice , but when i reboot i get msg Can`t find NTLDR press ctrl+ alt +del. Any ideas how to fix this. Thank you
I am also new to this but I also encountered this type of error I don't know if this will be useful to you!! 
Few days ago I accidentally deleted NTLDR and NTDETECT.com(hidden files) files present in Windows C drive using ubuntu.I solved it by copying these files from windows installation CD(present i folder i386) into C drive using ubuntu.

---

### Post by lyltln on 2010-01-11
thanks for  anwser .innstaled 9.10 version from cd. I format again and it works.(the install process was different now , so i dont get the error msg) The msg is for windows yes. 


Do you know any way to adjust the monitor screen. its a little dark:)

---

