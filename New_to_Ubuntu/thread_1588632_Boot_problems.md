---
title: "Boot problems"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by loseby on 2010-10-05
Quite often it wont boot from GRUB ( have win7 on another drive )and it goes to the shell which could be in chinese far as I am concerned. Did notice the following message " gave up waiting for root device " amongst the rest.

Even when it does boot its very very slow in both linux and win7. Have another hard drive I am not using and maybe it may be best to replace the other hard drive and install again ?

:confused:

btw :using the latest version of ubuntu

---

### Post by formaldehyde_spoon on 2010-10-05
Sounds to me like a dying disk is definitely a possibility.

---

### Post by sandyd on 2010-10-05
> **losbey said:**
> Quite often it wont boot from GRUB ( have win7 on another drive )and it goes to the shell which could be in chinese far as I am concerned. Did notice the following message " gave up waiting for root device " amongst the rest.

Even when it does boot its very very slow in both linux and win7. Have another hard drive I am not using and maybe it may be best to replace the other hard drive and install again ?

:confused:

btw :using the latest version of ubuntu

whats your HD's S.M.A.R.T. status?
If you havent checked, check it with something like gnome disk utility

---

### Post by loseby on 2010-10-06
> **sandyd said:**
> whats your HD's S.M.A.R.T. status?
If you havent checked, check it with something like gnome disk utility

is that already installed somewhere or do you have to download it ?


edit : found the disk utility ( system/admin ) and ran the short 10 min test and it showed as health as did the SMART there

---

### Post by loseby on 2010-10-06
well according to the disk utility there are no problems

so any other ideas?

---

### Post by loseby on 2010-10-07
any help out there ?


Jotted down some more details

> alert /dev/dish/by-uuid/e5a447af-87e4cb3-8cba-fff26b039552 does not exist...dropping to shell

now the shell doesnt help me as I have no ideas on how to use the shell

---

### Post by sandyd on 2010-10-07
> **losbey said:**
> any help out there ?


Jotted down some more details



now the shell doesnt help me as I have no ideas on how to use the shell

post output of
```

sudo blkid
```

---

### Post by drs305 on 2010-10-07
Please boot from a LiveCD and from the Desktop download and run the boot info script from here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Post the contents of the RESULTS.txt here, between "code" tags which you generate with the # icon.

---

### Post by loseby on 2010-10-13
> **sandyd said:**
> post output of
```

sudo blkid
```
/dev/sda1: UUID="e5a447af-87e4-4cb3-8cba-fff26b039552" TYPE="ext4" 
/dev/sda5: UUID="40683bc7-83ad-484a-815b-cd5107537e6e" TYPE="swap" 
/dev/sdb1: LABEL="System Reserved" UUID="042C11F42C11E18A" TYPE="ntfs" 
/dev/sdb2: UUID="8C9C17BA9C179E30" TYPE="ntfs" 
/dev/sdc1: LABEL="Seagate" UUID="8E28189528187F01" TYPE="ntfs"

---

### Post by P4man on 2010-10-13
You could try increasing the wait time.
Press alt+F2 or open a terminal and type

```
gksudo gedit /etc/default/grub
```

Find this line, or one very similar too it:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Change it to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **rootdelay=90**"
```

Save the file, close gedit. Then update grub to apply those changes:

```
sudo update-grub
```

Reboot and cross fingers.

---

