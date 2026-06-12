---
title: "Problem with places menu"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by joefluechter on 2010-05-08
when i try to open my home folder from the places menu i get an error message saying file not found. If i use the computer link in the places menu the file browser will open, this is the only functioning link. I'm not sure how to troubleshoot this issue so any ideas would be great,
I am using lucid lynx the kernel just updated yesterday which is when this problem began
cheers

---

### Post by spiky001 on 2010-05-08
can you type 
```
df -h
```
post the output sounds like home not mounted

---

### Post by joefluechter on 2010-06-08
sorry took so long to reply, this is the what came up when i typed the code df -h

user@user-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1              36G   16G   19G  46% /
none                  987M  304K  987M   1% /dev
none                  991M  1.2M  990M   1% /dev/shm
none                  991M  200K  991M   1% /var/run
none                  991M  4.0K  991M   1% /var/lock
none                  991M     0  991M   0% /lib/init/rw
/dev/sr1               24M   24M     0 100% /media/cdrom1
/dev/sr0              4.3G  4.3G     0 100% /media/cdrom0
user@user-desktop:~$ 

cheers for the reply.

---

### Post by Buuntu on 2010-06-08
The links might be broken for whatever reason.  I would just simply edit or add new entries.  
To do that just go to any Nautilus window (your window manager), click on Bookmarks > Edit Bookmarks (or Add Bookmarks if you want).  

Make sure your home and other folders have the correct location and if they do, it won't hurt to just remove them and then re-add them :)

---

### Post by joefluechter on 2010-06-08
Thanks mate I'll give that a crack

---

### Post by joefluechter on 2010-06-08
Still seem to have the same problem, file not found message. Anything else I can do to provide some insight as to what's happening from my end?

---

### Post by joefluechter on 2010-06-08
Someone sugested earlier it could be a problem with the mounting of the home folder, how do I fix this?

---

### Post by Buuntu on 2010-06-08
Umm, well that shouldn't be a problem unless you created a separate partition for your /home folder, and I doubt you did that.  What's the output of 
```
ls -l /home
```

And what exactly did you do before all the items in the Places menu started malfunctioning?

---

### Post by joefluechter on 2010-06-08
My missus may have shut down the computer while updates were being installed and configured, its the only thing thats happened differently that I can think of, this is speculation cause I left mid process. the kernels updated again since then.. The other thing I have noticed is when I plug in usb devices, ipod/memory sticks etc, when I right click I don't get the mount unmount option. To get banshee to pick up my ipod in Karmic I unmounted and remounted, thats how I noticed. These devices show up on the desktop but if I try to open them from the desktop it says file not found. To access these I have to go through the computer shortcut in the places drop down. I think i've gotta start using the terminal instead of being lazy buddy.

 
user@user-desktop:~$ ls -l /home
total 4
drwxr-xr-x 47 user user 4096 2010-06-09 10:18 user
 
thanks for your patience, haven't been using linux long, probably pretty obvious.

---

### Post by Buuntu on 2010-06-08
Yeah, if your user name is 'user' then it looks like you have a home folder with the correct permissions and everything.  I really can't tell you what to do from here.  If you haven't tried it already you might want to run
```
sudo apt-get update && sudo apt-get upgrade
```
just in case the problem has to do with broken dependencies or something of the sort.  It could also be a problem with some configuration files.  

Good luck

---

