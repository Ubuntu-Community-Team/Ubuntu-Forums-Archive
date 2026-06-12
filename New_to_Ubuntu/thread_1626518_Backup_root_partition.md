---
title: "Backup root partition"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by mikeserv on 2010-11-20
Ok, I've got 10.04 netbook edition running on my HP Mini. I have separate partitions mounted for / and /home. I want to wipe / and install 10.10 64-bit (my netbook is 64-bit but netbook edition only comes in 32-bit). I also want the full version for when I connect my netbook to my monitor at home (I have a spare set of keyboard, mouse, monitor setup in the garage on an old desk specifically for this purpose) because the netbook shell plain old sucks (I know netbook edition comes with the full gnome interface, too, but I wound up over-writing it for my user-name because I wanted to be able to edit the netbook edition gnome-bar).

Anyway, before I go ahead with this I want to run a backup of / and NOT /home. I know there are some guides here and there for runnning backups with tar, but I'm hoping someone out there can help me tailor the command to suit my needs? I just want to get a backup of my system before I wipe it just in case I find I don't like 10.10 (for one thing I know that the netbook shell has dramatically changed).

Thanks everybody for any help you can provide.

-Mike

---

### Post by Jahid65 on 2010-11-20
you can use remastersys to backup or mak a clone of your current ubuntu installation. 

Open terminal & run these...
```
sudo gedit /etc/apt/source.list
```A file will open in gedit. Add the following lines....
```
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/
```Save the file. Then
```
sudo apt-get update
sudo apt-get install remastersys
```Then to backup your root type this
```
sudo remastersys dist
```This may take 15-20 minutes depending on your machine. When done you will find an bootable ISO named custom.iso in File system => home > remastersys(/home/remastersys) folder.
you should have 512 MB ram to run this.

Caution: Be sure that **ubiquity** package is installed along with ISO. Because this package controls the installer option. I suggest you first install **ubiquity** from software center or synaptic.

---

### Post by Rubi1200 on 2010-11-20
Clonezilla might be another option worth considering:
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by oldfred on 2010-11-20
If you have installed a lot of applications, you can make a list of installed apps and then reinstall in your 64 bit version.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

 dpkg --get-selections | grep -v deinstall > ubuntu-files
or
 dpkg --get-selections > ubuntu-files

---

### Post by mikeserv on 2010-11-20
Thanks, guys. It turns out I already had remastersys installed. I tried the 10.10 beta netbook edition a coupla months ago and before I did I made an live image of my setup. I didn't like the 10.10 beta and reverted. I wonder why it took you guys to remind me of that?

That package list is pretty nice, too. I'm gonna go ahead with that. I wonder, though, if I have outside software sources will it also back those up?

-Mike

---

### Post by oldfred on 2010-11-20
If you installed thru dpkg it will list them but not install them. If you have added sources you should back up those or keep a list. Note that Ubuntu version will be different so sources list cannot be used without major edits.

The list for install is just a text list without versions or other info.

If you want a list with more info.
List with explanations of programs, not for reinstall
dpkg -l > ~/Desktop/installed_programs.txt

$ vim /etc/apt/sources.list
or
sudo cp /etc/apt/sources.list ~/sources.list.backup

---

