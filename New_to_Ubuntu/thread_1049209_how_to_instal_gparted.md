---
title: "how to instal gparted"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by asmodeuzz on 2009-01-24
I have downloaded gparted from sourceforge.net,but i can't instal it in ubuntu8.10?

---

### Post by yeats on 2009-01-24
Gparted runs on a live CD (or I guess, USB, though I'm unfamiliar as to how to set that up), so you'll need a blank CD and a CD burning program - I use Kubuntu, so I'm forgetting the names of the default Ubuntu disk burning programs . . .   Inserting a blank CD should bring up that option.

---

### Post by mkvnmtr on 2009-01-24
Put what you downloaded in the trash and go to your package manager. In the search box type in Gparted. When it comes up click on the install button. Follow through clicking apply and in about two minutes it will be installed on your system. Be aware that to alter your disk you will need to use it on a live disk. I still like to have it installed to work on external drives.

---

### Post by jakupl on 2009-01-24
Go to Applications ---> Accessories --> Terminal

and write

```
sudo apt-get install gparted
```

It will then ask you for your password. When you write the password, you will not get any feedback. So even if it looks as though the terminal isn't accepting what you are typing, just continue and press enter when finished.

EDIT: AAARH beat me.
mkvnmtr's solution does exactly the same as mine, you can use either solutions.

---

### Post by BatteriesNotIncluded on 2009-01-24
As in the previous you could use Brasero (Gnome) or K3B(KDE). If you're just looking for the program and not the livecd version open a prompt and type

sudo apt-get install gparted

---

### Post by boof1988 on 2009-01-24
> **mkvnmtr said:**
> Put what you downloaded in the trash and go to your package manager. In the search box type in Gparted. When it comes up click on the install button. Follow through clicking apply and in about two minutes it will be installed on your system. Be aware that to alter your disk you will need to use it on a live disk. I still like to have it installed to work on external drives.

+1 *sorta*

It is a very good idea to install GPartEd using the installed Package Manager (if you want to use it while logged in to you Ubuntu install).

If you are going to be doing a lot of testing, playing and whatnot, I would recommend downloading the GPartEd LiveCD and burn that to a disk (it's a very good utility to have handy).  It uses a very minimal xfce-desktop.  Including:

[LIST=1]
[*]GParted - GUI version
[*]a Command Line Interface
[/LIST]

This gives the comfort of a GUI when you need to do some partitioning using a LiveCD, but don't want to load the full Ubuntu LiveCD.

The GPartEd LiveCD also has a load to RAM option.  The system loads to RAM so you can remove the CD so it frees up the CD/DVD-drive if needed.

---

### Post by asmodeuzz on 2009-01-24
ok thx a lot

---

