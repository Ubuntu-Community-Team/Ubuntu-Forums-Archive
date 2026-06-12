---
title: "NLite"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by kakashi_12 on 2009-12-03
I've tried installing this program 3 times now on my computer. All different times (within different months), not one after another. I can't get it to work on my computer for some reason. Is there an equivelant that work well that you're familiar with?
 
I need to create a custom XP disc with SP3 and ALL the apps I used pre-installed and some apps (that came with the computer) not installed, etc.

---

### Post by kakashi_12 on 2009-12-03
actually nvm. i finally got it working. i remember i was told i needed .netframework 2.0. i knew that, but i thought it still wouldnt work. i might still need help using it though.

---

### Post by mikewhatever on 2009-12-03
Glad you did get it working, cause we don't support Windows xp on ubuntu forums.;)

---

### Post by kakashi_12 on 2009-12-03
ok my first prob is finding the correct installation folder. i386. i did a search for it and there are multipe ones. i tried c\windows and system32.

---

### Post by seeker5528 on 2009-12-03
> **kakashi_12 said:**
> ok my first prob is finding the correct installation folder.

It's on your installation disk, you have to have an installation disk to create a customized installation disk. I don't think NLite is going to do what you want it to do, it doesn't just let you include anything and everything.

What you want sounds more like a sysprep thing.

[http://technet.microsoft.com/en-us/library/bb457073.aspx](http://technet.microsoft.com/en-us/library/bb457073.aspx)

Later, Seeker

---

### Post by kakashi_12 on 2009-12-03
hmmm. ok. i read that page, but idk if that will do it either. i'll see....
 
anyway, my buddy told me that he uses nlite all the time and says that he puts in whatever programs he wants and everything and takes out crap he doesn't want.
 
I have the install disc. Can I NOT INPUT my license key... that way I can make copies of the disc as backups for any computer. And have the user of that computer input THEIR OWN key? If not, oh well.
 
I also want the apps to be able to just already be installed and have the options/preferences of those apps be set too. If that's possible.
 
I know I was talking about using CloneZilla before, which sounded great but... the only problem was... what if I want to use the disc for more than one computer in my house. They aren't all going to be partitioned the same. And not all the computers are going to have both XP and linux like this one does. I guess I just want a custom XP disc with all the updates and apps pre-installed. If at all possible.
 
Clonezilla would work if I could clone everything but not set a particular size.

---

### Post by electricFan on 2009-12-03
You might want to try another forum for more help with this, just because this is mainly about ubuntu and not about Windows XP tasks.

---

### Post by kakashi_12 on 2009-12-03
nvm. i found a video tutorial. sorry for the bothersome guys.
i'll have to research the sysprep thing this weekend and clonezilla.

---

### Post by seeker5528 on 2009-12-04
> **kakashi_12 said:**
> anyway, my buddy told me that he uses nlite all the time and says that he puts in whatever programs he wants and everything and takes out crap he doesn't want.

You can customize the Windows components that get installed, add service packs, and include additional drivers if the drivers include a .inf file for installation.

The slipstream process was created by MS, Nlite just makes it easier. If Nlite has additional features that allow you to include other things I know nothing about that.

> I have the install disc. Can I NOT INPUT my license key... that way I can make copies of the disc as backups for any computer. And have the user of that computer input THEIR OWN key? If not, oh well.

You don't put your key in, you are just creating an updated install disk, you put the key in at the time you do the installation. As long as all the computers are the same type of install, home or pro, OEM or boxed, upgrade or intended for computer that doesn't already have windows on it, the same disk should work for all of them using the key that belongs to each computer. 

With sysprep you do a new install, don't activate it, install the software you want, configure it the way you want, seal it, then clone the disk to an image. So the partition only needs to be big enough to install what you want, then after you clone the image to the disk on the computer where you actually want to run it, the first time you start up it asks for the license, and activation. Then you can use gparted to expand the partition to fill the disk.

The drawback is it might not work on a computer with different hardware than the image was created on. 
 
People seem to be getting up-tight, so probably best to end the thread here. Can't really tell you any more than that anyway.

Later, Seeker

---

