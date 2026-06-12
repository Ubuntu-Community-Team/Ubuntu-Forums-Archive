---
title: "Really weird graphics making PC totally unusable"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by FlorenceSmith on 2011-03-08
Hi :)
 
I just upgraded to Ubuntu 10 and now when I turn on, the screen goes completely loopy!! 
 
At first it looks fine - words are readable, wallpaper is fine, icons are visible - but slowly the whole thing totally becomes goobledeegook and I just have to turn off. The weird thing is that things like the Pebble wallpaper remains just fine.
 
The first sign is little tiny specks dotted all over the screen. Then they become dashes. The words (Application, system, etc) disappear when I click on them. A box drops down for the menu but all the words are just upright dashes. All the words everywhere become these upright dashes so are totally useless and I can't do anything. But the Pebble wallpaper remains just fine still!!
 
So I don't think its graphics card as such, because of the wallpaper, but don't know what to do!
 
If I hit Esc as its turning on I get a list of about 10 choices of Ubunto 10, five of which say Recoverable (I think). If I try any of the Recoverable ones then I just end up with a black screen and get nowhere at all.
 
Would be very grateful for advice.
 
Thanks
 
:)

---

### Post by cariboo on 2011-03-08
What make/model graphics adapter are you using, and what driver? Open an Applications->Accessories->Terminal and type:

```
lspci | grep VGA
```

to find the make and model of your graphics adapter, and in the same terminal type:

```
lshw -C display
```

to find the driver.

---

### Post by FlorenceSmith on 2011-03-08
I may not even be able to do that much as it all goes wrong really quickly but I'll have a go to see if I can type it in before it goes to pot!!
 
I'll get back to you :)
 
I should've mentioned that I'm very very new to all this so your full directions are greatly appreciated :)

---

### Post by wep940 on 2011-03-08
Try holding down the ctrl and alt keys and pressing F1 to see if it gives you a terminal window to log into even if the screen is displayed all "goofy".

---

### Post by FlorenceSmith on 2011-03-09
Thanks guys :)
 
The results are:
VGA Compatible Controller: NVidia Corporation NV34 (GeForce FX5200)(rev A1)
 
and the second one basically said the same.
 
Does that help with anything?
 
I've taken some photos of how the screen is looking when it goes weird which I'll try and upload tomorrow.
 
Thanks

---

### Post by wep940 on 2011-03-10
I've found some references on the net for installing the driver for your card in 10.10.  What I don't know is how to do it in your current state - perhaps someone with more experience than me can walk you through getting it via the terminal window and installing it from there.  Here is one such reference, and note the mention that the one version of the driver doesn't work:
 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
 
 
I'm really sorry I can't help you further as I assume it will be using apt-get on the command line, but I really don't want to mess you up so hopefully someone with more experience can help you.

---

### Post by wep940 on 2011-03-10
I hope you don't mind, but I'm bumping this for the OP.  It appears the driver needs to be installed, but I don't know how to do that from the command line.  Can someone else help the OP?

---

### Post by Hedgehog1 on 2011-03-10
FlorenceSmith, wep940,

[SIZE="3"]EDIT:  Based on the type of NVidia card **FlorenceSmith** is running, you may need legacy NVidia rather than current NVidia drivers.  based on this info, please use the **nvidia-173** command set instead.[/SIZE]

```
sudo apt-get build-depend nvidia-173
sudo apt-get install nvidia-173
```

[SIZE="4"]EDIT: The commands below are for more current NVidia cards[/SIZE]

```
sudo apt-get install nvidia-current
```

Otherwise, use the 'bigger hammer' one:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-add-repository ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu
sudo apt-get update
sudo apt-get install nvidia-current
```

***The Hedge***

:KS

---

### Post by wep940 on 2011-03-10
Thank you!!

---

### Post by Hedgehog1 on 2011-03-10
If it works, **then** you may thank me.

If it doesn't work, then my name is really 'hamster1', not 'hedgehog1'.

***The Hedge (or _The Ham_, we shall see)***

:KS

---

### Post by sandyd on 2011-03-10
you know... I don't think thats going to work.

Nvidia now has two streams of drivers - one for the newer cards, and one for the older.

[Nvidia-Current ]("http://packages.ubuntu.com/maverick/nvidia-current")(click link) is for cards 6000* and over.

The Legacy drivers are now known as the cute little [nvidia-173]("http://packages.ubuntu.com/maverick/nvidia-173")

---

### Post by Hedgehog1 on 2011-03-11
> **sandyd said:**
> you know... I don't think thats going to work.

Nvidia now has two streams of drivers - one for the newer cards, and one for the older.

[Nvidia-Current ]("http://packages.ubuntu.com/maverick/nvidia-current")(click link) is for cards 6000* and over.

The Legacy drivers are now known as the cute little [nvidia-173]("http://packages.ubuntu.com/maverick/nvidia-173")

You may well be right...  

Is it as simple as the OP running:

```
sudo apt-get install nvidia-173
```

instead of:

```
sudo apt-get install nvidia-current
```

***The Hedge***

---

### Post by wep940 on 2011-03-11
I think I'm starting to see how the OP can do this:
 
- open a terminal window via CTR/ALT & F1
 
- type:
 
sudo apt-get build-depend nvidia-173 <press enter>
 
sudo apt-get install nvidia-173 <press enter>
 
 
I think the build-depend needs to be done because of all the things associated with nvidia-173 according to [http://packages.ubuntu.com/maverick/nvidia-173](http://packages.ubuntu.com/maverick/nvidia-173)
 
Things I don't know:
 
- if the OP has a hard-wired connection available or not and if there is anything special they need to do to get on that connection from the command line
 
- does the nvidia-173 package require xorg.conf?  Given that it doesn't exist in 10.04 or 10.10, how does one be sure the driver installs, or does the new Xorg just find the driver?

---

### Post by FlorenceSmith on 2011-05-14
Hi Guys. Thanks for all your efforts with this.  It was all a bit beyond me, I'm afraid, and I ended up formating the whole thing and reinstalling the latest Ubunto, which seems to be working ok now.  Just wanted to thank you.
:popcorn:

---

