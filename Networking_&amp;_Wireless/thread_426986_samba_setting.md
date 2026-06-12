---
title: "samba setting ??"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by thoeng on 2007-04-29
Hi All,

I have installed  feisty fawn + beryl AIGLX for my laptop and feisty fawn _ beryl + nVidia + enable NTFS write-read successfully from this great forum. however there are few more things to even make my computers at home healthier. Here is my situation at my home...

I have 4 PC at home 3 laptops (1 among them is feisty fawn) and a desktop (feisty fawn), I used to transfer files from a PC to another frequently. But installing linux among 2 of the PCs disable me to transfer files by router anymore.

Short word is, how can i enabled networking on my linux - windows PC environment easily (given that i am newbie) i have heard about samba or stuff like that but i have no idea to install and use it to enable access among my computers.

Also i have a question on how to enabled VPN to work on feisty fawn ? and what software can be used in subtitute of SQL studio on linux

i am sorry for bunch of question but all of this is to make sure that i won't turn back on windows again 


Cheers,

---

### Post by jhnthn on 2007-04-29
Type smb:// into the address bar in nautilus and you should see the other computers in the windows network.

Also, if you right click on a folder in nautilus and click "Share folder" a dialogue will pop up and tell you to install something to be able to share stuff.

At least that's how it works for me.

---

### Post by thoeng on 2007-04-29
Thanks for the reply .

Are you saying that samba has been installed by default on feisty fawn ?

Do i have to set anything elses on windows network protocols or linux ?
how about if i want to access other linux pcs on the network or vice versa (windows pc need to access linux pc)

again many thanks for the reply

---

### Post by jhnthn on 2007-04-29
Yeah some samba stuff does appear to be installed by default (type smb then hit tab in a terminal and you'll see). Though you have to install some other stuff to enable shares on Ubuntu.

I don't think you need to do anything else. Just enable shares then browse your network from windows and you should see the shares on your Ubuntu computer.

Sorry, I'm not sure about sharing between other Linux PCs. I only have one computer with linux and a laptop with windows.

---

### Post by thoeng on 2007-04-29
Hi Thanks,

I have tried to install samba on both linux PC 1st to find out if it works. Currently after downloading and installing samba and enabling shared folders on both linux ( both doman: mshome, and wins server: empty),opened nautilus and typed smb:// then i can see both computers there but after click on the icon there is an error message says : 

the folder content can not be displayed.
sorry couldn't display all the content of "windows network: meta4"

meta4 is the name of other Linux laptop also samba installed, shared folders enabled.


what is the difference between windows (SMB) and unix (NFS) networks ? which one should i pick. if i pick unix (NFS) i think then both linux PC will be inaccessible for other windows PC

---

### Post by jhnthn on 2007-04-29
A quick search on the [Ubuntu wiki](http://wiki.ubuntu.com) finds this:
[list]
[*][Setting up samba](https://help.ubuntu.com/community/SettingUpSamba)
[*][Comprehensive samba guide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)
[*][NFSv4 howto](https://help.ubuntu.com/community/NFSv4Howto)
[*][Setting up NFS howto](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[/list]

They might help.

Theres a good little intro to what samba is and what it's needed for in *Setting up samba*.

---

### Post by thoeng on 2007-04-29
hi again ..

after installing samba on both linuxes and windows (well nothing to do much on windows system, just to make sure file and printer sharing are ticked)

Now its getting crazy. Linux Desktop were unable to detect at all any shared or networked computer, linux laptop able to see all networked computer but no folder accessible, windows laptop both can see nothing as the same the desktop.

I am getting frustrate here and it seems it is more complicated than i thought. Please help !!

---

### Post by jdunn on 2007-04-29
SAMBA is fubar'd in Feisty but it worked fine in previous revisions.  Some people have had luck following the advice in this bug report.  I haven't had luck.  Try anyway

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/95460)

---

### Post by thoeng on 2007-04-29
is this really a bug ??

I can not even see the shared folder from linux to linux ... Yesterday i managed to do for about 15 mins and then  simply can not access anything.


The network is really unrealible sometimes it is able to detect networked computers sometimes it just failed.


Can somebody provide me guide to build network between linux to linux and linux to windows in simple way ?? i would like to rebuild the network from scratch

---

### Post by jdunn on 2007-04-29
yes, its a bug

---

### Post by thoeng on 2007-04-30
Hi all,

I am now begin to see light of the sun, updated situation:

1. Linux laptop has able to access shared folders (read & wirite) to the Linux desktop
2. Windows laptop has now access to linux desktop


but whats lack yet:
1. None of linux (laptop & desktop) is able to access shared folders of windows system (both laptop)
2. Windows laptop is not yet able to access linux laptop
3. Linux desktop is not yet able to access linux laptop


Any hint guys ??

---

### Post by thoeng on 2007-05-06
bump.


Any help guys

---

### Post by thoeng on 2007-05-12
bump.


anyone

---

