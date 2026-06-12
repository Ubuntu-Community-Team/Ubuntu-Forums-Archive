---
title: "create a system disc"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by malp on 2011-02-04
Hi
Is there a way to create an installation disc for my ubuntu 10.10 from the system as it is now.
What I mean is that I have customised the desktop and added a lot of apps that I needed and would like to be able to put the system back as it is now for instance if a hard disc failed instead of having to download all the apps and customisations again.
Please note I have next to no knowledge of the terminal commands yet but every one has to start somewhere.
thanks for any help
malc

---

### Post by cavh on 2011-02-04
Do a search on the Ubuntu forums for Remastersys and Clonezilla

---

### Post by CadetD on 2011-02-04
This would require a whole lot of disk space. It may be easier to use dpkg to list the existing packages and redirect to a file. Then you can feed that file back to dpkg to reinstall all those packages on your new system. 

You get a clean system with all your previous apps. 
(Sorry, not at my box now, would send you the commands)

---

### Post by oldfred on 2011-02-04
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

Since I converted to clean installs I install the system and update with all my installed apps. I only backup /home, some settings from /etc where I have manually edited the file, /data where most of my data is, a current run of boot info script to document system, & a current list of apps.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

---

### Post by malp on 2011-02-04
hi 
Sorry i dont understand this bit

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings

does this backup your installed apps so that you can recover them  later and does it back up the desktop configuration. I dont want to reinstall the system now but if i need to in the future i want to put it back as its now. What does dpkg -- get-selections do
thanks for explaining but please note you are dealing with someone who has only used windows before.
malc

---

### Post by oldfred on 2011-02-04
dpkg just makes a list of installed apps. If you install a newer version of Ubuntu it will install the newer versions of the apps. All your configurations are in /home in hidden files & folders. Some data like all of firefox & thunderbird are also in /home hidden folders. so you have to backup /home & its hidden files.

List looks like this:
```
abiword                        install
abiword-common                    install
abiword-plugin-grammar                install
abiword-plugin-mathview                install
acpi-support                    install

```If you are interested in a list with more explanation, but it cannot be sued to reinstall:
List with explanations of programs, not for reinstall
dpkg -l > ~/Desktop/installed_programs.txt

```
ii  abiword                               2.8.6-0ubuntu1                                    efficient, featureful word processor with collaboration
ii  abiword-common                        2.8.6-0ubuntu1                                    efficient, featureful word processor with collaboration -- common files
ii  abiword-plugin-grammar                2.8.6-0ubuntu1                                    grammar checking plugin for AbiWord
ii  abiword-plugin-mathview               2.8.6-0ubuntu1                                    equation editor plugin for AbiWord


```Only if you are running same version and have not housecleaned:
Location of downloaded debs
/var/cache/apt/archives/

---

### Post by malp on 2011-02-04
Hello again
Thanks for the explanatiom I have run the command in the terminal.
dpkg --get-selections > ubuntu-files
It is like redirecting the output in a windows command window to a text file. It produces as you say a file called ubuntu-files in my directory showing installed apps and I have also shown hidden files and there is a lot more there than I thought. 
From what I understand all I have to do is back up my directory as most of the system settings for me are in there. Does the other terminal command
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade
restore the apps list to the system or does it restore the apps list and then reinstall the apps. If it does not reinstall the apps will this be done on the first update.
all the best
malc

---

### Post by oldfred on 2011-02-04
The first part of the command add the apps to the list of too be installed the second command (after the &&)downloads & installs the apps. It will download them fresh. If you have upgraded/reinstalled a new version, you get the new versions if the app has been updated. If it is already installed (many in list will be the defaults from an install) it will not reinstall them.

User settings for you are in  /home. Each user may have different settings in /home as Linux is a multiuser system by default. System settings like custom video, grub2 settings, special Ethernet settings or anything else that might be considered system wide is usually in /etc.  I only save a copy of those I have manually edited and sometimes they change from version to version, so you should not just copy files from /etc back.

---

### Post by malp on 2011-02-05
Hi
Thankyou oldfred its just what I needed and I have learnt something as well.
malc

---

