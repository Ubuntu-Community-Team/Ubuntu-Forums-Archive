---
title: "Cant reboot wine"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by SwatKat on 2010-04-11
Hi,
I am unable to reboot wine after installing a program that requires it. When I run wineboot in the terminal, I get this
```
swat@swat-desktop:~$ wineboot
err:wineboot:ProcessRunKeys Error running cmd #0 (2)
```Does anyone know what that means? Any help is greatly appreciated. Thanks.

---

### Post by DexterLB on 2010-04-11
Which is that programme that requires it?
Generally if a windoze programme inside wine requires reboot you don't need to reboot it, just exit all wine programs and, to make absoulutely sure, execute ```
wineserver -k
``` and after that it'll look to the programme as a reboot and will be as effective.

Wineboot can't be run on an existing wine configuration, as it does something way different from reboot (creates new prefix)

---

### Post by SwatKat on 2010-04-11
Thanks, but its still not working. I am trying to install a software called isodisk to mount isos as virtual disks in windoze ( I have a dictionary cd which works only in windows and requires the original cd to be inserted). I did what you suggested, but it has still not rebooted, apparently. I have uploaded a screenshot. 

Nothing seems to happen when I type 
wineserver -k

This is what I get when I say wineboot again ,if its of any help
```
swat@swat-desktop:~$ wineboot
err:winedevice:ServiceMain driver L"ISODisk" failed to load
err:wineboot:ProcessRunKeys Error running cmd #0 (2)
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
```

---

### Post by DexterLB on 2010-04-11
You cannot mount iso's on wine - any software to do that simply won't work.
Use gmount-iso on ubuntu instead (sudo apt-get install gmount-iso) and wine will automatically recognize the CD and present it to it's programs too.

---

### Post by SwatKat on 2010-04-11
> **DexterLB said:**
> You cannot mount iso's on wine - any software to do that simply won't work.
Use gmount-iso on ubuntu instead (sudo apt-get install gmount-iso) and wine will automatically recognize the CD and present it to it's programs too.

Thats too bad. I use gmount iso all the time. But it didn't work with this one. The installation works fine. But you see, even after installation ,this software requires the cd to be mounted for it to work. Since the software is installed with wine, the iso also needs to be mounted on wine . The program does not recognize the image mounted with gmount iso. Looks like I have to find another dictionary software. 
Thanks for the help :).

---

### Post by J V on 2010-04-11
Look in the configuration at the drives menu, there is no such thing as mounting in wine...

Besides, plenty of windows applications have fixed exes that allow it to run without the disc (Unless there is actually data on there it needs which is very unlikely for modern applications)

---

### Post by DexterLB on 2010-04-11
Yeah, go to winecfg, to drives, and add a fake cdrom, for example F:, pointing to your mountpoint (where the iso is mounted with gmount-iso)

---

