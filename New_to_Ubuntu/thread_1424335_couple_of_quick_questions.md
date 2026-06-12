---
title: "couple of quick questions"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by JustinHicks on 2010-03-07
i have a gateway wireless keyboard Model number kr-0350 which has some extra buttons on the top that i would like to work... so i need the drivers for it and linux... any ideas on where to get them and how to install them?

Also i have an extra HDD installed in my computer but every time i reboot my computer i have to re-mount this hdd which is annoying because some of my programs use it to install to... and i have to type in my sudo password every time i do this which gets rather annoying is there a way that it can be permanently mounted? 

Thanks in advance.

---

### Post by Barriehie on 2010-03-07
> **JustinHicks said:**
> i have a gateway wireless keyboard Model number kr-0350 which has some extra buttons on the top that i would like to work... so i need the drivers for it and linux... any ideas on where to get them and how to install them?

Also i have an extra HDD installed in my computer but every time i reboot my computer i have to re-mount this hdd which is annoying because some of my programs use it to install to... and i have to type in my sudo password every time i do this which gets rather annoying is there a way that it can be permanently mounted? 

Thanks in advance.

Can't help with the keyboard but can with the drive.  Post the output of ```
sudo fdisk -l
``` and we can make it automount.

---

### Post by mechro on 2010-03-07
The Gateway keyboard may be listed as Chicony. **Go to System > Preferences > Keyboard > Layouts : Keyboard model**. Do any of the Chicony models worK?

---

### Post by JustinHicks on 2010-03-07
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa8faa8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9591    77039676   83  Linux
/dev/sda2            9592        9964     2996122+   5  Extended
/dev/sda5            9592        9964     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32e226fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001    7  HPFS/NTFS
justin@Justin:~$

---

### Post by JustinHicks on 2010-03-07
sweet, the chicony internet keyboard worked perfectly! thanks man...

---

### Post by Kaligo on 2010-03-07
For the drive you will need to edit your fstab file located in /etc/fstab
This file lists the permantly installed drives that are mounted at startup, there should already be an entry for your main linux HDD and your optical drive.

All you need to do now is add an entry for your windows HDD.

You need root privileges to edit this file so open it by typing this in a terminal window (Applications -> Accesories -> Terminal)
```
gksudo gedit /etc/fstab
```

At the bottom of that file insert the following:

```
/dev/sdb1 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```

Then save and close the file. This tells the computer to mount a NTFS formatted drive to the folder /windows with all the appropriate permissions.

Now the folder /windows probably doesn't exist yet so the next step is to create it.  Back in the terminal window type: ```
sudo mkdir /windows
```

And you're done! Just restart the computer then open the windows folder in your root directory and you should see all your windows files laid bare.

---

