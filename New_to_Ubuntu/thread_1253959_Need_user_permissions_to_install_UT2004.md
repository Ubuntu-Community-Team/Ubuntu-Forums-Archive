---
title: "Need user permissions to install UT2004"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by silverfang77 on 2009-08-30
I'm an absolute beginner at Ubuntu (9.04 Jaunty Jackalope), so I posted this here. If it is in error, I apologize.

Anyway, I wanted to install UT2004 on my Ubuntu laptop (Toshiba Satellite X205-S7483, Intel Centrino Core2 Duo @ 1.7 GHz, 2 GB RAM, nVidia GeForce 8700M GT). All went well enough until the installer attempted to put it in the usr/games directory. It gave me an error saying I didn't have permissions to install it, so I aborted the installation.

I went to the directory itself and checked its properties. It said that I do not own the directory, so cannot alter its properties or install anything to it. 

What am I missing? Do I need to log into the root account to install UT2004?

Thanks!!!!!:confused:

---

### Post by Bachstelze on 2009-08-30
You need to run the installer as root, yes. However, you don't login as root in Ubuntu. You use [font=monospace]sudo[/font] to execute a command with the privileges of the root user. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information.

---

### Post by phillw on 2009-08-30
> **silverfang77 said:**
> I'm an absolute beginner at Ubuntu (9.04 Jaunty Jackalope), so I posted this here. If it is in error, I apologize.

Anyway, I wanted to install UT2004 on my Ubuntu laptop (Toshiba Satellite X205-S7483, Intel Centrino Core2 Duo @ 1.7 GHz, 2 GB RAM, nVidia GeForce 8700M GT). All went well enough until the installer attempted to put it in the usr/games directory. It gave me an error saying I didn't have permissions to install it, so I aborted the installation.

I went to the directory itself and checked its properties. It said that I do not own the directory, so cannot alter its properties or install anything to it. 

What am I missing? Do I need to log into the root account to install UT2004?

Thanks!!!!!:confused:


Now, I hope someone will give a safer method... So use this one with caution, I am about to make you 'God' on you computer.

Every file / directory has an owner, then a group, then everyone permissions.

if you want to do an install with your name (i.e. user) then you can chown the area.

I'm sure people will correct me, but ....

~$ su
<enter the root password>
It will change to
~#
chmod -R 777 /usr/games

that will give access to everyone / anyone ..

I think what you are looking for is ownership, in which case

chown -R name /usr/games

where 'name' is what your computer knows you as.

A word of warning, being in '#' mode is all powerful. Get out of it as soon as possible (just type 'exit' and you will be safelyback in $ mode)

Hope that helps,


Phill.

---

### Post by silverfang77 on 2009-08-30
Yes. I am looking for ownership. Will I type that chown -R command in the terminal window?

Sorry for the stupid question.

---

### Post by Bachstelze on 2009-08-30
> **silverfang77 said:**
> Yes. I am looking for ownership. Will I type that chown -R command in the terminal window?

Sorry for the stupid question.

Don't do that.

---

### Post by silverfang77 on 2009-08-30
Installing UT2004 base install now. I hope that's the right one.

edit: Got it installed, but is it slooooowwww.

---

### Post by Bachstelze on 2009-08-30
> **silverfang77 said:**
> Installing UT2004 base install now. I hope that's the right one.

edit: Got it installed, but is it slooooowwww.

Do you have the nvidia drivers for your card installed?

---

### Post by silverfang77 on 2009-08-30
Linux uses drivers? No. I don't. I'll hunt for some when I attempt to set up an Internet connection on the Linux laptop tonight. Are they easy or hard to install?

---

### Post by Bachstelze on 2009-08-30
Normally, it's as easy as clicking System -> Administration -> Hardware Drivers and checking the box next to the nvidia drivers.

If it fails for some reason (or if you are so inclined), the fail-safe command-line way is:

```
sudo apt-get install linux-generic linux-headers-`uname -r`
sudo apt-get install nvidia-glx-180
sudo nvidia-xconfig
sudo /etc/init.d/gdm restart
```

But make sure your system is up-to-date beforehand.

---

### Post by silverfang77 on 2009-08-30
I'll install any needed updates tonight, assuming I can get my Option Icon cellular modem to work under Ubuntu.

Thank you.

---

