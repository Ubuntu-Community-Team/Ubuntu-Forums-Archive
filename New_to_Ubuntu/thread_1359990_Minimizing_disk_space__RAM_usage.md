---
title: "Minimizing disk space / RAM usage"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-12-20
Hello again.

I'm trying to minimize the amount of disk space that ubuntu takes up. So far I have reduced the size to 3.9 GB, but I would like to minimize that even further (I'm going to clone my hard drive).

Using the disk space analyzer tool, I can see that most of the space is being taken up by /var/cache. Is it safe to remove some of the files in here? If so, which ones?

I am also trying to reduce the amount of RAM my system takes to run. Right now its base amount is around 78 MB on startup, but it seems that Xorg is taking up a majority of the RAM usage. I am using metacity (no compositing). Is there someway I can reduce the footprint of Xorg even further?

I used to have bootchart installed, but I have sinced removed it. Since then, I removed quiet and splash from my grub entry. I can still see bootchart being loaded (on startup), and then the process is killed. I have purged the configuration files and everything! 

My system boots fairly fast, but it seems that most of the time is used shortly after the Apparmor profiles are loaded. Then it seems to sit there for a few seconds before fsck, and then a few more seconds after. Can I minimize this as well? 

Thanks again!

---

### Post by The Real Dave on 2009-12-20
Can't help you with bootchart, and I'm assuming you've already removed as many unused packages as you can? If not, use Synaptic to uninstall them. Things like OpenOffice take up a lot of space :)

With /var/cache, I'm not sure, but your probably safe in removing /var/cahce/apt/archives/. It holds archives and half completed .deb packages. Mines currently taking up 300Mb, so maybe you could trim down there :)

---

### Post by jward3010 on 2009-12-20
Just to say, my Ubuntu installations, with a small amount of apps and fully updated, takes up around 2.7GB. Have you a lot of applications installed or a lot of stuff saved in your home folder?

If you already haven't done it, clean up apt-get.

```
sudo apt-get autoremove
sudo apt-get autoclean
```
It will tell you straight after how much you have gained.

In regards the above suggestion to remove OpenOffice you might be greeted with the fact that it wants to remove the desktop and many VERY important packages, that's because it might be a meta package, tightly linked into the main desktop components like Gnome, gdm, metacity, ubuntu-desktop. If you try and remove it and it IS a meta-package you're entire GUI desktop will go too. I think it's crazy but it's the way it's done with Ubuntu.

---

### Post by darkeye123 on 2009-12-20
I have already removed all unnecessary packages, and I use abiword/gnumeric instead of openoffice. I just removed the /var/cache/apt folder and that cleared up a fair bit of space.

I am running LXDE desktop on top of ubuntu, so that takes up a fair bit of space, but I think the space it uses is well worth the performance it gives me.

As for my home folder, it takes up 100 MB of space, almost half of that is from my firefox profile. 

Right now the biggest folder is the /usr/ folder, which is taking up a monster amount of space: 1.8 GB

Now I obviously need my /usr/ folder, but what can I remove from it? the two folders taking up the most space in it are: share and lib (850 MB and 700 MB respectively.)

Thanks a lot for your help! :)

---

### Post by k3lt01 on 2009-12-20
Try [this thread]("http://ubuntuforums.org/showthread.php?t=140920") for some help. it is amazing how much you can clean up.

---

### Post by darkeye123 on 2009-12-20
Thanks a lot for posting that thread! Helped me clear up a lot of space! 

Anyone have any ideas on how to to fix the bootchart problem?

---

### Post by Tikkyca on 2010-03-26
I have a problem,too,when i boot my system it boots really fast i use compiz without any problems,and all those stuff.Now when i look at my system usage i can clearly see that it is allways using 700mb-s of ram,when i head over to the processes tab i see that there is no way processes are using that much memory,because each process uses 1mb or 300kb and  i have them around 30,can someone help me fix this?

---

### Post by NightwishFan on 2010-03-26
In system monitor go to view -> All Processes. Or as an alternative use the top command in the terminal.
```
top
```

If you are running a full Gnome 70mb is not bad. My Debian install uses more than that. Granted it is using the AMD64 arch.

---

### Post by audiomick on 2010-03-26
This might interest you
[http://www.linuxatemyram.com/index.html](http://www.linuxatemyram.com/index.html)
I found it helped me understand the way Linux uses RAM.

---

