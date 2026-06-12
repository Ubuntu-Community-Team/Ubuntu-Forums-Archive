---
title: "graphics problem VMD 1.8.7 and upgrading while deleting win vista OS"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Morpholinux on 2009-12-07
Hi....

I began with Ubuntu 8.10..
...
I crashed the system a couple of times (got help from here...) in my first month..or something..


////////
Now...I have 2 problems...
/>I Use a program called VMD 1.8.7
The problem is with the graphics...(it's supposed to show beautiful proteins and molecules...and also does a lot of other things....)..problem is that ..they appear white..with some color on it...but mostly...white.......I know I have to upgrade my OpenGL driver.....but ..how I do that?

and

/> Second thing I wanna know is....
I want to upgrade to Ubuntu 9.10 ...while deleting my win vista OS...Is that possible? 
(I use Ubuntu 99.99999% of the time)

If I upgrade/delete there's a chance that I don't have to solve the first problem?


well...
that's all
thanks...

---

### Post by Sin@Sin-Sacrifice on 2009-12-07
The drivers should be listed in System>Administration>Hardware Drivers. Upgrading can be done at your leisure. Not sure what you mean by "while deleting Windows" If you mean while formatting the Windows partition... sure.

---

### Post by Morpholinux on 2009-12-07
Hello [email]sin@sin-sacrifice.....yes[/email] I mean upgrading Ubuntu "while formatting the Windows partition..."
how can I do that?


and....mmmmm

I do System-->Administration--> hardware drivers....(then it starts searching....and then it says something like.."No propietary drivers are in use on this system")....what I do next?

---

### Post by Sin@Sin-Sacrifice on 2009-12-09
You can format the windows partition with gparted while running ```
sudo apt-get dist-upgrade
```. You're gonna have to figure out which drivers you need. What kind of video card do you have? I would also wait until you upgrade Ubuntu to install your video card drivers though.

---

### Post by Morpholinux on 2009-12-11
hi again!!...I did the upgrade a few days ago....now a I am with karmic koala..


I had (maybe still have...) some problem with Gromacs openmpi bin or something..(I reported that as bug...-my first time XD- ... somebody else won me :(  ) 

..but hmmm...
at least the problem with VMD 1.8.7 was solved and besides that..everything seems working fine..(I can't see the icon of firefox at the gnome panel...but I can live with that!)


didn't delete  win-vista while upgrading to Ubuntu 9.10.....It seems very complicated....
but still  want to do it ...

somebody knows if there's a video tutorial or something for that?


thanks in advance!!

...btw...
Karmic looks veeeeery nice!!!

---

### Post by Sin@Sin-Sacrifice on 2009-12-16
Just open gparted, right click the partition you want to format and hover "Format to" and it will bring up a list of file system to format it to. Pick one (ext3 for example) and then click the check mark at the top of the program. It will do the rest for you. Also make sure you back up anything on the Windows partition you want to keep because it will be gone after you click the check mark.

---

