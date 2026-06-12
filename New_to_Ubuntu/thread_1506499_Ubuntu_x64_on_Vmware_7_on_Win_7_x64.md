---
title: "Ubuntu x64 on Vmware 7 on Win 7 x64"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by wajed on 2010-06-10
I have just installed VMware on my win 7 OS.

I downloaded Ubunutu 10 two weeks again, and now I wanted to give it a try, I followed a tutorial, but this message hasn`t popped up in the tutorial, so what do I do? Will anything happen to the current OS if I press yes?

[IMG]http://img99.imageshack.us/img99/7049/ubuntupartitiondisks.jpg[/IMG]

---

### Post by nhasian on 2010-06-10
if you are running the ubuntu install from inside of vmware then it will not affect your real hard disks or partitions.  it will only have access to the disk image you gave it in vmware.

---

### Post by wajed on 2010-06-10
Thank you :)

---

### Post by wajed on 2010-06-10
Actually that passed fine, but I faced one another problem.
I was following a vid tutorial, but now I find myself diverging from the vid, here it is: [http://www.youtube.com/watch?v=ZugFapj1dWo](http://www.youtube.com/watch?v=ZugFapj1dWo)

Anyway, that`s the window I`m facing, what should I do? I thought installation process was GUI!
[IMG]http://img199.imageshack.us/img199/6011/38465106.jpg[/IMG]


PS: I logged in, but I don`t know what to do. I tried to power off the virtual image and turn it on again, but it took me automatically there again.

---

### Post by RiceMonster on 2010-06-10
> **wajed said:**
> Actually that passed fine, but I faced one another problem.
I was following a vid tutorial, but now I find myself diverging from the vid, here it is: [http://www.youtube.com/watch?v=ZugFapj1dWo](http://www.youtube.com/watch?v=ZugFapj1dWo)

Anyway, that`s the window I`m facing, what should I do? I thought installation process was GUI!
[IMG]http://img199.imageshack.us/img199/6011/38465106.jpg[/IMG]


PS: I logged in, but I don`t know what to do. I tried to power off the virtual image and turn it on again, but it took me automatically there again.

Did you install Ubuntu server?

---

### Post by sourchier on 2010-06-10
What happen when you type in the words startx after logging in? Any messages?

---

### Post by wajed on 2010-06-10
that`s the name of the file, ubuntustudio-10.04-alternate-amd64.iso
There was a torrent like on the ubuntu website, and I used it.
 
Actually I have Core 2 Duo (from Intel,) and it`s mentioned on the site that this will work for Core 2.
 
> [http://cdimage.ubuntu.com/ubuntustudio/releases/10.04/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/10.04/release/)[URL="http://cdimage.ubuntu.com/ubuntustudio/releases/10.04/release/"]
[/URL]

---

### Post by wajed on 2010-06-10
>  What happen when you type in the words startx after logging in? Any messages?

I got this:-
"The program startx is currently not installed..."
 
 
then I used sudo apt-get install xinit, and I got this at last line:-
"E: Couldn`t find package xinit"

---

### Post by nhasian on 2010-06-10
please give us the output of the following command:

```
apt-cache policy ubuntu-desktop gdm
```

that will tell us if you have the gdm and gnome installed.  if it isn't (ie you installed ubuntu server by mistake) then you can easily fix it with the following command:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by wajed on 2010-06-10
for first command:-
"
Installed: (none)
...
... 
"
 
For the second command, same thing: package not found. 
 
And to use time, I also tried to make a new "virtual machine" and here is how it`s going:-
[IMG]http://img190.imageshack.us/img190/8285/72457306.jpg[/IMG]
I added this as it may show I`m installing something wrong (Although I don`t have control to install anything, as all of this is going automatically.)
 
EDIT: A screen came and it`s gone away now but there was something like "Installing VMware tools now... you can use commands, depending on what version you have (during the installation/setup).... the GUI will show after the VMWare tools is/are installed.
I prefered not to try to enter any commands and I left VMware for a bit, then I came back to find he screen like the one of the first "virtual machine":-
[IMG]http://img199.imageshack.us/img199/6011/38465106.jpg[/IMG]
 
I`ve logged in, what should I do next?
 
 
 
 
EDIT2:-
I`ve tried the last command ("sudo apt-get install ubuntu-desktop",) and it worked, and I got a message telling me 2,274MBs are needed, I answered "yes". and now it`s downloading some files, Is it gonna download the whole 2,274MB? It`s too slow, can I download it myself and install it?

---

