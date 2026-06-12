---
title: "Accessing Shared Folders on Network"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by breNTx22 on 2010-09-29
I have a Desktop and my roommate has a desktop. Both are Windows 7 x64. We both have our movie collection on our computer. I have a HP laptop that I have the latest Ubuntu on. I also have a TV that I want to watch our movies on. Running a cable from my desktop to my TV gets a little sloppy so what i'd like to do is use my HP laptop (Which is 2nd string to my Macbook Pro) and hook it up to my TV via HDMI then set it up in dual display and access the shared folders on both the windows 7 desktops. How do I go about doing this?

Is this the way you do it?

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Terminal/Dos commands intimidate me so is there a GUI way to do it?

Cliffs:
-Shared movie folder on network (from 2 Win. 7 machines)
-Want to access it with Ubuntu Laptop
-Dual display movies to my TV.

---

### Post by BigRedButton on 2010-09-29
To make a folder on a linux computer shared on a windows network, just right click on the folder and go to sharing options. there's a checkbox in there for "share this folder." click that and you will get a window saying something to the effect that "sharing is not installed on this computer... would you like to install?" just click yes, authenticate, and done. as long as the computer is on, the folder will be accessible from any windows computer.

It uses a program called Samba. You can also share devices and printers this way, but its much more complicated

---

### Post by breNTx22 on 2010-09-29
> **BigRedButton said:**
> To make a folder on a linux computer shared on a windows network, just right click on the folder and go to sharing options. there's a checkbox in there for "share this folder." click that and you will get a window saying something to the effect that "sharing is not installed on this computer... would you like to install?" just click yes, authenticate, and done. as long as the computer is on, the folder will be accessible from any windows computer.

It uses a program called Samba. You can also share devices and printers this way, but its much more complicated

Thank you but i'd like to do the opposite. I want to access shared folders that are on a Windows machine FROM my ubuntu machine. I don't actually have any folders on my Ubuntu machine that need shared.

---

### Post by spiky001 on 2010-09-29
Hi 1st how are the pc,s connected on the network is it by a router, then 2nd they mst make the folder yo want to share shareable, then you should be able to go to places network find the pc then the folder

---

### Post by ddonohu2 on 2010-09-29
I believe the article you linked to is for permanent mounting of network drives (similar to the "map network drive" function under windows). You could do this if you want but it's not necessary for what you want to do since your windows shares should be accessible from Ubuntu already. As Spikey001 said, all the hosts need to be on the same network. Assuming they are then you should click on "Places" and select "Network". The Network folder should list the Windows hosts with shares on the network. Double click on the host you want and then double click on the shared folder to mount it to your Ubuntu machine (at least this is how it works for me).

---

