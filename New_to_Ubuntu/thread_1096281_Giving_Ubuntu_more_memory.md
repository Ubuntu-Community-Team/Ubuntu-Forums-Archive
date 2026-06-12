---
title: "Giving Ubuntu more memory"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Skol312000 on 2009-03-14
When i first installed "dual boot" (i now have windows and Ubuntu) i chose for ubuntu to have 15 memory, how can i make my laptop a Ubuntu as thr main OS meaning for it to be able to use thr most part of the harddrive and stuff and leaving windows with a minimum... I would like to know how i can do this without uninstalling or removing Ubuntu and then install Ubuntu again... Is there a way?  Thank u so much for ur help, this is by far the best forum boqrd of any kind with fast replyes and accuracy, thanks...

---

### Post by taurus on 2009-03-14
If you want to shrink windows partition and expand Ubuntu, you have to use gparted either from Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

Also, it depends on where are your partitions.  While in Ubuntu, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Skol312000 on 2009-03-14
What will that code do? I cant use internet for aweek if that matters, so i would have to remove ubuntu and then install ubuntu again? Using thr live cd that i used to install the first time?  Doing this will remove my curren settingsnand info in Ubuntu?  Am i a nerd for using ubuntu? Lol. I like it so far and its my first day...

---

### Post by billgoldberg on 2009-03-14
> **Skol312000 said:**
> When i first installed "dual boot" (i now have windows and Ubuntu) i chose for ubuntu to have 15 memory, how can i make my laptop a Ubuntu as thr main OS meaning for it to be able to use thr most part of the harddrive and stuff and leaving windows with a minimum... I would like to know how i can do this without uninstalling or removing Ubuntu and then install Ubuntu again... Is there a way?  Thank u so much for ur help, this is by far the best forum boqrd of any kind with fast replyes and accuracy, thanks...

You can use gparted for that.

The application must be run from the Ubuntu live cd.

Or if you don't have it laying around, you can download and burn the gparted live cd.

--

Usually when people say they want to give "Ubuntu" more memory they talk about RAM memory.

Just saying.

---

### Post by Skol312000 on 2009-03-14
Ok , can i give it ram and hdd? Using that program u listed above?   

Using the program wont make me delete ubuntu or windows right?

---

### Post by billgoldberg on 2009-03-14
> **Skol312000 said:**
> Ok , can i give it ram and hdd? Using that program u listed above?   

Using the program wont make me delete ubuntu or windows right?

If you want more ram, you'll need to buy it, open up your pc case and add it.

--

Gparted will be able to "grow" the Ubuntu partition while "shrinking" the Windows one.

When you do things right, it won't delete Ubuntu or Windows, but if you do something wrong you could end up wiping your hard drive.

There are guides found online that will take you trough the process step by step (google "gparted grow Ubuntu partition").

Be careful and make sure you back up your data before doing it.

---

### Post by Skol312000 on 2009-03-14
Thank u a lot for the help!  Would it be technical and command line stuff?

I cant look because im on mobile internet and cant really check on ubuntu because i dont have internet ror a week, so if u could tell me if it is comand line stuff or way too technical i would apreaciate it

---

### Post by lisati on 2009-03-14
> **Skol312000 said:**
> Thank u a lot for the help!  Would it be technical and command line stuff?

I cant look because im on mobile internet and cant really check on ubuntu because i dont have internet ror a week, so if u could tell me if it is comand line stuff or way too technical i would apreaciate it

Installing RAM will depend on your computer, and, all going well, won't need much (if anything) in the way of command line stuff.

gparted for Ubuntu comes with a GUI (graphical user interface) so you might be able to do what you want without the command line. It might be easier to run it from a "Live CD".  **Important:** Make sure you backup your data, and take your time to think about whay you're doing.

---

### Post by Skol312000 on 2009-03-15
Why do u say "think about what your doing?" 
I will be able to install windows again at a later time if i need it right?

Also, how do i deletenUbuntu completely off the laptop if i ever need to do that?

---

