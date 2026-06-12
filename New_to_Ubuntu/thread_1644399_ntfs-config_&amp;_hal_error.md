---
title: "ntfs-config &amp; hal error"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by tanmoykrthakur on 2010-12-13
I INSTALL ntfs-config & hal in ubuntu 10.10, it auto mount ntfs drive with some error (error mounting some drive, press s skip or m to manual). so i completely remove ntfs-config & hal but still ntfs drive are mounting with this error.
i want get back my default ntfs setting

ntfs drive are mount in read only mood
i remove ntfs-config & hal
i want get back my default ntfs setting, where i click a drive and it mount (ubuntu default setting)

---

### Post by MooPi on 2010-12-13
Your going to have to edit /etc/fstab
Can you give us the results of ```
sudo blkid
```With that information we can help you edit.

---

### Post by tanmoykrthakur on 2010-12-13
/dev/sda1: LABEL="System Reserved" UUID="A2FC4A02FC49D0E9" TYPE="ntfs" 
/dev/sda2: UUID="5440256C40255650" TYPE="ntfs" 
/dev/sda3: LABEL="Application & Document" UUID="5202014302012D93" TYPE="ntfs" 
/dev/sda5: LABEL="Entertainment" UUID="2E106E90106E5F39" TYPE="ntfs" 
/dev/sda6: UUID="6C007B91007B60CE" TYPE="ntfs" 
/dev/sda7: UUID="627A7DEF7A7DBFF9" TYPE="ntfs" 
/dev/sda8: UUID="0dea35a9-f650-42a3-a7d5-0da33584ff58" TYPE="ext4" 
/dev/sda9: UUID="d506d613-0024-42fd-a051-80e1b3b4d458" TYPE="swap" 
/dev/sda10: UUID="8134b485-b37f-45e8-ae49-064c13a08c1f" TYPE="ext4"

---

### Post by tanmoykrthakur on 2010-12-13
i remove ntfs-config & hal with this command 
sudo apt-get --purge remove

---

### Post by tajiknomi on 2010-12-13
> **tanmoykrthakur said:**
> i remove ntfs-config & hal with this command 
sudo apt-get --purge remove

[SIZE=2]Sorry for inter-fairing
...[/SIZE]
[SIZE=2]Reinstall ntfs-config , and open it ,it will show your ntfs-drive, just ***uncheck*** your drives, and it will get you back to your default FSTAB,

You can check out the screen-shot,which i had attached...




[/SIZE]

---

### Post by tanmoykrthakur on 2010-12-13
i reinstall & try this, but it is not working

---

### Post by tajiknomi on 2010-12-13
> **tanmoykrthakur said:**
> i reinstall & try this, but it is not working

[SIZE=2]I don't know why its not Working, anyway...edit your fstab...

_1._ to find UUID, Current-Drives & filesystem type, run the following in a terminal[/SIZE]:-

```
sudo blkid -c /dev/null
```[SIZE=2]it should give something like 
/dev/sdb3: LABEL="Extras" UUID="**0C2A39615EAFB871**" TYPE="**ntfs**" [/SIZE]

[SIZE=2]2) Create the mount point:-

[/SIZE]```
sudo mkdir **/media/Example**
```[SIZE=2]_3._ then edit fstab[/SIZE]:-

```
sudo gedit /etc/fstab
```[SIZE=2]Add each Line for each-drive,which you want to mount at boot time:-[/SIZE]For e.g

```
UUID=**0C2A39615EAFB871  /media/Extras  ****ntfs  **defaults  0  0
```***[SIZE=2]please note[/SIZE]*** : [SIZE=2]While editing, you shouldn't remove the line/or above this Line:-[/SIZE]

```
[SIZE=3]proc    /proc    proc    nodev,noexec,nosuid    0    0[/SIZE]
```[SIZE=2]it will be much better to have a Backup of your FSTAB before you edit..

I had also attached a ***screen-shot*** of My-FSTAB, and highlighted those Drives,which i had ***manually Edited***...Good-Luck :p
[/SIZE]

---

### Post by tanmoykrthakur on 2010-12-13
i not want to drive mount at boot time, it is already happening, i want to get back ubunru default setting,where i click a drive and it mount

---

### Post by tajiknomi on 2010-12-13
> **tanmoykrthakur said:**
> i not want to drive mount at boot time, it is already happening, i want to get back ubunru default setting,where i click a drive and it mount

[SIZE=2]ok...paste the output of this :-

gedit /etc/fstab
[/SIZE]

---

### Post by tanmoykrthakur on 2010-12-13
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda10 :
UUID=8134b485-b37f-45e8-ae49-064c13a08c1f    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda8 :
UUID=0dea35a9-f650-42a3-a7d5-0da33584ff58    /boot    ext4    defaults    0    2
/dev/sda7    /media/627A7DEF7A7DBFF9    ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev    0    0
#Entry for /dev/sda3 :
UUID=5202014302012D93    /media/Application___Document    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda5 :
UUID=2E106E90106E5F39    /media/Entertainment    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda1 :
UUID=A2FC4A02FC49D0E9    /media/System_Reserved    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda2 :
UUID=5440256C40255650    /media/sda2    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda6 :
UUID=6C007B91007B60CE    /media/sda6    ntfs    defaults,nls=utf8,umask=0222    0    0
/dev/sda7    /media/sda7    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda9 :
UUID=d506d613-0024-42fd-a051-80e1b3b4d458    none    swap    sw    0    0

---

### Post by tajiknomi on 2010-12-13
[SIZE=2]Ok i have Edited it, it will bring you back to your Default, Download your fstab from the link > [/SIZE][http://dl.dropbox.com/u/16158781/fstab](http://dl.dropbox.com/u/16158781/fstab)

---

### Post by tanmoykrthakur on 2010-12-13
thanks friend, its work perfectly. i am a windows user & recently i install ubuntu 10.10 & try to learn. can you give me some link where i learn about command (terminal), man command is for advance user

---

### Post by tajiknomi on 2010-12-13
> **tanmoykrthakur said:**
> thanks friend, its work perfectly. i am a windows user & recently i install ubuntu 10.10 & try to learn. can you give me some link where i learn about command (terminal), man command is for advance user

Basics Command > [https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

ALSO>[SIZE=2]> [/SIZE][http://oreilly.com/linux/command-directory/](http://oreilly.com/linux/command-directory/)

[SIZE=2]Starting-place > [/SIZE][https://help.ubuntu.com/community](https://help.ubuntu.com/community)

[SIZE=2]You can now Mark the ***thread-as-solved ***in ***thread-tools*** Above.

Good-Luck :p
[/SIZE]

---

### Post by snappwrench on 2011-10-19
Hopefully someone sees this since there hasn't been a reply in so long. I've looked through the forums and this is the closest i could find to my prob. I'm running 10.10 w/KDE 4.4 installed and i installed ntfs config like an idiot when i didn't need to and now even when i uninstall it i'm still asked to mount so and so drive at start up. How can i get rid of this when i restart or boot up?

---

