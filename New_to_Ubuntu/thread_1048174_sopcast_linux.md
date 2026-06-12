---
title: "sopcast linux"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by NorthWesterUK on 2009-01-23
3 Easy Steps

Step: 1

Install sopcast on linux download this [http://download.sopcast.cn/download/sp-auth.tgz](http://download.sopcast.cn/download/sp-auth.tgz) and save to your home folder, then extract it, then in the extracted folder (sp-auth) there is a file called (sp-sc-auth) rename the file to (sp-sc) 

Then in the Terminal (command prompt) type  

sudo nautilus 


This will open a file browser  

Select (File System) then open the (bin) folder, drag and drop the (sp-sc) file you renamed into the (bin) folder.

close the file browser's and Terminal when you are done.


Step: 2

Download this [http://www.sopcast.com/download/libstdcpp5.tgz](http://www.sopcast.com/download/libstdcpp5.tgz) and save to home folder, extract it, then in the extracted folder (usr) open the folder (lib) there will be two file's (libstdc++.so.5) and (libstdc++.so.5.0.1) you need to drag and drop these two file's into the (bin) folder.

 Same process as step: 1

In Terminal (command prompt) type 

sudo nautilus 

This will open a file browser  

Select (File System) then open the (bin) folder, drag and drop the  (libstdc++.so.5) and (libstdc++.so.5.0.1) files into the (bin) folder.

close the file browser's and Terminal when you are done.


Step:; 3

Download this [http://petepr.drivehq.com/humpty/sopcaster/sopcaster-3.5.tar.gz](http://petepr.drivehq.com/humpty/sopcaster/sopcaster-3.5.tar.gz) and save to your home folder, extract it, then in the extracted folder (sopcaster) there will be a file called (sopcaster) you need to drag and drop the (sopcaster) file into the (bin) folder

In Terminal (command prompt) type

sudo nautilus

 This will open a file browser 

Select (File System) then open the (bin) folder, drag and drop the (sopcaster) file into the (bin) folder.

close the file browser's and Terminal when you are done

FINISHED

All you have to do now is create a launcher for it

System>>Preferences>>Main menu>>  Internet>>  New item

Type : Application
Name : SopCaster
Command : sopcaster

press OK then your done 

To launch SopCaster    Applications>>Internet>>SopCaster

When SopCaster launches go to channels>>wget to get channel list:

The default player is mplayer if you want to use a different player you have installed put the player command in sopcaster  eg: VLC  would be command ( vlc) without the brackets.

[ATTACH]100792[/ATTACH]

[ATTACH]100793[/ATTACH]

Enjoy

NorthWesterUK

---

### Post by clive littlewood on 2009-01-23
Hi

Thanks for the howto but!

The step 3 file  petepr.drivehq.com/humpty/sop...ter-3.5.tar.gz

is actually a tar.exe and will not extract.       :(

Don't know if you have the correct address ?

thanks 

Clive

Edit:  Ok i found the correct link on Mp2p (your Howto) now works perrrrrrrrrrrfect thanks again

---

### Post by NorthWesterUK on 2009-01-23
Hi Clive, im new to Linux Os's!! Googling sopcast + linux/ubuntu didnt find a simple way to install Sopcast, so from various sites i searched i put together the ways and hows i installed it successfully lol.

Glad to hear you have it up and running aswell :o)

---

