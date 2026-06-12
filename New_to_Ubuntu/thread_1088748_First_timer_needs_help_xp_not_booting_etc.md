---
title: "First timer needs help: xp not booting etc"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by 0z0 on 2009-03-06
hello ubuntu forums; this is my first linux experience, so far so good and especially ubuntu rocks :D.Its user friendly and setting internet connection (network) is not difficult as i thought to be.Now first time using my broadband using ubuntu(8.0.4), not so bad:)

i have a problem of dual booting with XP i searched the forum but i could not find a suitable answer for my problem.

i have two HDD 40GB and 500GB.

40GB is partitions into two 20gb each; one for XP and other for ubuntu with 2GB swap space.

my problem is i cant boot xp (not yet ready to give up :)).the grub boot loaders shows xp pro.

during installation i set boot loader for (hd0,0)

any help would be appreciated, thanks

---

### Post by bsharp on 2009-03-06
can you post your /etc/grub/menu.lst?

---

### Post by Darkoan on 2009-03-06
Hi, Im a noob too, and had all sorts of dramas with my Ubuntu 8.10/ XP dual boot (Windows was the culprit).

Please provide more info - what do you mean it doesnt boot? Its in the grub selections, what happens after you press enter?

How did you partition exactly?

Some pro is going to ask you to look at your menu.lst file (your Grub boot config)

---

### Post by 0z0 on 2009-03-06
thanks here it is; when i press enter nothing happens just give me back grub interface.

```
Edited:Not needed

```

---

### Post by bsharp on 2009-03-06
Ah, I just reread your first post and I think the problem is that you told the installer to install GRUB to (hd0,0) which is the first partition instead of the MBR.

Ultimately, what I think you are going to have to do is:
```
sudo grub-install /dev/sda
```

That *should* fix it.

Edit: You might need to boot up from your XP disc, go to the recovery console, and type
```
fixboot
```
to restore the XP bootloader.

---

### Post by 0z0 on 2009-03-06
many thanks ;-) 

i will try and be back as soon as possible.

thanks again

---

### Post by 0z0 on 2009-03-06
Am i doing something wrong? bootfix give me back xp but not grub loader

i ran that sudo grub-install/dev/sda using alt+F2; i ran that command but nothing happened.

i am now on xp ;-)

---

### Post by lundholmj on 2009-03-06
Boot with the live cd and follow these instructions.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by 0z0 on 2009-03-06
> **lundholmj said:**
> Boot with the live cd and follow these instructions.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

thanks ill try that; hope i make it worked :)

Edited:Works perfectly thanks to[COLOR="PaleGreen"] bsharp[/COLOR],[COLOR="Lime"]Darkoan [/COLOR]and [COLOR="Green"]lundholmj[/COLOR]

---

