---
title: "New Nvidia driver install?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by servicetech on 2009-07-10
I see nvidia has drivers 185 out for Linux but it doesn't show up in "hardware drivers". I manually downloaded them but don't know which program to use for the .run file.

---

### Post by Elfy on 2009-07-11
[http://ubuntuforums.org/showpost.php?p=7461612&postcount=2](http://ubuntuforums.org/showpost.php?p=7461612&postcount=2)

That has all the steps you need to take it seems. Certianly it is how I did it once.

---

### Post by cariboo on 2009-07-11
If you want to install the graphics drivers from Nvidia, make sure you have build-essential and dkms installed. They are both in the repositories. 
[list=1]
[*]press Ctrl-ALt-F1 to go to a console
[*] uninstall all mention of NvidiAa
```
sudo apt-get purge nvidia*
```
[*]stop gdm
```
sudo /etc/init.d/gdm stop
```
[*]assuming the driver is on your desktop, make it executable
```
chmod +x ~/Desktop/*run
```
[*]run the file
```
sudo ~/Desktop/*run
```
[*]answer yes to all the question
[*]once the driver is compiled and installed, restart gdm
```
sudo /etc/init.d/gdm start
```
[/list]

Your desktop should start up after the last command.

---

### Post by nhasian on 2009-07-11
word to the wise,  if you use this method you will need to recompile the drivers every time you update your kernel.  its much easier just to use the drivers from the repos.

---

### Post by servicetech on 2009-07-11
Does the new driver typically come with a new repo?
Odd that Nvidia released the driver June3 and we still can't get it through hardware manager.

---

### Post by philip5 on 2009-07-11
I have (among a bunch of other updated packages) the latest 185.18.14 version (for the moment) of the nvidia driver as packages in my repo for ubuntu 9.04 (jaunty) for anyone who like to give it a try and don't want to mess around installing development packages, fiddling with Xorg shutdown and compiling.

You find my repo at the url in my signature and at the site you also find instructions on how to add the repo if you have any problems with that.

Have fun!

---

### Post by Arup on 2009-07-11
Also don't forget to mark total remove in synaptic for linux restricted modules or else you might have trouble with the driver when rebooting. The nvidia drivers are the best and bring latest features for your card, the ones in repos are tested but can have issues, for instance the 180.44 in the Jaunty repos have regression with VDPAU and also has issues with FF using smaller pixmaps. Alwahys a good idea to use latest.

---

### Post by wo1fe on 2009-07-11
i have pretty much tried everything i can think of to get the new nvidia driver 185 installed. it is something that is actually need to run the apps that i run. one of the things that i have tried is in the post link below

[http://ubuntuforums.org/showthread.php?p=7592861#post7592861](http://ubuntuforums.org/showthread.php?p=7592861#post7592861)

i will try [[COLOR=#D40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104")'s way of doing it but i am not having much hope. as of right now i have a notebook with probaably about 4 pages back to front of possible fixes none have worked yet.

---

### Post by Arup on 2009-07-11
> **wo1fe said:**
> i have pretty much tried everything i can think of to get the new nvidia driver 185 installed. it is something that is actually need to run the apps that i run. one of the things that i have tried is in the post link below

[http://ubuntuforums.org/showthread.php?p=7592861#post7592861](http://ubuntuforums.org/showthread.php?p=7592861#post7592861)

i will try [[COLOR=#D40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104")'s way of doing it but i am not having much hope. as of right now i have a notebook with probaably about 4 pages back to front of possible fixes none have worked yet.

Have you tried following this to a T? [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Specially the line *If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled.*

---

### Post by philinux on 2009-07-11
Just done some digging. Seems the deb files are available from launchpad.

32bit
[https://launchpad.net/~nvidia-vdpau/+archive/ppa/+build/1103831](https://launchpad.net/~nvidia-vdpau/+archive/ppa/+build/1103831)


64bit
[https://launchpad.net/~nvidia-vdpau/+archive/ppa/+build/1103830](https://launchpad.net/~nvidia-vdpau/+archive/ppa/+build/1103830)

---

### Post by wo1fe on 2009-07-11
> If you use Ubuntu, please also ensure that the *linux-restricted-modules* or *linux-restricted-modules-common* packages have been uninstalled. Alternatively, you can edit the [FONT=Courier New]/etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common[/FONT] configuration file and disable the NVIDIA *linux-restricted* kernel modules (*nvidia*, *nvidia_legacy*) via:

i have been trying to uninstall one of them but for some reason it will not uninstall. if you read further into the posts you will see what the error i get is.

---

