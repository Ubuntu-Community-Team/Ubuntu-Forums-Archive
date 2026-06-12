---
title: "No dual boot option for Ubuntu"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by webheadjunky on 2011-08-22
Hi there

Installed Ubuntu via wubi on my wife's laptop several weeks ago and it was working great

Sadly Windoze 7 developed a serious problem today and I had to do a factory restore and although I managed to backup and restore docs and getting Windoze working again, I seem to have sacrificed Ubuntu:cry:

I can still see an Ubuntu folder that is 17.2GB in size but have no idea what to do with it

Is there anyway for me to return to the dual boot without jeopardising my wife's Windoze? Has taken me over 2 hrs so far and really don't want to go through all that again....

Thanks in advance

---

### Post by beew on 2011-08-22
Wubi is not dual boot. It is sort of a castrated version of Ubuntu installled in Windows meant only as a demo. You can't save WUBI if you have to reinstall WIndiows, it will be gone. I just hope that they are more clear about this point so that people don't mistaken WUBI with a real install of Ubuntu.

To create a real dual boot you have to partition your hard drive and put Ubuntu on a separate partition.

---

### Post by Jonny87 on 2011-08-22
> **beew said:**
> Wubi is not dual boot. It is sort of a castrated version of Ubuntu installled in Windows meant only as a demo. You can't save WUBI if you have to reinstall WIndiows, it will be gone. I just hope that they are more clear about this point so that people don't mistaken WUBI with a real install of Ubuntu.

To create a real dual boot you have to partition your hard drive and put Ubuntu on a separate partition.

This is probably your best option.

However if you really need to restore the Wubi you could try adding it to the windows boot.ini though I'm not sure what the configuration would be for it. Try looking it up. EasyBCD may make it easier. Though I'm not sure if this will work at all, just an idea that I'd try if I was in your position.

---

### Post by Karlchen on 2011-08-22
[B]<side issue>
[/B]
> **beew said:**
> Wubi is not dual boot.Well, Wubi is dual boot. If you boot (Wubi) Ubuntu, you will launch Ubuntu. No Windows component will be active. Only the Windows bootmgr will be started and hand over control to Ubuntu.
The main difference between Ubuntu installed on a separate partition and a Ubuntu Wubi installation is that Ubuntu will use a large file formatted as Ext4 as its root.disk and another smaller file as its swap partition.
Wubi depends on the Windows NTFS partition where its root.disk and swap disk are located. But it does not run under Windows. 

> It is sort of a castrated version of Ubuntu installled in Windows meant only as a demo.It is a complete Ubuntu installation, not castrated in any way. I have been using a Wubi installation of Lucid Lynx for more than a year now for my everyday office work. So much for the castration and for demo mode. :wink:

> You can't save WUBI if you have to reinstall WIndiows, it will be gone.This will be true in case the Ubuntu root.disk and swap file are located on the Windows system drive and in case you format this drive when re-installing Windows. Yet, in the thread starter's case the Ubuntu folder is still present. Therefore it should be possible to re-activate the Wubi installation, though it may not be too trivial. In particular it will be necessary to find out / know the UUID which had been assigned to the root.disk. Anyway, it is not impossible to re-activate a Wubi installation as long as the Wubi folder and its content are still present.

I would not be amazed if the steps to reactivate such a Wubi installation could be found inside the [**Sticky: WUBI Mega Thread**]("http://ubuntuforums.org/showthread.php?t=1639198&highlight=WUBI+Mega+Thread"), because Webheadjunky is not the only person and not the first person to experience the problem that he reported. :wink:

Cheers,
Karl

[B]</side issue>
[/B]

---

### Post by beew on 2011-08-22
> **Karlchen said:**
> [B]<side issue>
[/B]
Well, Wubi is dual boot. I

[/B]
snip ..

No it is not. If it were you wouldn't have to use the ntfs system and removing Windows should have no effect on Ubuntu.

Instead of going through great length to run an unstable shadow of Ubuntu which depends on Windows (whether it technically runs inside WIndows or not) why not just do a real dual boot if OP really likes Ubuntu?

---

### Post by Frogs Hair on 2011-08-22
It is a complete Ubuntu installation, not castrated in any way. I have been using a Wubi installation of Lucid Lynx for more than a year now for my everyday office work. So much for the castration and for demo mode.

Wubi is meant for trial use according to the Ubuntu documentation and its developers . A wubi installation cannot hibernate due lack of swap , a 30 Gb maximum of disc space , and is installed as a file and not on its own partition.

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)

I agree with Karlchen , see the Mega thread because the problem has been addressed before. You have already discovered Wubi's biggest issue in that is dependent on the health of the Windows operating system .

---

