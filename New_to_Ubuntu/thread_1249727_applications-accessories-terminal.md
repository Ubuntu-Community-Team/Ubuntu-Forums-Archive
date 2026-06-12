---
title: "applications-accessories-terminal"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by whalescreams on 2009-08-25
A friend was trying to walk me through something over the phone... but it wasnt working 

I was instructed to go to applications-accessories-terminal and type in sudo apt-get compiz (tab)
but I cant seem to get anything to work via this method

---

### Post by pedro3005 on 2009-08-25
It should be 'sudo apt-get install compiz' .

---

### Post by crystal88_ on 2009-08-25
...and of course press enter after typing what you want in the terminal

---

### Post by oldos2er on 2009-08-25
> **whalescreams said:**
> A friend was trying to walk me through something over the phone... but it wasnt working 

I was instructed to go to applications-accessories-terminal and type in sudo apt-get compiz (tab)
but I cant seem to get anything to work via this method

 Compiz is already installed in Ubuntu versions 7.10 and up. To enable it, go to menus System, Preferences, Appearance, Visual Effects tab, choose either normal or extra.

---

### Post by zkriesse on 2009-08-25
But you can go to applications/add-remove and from the dropdown choose all available applications and type in the search bar, compiz. Install the first two by clicking the checkboxes. click apply it will install then close. again, go to applications/system tools/you should see a blue icon which says compiz menu or something like that. click it and down in your taskbar you should see the icon. opposite click and there you go. I will warn you though that it will slow down your system so be warned.

---

### Post by whalescreams on 2009-08-25
so i added install to the command and it did say that compiz was already installed but when i try to choose normal or extra it didnt work... so i went to add/remove and searched compiz(1 selection came up which I installed and got an error message... when i went to appearance and tried to install extra again it came up with a window to enable nvidia graphics driver which i did and then get a message saying unable to write mmap-msync(28 no space left on device)e: the package lists or status file could not be parsed or opened.... I did not find system tools or compiz anything under applications or anything else for that matter 

is my hard drive not partitioned properly(this is the first time I have ever used ubuntu)

---

### Post by oldos2er on 2009-08-25
"No space left on device" means just what it says. What size is the partition where Ubuntu is installed?

---

### Post by whalescreams on 2009-08-25
I'm not completely positive... it started doing some odd stuff upon install... but all that is on the 300gb hard drive is unbuntu 9.0.4 and windows 7 

where can i check the partitions or how

---

### Post by oldos2er on 2009-08-25
Run **df -h** in a terminal, then copy and paste the output here.

---

### Post by whalescreams on 2009-08-28
ended up installing kubuntu and set partition correctly... got it all figured out now.. thanks

---

