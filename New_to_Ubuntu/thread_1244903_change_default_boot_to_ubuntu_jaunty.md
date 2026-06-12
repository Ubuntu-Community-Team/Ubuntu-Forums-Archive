---
title: "change default boot to ubuntu jaunty"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by tyler.mcg on 2009-08-20
whenever I start my computer it defaults to ubuntu studio booting up but I don't use it how can I switch the default OS to ubuntu jaunty instead?

---

### Post by zeroseven0183 on 2009-08-20
1. Open a terminal and type
```
gksudo gedit /boot/grub/menu.lst
```

2. Locate the line that shows
> default 03. Replace the 0 with the number on the startup list corresponding to the option you want, counting from 0. You should see the options when you scroll down a little bit more where it usually shows:
> 
title  Ubuntu 9.04, kernel 2.6.28-15-generic
....
title  Ubuntu Studio
....
For more information, you can check out this reference
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by warreno on 2009-08-20
This may be related to a [similar thread]("http://ubuntuforums.org/showthread.php?t=1241435") having to do with themes. [dixiedancer]("http://ubuntuforums.org/member.php?u=809532") got it in one. Check out the last page and try setting your desktop theme to "Human".

---

### Post by zeroseven0183 on 2009-08-20
Or maybe, you're referring to the Sessions when booting up?

You can change it in **System > Administration > Login Window > Default session**
Choose **GNOME**.

---

### Post by warreno on 2009-08-20
I thought it was sessions too, at first, but apparently that's not how Ubuntu Studio works; it appears to be largely a GNOME *theme*, not an actual different *session* a la KDE.

---

### Post by tyler.mcg on 2009-08-20
more about my problem:

when I boot my computer up it shows:

ubuntu studio
ubuntu studio (dev?)
other operating systems:
ubuntu jaunty (the one I use)

so I put default 2...

still no change... it says after 8 seconds it will automatically boot the highlighted OS. which despite the change  to menu.lst is still ubuntu studio. do I need to access the terminal before I load ubuntu jaunty? I also tried going to login window and changing it to GNOME. this has not made any difference in this matter.

so im thinking i should just get rid of ubuntu studio altogether since I don't really know how to use it. it being just a command line.

---

### Post by Paddy Landau on 2009-08-20
I think that Startup Manager is what you want.

Install startupmanager with Synaptic Package Manager.

---

### Post by LewRockwell on 2009-08-20
back-up your menu.lst file FIRST```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

then you can edit and experiment via:```
gksudo gedit /boot/grub/menu.lst
```

and if you goof the menu.lst file up you can boot the LiveCD, mount your Ubuntu partition, and copy the good menu.lst.backup back to menu.lst

Wheeeee......

.

---

### Post by mikechant on 2009-08-21
My guess is that your grub setup is looking at the menu.lst file in the Ubuntu Studio partition, not the one in the jaunty partition. In that case you just need to boot Ubuntu Studio and edit menu.lst as described above.
However, if this is the case it would be better to switch grub to running off the jaunty partition. 
Instructions can be found on this forum or someone will post them here if necessary. I'd do it but I don't have the time at this point.

---

### Post by tyler.mcg on 2009-08-21
> **mikechant said:**
> My guess is that your grub setup is looking at the menu.lst file in the Ubuntu Studio partition, not the one in the jaunty partition. In that case you just need to boot Ubuntu Studio and edit menu.lst as described above.
However, if this is the case it would be better to switch grub to running off the jaunty partition. 
Instructions can be found on this forum or someone will post them here if necessary. I'd do it but I don't have the time at this point.

Someone?

---

### Post by louieb on 2009-08-21
You must have installed Ubuntu Studio after installing Jaunty. 
Take a look at this thread. It explains how to get  grub back after installing windows but it will work for you - just pretend Ubuntu Studio is windows. What you want to do is replace Studios GRUB with Jauntys GRUB  in the hard drives MBR. 

[Fix Grub after Win install - catlett]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

> My guess is that your grub setup is looking at the menu.lst file in the Ubuntu Studio partition, not the one in the jaunty partition. Thats my guess too.

---

