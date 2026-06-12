---
title: "Help with network hard drive"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by BRFC on 2008-02-24
Ok I need a little help, I have just installed ubuntu and everything is going great except I cant see my network hard drive [http://www.freecom.com/ecproduct_detail.asp?ID=3400&CatID=8020&sCatID=1146195&ssCatID=1146196](http://www.freecom.com/ecproduct_detail.asp?ID=3400&CatID=8020&sCatID=1146195&ssCatID=1146196)

Anybody tell me is it possible to use this drive with my nice new Linux setup, which I have to say is fantastic to use after too many years of windows.
                       
Please base any advice on an idiot friendly level.

---

### Post by jhetrick62 on 2008-02-24
BRFC,

It depends on the protocols it uses for connection.  

What is it's IP address?
How do you connect to it in Windows?

If in windows you just map it with a valid username and password, then yes it would be easy in Ubuntu.

You can test it my making a directory under mnt

sudo mkdir /mnt/test

Then attempt to mount it with

sudo mount //192.168.0.50/sharename /mnt/test -t cifs -o rw,user=your_username_for_the_network-drive,password=your_password_for_the_network-drive

You should then be able to browse the share and possibly write to them.  Use the name that you map to in windows as your share name and the user and password that you use on your windows map.

If this works, there are several possibilities depending on how you want to use this.

Jeff

---

### Post by BRFC on 2008-02-24
Cheers for that, I now have it working, Can read/write to it so all is well.

---

### Post by AlanR8 on 2008-02-24
I have the 500 Gig version of your drive and it works. It seems to run a version of Linux as its operating system.

I find file transfers, particularly wireless transfers, VERY slow

---

### Post by Cochise on 2008-02-24
got the 500gb version on saturday, took me a while to get it to work too.

---

### Post by jhetrick62 on 2008-02-24
Add the definition to your fstab and indicate if you want to auto mount it or not, and away you go! Glad it worked for you.  Remote file system mounting is farily straight-forward in Linux.

Jeff

---

