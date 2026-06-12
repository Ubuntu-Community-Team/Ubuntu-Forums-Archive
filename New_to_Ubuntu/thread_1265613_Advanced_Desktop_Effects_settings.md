---
title: "Advanced Desktop Effects settings"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Captainflowers on 2009-09-13
I'm new at Ubuntu. I have version 8.04 I believe which comes with Compiz Fusion already installed. So anyway, I know that I need to have Advanced Desktop Effects Settings in order to use all the effects of Compiz Fusion, but I can't get the option. I've tried goint to add/remove and it did nothing. Please help!

---

### Post by K7522 on 2009-09-13
```
sudo apt-get install compizconfig-settings-manager
```

This will install the GUI, which can then be found at System > Preferences > CompizConfig Settings Manager

Welcome to the community. :)

---

### Post by gijsterbeek on 2009-09-13
Hi,

search for ccsm in Synaptic and install it or do 

```
sudo apt-get install ccsm
```

in a terminal window. After that, run 

```
ccsm
```

---

### Post by abrianb on 2009-09-13
Click on Applications > Add/Remove> search for compiz. Then Add Compiz Fusion Icon.
Once You have added the package Click on Applications > System tools > Compix Fusion Icon.
This starts The Icon. Its blue, right click on it and select settings manager. Then Pick what you want. Google Ubuntu compiz for more info on controlling the effects if you need help.

---

### Post by NoaHall on 2009-09-13
CCSM is the simple one. And it's called "simple-ccsm" not just "ccsm"

```
 sudo apt-get install compizconfig-settings-manager 
``` is the one the OP wants.

---

### Post by kpholmes on 2009-09-13
once everything is installed, and have the cube in effect, how can i select how many "workspaces" i want?

---

### Post by NoaHall on 2009-09-13
Here -> [http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/cool-compiz-fusion-tricks-on-ubuntu.html](http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/cool-compiz-fusion-tricks-on-ubuntu.html)

---

### Post by K7522 on 2009-09-13
> **kpholmes said:**
> once everything is installed, and have the cube in effect, how can i select how many "workspaces" i want?

Go to System > Preferences > CompizConfig Settings Manager, and select General Options. It is in the "Desktop Size" tab.

I run the following:
Horizontal Virtual Size: 10
Vertical virtual Size: 1
Number of Desktops: 1

This gives me 10 desktops, and a very big decagon instead of the cube (Horizontal virtual Size: 4)

---

### Post by Captainflowers on 2009-09-13
Ok, so I'm really new at Ubuntu and anyway, how do you set effects for when you exit out of a window, minimize the window and things like that? I have the wobbley windows effect but idk how to get the others like burn, explode and things like that. Please help! 
I also have 8.04 so I already have Compiz Fusion

---

### Post by Captainflowers on 2009-09-13
Ok, so I'm new on ubuntu and anyway, I was wondering if theres anyway to set a background that displays when you rotate the cube effect in Compiz. I've tried everything it seems to figure out both that and the object dock. Any help would be greatly appreciated! :)

---

### Post by gamerchick02 on 2009-09-13
Install the Compiz Settings Manager from synaptic.

Then enable Compiz via the "Appearances" menu.

Then, go to Compiz Settings Manager and configure to your heart's content!

Amy

---

### Post by whitethorn on 2009-09-13
Do you mean something like a background behind the cube?  If yes then what you're looking for is called the skydome.  In compiz setting manager, in Desktop cube, click on Appearance then at the bottom skydome.  You can then choose a picture to be kinda like a wallpaper behind the cube.

---

### Post by whitethorn on 2009-09-13
What you're looking for is the animations plugin, also if you want some nifty ones enable extra animations.

---

### Post by Hosmion on 2009-09-13
I have the same question..  Where do you get the animations plugin?

---

### Post by themusicalduck on 2009-09-13
I think Animations comes from the compiz extra plugins package.

```
sudo apt-get install compiz-fusion-plugins-extra
```

You can get even more by installing the unsupported package.

```
sudo apt-get install compiz-fusion-plugins-unsupported
```

---

### Post by redbob on 2009-09-13
to be more specific, you must do these things:
1) Install Compiz-manager:
> suto apt-get install compizconfig-settings-manager

2) Goto Compiz Manager, and chose in General Options, increase Desktop Size to 4 ;
sdsdsdsd
3) On Compiz Manager yet, choose Desktop Cube (must disable Desktop walls).

---

### Post by Captainflowers on 2009-09-13
> **gamerchick02 said:**
> Install the Compiz Settings Manager from synaptic.

Then enable Compiz via the "Appearances" menu.

Then, go to Compiz Settings Manager and configure to your heart's content!

Amy


How do I do that?

---

### Post by Captainflowers on 2009-09-13
Thanks guys! I got it working! BTW does anybody know about the object dock?

---

### Post by whitethorn on 2009-09-13
I'm guessing you've installed compizconfig-settings-manager.  If not open a terminal Applications -> Accesories -> Terminal

```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```

You can then find it under System -> Preferences -> CompizConfig settings manager

---

### Post by pedro3005 on 2009-09-13
If you don't have one already, go to [http://www.gnome-look.org](http://www.gnome-look.org)  for some neat skydomes.

---

### Post by Captainflowers on 2009-09-13
Ok, I was watching some youtube videos with Ubuntu demos and noticed, some people have an object dock on there desktop. Does anybody know where or how I can get one? Please help this poor noob!

---

### Post by Ms_Angel_D on 2009-09-13
search for Dock in the synaptic package manager I believe their are several options available.

---

### Post by Captainflowers on 2009-09-13
So, I posted a thread asking about this, but maybe I wasn't specific enough. I have a list of effects I can use under Compiz config manager. But whenever I select one, it never works. I know how to get to the list, I just can't get them to work. Please help

---

### Post by overdrank on 2009-09-13
Threads merged. You may look at the FAQ's link in my signature about the Desktop effects. :)

---

### Post by Captainflowers on 2009-09-13
Oh man, ur right?!

---

### Post by kpholmes on 2009-09-13
> **K7522 said:**
> Go to System > Preferences > CompizConfig Settings Manager, and select General Options. It is in the "Desktop Size" tab.

I run the following:
Horizontal Virtual Size: 10
Vertical virtual Size: 1
Number of Desktops: 1

This gives me 10 desktops, and a very big decagon instead of the cube (Horizontal virtual Size: 4)



ahhh. thanks very much! 
thanks just what i was looking for.

---

### Post by k33bz on 2009-09-14
> **Captainflowers said:**
> Ok, I was watching some youtube videos with Ubuntu demos and noticed, some people have an object dock on there desktop. Does anybody know where or how I can get one? Please help this poor noob!

you have two different options I know of, they are both in the synaptic manager.
1. Cairo Dock (which is my fav)
2. AWN

> **pedro3005 said:**
> If you don't have one already, go to [http://www.gnome-look.org](http://www.gnome-look.org)  for some neat skydomes.

From my own experience just about any image will do, depending on size some work better than others.

---

### Post by myolbug on 2009-09-14
Okay, I haven't even read all of this yet, but I gotta say a huge thanks for the animations and skydome stuff.  This kicks posterior!!!:KS

---

