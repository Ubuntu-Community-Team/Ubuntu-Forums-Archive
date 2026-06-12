---
title: "Trying to install Sopcast, need ROOT to move files."
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Zaosyn on 2010-06-11
Hi guys I'm throughly enjoying Ubuntu and I'm starting to feel comfortable on it. My main issue befor was getting my Zune to work on Linux so I can manage it and I have done that thanks to VirtualBox :] Now I'm getting all my necessary applications that I used on Windows to work on Ubuntu.

Right now I'm running into problems with Sopcast and I believe it's a beginner issue I'm facing. I've read 5-6 tutorials and have tried to install 3-4 different packages. My problem right now is extracting these 2 core files needed to run Sopcast in my /usr/local/bin folder.

libstdc++.so.5.0.1
libstdc++.so.5

^ These are the files and I have them on my desktop now. I'm not used to the terminal very much so I've tried to manually move them into the usr/loca/bin folder myself and I get the error message:

> Error moving file: Permission denied
I can understand this since I need root to move files into certain folders but I have no idea how I can get root to drag and drop these 2 files. I'm sure I could use terminal but it's a very confusing process for me in terminal and most of the time I just copy and paste the command line when someone says it. I've not memorized the commands myself yet.

If anyone could help me I'd be very thankful!

---

### Post by pizza-is-good on 2010-06-11
> **Zaosyn said:**
> Hi guys I'm throughly enjoying Ubuntu and I'm starting to feel comfortable on it. My main issue befor was getting my Zune to work on Linux so I can manage it and I have done that thanks to VirtualBox :] Now I'm getting all my necessary applications that I used on Windows to work on Ubuntu.

Right now I'm running into problems with Sopcast and I believe it's a beginner issue I'm facing. I've read 5-6 tutorials and have tried to install 3-4 different packages. My problem right now is extracting these 2 core files needed to run Sopcast in my /usr/local/bin folder.

libstdc++.so.5.0.1
libstdc++.so.5

^ These are the files and I have them on my desktop now. I'm not used to the terminal very much so I've tried to manually move them into the usr/loca/bin folder myself and I get the error message:


I can understand this since I need root to move files into certain folders but I have no idea how I can get root to drag and drop these 2 files. I'm sure I could use terminal but it's a very confusing process for me in terminal and most of the time I just copy and paste the command line when someone says it. I've not memorized the commands myself yet.

If anyone could help me I'd be very thankful!


OK, if you don't want to use the terminal, you can use nautilus(the file browser) with sudo privileges.

On a terminal, type:

```
gksudo nautilus &
```

gksudo - to get admin privileges
nautilus - to open file broser
& - so you can close the terminal window after nautilus pops up

Now, be very careful. Do what you need to do and then close that admin nautilus. if you accidentally delete something in it, you could really mess up your system.

good luck,

~pizza

---

### Post by cariboo on 2010-06-11
You can use nautilus to move your files with a gui. Press Alt-F2 and type:

```
gksu nautilus
```

This command will start the file manager as root, allowing you to move the files where you need.

---

