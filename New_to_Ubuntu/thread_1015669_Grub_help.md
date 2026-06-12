---
title: "Grub help"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Frederyck on 2008-12-19
I have just started using linux, and I am still a long way away from grasping even the fundamentals. My system is a dual boot xp/ubuntu and it works fine with a separate hd for each OS. However, I would like grub to have XP as the standard boot choice instead of ubuntu as I am not the only user of the machine in question, and I don't want to burden the others with my experimentations into non-MS territory.

So if anyone has any tips on how I should do this, I would be grateful!

---

### Post by Existentialist on 2008-12-19
From within linux, open a the terminal. applications > accesories > terminal
Then you will wan to edit the grub menu file.  Type:

>gksudo gedit /boot/grub/menu.lst

At the bottom of this file there is a list of all boot options (ubuntu, ubuntu recovery mode, memtest, windows is last).  There is a line in here called default that is currently set to 0.  You will want to change this to be the number that windows is in the list of boot options.  On a default install this should be 3 (numbering starts from 0).

Hope this is clear enough; let me know if you need anything clarified.  If you want to post the output of:

>cat /boot/grub/menu.lst

I can show you what to change specifically.

---

### Post by overdrank on 2008-12-19
More info on the grub
[http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu](http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu)

---

### Post by talsemgeest on 2008-12-19
> **Existentialist said:**
> From within linux, open a the terminal. applications > accesories > terminal
Then you will wan to edit the grub menu file.  Type:

>sudo gedit /boot/grub/menu.lst

At the bottom of this file there is a list of all boot options (ubuntu, ubuntu recovery mode, memtest, windows is last).  There is a line in here called default that is currently set to 0.  You will want to change this to be the number that windows is in the list of boot options.  On a default install this should be 3 (numbering starts from 0).

Hope this is clear enough; let me know if you need anything clarified.  If you want to post the output of:

>cat /boot/grub/menu.lst

I can show you what to change specifically.
It would be easier to change the "0" to "savedefault", then boot into xp.

Also, please use ```
gksudo gedit /boot/grub/menu.lst
``` instead of ```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Michael.Godawski on 2008-12-19
just adding some info
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

> **Graphical sudo**

 You should **never** use normal sudo to start graphical applications as root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs.  gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo). 
Examples: 
gksudo gedit /etc/fstab

---

### Post by Existentialist on 2008-12-19
> **talsemgeest said:**
> 
Also, please use ```
gksudo gedit /boot/grub/menu.lst
``` instead of ```
sudo gedit /boot/grub/menu.lst
```

Fixed.  Sorry about that.  Bad habit of mine.

---

### Post by kwokyinc on 2008-12-19
Sorry, off topic a little bit.

Why is "gksudo" better than "sudo"?

---

### Post by talsemgeest on 2008-12-19
gksudo is safer for gui programs. It is what it was designed for and causes less problems.

---

### Post by muteXe on 2008-12-19
> **talsemgeest said:**
> gksudo is safer for gui programs. It is what it was designed for and causes less problems.

I've never been able to understand this.
Why is opening up a file using gedit classed as a gui program?

---

### Post by talsemgeest on 2008-12-19
Because gedit is a gui program. It can not be run in black and white in a terminal.

Graphical editor: ```
gksudo gedit /boot/grub/menu.lst
```

Command line editor: ```
sudo nano /boot/grub/menu.lst
```

---

### Post by muteXe on 2008-12-19
Ah right. I've always used vim to edit mine so i guess i'm okay with sudo.  
Ta mate :)

---

### Post by talsemgeest on 2008-12-19
> **muteXe said:**
> Ah right. I've always used vim to edit mine so i guess i'm okay with sudo.  
Ta mate :)
Yep, vim is fine with sudo.

---

