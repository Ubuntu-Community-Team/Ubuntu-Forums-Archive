---
title: "file not found"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by leeannec on 2010-11-26
I have downloaded ubuntu on my pc with a wubi installer.

It was working great until I went to get on my computer this morning.

When I choose ubuntu as my os I get an error message of file not found.

How do I fix this. I can run the windows os.

---

### Post by WildOscar on 2010-11-26
> **leeannec said:**
> I have downloaded ubuntu on my pc with a wubi installer.

It was working great until I went to get on my computer this morning.

When I choose ubuntu as my os I get an error message of file not found.

How do I fix this. I can run the windows os.

noob=Newbie ;)

Did you perform any kind upgrade of system update a little bit more info would help.

---

### Post by leeannec on 2010-11-26
I did perform an upgrade last night.

---

### Post by leeannec on 2010-11-26
Also, when I try to get into the os it says "unknown error" and "loadfont", then file not found underneath it.

then it sends me back to "select os."

---

### Post by Hippytaff on 2010-11-26
Wubi doesn't like upgrades. Wubi is only really to try out ubuntu, if you intend using it for any perriod of time it is always best to do a 'proper' install
 
[https://wiki.ubuntu.com/WubiGuide#Troubleshooting](https://wiki.ubuntu.com/WubiGuide#Troubleshooting)

---

### Post by Rubi1200 on 2010-11-26
For a description of the problem and possible solutions, see here:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

Forum member bcbc is one of the experts on Wubi installs and although the instructions may seem a bit daunting, they almost always work.

If anything is unclear, please ask before proceeding.

Thanks.

---

### Post by leeannec on 2010-11-26
I think it may be time for a proper install

---

### Post by Rubi1200 on 2010-11-27
You also have the option, if you want, of migrating the Wubi install to a dedicated partition.

See here for more details:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Let us know if you need help either with this method or a regular install.

---

### Post by leeannec on 2010-11-27
> **Rubi1200 said:**
> You also have the option, if you want, of migrating the Wubi install to a dedicated partition.

See here for more details:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Let us know if you need help either with this method or a regular install.

I was thinking of using 

[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

I did try to trouble shoot the problem and it's to no avail yet. 

I will need much help fixing this as I am a noob of the highest order. This is all still greek to me.

---

### Post by Rubi1200 on 2010-11-27
Before trying anything else, take a look here for a possible solution for the problem:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

---

### Post by leeannec on 2010-11-27
> **Rubi1200 said:**
> Before trying anything else, take a look here for a possible solution for the problem:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

I'll try. I won't be able to boot from a "live" disk (meaning cd rom? This is how noob I am. It's impressive I managed to get the wubi install to work in the first place)

> If it's a 10.04 install, the fix is to boot an Ubuntu live cd, loop mount the wubi root.disk and manually edit the grub.cfg.

I think 10.04 is what I have but I am not sure, I am having to operate from windows XP, and I am a bit lost.

I have never loop mounted anything ever. The rest is greek to me.

My brain hasn't melted yet, surprisingly.

I tried to do the ext2read thing as this is too much, and it just linked me back to the same page.

Bear with my noobness.

---

### Post by Hippytaff on 2010-11-27
It's getting late here so apologies if I'm completely missing the point, but I'm wondering whether what this guy did might benefit you!? :-s

[http://ubuntuforums.org/showthread.php?t=1631462](http://ubuntuforums.org/showthread.php?t=1631462)

---

### Post by leeannec on 2010-11-27
> **Hippytaff said:**
> It's getting late here so apologies if I'm completely missing the point, but I'm wondering whether what this guy did might benefit you!? :-s

[http://ubuntuforums.org/showthread.php?t=1631462](http://ubuntuforums.org/showthread.php?t=1631462)

Okay so I went to thread and here are my questions.

> I booted into Windows
I then copied the C:\ubuntu directory to a different location (C:\Copy of ubuntu), which took all night.

Okay how do I do this? That one little step is missing which I need. Yes you need big easy pictures to probably show me how.

> I then tried to re-install Wubi hoping it might repair the issue
Wubi required an un-install and purged the original C:\ubuntu folder
I completed the Wubi installation and booted into the new Ubuntu installation
I then booted back into Windows

I think i'll figure this part out.

> I renamed the new root.disk and swap.disk inside the new C:\ubuntu\disks to a different extension

What does an extension look like. what is it? Why should I move it there? I fundamentally do not understand this.

> I then moved the root.disk and swap.disk from copied location (C:\Copy of ubuntu\disks) to the new installation (C:\ubuntu\disks)
I then booted back into ubuntu just fine

My brain just melted. I may pay someone to do it for me. Or I will just download whatever program that fixes the problem.

---

