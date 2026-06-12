---
title: "GRUB menu question"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by Carolla on 2009-06-26
When I boot Ubuntu 9.04 and the GRUB menu comes up, I press "ESC" and get no response at all. Can that be fixed? I can use "del" to get into the BIOS, but "ESC" doesn't get into that menu. Thanks for any help.

---

### Post by Michael.Godawski on 2009-06-26
hi, 

> If you need to get into the grub menu to modify boot options or choose a different kernel, you need to press 'ESC' just after it starts.
 By default you have to press 'ESC' within three seconds. If you want to increase this time limit, you can edit the grub configuration file /boot/grub/**menu.lst**, increasing the seconds in the TIMEOUT part.
Alternatively you could have the menu always come up at boot time. To do this, comment out 'hiddenmenu' by inserting a # at the beginning of the line.

Worth a try. I mean the hiddenmenu option. 

You can edit the menu.lst with this command:

```
gksudo gedit /boot/grub/menu.lst
```

But make a backup of the menu.lst first. 
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_back
```

---

### Post by Carolla on 2009-06-26
Thanks we set it up with the option to display the menu on start up (for now) and to give it a bit more time. We'll see if that works when we need it again.

---

### Post by mikewhatever on 2009-06-26
> **Carolla said:**
> When I boot Ubuntu 9.04 and the GRUB menu comes up, I press "ESC" and get no response at all. Can that be fixed? I can use "del" to get into the BIOS, but "ESC" doesn't get into that menu. Thanks for any help.

What kind of respond do you expect? Had the menu been hidden, pressing Esc would have shown it, but nothing else.

---

### Post by pissedoffdude on 2009-06-26
> **Carolla said:**
> When I boot Ubuntu 9.04 and the GRUB menu comes up, I press "ESC" and get no response at all. Can that be fixed? I can use "del" to get into the BIOS, but "ESC" doesn't get into that menu. Thanks for any help.

As the second post suggested, try the hidemenu option.  Are you using a USB keyboard by any chance?  If you are, usb keyboard support may be disabled in the BIOS.

---

### Post by Done_Fishin on 2009-07-05
pressing escape just stops the countdown

after that you need to press "e" to get into and edit grub.
you may need to scroll down with the arrow keys when you see the listing. One site I saw suggested (for a much older version of Ubuntu) that you required to press "e" again for editing but I haven't found that in 9.10 - just move to the required position & line then type in your extra command.

On the 9.10 that I am editing right now, after pressing "e" once this shows 

> GNU GRUB Version 1.96
```
set root=(hd1/1)
searcg --fs-uuid --set 894ec0c8-a9d4-4d76-8bf0-d2f9ef97db3f
linux /boot/vmlinuz-2.6.30-8-generic root=UUID=894ec0c8-a9d4-4d76-8bf0-d2f9ef97db3f ro  quiet splash
initrd /boot/initrd.img-2.6.30-8-generic


```
Minimum Emacs-like screen editing is supported. TAB lists completions. Press Ctrl-x to boot, Ctrl-c for a command line or esc to return menu



follow the instructions on screen 

point to note that it's said that one needs to edit (after booting) /boot/grub/menu.lst in order to make changes permanent, however on my version (Karmic UNR 9.10 version Alpha 2) I have no menu.lst and I am searching around trying to find where the grub is stored. The only file I have found so far is grub.cfg but it says NOT to edit the file

---

