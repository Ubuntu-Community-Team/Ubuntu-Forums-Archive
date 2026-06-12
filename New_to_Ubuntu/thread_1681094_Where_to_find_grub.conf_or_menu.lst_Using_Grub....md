---
title: "Where to find grub.conf or menu.lst? Using Grub... :/"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by newn on 2011-02-03
The final step before reboot will be to tell your boot loader to use the  new kernel. If your distribution uses grub (which is very likely) you  need to edit the file */boot/grub/menu.lst (or /boot/grub/grub.conf)* so it looks like this (**do not copy+paste this**, it has to be changed according to your Linux installation!):

This is a step from a tutorial. Where do I find these files, if they are not there? I've got grub.cfg though, but there's nothing like what I need to edit:

> default         0 timeout         1  title           Debian GNU/Linux, RT Kernel root            (hd0,1) kernel          /boot/vmlinuz-2.6.26.8-rt16 root=/dev/ram0 real_root=/dev/sda1 initrd          /boot/initrd.img-2.6.26.8-rt16  title           Debian GNU/Linux, kernel 2.6.24.2 root            (hd0,1) kernel          /boot/vmlinuz-2.6.24.2 root=/dev/ram0 real_root=/dev/sda1 initrd          /boot/initrd.img-2.6.24.2

And my file doesn't contain anything like that, except initrd, which looks completely different.
Id doesn't contain kernel, nor title, nor root...
What can I do? :/

Using Ubuntu 9, x64.

---

### Post by TechWiz2100 on 2011-02-03
You are probably using Grub2 which eliminated those files without telling the poor souls who aren't subscribed to their newsletter lol

Now its something along the lines of a config file for every single boot option as well as the main config

---

### Post by newn on 2011-02-03
Could I receive some help configuring it? I could upload the file, but is there any security risks? There's some codes in there...

---

### Post by Wobblybob on 2011-02-03
I'm no expert so have a look at this link [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1195275[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275") good luck

---

### Post by drs305 on 2011-02-03
If you are using Grub2, when a new kernel is added by normal means the menu is automatically updated after the kernel is installed. It's part of the post-install script. Otherwise, the user can update the G2 menu to reflect  changes to various system files by running:
```
sudo update-grub
```

If you want to see what menu choices will display when you reboot, you can run this command:
```
grep menuentry /boot/grub/grub.cfg
``` 

My signature links contain various guides about Grub2. "Basics" is an intro on this site, "GRUB2" is the Ubuntu community doc. "Tasks" cover the most common changes.

---

### Post by kimberlite on 2011-02-03
Grub customizer could be a good choice, if you would not prefer to read manual pages :-)
Recommended alternatives: [ubuntuguide.net]("http://ubuntuguide.net/new-grub-customizer-with-default-osbackgroundmenu-colorsresolution-support") 
and a little bit threating [one here.]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by newn on 2011-02-03
I should've mentioned, that I only have console access trough PuTTy. :/

And there are those new options, but how do I choose which ones to use on boot?

---

### Post by mlentink on 2011-02-03
Uh,

Just a question: The OP is using 9.xx, which afaik is pre GRUB2. So wouldn't he be better served with pointers to */boot/grub/menu.lst? *
I've been on GRUB2 for quite a while, so I don have a sample available[I].
[/I]

---

### Post by CharlesA on 2011-02-03
> **mlentink said:**
> Uh,

Just a question: The OP is using 9.xx, which afaik is pre GRUB2. So wouldn't he be better served with pointers to */boot/grub/menu.lst? *
I've been on GRUB2 for quite a while, so I don have a sample available[I].
[/I]
Grub2 doesn't use menu.lst.

You can edit the different options in /etc/default/grub

Then run update-grub.

---

### Post by newn on 2011-02-04
Configured everything, it worked... Except my system won't boot now. About that, I'll create a new thread.
Thanks.

---

### Post by TechWiz2100 on 2011-02-04
lol I wouldn't call an unbooting system the result of something that "worked"

---

### Post by Omar.Fayyad on 2011-03-26
I couldn't find neither "grub.cfg" nor "menu.lst" under /boot/grub/

What can i do to solve this issue..

Please help...

---

### Post by drs305 on 2011-03-26
> **Omar.Fayyad said:**
> I couldn't find neither "grub.cfg" nor "menu.lst" under /boot/grub/

What can i do to solve this issue..

Please help...

Omar,

I've posted what you need to do in your other thread, where you provided the RESULTS.txt information which is helpful in resolving this issue.
[http://ubuntuforums.org/showthread.php?p=9863812#post9863812]("http://ubuntuforums.org/showthread.php?p=9863812#post9863812")

---

