---
title: "Home Network - looking for advice!!!"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by juny20 on 2008-11-17
Hello everyone. Ok, I have been using Ubuntu since 7.10, before that Fedora. Anyways, I have two laptops and one desktop. The desktop is a dual boot of XP and Ubuntu 8.04, one laptop is running 8.04 exclusively and the other is running Kubuntu 8.10. I just ordered a 500gb external hardrive and I would like to set-up a home network. I was thinking about buying another desktop to accomplish this. My question is; how to best accomplish this? I would like to have the hard drive as the "network" drive with access to it from all the computers. I also have a Brother MFC 420CN printer that I want to set-up as a network printer.

I have a D-Link DI524 router that will be the main component of the network for now, although I was thinking about upgrading to a N range router. My main objective is to access the music and pictures collection from any computer and be able to save files to it. The desktop will be on windows some times for my wife. 

Any ideas, suggestions, and advice will be extremely appreciated!!!
Thanks!!!

---

### Post by juny20 on 2008-11-19
Hello Ubuntu gurus out there! I would appreciate any input on this! I received my 500gb external hard drive today. Should I partition it as EXT3 for Ubuntu or as NSTF for Windows? Any ideas as to how best for me to accomplish a nice home network?

---

### Post by SpaceTeddy on 2008-11-19
i know nothing about "the best way" - but i can tell you how it works my way. I build myself a server, and i am servicing 4 Windows XP and 2 Ubuntu clients at the moment.

i personally am a big a fan sshfs. it is simple, elegant and fast (not to mention encrypted) and easy to install. the downside is - there is no automatic share distribution (but then, you don't need that, either)... so here is what i would do. 

create your server.
format the drive with ext3 and enable acl on it. Then setup the directory permission and users you want to be able to access the drive. Lastly, install the openssh server on the server and you are pretty much done.

for a client - on ubuntu you need sshfs (via fuse). add the user to fuse group, generate a public/private for the user and distribute the public key to the server. Now - you can mount the server with one command and passwordless into your own filesystem - it will even show up as a drive. 

The other ways i can think of are samba and nfs - samba i would not really recommend, and nfs i have no idea about as i have never used it. 

my two cent...

---

### Post by MarkM06 on 2008-11-19
Hey,

If I were you I would format it as NTFS because Ubuntu can read NTFS but xp cannot read EXT3.

I'm not quite sure how to share the drive over a network in Ubuntu, it should be fairly easy to do or at least find information about though.

Mark

---

### Post by SpaceTeddy on 2008-11-19
wrong... xp can read ext2 and ext3... 
check this out
[[COLOR="Blue"]http://www.fs-driver.org/[/COLOR]]("http://www.fs-driver.org/")

---

### Post by him610 on 2008-11-19
You might want to check out freenas - follow the link below

[http://www.freenas.org/]("http://www.freenas.org/")

My network is a mixture: wired and wireless routers, switches, network printer, machines running WinXP, Vista, Ubuntu 8.10, Xubuntu 8.10 and 8.04, Linux Linpus, and one ten year old Dell Dimension XPS/266 running "freenas". Each workstation can access the files, photos, and mp3s residing on the disk drives on the freenas server with no problems whatsoever. You may have to install and configure Samba on each machine; however, I believe it may be installed by default with Ubuntu.

Download the freenas documentation; give it a good read to decide if it will do what you want to do then go from there.

Nothin' tried is nothin' gained.

---

### Post by Cracauer on 2008-11-19
A Mac Mini with Samba and NFS as the "network drive". Or a PC notebook.

Some Linksys 54GL or whatever with openwrt or whatever as router.

Then you can nuke and reboot your work computers as much as you wish, you'll always find your data.

---

### Post by frenchsquared on 2008-11-19
samba

THis inst hard, put the new harddrive in one of the linux machines then install and configure samba. I have 35pc's 6mac's and a few linux machines that can all share one 750gb hard drive as a network share. 

Everone is making this seem very hard because not many know how to properly set up a network. Just spend sometime google samba and you will be fine.

---

### Post by juny20 on 2008-11-21
Thank you all for your help.
I am going to research Samba.
I'll post once I figure everything out.

---

### Post by juny20 on 2008-11-21
frenchsquared, thanks for your advice. One questions; how did you format the hard drive? I have a Western Digital My Book edition, 500gb, and it was factory formatted as FAT32. I though about re-formatting, but don't know if I should?

---

### Post by frenchsquared on 2008-11-21
I used linux to format it ext3 with some command like mkfs -t ext3 /dev/hdb1

Then in the Samba configuration I pointed the path of the share folder to the root directory on the new hard drive.

I new almost nothing about linux when I got Samba working. There are alot of tutorials on the configuration. Just read and keep trying. 

Remember that in Windows you can map a newtwork share and make the samba share show as a network drive in my computer.

Good Luck

---

### Post by MarkM06 on 2009-04-17
> **SpaceTeddy said:**
> wrong... xp can read ext2 and ext3... 
check this out
[[COLOR="Blue"]http://www.fs-driver.org/[/COLOR]]("http://www.fs-driver.org/")

I was referring to a basic installation without third-party software.

---

