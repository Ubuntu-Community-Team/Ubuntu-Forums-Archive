---
title: "Can't update / Home directory is Desktop"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by Lupatrian on 2009-07-31
I don't know what I did for this to be happening; things are odd today:

Updates won't install because I get this message:
The upgrade needs a total of 15.7M free space on disk '/boot'. Please free at least an additional 2419k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

When I open terminal, USERNAME@USERNAME-desktop is the default directory. 

I found other posts about this being a bug, but I don't know what to do to fix it. 

USERNAME .config / userdirs-dirs.dirs =

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

THANKS! :confused:

---

### Post by bodhi.zazen on 2009-07-31
The information in the terminal, "USERNAME@USERNAME-desktop" I assume is normal.

The error message indicates your disk is full.

You can empty your trash and remove unnecessary files.

```
sudo apt-get autoclean
```

Do you have any idea what is filling your partition ? Any large multimedia files or .iso ?

---

### Post by decoherence on 2009-07-31
What is the output of

```
df -h
```

---

### Post by gastly on 2009-07-31
It looks like the updates want to install a new kernel and you don't have enough free space on your /boot drive.
Open up a terminal and type:
```
 df -h
```

And paste the output here.

And the 'USERNAME@USERNAME-desktop' is not the default directory. It's your username and after the '@' it is the name of your computer (that you specified during installation). Everything seems to be normal here, so don't fret it's not a bug ;)
If you really want to see what directory you are in type 'pwd' (stands for 'print working directory') and it will show you the directory which you are currently in.
The output of pwd should be like: **/home/USERNAME**

---

### Post by Lupatrian on 2009-07-31
I had tried autoclean; still same message on updating (sorry - I should have mentioned that).

Results of df -h:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              89G  3.4G   81G   5% /
tmpfs                 502M     0  502M   0% /lib/init/rw
varrun                502M   92K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  180K  501M   1% /dev
tmpfs                 502M   76K  502M   1% /dev/shm
lrm                   502M  2.2M  499M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda5              46M   31M   13M  71% /boot
/dev/sdc1             7.5G   11M  7.5G   1% /media/disk

FYI: When I startup, I have two Ubuntus listed: 9.04 2.2.28-13 and -11
Did an update add a version instead of overwriting? 

I installed from an official U-disk; dual boot with WinXP. I thought I had allocated plenty of space at install. 

If I need to reallocate partition sizes, I assume I'd use gParted from the install disk?  And is it the /boot partition that I need to enlarge? 

Thanks much, everyone.

---

### Post by Liolikas on 2009-07-31
/dev/sda5 46M 31M 13M 71% /boot
No enough space for 3 Ubuntu kernels. At all this partition should be something like 200Mb.
>Did an update add a version instead of overwriting? 
Yes just in case new will not work so you will end up with no start at all. After you confirm that new version works fine you can remove old or leav them as ~ safe mode.

Simply remove -11 version so it will give enough space to update.

---

### Post by gastly on 2009-07-31
Ok, so here's the problem. You don't have enough free space on your /boot partition. 
```

Results of df -h:
Filesystem Size Used Avail Use% Mounted on
/dev/sda3 89G 3.4G 81G 5% /
tmpfs 502M 0 502M 0% /lib/init/rw
varrun 502M 92K 502M 1% /var/run
varlock 502M 0 502M 0% /var/lock
udev 502M 180K 501M 1% /dev
tmpfs 502M 76K 502M 1% /dev/shm
lrm 502M 2.2M 499M 1% /lib/modules/2.6.28-13-generic/volatile
**/dev/sda5 46M 31M 13M 71% /boot**
/dev/sdc1 7.5G 11M 7.5G 1% /media/disk

```

The solution is to remove the kernel which you do not use. I recommend removing the old 2.6.28-11 kernel (or remove the one which you don't use):
```

sudo apt-get purge linux-image-2.6.28-11-generic

```

If you want to remove the other one, then use 'linux-image-2.6.28-13-generic'.

---

### Post by Lupatrian on 2009-08-01
Thank you everyone - and thanks Gastly. I uninstalled old version; update then went through fine, which was a distro upgrade. I'll wait a bit and get rid of the older one again. Y'all are the life-savers of the Noobs! Thanks much. ~:)

---

