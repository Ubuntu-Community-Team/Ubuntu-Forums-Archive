---
title: "Update-Grub"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by McTwitch on 2010-10-08
Okay, so I've got an external harddrive running Ubuntu, with Windows Vista on the actual computer's internal harddrive. I installed Fedora 13 on a partition on the harddrive. I'm sure I should run update-grub to use the bugger, but I don't know if it'll screw over my Windows, as it is the family install. So, long story short, will update-grub do anything to Windows?

(Unplugging the bugger manually, or using BIO's isn't possible. 1 would freak the family out, 2 I just can't seem to do.)

---

### Post by garvinrick4 on 2010-10-08
> **McTwitch said:**
> Okay, so I've got an external harddrive running Ubuntu, with Windows Vista on the actual computer's internal harddrive. I installed Fedora 13 on a partition on the harddrive. I'm sure I should run update-grub to use the bugger, but I don't know if it'll screw over my Windows, as it is the family install. So, long story short, will update-grub do anything to Windows?

(Unplugging the bugger manually, or using BIO's isn't possible. 1 would freak the family out, 2 I just can't seem to do.) Which drive did you install fedora 13 and where did you put its grub? Different grub used by fedora 13 than more recent Ubuntu's. It uses
grub legacy and ubuntu 9.10 and up uses grub2.

---

### Post by McTwitch on 2010-10-08
Fedora 13 -sdc1 Ubuntu-sdc2 and some other random partitions.

---

### Post by -kg- on 2010-10-08
OK, where did you put Fedora's GRUB?  If you don't know, it's likely already installed in place of the Windows bootloader.

In any case, "update-grub" itself won't affect anything with Windows (or at least, shouldn't).  If you've installed Fedora's GRUB to the default location, you will get the GRUB menu every time you boot up the computer, and Windows will be one of the selections in the menu.\

> Fedora 13 -sdc1 Ubuntu-sdc2 and some other random partitions.

Considering the partitions that Fedora and Ubuntu are installed to, which OS did you install most recently?  If you installed Fedora *_and then_* Ubuntu, then Ubuntu's GRUB will be accessed by the GRUB bootloader in the MBR.  You won't even need to run "update-grub" from Fedora...you'll need to run it from Ubuntu.

---

### Post by McTwitch on 2010-10-08
Right, ran update-grub, and now I can get on Fedora. Don't know about Windows, but I'm hopeful. Random question, though. When I try to install things using the Terminal on Fedora, such as ```
sudo apt-get install etc
``` I get this error message
```
McTwitch is not in the sudoers file.  This incident will be reported.

``` after I input my password.

---

### Post by andrewthomas on 2010-10-09
With fedora you will have a root account so you would to 


```
su -c 'yum update'
``` and input the root password

or just 

```
su
```to switch to root

---

### Post by garvinrick4 on 2010-10-09
Here is a link to set up your Fedora. You have to configure sudo and yum (apt-get) follow the fedora 12 post installation here. It is the same as 13. You can get used to fedora, takes a bit of a study. 
 When I install I just do not install grub at all. It is there at install a selection not to use grub. And after install boot into my grub2 and update-grub and it finds fedora or any other
O.S. It seems grub legacy and grub2 just do not get along very well so I avoid having them conflict. (Nice to give other distro's a spin but Ubuntu is really #1)

[http://www.my-guides.net/en/content/view/174/26/](http://www.my-guides.net/en/content/view/174/26/)

---

