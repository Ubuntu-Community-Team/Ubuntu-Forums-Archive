---
title: "Tried to erase Ubuntu Partition but can't boot anymore"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by dondrup on 2009-04-16
I have a cheapie emachine 1.6 GHz AMD with 3GB RAM and I have Vista on one partition, Ubuntu 8.10 on another. I tried deleting the Ubuntu partition using Acronis Disk Director but now when I start up I get:

GRUB loading stage1.5.

GRUB loading please wait...
Error 22
_    << I have an underline cursor blinking here but can't type anything in - I wouldn't know what to type anyway.

So obviously I did the uninstall incorrectly as I can see through looking at other threads. What I'd like to do is uninstall ubuntu and merge its partition with the Vista partition. I expect it is not too hard, but I haven't a clue and would appreciate help... I am an absolute beginner! On a side note is there a key combination for ellipsis [...] in ubuntu?

I haven't given up on ubuntu but I think I'll do some more reading before I give it another go.

Thanks

---

### Post by LowSky on 2009-04-16
you will need a Vista disk to reinstall Window's MBR, once done you can fi the partitions.

Deleting Ubuntu deleted the Grub config files which is why you can booot into Vista

---

### Post by iiiears on 2009-04-16
I hope this helps.

[https://lists.ubuntu.com/archives/ubuntu-users/2009-March/178501.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-March/178501.html)

or

[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/254009228831](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/254009228831)

~Best Wishes.

---

### Post by dondrup on 2009-04-16
can i do that this way: [http://digg.com/d1KIDe](http://digg.com/d1KIDe) by booting from the 8.10 CD? I don't have a Vista disk just the recovery disks I made from the pre-installed Vista.

---

### Post by iiiears on 2009-04-16
To preserve your windows install assuning you aren't going to re-install Ubuntu or willing to do an hours long windows install immediately. 
  I would first look for the windows recovery console in the self-created OEM restore disks. 
  Second google if you don't see it as described on the microsoft site BART's PE boot disk to see if there is an alternative recovery console there.
  Third Use an Ubuntu disk to create a /boot partition at the end of the HD (50MB would be enough) and use GRUB to boot Windows. Yeah, would of been better if OS'es were more careful with the boot sector.

ubuntuforums.org/showthread.php?t=224351

I don't understand why Ubuntu doesn't include a nifty uninstall function. Why make a user unhappy now and unwilling to try Ubuuntu again. right?


 Though this advice is of absolutely no value to you at the moment i hope that you find it helpful to use a disk imaging application back up disk partitions. Having a fast install option gives a lot of confidence. 
 It's Fast (20-30 min Windows installs and 10 minute Ubuntu Installs)

---

### Post by Grishka on 2009-04-16
> **iiiears said:**
> <SNIP>
I don't understand why Ubuntu doesn't include a nifty uninstall function. Why make a user unhappy now and unwilling to try Ubuuntu again. right?
</SNIP>

yea it does, provided you install with wubi. but pray tell, why doesn't windows provide this functionality? or mac osx, for that matter?

---

### Post by Bios Element on 2009-04-16
> **Grishka said:**
> yea it does, provided you install with wubi. but pray tell, why doesn't windows provide this functionality? or mac osx, for that matter?

Exactly. You should use wubi for testing that kinda stuff. Not a full partition install. So like Grishka said, no need to flame when it's working better then everyone else and as intended.

---

### Post by dondrup on 2009-04-16
The solution sent to me via PM is to make a SuperGrub boot CD and use it to make the change to booting from Vista. So easy that I didn't even realize it was done til I took the CD out and it started up fine. So I'm a SuperGrub convert.
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by rucadulu on 2009-04-16
If you do not plan on putting linux back on the computer you will have to boot off the vista install dvd. 

When prompted during the boot process select to go into the recovery console. 

**Do not select automated recovery as this will reinstall vista and you loose a bunch of your installed items. **

When the recover console promt appears enter your admin password if you created one during the install otherwise leave blank and hit enter. 

You then should see a promt that is like this c:> here you enter two different commands to fix the windows chain loader. 

The first is "fixboot" all one word with no quotes. hit enter 

The second command is "fixmbr" All one word with no quotes. hit enter

Then type exit hit enter and the system should reboot normal. 

Remember to remove the dvd during the reboot.

---

