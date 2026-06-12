---
title: "Windows doesn't boot up after grub reinstallation"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by sugavaneshb on 2011-07-10
Hey there every one.. I recently installed ubuntu 11.04 on my friend's dell inspiron laptop... actually dual boot with windows in separate partitions... Somehow he managd to get his windows corrupted.. so he has to re-install windows 7..after re-installation of windows and restoring grub, system was rebooted... the grub window showed on.. so there was a sigh of relief but to our surprise when we chose to boot with windows 7, the following error msg showed up...
.
.
Error: no such device {SOME-UUID}
Error: no such disk
Press any key to continue.....
.
.
When booted with ubuntu it worked fine.. so we re-installed windows.. then windows worked fine.. restored grub again.. but the same issue happened again... 

Bit of a long explanation for the problem but if you have some ideas, help us out!!!

---

### Post by toasterboy1 on 2011-07-10
You might want to check your grub menu and make sure it is pointing to the right device. I was dual booting with Windows XP and Kubuntu and I wiped my Kubuntu for a fresh install. When I rebooted Windows would not load because it had assigned a different label to the Windows partition.

---

### Post by Quackers on 2011-07-10
Did you re-install Windows from an installation disc or recover it with a set of recovery dvd's?

---

### Post by sugavaneshb on 2011-07-10
> **Quackers said:**
> Did you re-install Windows from an installation disc or recover it with a set of recovery dvd's?
We installed from the re-installation of windows 7 dvd provided by dell

---

### Post by oldfred on 2011-07-10
Recovery DVDs from vendors are just an image of the hard drive as it was when you purchased system. It then totally overwrote everything.

To confirm, run this from liveCD or take screenshot from gparted:

```
sudo fdisk -lu
```

---

### Post by Quackers on 2011-07-10
This is why I asked the question. Oldfred is correct (as usual :-) ) in that a recovery from a set of recovery dvd's will normally over-write everything on the hard drive (some Sony Vaio recovery dvd's actually give you an option - like mine :-) but most don't).
In other words, it is likely that your Ubuntu installation is gone :-(

---

### Post by Wim Sturkenboom on 2011-07-10
> **Quackers said:**
> This is why I asked the question. Oldfred is correct (as usual :-) ) in that a recovery from a set of recovery dvd's will normally over-write everything on the hard drive (some Sony Vaio recovery dvd's actually give you an option - like mine :-) but most don't).
In other words, it is likely that your Ubuntu installation is gone :-(

If I read the opening post, that is not the problem. Install Windows and Windows works, install grub and Ubuntu works.

Conclusion: no overwriting of the whole HD.

That's how I read it

Not behind a dual boot at the moment, so I don't know if grub uses the UUID as well to identify the Windows partition. The error message indicates something in that direction. You can check the UUID from within Linux with the *blkid* command

```

wim@aa0:~$ sudo blkid
/dev/sda1: LABEL="crunchbang" UUID="4e8c9e38-845f-435a-b24a-ef8c37cba4a2" TYPE="ext4" 
/dev/sda5: UUID="ef260aa3-f22f-4730-8517-8546c15cba30" TYPE="swap" 
wim@aa0:~$ 

```

---

