---
title: "remastersys live cd"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-02-14
I want to add files to the live cd. I use distcdfs because backup errors out because i have too much data on dive. I have  the modify set to exclude everything but what I want. when i add my files in the /home/user/myfiles they do not transfer to the live cd? I'm using the gui so what I'm I doing wrong?

---

### Post by ankspo71 on 2011-02-14
Hi,
I've remastered my Ubuntu before using remastersys, but I have never had a problem with my system being to large so I never had to exclude files or directories within the remastersys application itself. (sorry).

I do have several ideas though... 

Install bleachbit and clean your system with it. On a new Ubuntu installation, it can remove as much as 1gb of unecessary files. If you have upgraded your system over and over, or installed alot of packages over time, that estimate can be over 2x, 3x, 4x  larger (and so on). You can always remove bleachbit after cleaning to save even more space too.

If this excessive data is due to personal files:
Burn your downloads, movies, music, wallpapers to a cd first, or USB drive etc. Then remove them from your system.

If you have a separate partition (or hard drive) for storage:
I recommend unmounting any unneeded partitions. For instance I have 2 extra partitions where I keep all of my downloads, backups, and everything else. I would unmount those partitions to ensure that those partitions do not get included by remastersys.

```
sudo umount /path/to/partition
OR 
sudo umount -a
```
(umount -a will not unmount system partitions because they are in use)

The problems with large packages:
You might need to decide if certain large package installations are worth having on your remastered live cd. Many games can be VERY large in size, so it might be easier to uninstall them to save space, and then burn their *.deb files on a cd. *.deb files can be installed with a few clicks anyways. 

Personal Repositories:
Keryx [http://keryxproject.org/](http://keryxproject.org/) and AptOnCD [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) are two programs to create your own mini repositories. This can be a solution for several large packages that aren't fitting on your remastered ubuntu.

You can also make scripts to download and install packages too... then you would need to include the script on the remastered cd.

Last but not least, try to remember that Ubuntu all by itself is 700mb on a cd. It doens't take much to fill up a dvd too. This leaves room for a few games, a few additional apllications, and your custom desktop settings.

Hope something I've said here helps.

---

### Post by ankspo71 on 2011-02-14
Hi again,
How big is the directory /home/user/myfiles ? The total system size can't be over 12GB (including that directory).
[http://remastersys.sourceforge.net/tips.html](http://remastersys.sourceforge.net/tips.html)
> Your system size cannot exceed 4GB as that is the maximum filesize supported by ISO9660. Of course this also applies when using squahsfs. But the differece is that a 4GB squashfs can contain roughly 12GB of data within it. 

---

### Post by ankspo71 on 2011-02-14
Unless you mean your desktop settings don't get transferred over to the remastered Ubuntu ISO... I could never get it to work right either. The results were always the same for me, a remastered image but only a default Ubuntu desktop.

The instructions are to copy your user settings in your home folder, and place them in the /etc/skel folder. Next would be to change the permissions of everything in the /etc/skel folder so that they are all owned by root.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)
> Clean up history and cache and copy over the contents to /etc/skel but be sure to change the ownership of everything in /etc/skel to root.

[http://remastersys.sourceforge.net/tips.html](http://remastersys.sourceforge.net/tips.html)
> COPY WORTHY CONFIG FOLDERS TO SYSTEM WIDE FOLDERS

    Don't copy .xchat/ as it saves your username in the config.
    Don't copy .wine/ as it is very problematic, try using the global wine folder, which is (??).
    Clear all Firefox cache and GNOME Recent Documents cache right before doing this.
    Clearly, you must be a superuser to do this, so don't forget about sudo.  Now might be a good time to use sudo's -s switch so you don't need to type sudo before all these commands:


sudo -s
cp -Rf .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ /etc/skel/
cp -Rf .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/ /root/
cd /etc/skel
chown -R root:root .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/
cd /root
chown -R root:root .config/ .fontconfig/ .gconf/ .gconfd/ .gnome2/ .mozilla/ .nautilus/

Maybe more information can be found in Remastersys forum....
[http://www.geekconnection.org/remastersys/forums/index.php](http://www.geekconnection.org/remastersys/forums/index.php)

---

