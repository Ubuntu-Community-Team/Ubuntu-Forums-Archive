---
title: "How do I reinstall nvidia drivers after package upgrade 10.04"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by wapfu on 2010-06-29
I have just upgraded some driver packages and lost my display settings on 10.04.
All was working well untill the last package updates.
I can remember seeing some nvidia packages in the new update.
I can get only emergency resolution from the repair mode.
What i get from a standard start is a very large top left display of very little resolution.
I have removed the noveau package.
start x does nothing
and  nvidia-xconfig does not work.
From terminal - what do i need to enter to get nvidia drivers working again.
I cannot even adjust the nvidia display.

Thanks
Bill

---

### Post by cariboo on 2010-06-29
> **wapfu said:**
> I have just upgraded some driver packages and lost my display settings on 10.04.
All was working well untill the last package updates.
I can remember seeing some nvidia packages in the new update.
I can get only emergency resolution from the repair mode.
What i get from a standard start is a very large top left display of very little resolution.
I have removed the noveau package.

> start x does nothing

the startx command starts the X-server from the command line.

> and  nvidia-xconfig does not work.

nvidia-xconfig creates a new /etc/X11/xorg.conf file

> From terminal - what do i need to enter to get nvidia drivers working again.
I cannot even adjust the nvidia display.


I would suggest you blacklist the nouveau drivers, as they are included as part of the kernel. To blacklist the nouveau drivers just add:

```
blacklist nouveau
```

to the bottom of /etc/modprobe.d/blacklist.conf.

It may be an idea to disable /etc/X11/xorg.cong by using the following command:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by wapfu on 2010-06-29
K I tried it like this.

billp@billp-desktop:~$ blacklist nouveau
blacklist: command not found
billp@billp-desktop:~$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
billp@billp-desktop:~$ 
billp@billp-desktop:~$ sudo /etc/modprobe.d/blacklist.conf. blacklist nouveau
sudo: /etc/modprobe.d/blacklist.conf.: command not found
billp@billp-desktop:~$

ummmmmmmmmmmmmmmmmmmmmmmmmm

---

### Post by wapfu on 2010-06-29
On reboot screen was back to correct resolution. Yeah

I tried to run the nvidia display settings
It told me to run as root nvidia-xconfig
so I ran nvidia-xconfig
Rebooted
I ended back where i was with no screen resolution.
So I reopened terminal in low graphics and re entered
billp@billp-desktop:~$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

and I have graphics back - bonus thanks.
Now I cannot get to nvidia dispaly settings with fear of stuffing things up again.
can I get back to where I was before the package upgrade which caused all this?
Kindest regards
Bill

---

