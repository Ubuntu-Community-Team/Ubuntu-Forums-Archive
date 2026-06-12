---
title: "Package installed software for later installation"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by zer010 on 2009-09-10
Is there a way that I can take apps that are already installed and package them for later installation on another machine?  I would like to package them into .debs or something easy to install.  Example of an app I'd like to package would be Audacity, or Freeciv, etc.  Thanks for any help.

---

### Post by Bölvaður on 2009-09-10
about making .deb then google is your friend, but I feel it is an overkill as you can just as well download the program from the same repo as you did on the other machine but copy the folder that contains all the user data (like configs and saves) and just replace it for the default one from a fresh install.

you can find all those folders under your home folder with a "." in front of them (that is just one dot).
you can show those hidden folders in nautilus by pressing ctrl+h

---

### Post by earthpigg on 2009-09-10
if you look in /var/cache/apt/archives, you will see .deb files for everything you have installed *since the last time you ran apt-get clean* (unless you are short on hard drive space, you should never run apt-get *clean* in my humble opinion). this will not resolve dependencies, however, and you will quickly find yourself in dependency hell....

using apt-get and aptitude is definitely the way to go to avoid that.

you can get a complete list of *every package installed* on your system with this command:

```
aptitude search -F '%100p' '~i!~M' > ~/deblist.txt
```

that will put a text file called deblist.txt containing every package installed in your home folder. you can then copy that txt file to a fresh install of ubuntu, and

```
sudo apt-get install $(cat deblist.txt)
```

will install everything in that list on the new computer.

combine that with what Bölvaður said about finding, backing up, and restoring dotfiles on the new system, and im sure you can see the possibilities.


(the .txt at the end of deblist.txt was to make what you are dong more recognizable.... you can call it buttmunch.mp3.superman.avi, if you like, and it will work exactly the same.)

---

### Post by zer010 on 2009-09-10
buttmunch.mp3.superman.avi  :lolflag::lolflag:
The crux of the situation is that I am half-expecting to lose my net connection.  In the mean time I am trying to install all kinds of apps that will be useful/entertaining while I'm not connected.  At some point in time, I can foresee having to do a reinstall. I just don't want to have to find a connected comp to reinstall what I already have.  I heard something about a full sys backup using Remastersys(haven't tried it yet).  Instead of an optical disk backup, I'd much rather use a USB flashdrive.  Thanks for the help so far.

---

### Post by earthpigg on 2009-09-10
> I heard something about a full sys backup using Remastersys(haven't tried it yet). Instead of an optical disk backup, I'd much rather use a USB flashdrive. Thanks for the help so far.

remastersys will create an installable LiveCD .iso.

system -> admin -> usb startup disk creator can then turn that .iso into a LiveUSB.

i've done it myself, see my sig :D

in theory, i see absolutely no reason why that "LiveUSB" cannot be a 150gb USB external hard drive packed with all sorts of awesomeness.

also, if you just want a whole bunch of .deb files:

install ubuntu, as normal.

install every package you could ever think of until your hard drive is full.

your /var/cache/apt/archives directory will then be packed with those same .deb files that could certainly be reused later -- with that same version of ubuntu.

---

### Post by Bölvaður on 2009-09-10
see earthpigg's answer and add to it what I said, including adding the repos, the reason for that is for updates after you install from a deb. So you dont need internet at first, but when you get it, then you will be able to update your software.

---

### Post by LowSky on 2009-09-10
getdeb.org miight have many of the programs you want

[http://www.getdeb.net/search.php?keywords=Audacity](http://www.getdeb.net/search.php?keywords=Audacity)

---

### Post by zer010 on 2009-09-11
Thank you all for your help!  @earthpigg,  I think I might have a go at your Masonux.  Sound really cool.  Might be what I need for this old pc.  Ubuntu works great, but my comp is still kinda old. A '99 I think.  We'll see. If I run into any problems with my live backup, I'll post here.  Again thanks, everyone!

---

### Post by achase79 on 2009-09-11
You may also try aptoncd.  With this program can create your own repository on cd (this implies that you still have internet access).  Or you may also check out Keryx.org for offline downloading of packages.

---

### Post by EXCiD3 on 2009-09-11
If you are using the same install on both machines you can just take the files from /var/cache/apt/archives and copy them to the other machine in the same directory and /var/lib/apt/lists/ as well.

Like achase mentioned, you could also use Keryx ([http://keryxproject.org](http://keryxproject.org)) or APTonCD. Keryx is great if the other machine is using a different version of Ubuntu or architecture (64bit compared to 32bit).

---

### Post by zer010 on 2009-09-16
Overall, I'm trying to prepare my machine for loss of net access.  If I download a bunch of packages now, but later on I have to do a clean, original install, I want to be able to fresh install the packages one by one.  I'm not expecting to get my net access back any time soon, maybe only sporadic access at a friend's place.  I wish everything in the world wasn't so internet dependent. :(
     Thank you all for your input and good advice.  I'm not sure if I can use everything that was suggested, but I guess I'll manage.  If not, then *gasp* I'll just get Win7 when it comes out in 2 years. :rolleyes:

---

### Post by EXCiD3 on 2009-09-16
As long as you don't lose the new packages you download, you installed off of the base installation then you can reinstall them just like the first time.

---

