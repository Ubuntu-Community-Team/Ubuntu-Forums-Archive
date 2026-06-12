---
title: "kernel panic HELP!!!!!!!!!!!"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by crtiviz on 2010-05-11
Ok i'm new and there's probably an easy way to do this but I don't know how to do it. Some two years ago after much thinking I got a live cd for ubuntu 8.4. It never gave myself the time to install it so i left it there. Some months ago I decided to install it and erase windows in my computer. back then I didn't have internet so I left it like that. Yesterday I finally got internet and decided to update my ubuntu from 8.04 to the 10.04 version. I had to go to work so when I came back the screen was white so and I restarted the computer the old holded-until-it-turns-off way. when I turned it back on i got this:

Kernel panic:not syncing: VFS: Unabl to mount root fs on unknow-block (0,0)

I was readying other post about this and saw that you could pick another grub by pressing ESC and i got this options:

Ubuntu 10.04 LTS, kernel 2.6.32-22- generic

Ubuntu 10.04 LTS, kernel 2.6.32-22- generic (recovery mode)

Ubuntu 10.04 LTS, kernel 2.6.24-24- generic

Ubuntu 10.04 LTS, kernel 2.6.24-24- generic (recovery mode)

I have pick all of them the first -22-generic gives me the Kernel Panic. The second,3rd and the fourth one gives me a big parragraph and the option to do write a comand.

I have no idea of what to do I've already read that there has being people with the same problems but I don't get what they are saying. So please help me.

---

### Post by charlie cat on 2010-05-23
Can you provide a link to a webpage where people have the same problem or what to do about it?  Maybe someone can "translate" for you.
Don't worry, we were all new once.

---

### Post by Ozymandias_117 on 2010-05-23
Did you try to upgrade from 8.04 to 10.04? If so... that's probably your problem :P I would just do a fresh install unless you're going from one to the very next (Like 9.10 to 10.04) and even then it doesn't always work.

---

### Post by sylvester_0 on 2010-05-23
> **Ozymandias_117 said:**
> I would just do a fresh install unless you're going from one to the very next (Like 9.10 to 10.04) and even then it doesn't always work.

Wut? LTS releases are specifically designed to be upgradeable from one to another. I went from 6.06 to 8.04 on a LAMP webserver without a single problem, save for apache not starting because of the silly Zend optimizer. I've also upgraded many desktops/laptops throughout the years without any problems. Fresh installs may be the norm in the world of Windows, but with Linux that's simply not the case (as with reboots.)

It sounds like you restarted in the middle of the install (you came back to a white screen and decided to power it off?)

Your best option right now is to read up on chrooting (basically booting a LiveCD and entering into the installation that's giving you problems and trying to complete the setup (apt-get dist-upgrade.) I'm guessing it got stuck somewhere in the middle of configuring the new packages. Good luck!

---

### Post by Ozymandias_117 on 2010-05-23
@sylvester_0 I don't know then, I just know I've never had a successful upgrade across multiple releases.

---

