---
title: "run exe on ubuntu"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by AxelFlames on 2009-08-30
ok- i didnt have any any cds with me so i installed ubuntu on my computer with wubi (exe program)

i did the winex thing and all, but i cant use my exe games on it any help?

im usin ubuntu (wubi)
wine x
laptop

im trying to run 2 games:
1. Combat arms
2. S4 league (also a shooting game)

---

### Post by Liolikas on 2009-08-30
Most popular solution is **wine** but it sometimes work sometimes not.
More info here.
[http://appdb.winehq.org/](http://appdb.winehq.org/)
Install wine with Synaptic package manager or with command:
sudo apt-get install wine

---

### Post by Wiebelhaus on 2009-08-30
Also [Codeweavers]("http://www.codeweavers.com/")

---

### Post by jrox717 on 2009-08-30
In general, a Windows program, which is an exe program, won't run on Ubuntu because Linux uses a different type of executable file, called bin (for binary). As Liolikas said, you can try to get it to work with a program called Wine, which is written for linux and tries to run Windows programs. You can search for your games on the Wine website to see if someone has reviewed them and how well they work (it seems like S4 League should but Combat Arms maybe not). But since you're using Wubi you might just want to play those on Windows and use Ubuntu for other things. Good luck!

---

### Post by sideaway on 2009-08-30
I would download the latest wine in the form of a .deb, the one in the repos aren't nearly up to scratch as the latest one from their website is.

---

### Post by steveneddy on 2009-08-30
Wubi is software so you can "try out" Ubuntu.

Why don't you install Ubuntu on a new partition and really use it. You'll be much happier.

Better yet, install Ubuntu on a virtual machine like[ VirtualBox]("http://www.virtualbox.org/wiki/Downloads"). That's the ideal way to use two operating systems.

---

