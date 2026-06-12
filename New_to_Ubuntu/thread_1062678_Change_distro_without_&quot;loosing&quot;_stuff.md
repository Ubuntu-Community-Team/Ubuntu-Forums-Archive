---
title: "Change distro without &quot;loosing&quot; stuff"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by OllieGab on 2009-02-07
Being new to Linux obviously means that there is a certain urge to try out new distros and desktop environments.
I mainly use Ubuntu at the moment but is there any way to install a different distro without loosing all configurations, personal files and application specific settings (eg all the bookmarks in Firefox), or for that matter, any applications that were installed with the original distro?
And I don't mean a dual boot, but instead of the original.

Or am I just asking for too much now? :)

Ollie

---

### Post by yoyoned on 2009-02-07
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by drs305 on 2009-02-07
Another option is to make a completely separate partition on a drive and install the new distro there. Your main system's configuration files won't be used or altered. 

If you do this, one thing to keep in mind is how the system will boot. I would personally keep my current grub configuration and then add the new distro to the existing grub menu once it is installed. And of course be very careful that when you install a new system you don't overwrite your existing one during partitioning/formatting.

Another excellent way to try other distros is to use virtual machines (such as VirtualBox). It takes a bit of learning but once you have it set up you can try all sorts of distros with minimal impact on your actual system and partitions.

And of course you can see what other flavors of ubuntu are like by just installing the applicable desktop (xubuntu-desktop, kubuntu-desktop) into your current system. You can then just switch  sessions to see what the other ones offer.

---

### Post by lkraemer on 2009-02-07
Why not just use the Distro's LiveCD for the testrun.  By the time
you have played with it for a day or two you'll know if it requires
an install for further investigation.

lkraemer

---

### Post by issih on 2009-02-07
<Engage pedant mode> loose is when something is rattling about in its enclosure, a nut can be loose, morals can be loose. You do not, however, loose things, you lose them<End pedant mode>

Sorry about that, but internet forum usage of loose and lose drives me absolutely bonkers, it is nearly as bad as dual and duel.

Feel free to ignore me :) just being an absolute pedant, have a nice day one and all..

---

### Post by Paqman on 2009-02-07
> **yoyoned said:**
> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I wouldn't really recommend using the same user account on multiple distros. You could give it a go, but there's no guarantee everything will work, as different distros use slightly different technologies.

Also, if you switch from one DE to another (ie: Gnome to KDE) as you'll generally have to do when you distro-hop, then preserving your home folder won't really achieve much, as different DEs keep their settings in different places.

As for keeping your apps from one distro to another, this is even less doable. Not only do different distros have different apps in their distros at different version levels, but they use completely different package managers. In fact, the different package managers are probably the main thing that differentiates the various distros.

---

### Post by ianp5a on 2011-07-20
Since the Unity controversy, many people have suggested changing to another distro like Xubuntu or Mint. Is there an easy way to do this? I wouldn't know where to start.
The old distro settings are no longer of interest, apart from my list of installed applications. What steps would I need to do to "change distro"?
Would it be:
[LIST=1]
[*]Back up my data
[*]Back up list of apps (somehow?)
[*]Boot and run new distro CD install (old file system is deleted?)
[*]Restore all apps (somehow?)
[*]Restore my data (copy from disk)

[/LIST]
Is this correct? Do I need to boot with a new distro to begin the install?

---

### Post by Bodsda on 2011-07-20
> **ianp5a said:**
> Since the Unity controversy, many people have suggested changing to another distro like Xubuntu or Mint. Is there an easy way to do this? I wouldn't know where to start.
The old distro settings are no longer of interest, apart from my list of installed applications. What steps would I need to do to "change distro"?

Would it be:[LIST=1]
[*]Back up my data
[*]Back up list of apps (somehow?)
[*]Boot and run new distro CD install (old file system is deleted?)
[*]Restore all apps (somehow?)
[*]Restore my data (copy from disk)

[/LIST]Is this correct? Do I need to boot with a new distro to begin the install?
 
Thats more or less how you would go about it. However, I would strongly suggest dual booting for a while, to ensure you are comfortable with the new distro before you trash your current one. Having a seperate /home partition helps a lot here.
 
To get a list of installed packages, you can run (i think this command is right)
```

dpkg -l

```
 
But you will get 'every' installed package.
 
The solution I would opt for, would be to install gnome3, or fluxbox or etc. etc. and then remove unity. (Please be aware that installing gnome3 breaks unity completely) This way you dont have to reinstall or loose your installed apps, and there is no danger of loosing your data either.
 
HTH,
Bodsda

---

### Post by ianp5a on 2011-07-20
Thanks.

Does dual boot means a separate *partition* per distro?
Is there an easy way to move the home onto another partition? Easy means not using the CLI.

As far as list of applications goes, I thought there is a tool in Ubuntu to save and restore the installed apps. Maybe it was planned for the next release if I remember correctly.

---

### Post by dasan on 2011-07-20
> **ianp5a said:**
> Thanks.

Does dual boot means a separate *partition* per distro?
Is there an easy way to move the home onto another partition? Easy means not using the CLI.

if you are booting to a live cd you can easily do it from there..

It is always recommended to use separate home partition if you want to keep on upgrading your machine

---

### Post by amjjawad on 2011-07-20
> **ianp5a said:**
> Does dual boot means a separate *partition* per distro?

Definitely, Dual-Booting means each OS must have its own partition and boot loader.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://en.wikipedia.org/wiki/Multi_boot](http://en.wikipedia.org/wiki/Multi_boot)

IMHO, if the main purpose of Dual-Booting is "learning" and discovering new world, then the best way is to install the new OS into an USB/External Drive.

By doing so, you are not messing with your internal HDD and everything will stay as it's. Just be careful when you install the boot loader.

In my signature (Avoid Wubi), there is a guide of HOWTO do so.
General Idea is the same but perhaps the OS Name will be different in your case.

Good luck!

---

### Post by oldos2er on 2011-07-20
> **ianp5a said:**
> Since the Unity controversy, many people have suggested changing to another distro like Xubuntu or Mint. 

The easiest way to install Xubuntu is to run ```
sudo apt-get install xubuntu-desktop
```

---

### Post by kroq-gar78 on 2011-07-20
also, for lubuntu:
```
sudo apt-get install lxde
```
and for kubuntu:
```
sudo apt-get install kubuntu-desktop
```

Also, isn't this thread kind of necro? The OP's post was from '09...

---