### Post by bcbc on 2011-08-22
You can totally recover the wubi install. You can also [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") to a full install from the wubi root.disk. Despite what beew says... the root.disk contains a full, un"castrated" ubuntu install.

If you just want to get the wubi booting, you can try this link: [http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)

There's another way to do it without using BCDedit: e.g.
1 Rename \ubuntu directory to \ubuntuold
2 Reinstall the same release of Wubi to the same windows drive
3 After the wubi tells you to reboot, first copy the \ubuntuold\disks\*.disk files into the new \ubuntu\disks directory

Either way - safeguard the root.disk file. Most people only have the one virtual disk and it contains everything.


PS I don't disagree that a full install is better ;) just that there are many legitimate reasons - and there's no need to resort to dramatic made-up claims about Wubi - to justify this. (especially from someone who doesn't seem to have used Wubi ever).

---

### Post by Jonny87 on 2011-08-22
> **bcbc said:**
> You can totally recover the wubi install. You can also [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") to a full install from the wubi root.disk. 

Wish I had know that a few weeks ago. I deleted my wubi install when changing to a partitioned setup because I didn't think it was worth trying to back it all up. Linux is so much easier than M$ Windows to start from scratch.

> **bcbc said:**
> 
If you just want to get the wubi booting, you can try this link: [http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)

There's another way to do it without using BCDedit: e.g.
1 Rename \ubuntu directory to \ubuntuold
2 Reinstall the same release of Wubi to the same windows drive
3 After the wubi tells you to reboot, first copy the \ubuntuold\disks\*.disk files into the new \ubuntu\disks directory

I thought it was possible. Thanks for that documention,  to confirm that. I have booked marked. I love it when I learn something new.

> **bcbc said:**
> 
PS I don't disagree that a full install is better ;) just that there are many legitimate reasons - and there's no need to resort to dramatic made-up claims about Wubi - to justify this. (especially from someone who doesn't seem to have used Wubi ever).

I agree, one big advantage as you kinda pointed out in your second solution is that backing up a wubi install is as easy as copying the root.disk to another location.

---

### Post by webheadjunky on 2011-08-24
> **bcbc said:**
> You can totally recover the wubi install. You can also [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") to a full install from the wubi root.disk. Despite what beew says... the root.disk contains a full, un"castrated" ubuntu install.

If you just want to get the wubi booting, you can try this link: [http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)

There's another way to do it without using BCDedit: e.g.
1 Rename \ubuntu directory to \ubuntuold
2 Reinstall the same release of Wubi to the same windows drive
3 After the wubi tells you to reboot, first copy the \ubuntuold\disks\*.disk files into the new \ubuntu\disks directory

Either way - safeguard the root.disk file. Most people only have the one virtual disk and it contains everything.


PS I don't disagree that a full install is better ;) just that there are many legitimate reasons - and there's no need to resort to dramatic made-up claims about Wubi - to justify this. (especially from someone who doesn't seem to have used Wubi ever).


Dear BCBC

Thanks to you and others for the advice. Downloaded BCDEdit and was up and running again in 5 minutes. In fact, I am typing this from within Ubuntu. Awesome!

So why Wubi for me then?

I already have an older linux only desktop running Kubuntu and an old linux only laptop running Mint. This is my wife's Windoze 7 laptop and I was just curious to see how the Wubi thing would work and I must confess I can see no difference between this and my other machines.

As far as I can tell, I can still access the same software repositories and download the same stuff.

So I'm happy to continue with this

Thanks again everyone

Raaj:)

---

### Post by bcbc on 2011-08-24
> **webheadjunky said:**
> Dear BCBC

Thanks to you and others for the advice. Downloaded BCDEdit and was up and running again in 5 minutes. In fact, I am typing this from within Ubuntu. Awesome!

So why Wubi for me then?

I already have an older linux only desktop running Kubuntu and an old linux only laptop running Mint. This is my wife's Windoze 7 laptop and I was just curious to see how the Wubi thing would work and I must confess I can see no difference between this and my other machines.

As far as I can tell, I can still access the same software repositories and download the same stuff.

So I'm happy to continue with this

Thanks again everyone

Raaj:)
Great! I'm glad it's working. 

PS I think you meant easyBCD since bcdedit is a built-in Windows command. Also, as you confirm, there is no difference with Wubi and some people choose to use Wubi for their own reasons. However, every now and then, you'll see someone have problems with ntfs corruption or root.disk corruption, perhaps due to [hard shutdowns]("https://wiki.ubuntu.com/WubiGuide#How_to_reboot_cleanly_even_when_the_keyboard.2BAC8-mouse_are_frozen") or perhaps other causes. So, my advice is to keep important data backed up. Other than that, the only difference is it's a little slower and you can't hibernate.

---

