---
title: "How do i remove the start up logo?"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by the_jlx on 2010-08-15
How do i remove the start up logo so i actually see what is going on?

Oh another thing how do i Change the autofsck thing as it is stuck on doing a check every reboot wont change from program.

And before someone says edit menu.lst
by using sudo gedit /boot/grub/menu.lst
i can already tell you it is empty
I have no idea where the Grub thats is in use is even installed in my 3 hardisks

---

### Post by candtalan on 2010-08-15
> **the_jlx said:**
> How do i remove the start up logo so i actually see what is going on? 

One way for temporary visibility is to press e key when the grub menu appears, then edit the boot string to remove quiet and or splash.

hth

---

### Post by candtalan on 2010-08-15
another possibility is to install the app startup-manager and uncheck the splash box

---

### Post by Fludizz on 2010-08-15
have you tried the following command to find you menu.lst?
```
find / | grep menu.lst
```

There might also be configuration in /etc/default/grub, in this file look for GRUB_CMDLINE_LINUX_DEFAULT and remove "quiet splash" from the options. Then update your grub :)

regarding the filecheck... if it runs it every day, it might be that the filesystems are not cleanly unmounted on shutdown?

---

### Post by mcduck on 2010-08-15
> **the_jlx said:**
> How do i remove the start up logo so i actually see what is going on?

Oh another thing how do i Change the autofsck thing as it is stuck on doing a check every reboot wont change from program.

And before someone says edit menu.lst
by using sudo gedit /boot/grub/menu.lst
i can already tell you it is empty
I have no idea where the Grub thats is in use is even installed in my 3 hardisks

That would be because Ubuntu 10.04 (and later) use Grub2, which doesn't have a menu.lst file... ;)

Anyway, the file you are looking for is /etc/default/grub, just edit the "GRUB_CMDLINE_LINUX_DEFAULT"-line and remove "splash" from it, save the file and run "sudo update-grub".

(you can also remove the "quiet" if you want, that would give *very* verbose output during the boot...)

Also note that Plymouth has a text-based theme as well, so if it's otherwise working fine for you and you just want to get more info during the boot then using that might be the way to go.

---

### Post by the_jlx on 2010-08-15
Mkays gonna test the startupmanager now as for the check it is the program autofsck that does it somehow its setting is stored permanently after i once choose arrange checks now

---

### Post by the_jlx on 2010-08-15
I higly doubt i am even using Ubuntus Grub anymore.
Sigh i guess i need to hunt it down lol
startupmanager did not work

Edit:
Mkays edited all GRUB_CMDLINE_LINUX_DEFAULT to just "" lets see what a update grub and sudo reboot does lol

---

### Post by the_jlx on 2010-08-15
Ok only change is i got a pretty blinking line for about 5 seconds...
:(:(
HA found it its dreamlinux grub still being around.
Fixed now just the autofsck thing

---

### Post by the_jlx on 2010-08-15
> **mcduck said:**
> that would be because ubuntu 10.04 (and later) use grub2, which doesn't have a menu.lst file... ;)

anyway, the file you are looking for is /etc/default/grub, just edit the "grub_cmdline_linux_default"-line and remove "splash" from it, save the file and run "sudo update-grub".

(you can also remove the "quiet" if you want, that would give *very* verbose output during the boot...)

also note that plymouth has a text-based theme as well, so if it's otherwise working fine for you and you just want to get more info during the boot then using that might be the way to go.

solved

---

