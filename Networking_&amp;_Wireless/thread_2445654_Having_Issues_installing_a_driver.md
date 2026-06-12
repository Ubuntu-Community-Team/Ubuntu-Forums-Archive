---
title: "Having Issues installing a driver"
date: 2020-06-17
forum: Networking &amp; Wireless
---

### Post by leflea on 2020-06-17
Hello! I tried to follow the instructions in the stickied post titled "How to install a driver for the broadcom series of PCI wireless cards" and ran into some difficulties,

When I type #sudo apt-get install bcmwl-kernel-source

It says #E: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2296 (apt)
N: Be aware that removing the lock file is not a solution and may break your system.
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?


Would anyone be able to help me? I am currently using my phone as a personal hotspot for internet but that won't be too sustainable.

ISSUE IS SOLVED, I DONT KNOW HOW TO EDIT THE TITLE SO ITLL SAY THAT

---

### Post by jeremy31 on 2020-06-17
You might need to reboot and try installing again, please post results from terminal for ```
lspci -nnk | grep -iA3 net
```

---

### Post by leflea on 2020-06-17
I finally fixed it, thank god, but I'll outline everything I did incase someone else it experiencing this error.

After receiving the message I posted about I rebooted my computer and it went away but said something about needing a CDROM

I went to the "Software and Updates" application and unchecked the box under "Installable from CDROM" then repeated the process and thankfully it worked :)

Thank you everyone! I had to piece this together with about 40 other forums posts haha, hopefully someone can get something out of this one.

---

