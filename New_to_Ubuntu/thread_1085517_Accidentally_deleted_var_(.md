---
title: "Accidentally deleted /var :("
date: 2009-03-03
forum: New to Ubuntu
---

### Post by irfan9727 on 2009-03-03
My friend accidentally deleted the /var/ folder contents and it seems that all of the configuration files are gone, mouse and keyboard cannot be used at login screen (but switching to terminal using alt+f1 is possible), and reconfiguring are failed because folder not found (subfolder of /var).
Is there anything to do except reinstalling ubuntu? To note: I used Wubi, and it's Ubuntu 8.10.

---

### Post by albandy on 2009-03-03
do a new installation and backup the /var folder
this will not work at all but may help a bit.

In your new installation :
sudo tar zcvf var.tgz /var

in your old installation:
cd /
sudo tar zxvf /routetofile/var.tgz

---

### Post by irfan9727 on 2009-03-03
Just asking, are it's possible to just copy it from the LiveCD? Because my harddisk space are low :(.
Thanks for your quick help!

---

### Post by albandy on 2009-03-03
what ubuntu version and language are you using, Today I'm installing virtual machines so I can do a backup of /var and send it to you.

---

### Post by irfan9727 on 2009-03-03
As I write in the first post, it's 8.10, and the language just default, used plain english. Thanks!

---

### Post by albandy on 2009-03-03
ok, in about 30 or 40 minutes, I need to know what you've installed, type this and send me the file packages.txt

dpkg --get-selections > /tmp/packages.txt

---

### Post by irfan9727 on 2009-03-03
Okay, but how I supposed to copy/upload that file? I have flash-drive laying around, and this is my only computer, (I dual-booted), so I boot into windows now. Thanks for helps!

---

### Post by albandy on 2009-03-03
When you do a wubi install your Windows HD is mounted in /host, so if you copy the file to /host you will see it in c:

---

### Post by irfan9727 on 2009-03-03
Sorry, because of that database errors :(
This is the file you asking.

---

### Post by jimmyhacker on 2009-03-03
if you will copy /var from LiveCD,all application`s registry on apt will be lost.your Ubuntu installation will be very slow cuz files in var/run/ folder will be replaced with LiveCD configs.

---

### Post by albandy on 2009-03-03
I cant download it, send me an email to gmail, my mail user is the same as my nickname

---

### Post by irfan9727 on 2009-03-03
Okay, file already sent to your email.

---

### Post by albandy on 2009-03-03
Ok, I'm installing the packages in my virtualized machine, when done I'll post it here

---

### Post by albandy on 2009-03-03
download var.tgz from here:
[http://www.linuxlleida.com/var.tgz](http://www.linuxlleida.com/var.tgz)
then copy it to directly to c:
go to linux and type:
cd /
sudo tar zxvf /host/folder_where_is_located_c:/var.tgz

---

### Post by irfan9727 on 2009-03-03
Thanks! downloading it now, will post whatever happens next after I done that.

---

### Post by irfan9727 on 2009-03-04
Sorry late to post this man, blame my ISP :(
Anyway, it works! Thanks man! You're awesome!

---

### Post by albandy on 2009-03-04
> **irfan9727 said:**
> Sorry late to post this man, blame my ISP :(
Anyway, it works! Thanks man! You're awesome!

you're welcome

---

### Post by Vishal Agarwal on 2009-03-04
Excellent way for help. My regards to you.

---

### Post by theozzlives on 2009-03-04
It takes a very dangerous command (which I can't post here) to delete your whole /var folder. My advice is to not use that command until you become more familiar with Ubuntu and Linux.

---

