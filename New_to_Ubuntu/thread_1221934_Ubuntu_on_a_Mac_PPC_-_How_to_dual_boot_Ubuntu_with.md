---
title: "Ubuntu on a Mac PPC - How to dual boot Ubuntu with Mac - Ubuntu partition is external"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by powel212 on 2009-07-24
Here's one for ya.

I have an old Mac PPC iBook and and old 10G ipod that still works.

The mac OS is fine but I would prefer to run ubuntu. Ubuntu is not fully supported to run on the old PPC CPUs so I don't want to go with a straight install. But I do have an old 10g ipod firewire drive that I cold use as the Ubuntu partition for dual booting.

Has anyone tried this?

Do I have any hope?

Any help or pointing me in a direction, web site, is appreciated.

Powel

---

### Post by Ratscallion on 2009-07-24
Urm, if you have another computer, you could try plugging the iPod in there, and then running the install from a Live CD. When you get prompted for where to install, select the ipod. Then you *should* be able to run from the iPod... Just a thought.

---

### Post by powel212 on 2009-07-24
I have other computers, but none of the others use the old PPC architecture with is proprietary for this job.

Thanks though.

Powel

---

### Post by Ratscallion on 2009-07-24
It shouldn't matter if they don't use the PPC.. You're installing and running on the iPod... Should work, in theory.

---

### Post by powel212 on 2009-07-24
Okay I'll give your suggestion a try but I would love to hear from anyone who has tried such a thing before. 

Honestly I didn't think that my intel system would even boot from the PPC Ubuntu disc. But I have not even tried so here goes nothing.

Will report back.

Powel

---

### Post by Ratscallion on 2009-07-24
Maybe try Xubuntu, or even the alternate installation... that's if Ubuntu doesn't boot.

---

### Post by powel212 on 2009-07-24
Tested. 

My intel based system won't boot from the PPC alternative CD so this way won't work.

I need to boot the PPC Alternative onto the iBook and then install to the iPod external.

Anyone have any experience with this?

Powel.

---

### Post by powel212 on 2009-07-25
The ubuntu PPC cd booted but after loading the install kernel from the CD it told me there is no CD drive. Odd seeing as I just booted from the CD. haha

Anyway I am having some success with Fedora 11 PPC. It is installing now. I am not crazy about Fedora but it is working so I guess I will spend some time getting to know it.

Powel

---

### Post by Ratscallion on 2009-07-25
Ok... Good luck! You could always try Debian, openSUSE or Xubuntu. They're a similar interface to Ubuntu (that's if you use the GNOME version of SUSE)

---

### Post by powel212 on 2009-07-25
The iBook G4 PPC is now running Fedora. I intalled it to the old 10G iPod and created a successful dual boot. Pretty straight forward using the Fedora PPC disc.

> You could always try Debian, openSUSE or Xubuntu

I tried Suse but the Suse PPC disc did not include the cd driver so it couldn't be used. I could try Debian but Fedora seems to be fine, and I can find very little difference between straight up vanilla Debian and Fedora. I don't think that Xubuntu will work either because the Ubuntu PPC disc won't load because it is also missing the cd driver. No Ubuntu means no Xubuntu.

I run Xubuntu on my server and it is perfect for that. But for the portable system on the iBook I would prefer to run Nautilus despite its weight.

Thanks for the help and I would still love to hear from anyone running Linux of any kind on an iBook PPC

Powel

---

### Post by Ratscallion on 2009-07-26
If you can install debian packages you can always install ubuntu (or a variant)-desktop. So, for example, if I wanted Kubuntu and I'm using Ubuntu, I could just do
```
sudo apt-get install kubuntu-desktop
```
That help? It would include all the packages you get by default, so ubuntu-desktop would include things like nautilus and gedit etc.

---

