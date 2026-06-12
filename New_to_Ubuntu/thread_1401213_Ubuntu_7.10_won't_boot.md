---
title: "Ubuntu 7.10 won't boot"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by DeeDez on 2010-02-07
I've just install ubuntu7.10 to a friend's laptop via livecd.  The install went fine only after the reboot is when system wouldn't start up.  I can push esc and get the grub options but it only boots in recovery mode.  Any ideas?

---

### Post by NightwishFan on 2010-02-07
If it is not an imposition perhaps you should use a newer Ubuntu such as 8.04 LTS or 9.10. 7.10 is outdated now.

---

### Post by DeeDez on 2010-02-07
> **NightwishFan said:**
> If it is not an imposition perhaps you should use a newer Ubuntu such as 8.04 LTS or 9.10. 7.10 is outdated now.

Yeah, its the only disc I have at the moment.

---

### Post by NightwishFan on 2010-02-07
Well, when you get to the menu with the recovery mode options, highlight the standard Ubuntu boot option, press "e". At the list of commands highlight the kernel line and press "e" again. Add this on the end:
```
acpi=off
```
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by howefield on 2010-02-07
> **DeeDez said:**
> Yeah, its the only disc I have at the moment.

Just so that you know, 7.10 is no longer supported with security updates. Poor choice, even if it is the only disk that you have.

---

### Post by DeeDez on 2010-02-07
> **NightwishFan said:**
> Well, when you get to the menu with the recovery mode options, highlight the standard Ubuntu boot option, press "e". At the list of commands highlight the kernel line and press "e" again. Add this on the end:
```
acpi=off
```[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Hey, that worked, thanks!  What did I actually do?  (for my knowledge)

---

### Post by NightwishFan on 2010-02-07
It turns off some sort of power management I believe. That is only temporary, it will revert the next boot. To make the change permanent, press alt+f2 and type:
```
gksudo gedit /boot/grub/menu.lst
```
Now find the line that looks something like this:
> kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro quiet splash
Add acpi=off at the end of the line and save the file.

Do not edit anything else, and for safety you should always make a backup when editing files.

---

