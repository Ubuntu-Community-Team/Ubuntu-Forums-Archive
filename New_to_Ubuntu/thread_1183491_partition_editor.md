---
title: "partition editor"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by RajaAjmal on 2009-06-10
when running the ubuntu 9.04 live CD, the software partition editor (under system-> administration) is available. but after installing it, the partition editor is no more available. is there a way to install Partition Editor from the live CD without downloading and installing it from the Internet?

---

### Post by PocketDog on 2009-06-10
Maybe it's just missing from the menu. Can't think how though. Try ```
gksudo gparted
``` in the Terminal.

---

### Post by zeroseven0183 on 2009-06-10
I don't think you can do that. Let's wait for the other guys if they have doen that.

Installation of Gparted is very easy (download):

```
sudo apt-get install gparted
```

Partition Editor can be found in System > Administration after the installation. Or just launch it through the terminal by simply typing **gparted**

---

### Post by RajaAjmal on 2009-06-10
thanks for the reply
i've tried the 'gksudo gparted' but nothing happen (that is, it is not installed).
seroseven, you too, thanx for the reply. but i want to know if there's a way to install it from the live CD, before trying to download it. 
i've a limited internet package. As such, i don't want to download it, if somehow it is possible to install it from the live CD.

---

### Post by duruttye on 2009-06-10
Hey there!

Open up software properties and on ubuntu software check the cdrom!
That means that whenever you try to install anything, first it looks for the package files on the cdrom. On the live cd the gparted was there, so it must be on the cd itself :)

I'm just a newbie, so anyone, correct me if I'm wrong!
Take care!

---

### Post by Cheesemill on 2009-06-10
You wont be able to install it from the Live CD as it doesn't contain any packages. You could install it from the Alternate CD if you have a copy of that though.

Cheesemill

---

### Post by antoz on 2009-06-10
Why don't you just use the live CD whenewer you want to change your partitions? After all you are not going to change them that often anyway. Other then that you may have to download and install it as was sugested in the previous posts. In the older versions of Ubuntu it is under system->administration->disks so it must not be there anymore in the newer versions. A.

---

### Post by oldos2er on 2009-06-10
> **RajaAjmal said:**
> when running the ubuntu 9.04 live CD, the software partition editor (under system-> administration) is available. but after installing it, the partition editor is no more available. is there a way to install Partition Editor from the live CD without downloading and installing it from the Internet?

 I'm not sure if gparted can be installed from the LiveCD; but you can find out by adding it (the LiveCD) to your Software Sources. See [https://help.ubuntu.com/community/AptCdrom](https://help.ubuntu.com/community/AptCdrom)

 Another option would be to use Keryx ([http://keryxproject.org/](http://keryxproject.org/)) or AptonCD ([http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)) if you have another computer available with internet access.

---

### Post by joyneo04 on 2009-06-10
have u tried for add and remove programme....if not then try it na...

---

### Post by Bölvaður on 2009-06-10
I guess you already got it working by now. But as for other's... click my link to install it


[sudo apt-get install gparted]("apt:gparted")

---

### Post by bodhi.zazen on 2009-06-10
In general, partitions should be managed form a live CD.

Probably for this reason, gparted is on the desktop (live) CD , but does not get installed by default.

You can either install gparted manually or run it from the live CD (or download the gparted live CD).

In general you can not install packages from the desktop CD, although you can with the alternate CD. I am not sure gparted is on the alternate CD. That is not to say it is impossible to "install" binaries from the desktop CD, just that it is more difficult then apt-get install foo ;)

---

