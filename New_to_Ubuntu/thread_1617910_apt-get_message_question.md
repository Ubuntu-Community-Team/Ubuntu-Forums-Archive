---
title: "apt-get message question"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by wog on 2010-11-09
when I run apt-get it says:
"0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded."

How can I find out what isn't upgraded?
How do I upgrade those things once I know this?

Thanks in advance!

---

### Post by sully101 on 2010-11-09
I get this

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**[COLOR="Blue"]The following packages have been kept back:[/COLOR]**
[COLOR="Red"]**  linux-generic linux-headers-generic linux-image-generic**[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

thus

linux-generic
linux-headers-generic
linux-image-generic

were not upgraded.

---

### Post by wog on 2010-11-10
Thank you very much. I kept notes from my last exposure to Ubuntu, but they apparently weren't totally complete. :)

---

### Post by sully101 on 2010-11-10
I see hardy was a while ago now. I just did a quick google and to upgrade the kernel from the terminal I think the command is

sudo apt-get dist-upgrade

but this would bump you from 10.04 to 10.10. The other option would be to explicitely install the kernel version that you want. Much easier to use synaptic or update manager from a gui in my humble opinion.

As a side note apt-get doesnot update the kernel automatically because you may have third party/custom modules that upgrading the kernel would break. Its definitely not a good thing to do that.

---

### Post by wog on 2010-11-10
> **sully101 said:**
> I see hardy was a while ago now. I just did a quick google and to upgrade the kernel from the terminal I think the command is

sudo apt-get dist-upgrade

but this would bump you from 10.04 to 10.10. The other option would be to explicitely install the kernel version that you want. Much easier to use synaptic or update manager from a gui in my humble opinion.

As a side note apt-get doesnot update the kernel automatically because you may have third party/custom modules that upgrading the kernel would break. Its definitely not a good thing to do that.

I've used the apt-get line in the past, but every time it tends to break my system and I end up having to install from the LiveCD. I've learned a lot trying to fix it before giving in to the LiveCD install process, although it's very frustrating.

I don't actually know how to use anything else to dist-upgrade except apt-get. Are there instructions somewhere?

I keep hearing I can backup grub and other files to help out in case something catastrophic happens, but I don't know what to back up or where on my drive to find it.

The additional problem is, how would I know in advance whether upgrading my kernel would break something? Is there some way of finding out?

Thanks. Sorry for the disorganized way I have for asking questions.

---

### Post by sully101 on 2010-11-10
On my system (Ubuntu 10.04) the package manager is under.

System >
        Administration >
                        Synaptic Package Manager

In the Main Menu on the desktop. Sorry to hear of your troubles. I have been down many a similar road.

You should find some additional information here [http://ubuntuforums.org/showthread.php?t=801404]("http://ubuntuforums.org/showthread.php?t=801404") and here [https://help.ubuntu.com/]("https://help.ubuntu.com/")

> The additional problem is, how would I know in advance whether upgrading my kernel would break something? Is there some way of finding out?

If you have had to manually compile a module "driver" such as one from ati/nvidia then that module would have been built for that particular kernel. If you then go and upgrade your kernel to the latest version the module would have to be compiled again. (or the hardware it is for wont work, not good if its the display and you cant see anything on the screen) There have been some inroads made into simplifying the process. And to put things simply. If you dont know what compiling a module is then you probably havn't done it so you should be able to upgrade your kernel without worrying. If you have installed an ATI or NVIDIA driver from their websites then you will need to do some more reading elsewhere such as [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

If you do upgrade your kernel then don't remove the old one until you are sure the new one works as expected. That way you can always get into grub and boot the old one.

---

### Post by kesman on 2010-11-10
> **sully101 said:**
> 

sudo apt-get dist-upgrade

but this would bump you from 10.04 to 10.10.

Wrong. Dist-upgrade is slightly different from upgrade, but it certainly doesn't update the system to a newer version. I've always updated my system with
```
sudo apt-get update && sudo apt-get dist-upgrade
```
with no problems whatsoever so far.

---

### Post by sully101 on 2010-11-10
> **kesman said:**
> Wrong. Dist-upgrade is slightly different from upgrade, but it certainly doesn't update the system to a newer version. I've always updated my system with
```
sudo apt-get update && sudo apt-get dist-upgrade
```
with no problems whatsoever so far.

Thank you there are a few extra steps before you can go up a version. I stand corrected.

---

### Post by mcduck on 2010-11-10
> **kesman said:**
> Wrong. Dist-upgrade is slightly different from upgrade, but it certainly doesn't update the system to a newer version. I've always updated my system with
```
sudo apt-get update && sudo apt-get dist-upgrade
```
with no problems whatsoever so far.

That's correct.

The only difference between "apt-get upgrade" and "apt-get dist-upgrade" is that "upgrade" can only replace existing packages with new versions and if required, add new packages, while "dist-upgrade" is also allowed to remove packages if that's necessary.

Actually upgrading into next release version could be done with dist-upgrade, if you edited your sources.list beforehands to point into the new release's repositories, but the recommended way is actually running "sudo do-release-upgrade" or using the Update Manager. So you really don't need to worry about accidentally upgrading to new release version. :)

---

### Post by mcduck on 2010-11-10
> **wog said:**
> I've used the apt-get line in the past, but every time it tends to break my system and I end up having to install from the LiveCD. I've learned a lot trying to fix it before giving in to the LiveCD install process, although it's very frustrating.

I don't actually know how to use anything else to dist-upgrade except apt-get. Are there instructions somewhere?

I keep hearing I can backup grub and other files to help out in case something catastrophic happens, but I don't know what to back up or where on my drive to find it.

The additional problem is, how would I know in advance whether upgrading my kernel would break something? Is there some way of finding out?

Thanks. Sorry for the disorganized way I have for asking questions.

No upgrade should break anything, ever. Of course this is assuming that you are only using Ubuntu's official software repositories.

If things like kernel updates break things on your system then that's pretty much a sign that you have some other, underlying problem that's causing this to happen.

(What comes to backups, just make sure you have backups of all your personal stuff. Backing up everything in your home directory, including the hidden files, will store all your personal stuff and program settings etc. The rest is always easy to reinstall from repositories.)

---

