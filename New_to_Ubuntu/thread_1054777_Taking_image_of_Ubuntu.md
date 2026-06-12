---
title: "Taking image of Ubuntu"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by halovivek on 2009-01-30
Hi
i am using Ubuntu for more than six months and i have done working upto my mark. I am planning to make the whole image and to store in separate DVD. In windows you can use Ghost. I want to take the whole Image. If something goes wrong i want to restore. I am not looking just files backup. I use to back up all datas. 
I could not find a particular software and i am looking for particular software as well as the good Tutorial. 
Because already i have installed ubuntu 10-12 times in my system.

---

### Post by blazemore on 2009-01-30
Download and install remastersys.
Run all these commands in this order:
```

sudo su
echo deb http://www.remastersys.klikit-linux.com/repository remastersys/ >> /etc/apt/sources.list
apt-get update
apt-get install remastersys -y --force-yes
remastersys backup **ImageName.iso**

```
This saves **ImageName.iso** in your home/**user**/remastersys folder.

You can then burn it on a DVD/CD, or use unetbootin to make a bootable USB drive.

From the Remastersys website:
>  You can log into the livecd/dvd with any valid user that was on the system on the hard drive but it is recommended to log into the first one created during the initial installation as that is the user that can sudo.  When you come to install this back to a hard drive, the user setup portion of ubiquity (the install program) is just a placeholder other than the system name.  The username and password set here will not be used but must be created in order to continue with the installation.  Part of the reason for this is that your users are already created so you don't need to create them again,  but more importantly because user setup is an integral part of the install program and cannot be removed or bypassed easily.  If you were using proprietary video drivers like the nvidia or ati ones, you will need to reinstall them.  The Ubuntu livecd scripts prevent these from running properly but reinstalling them after installation will make them work again.

---

### Post by halovivek on 2009-01-30
You can then burn it on a DVD/CD, or use unetbootin to make a bootable USB drive.


Can you tell me what is meant by unetbootin? need some more details about this one.

---

### Post by halovivek on 2009-01-30
Thanks I find the details from this [site]("http://unetbootin.sourceforge.net/")

---

### Post by blazemore on 2009-01-30
unetbootin is similar to the USB creator tool in Ubuntu.

It's an application which can download linux distros from the Internet, and "burn" it to a USB drive. You can also feed it a disk image to do the same.

The only thing it can't do is a persistant install, but that's not a problem in this case.

Google unetbootin, it's a small utility. You just run it from command-line (It has a GUI though)
```
cd /path/to/unetbootin
```
```
sudo ./unetbootin
```

If you use it a lot, you can copy to /usr/bin, so you can just run "unetbootin" command.

---

### Post by Neural oD on 2009-01-30
you could also use dd or ddrescue - command line - very stable - they will do a bit for bit copy. check out their man pages for usage.

---

### Post by halovivek on 2009-02-05
Thank you so much. Now i am making image in the Ubuntu.

---

### Post by quinnten83 on 2009-02-05
you can also try clonezilla which is a toll similar to ghost.

---

### Post by halovivek on 2009-02-05
> **quinnten83 said:**
> you can also try clonezilla which is a toll similar to ghost.

Ok i will try that one. How to install the clonezilla from where i can get it?

---

### Post by quinnten83 on 2009-02-05
[http://clonezilla.org/]("http://clonezilla.org/")

---

