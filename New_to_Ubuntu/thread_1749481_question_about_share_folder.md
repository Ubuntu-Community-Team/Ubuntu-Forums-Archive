---
title: "question about share folder"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by waddledee007 on 2011-05-04
Ok sorry if this sound like a newb type of question. But I only had Ubuntu 11.04 for a week. Anyway my notebook does not have much space on it so I thought I might as well delete anything I don't need. So I have space if I ever need it. So I was looking at some of the folder and note a folder call "share" I found this folder in the folder call "usr". I found the folder contain 600 mb of files. Is it ok to delete these files since I guess it like windows where these files and in there to share with other computer on a local network.
Sorry if that was a little long winded.

---

### Post by spiky001 on 2011-05-04
Nope dont do that they are needed files

---

### Post by Morbius1 on 2011-05-04
No you may not erase those files. Well, you can but they contain the  config files and such for the largest number of the applications and utilities currently present on your system. Without them bad things will happen.

---

### Post by waddledee007 on 2011-05-04
Right thanks. Do you know if there any files I could delete to free up space then.

---

### Post by spiky001 on 2011-05-04
what size hard drive do yo have ? Also if needed you could remove some programs you dont want example office

---

### Post by waddledee007 on 2011-05-04
It total hard drive space is 7 gb at the moment it 1.6 gb free and I just want to get it above 2 gb just in case. I need the office programs on the netbook as I mostly will use it for school work.

---

### Post by oldfred on 2011-05-04
You can do some basic housekeeping:

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by spiky001 on 2011-05-04
that was only a suggestion maybe have a look throgh see if there is anything you dont want

---

### Post by waddledee007 on 2011-05-04
Thank I see what I can do. Last question I was looking at what was taking the some of the spaces and I found that there was 2 gb use for what call swap space. I understand the important of swap space but I'm sure I could take off 1 gb from that since I know I wont be running a lot of software at once. So how do I remove 1 gb from that so it can come back to the main part of the hard drive.

---

### Post by spiky001 on 2011-05-04
not much of a saving but remove games is 32 mb not sure about swap how that would work

---

### Post by waddledee007 on 2011-05-04
I  think I should try to just move files to my external hard drive. Have not use that external drive much since my laptop broke and I been reduce to this here netbook. But thanks you for being helpful any way. Any way I will put this topic as solve now.

---

