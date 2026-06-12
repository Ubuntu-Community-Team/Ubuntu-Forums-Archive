---
title: "Bootloader"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by Neutralinos on 2011-08-06
So I'm dual-booting 11.04 and Windows 7. I installed ubuntu mainly as a way to mess with my friends and don't plan on booting it that often. 
When I turn on my laptop I have to choose what I want to boot. I'd like to have it set up so that it just boots windows automatically unless I press something at a certain time and then get a prompt. 

So far from Google I've learned that I need to do something to Grub, but as this forum suggests I have no idea how to do so. Any help would be greatly appreciated!

Thanks

---

### Post by drs305 on 2011-08-06
Neutralinos,

Welcome to Ubuntu and the Ubuntu forums.  :-)

For changing Grub2 settings, Grub Customizer is a great GUI app that can tweak a lot of settings. Click on the 'Customizer' link in my signature.

If you would rather manually edit the Grub configuration files, you can click on "Tasks" (but I'd recommend Customizer).

---

### Post by Basher101 on 2011-08-06
hello, setting up GRUB and what it boots by default is really easy!
Press Alt+F2 and type: ```
gksudo gedit /etc/default/grub
``` you will be prompted for a password, just type it in. then a text editor will open. It should look like this ```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
Edit the line ```
GRUB_DEFAULT=0
``` to ```
GRUB_DEFAULT=4
```

note: the default counts from 0. Linux installs with total 4 entries, making windows the 5th. so 4 = 5th entry. If you update your kernel, then it will add the entry "Previous linux versions" and windows will be the 6th entry. You will then need to set ```
GRUB_DEFAULT=5
``` and so on.

---

### Post by Neutralinos on 2011-08-07
I got it working wonderfully. Thanks for the help :)

---

### Post by Basher101 on 2011-08-07
No problem^^ now the last thing to do is mark your thread as [SOLVED]

---

### Post by amjjawad on 2011-08-07
Glad it worked for you.

Please mark this thread as SOLVED :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

