---
title: "Normal Booting failed and gives GRUB screen"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by nns2006 on 2009-11-14
Hi,
yesterday night I was very happy as after some updates my computer finally shut-down properly. My happiness vanishes in the morning when I got GRUB screen while booting Ubuntu.

Here is the full story... yesterday night I updated my computer for Ubuntu 9.10 updates.I shut it down after updates and in the morning when i started my computer I opted for Ubuntu when choice screen come up. Then i got the grub screen with following text(reproducing exactly)
> GRUB4DOS 0.4.3 2008-07-08, Memory: 636K / 2037M, CodeEnd: 0x41a38
[minimal Bash like line editing is supported.(some  more text for commands)........]
grub>


Additonal info- I am using DEll Vostro 1500 dual booted with Windows XP and Ubuntu 9.10 (upgraded through 8.04(installed by wubi installer))

I am posting this thread from my room-mates laptop.
What should I do?

---

### Post by drs305 on 2009-11-14
Here is a link to booting from the grub command line.
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

Use the tab key to help complete the lines.
Basically, you will enter  lines:
set root=(sdXY)
linux /boot/vmlin>tab...  root=/dev/sdXY
initrd /boot/initrd>tab...
boot

If you are able to boot into your Ubuntu you will need to try to fix GRUB 2. Start with "sudo grub-install /dev/sdX".

---

### Post by nns2006 on 2009-11-14
there is no commands like > ls and > set in it. It gives error 27: Unrecognised command. So I am halted at start itself following the link.

---

### Post by SuaSwe on 2009-11-14
Do you get a list of commands upon pressing Tab? Also, are you still able to boot OK using a LiveCD?

Edit:
Also, this thread contains tips that may help:

[http://ubuntuforums.org/showthread.php?p=8312568](http://ubuntuforums.org/showthread.php?p=8312568)

---

### Post by nns2006 on 2009-11-14
Yes i got the commands upon pressing Tab and I can boot from Live CD

---

### Post by SuaSwe on 2009-11-14
See my edit above, re: another post that might be helpful. I'm just checking it out now as well. :)

---

### Post by SuaSwe on 2009-11-14
I'd read the whole thread through before making any changes as there's some mistyping of commands and such here and there, but I get the impression it solved the problem in the end!

To my n00b-to-intermediate eyes, it looks as though your menu.lst may have become corrupt. Have you checked it for wonky-looking entries by accessing it via the LiveCD (/boot/grub/menu.lst)?

---

### Post by nns2006 on 2009-11-14
> **SuaSwe said:**
> See my edit above, re: another post that might be helpful. I'm just checking it out now as well. :)

That post also start with command > set and> ls. Which I am not getting in my command list. 
Still halted

---

### Post by SuaSwe on 2009-11-14
Have you taken a look at /boot/grub/menu.lst via the LiveCD?

---

### Post by nns2006 on 2009-11-14
In the /boot directory I am not finding grub using Live CD.

---

### Post by SuaSwe on 2009-11-14
Can you see and access your original installation from the live environment? The GRUB directory should be in a mountable partition, usually root (may not be labelled as such). 

E.g. when I boot into a LiveCD, I have two mountable partitions, one of 10GB (root) and one of 60GB (home). My menu.lst is in the /boot/grub/ directory of the 10GB partition.

---

### Post by SuaSwe on 2009-11-14
Hmm, just noticed the "GRUB4DOS" bit of the error message you're getting - have to admit I'm not familiar with this bootloader at all, and config files and such may well differ from GRUB. Maybe this could help though:

[http://diddy.boot-land.net/grub4dos/files/commands.htm](http://diddy.boot-land.net/grub4dos/files/commands.htm)

---

### Post by nns2006 on 2009-11-15
I am not able to figured out what to do following the link. Nothing seems to be working for me today.

---

### Post by SuaSwe on 2009-11-15
I'm having one of those days myself so you're not alone!

It appears that you're not using GRUB but Grub4dos, e.g. an alternative bootloader. If this is the case my recommendation would be to reinstall good old-fashioned GRUB - to my knowledge this can be done via the GRUB prompt you keep ending up in, but then if that prompt belongs to a different type of GRUB loader all bets are off regarding what commands to use. 

What commands *do* you have at this prompt, if none of the regular ones?

---

### Post by garvinrick4 on 2009-11-15
grub4dos is the Windows Grub and it is used in a WUBI install

WUBI attaches itself to the Dos grub and does not use Grub legacy
or Grub2.

If new install just uninstall in windows or you can even use Add or
remove programs in Windows. 

It will put the grub menu back to original then reload the disc and
choose Wubi install pick size of disc to use. Your Password and takes about 12 minutes to install.

It will be in folder right next to Users in C: in Windows.

In Ubuntu it will be /host.    See ya

---

### Post by nns2006 on 2009-11-15
Thank you for your help.
I did installation of 9.04 (with 9.10 wireless problem prevent me doing it ).Now I can see that Ubuntu has made a backup file called called "root.disk" and "swap.disk" . Is this files contains the files of previous installation? If yes how can I access it?


*There were many nagging issues with my lappy which prompted me to install a fresh version.*

---

