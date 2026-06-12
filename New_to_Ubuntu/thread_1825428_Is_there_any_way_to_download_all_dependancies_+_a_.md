---
title: "Is there any way to download all dependancies + a program to install on multi comps?"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by Lucypie on 2011-08-15
Okay, So I am now in a place where I can dl whatever the crap I want :D Whoo hoo for unlimited internet! xD. Anywho, I need to download a bunch of programs, and I need them to be installed on multiple computers. One is a desktop, which cannot be moved from our house, with limited internet. I've tried things like this before, but usually I won't have any of the dependencies, and therefore, break things. Here is a list of programs I wish for...


Thunderbird
Gimp (+ plugin registry addon)
Supertuxcart
Wacom GUI
WINE
Pidgin
Audacity
AmroK
Filezilla
Compiz
Kate (kde for kubuntu)
KompoZer
Stellarium


If I CAN'T download all dependancies for multiple use, is it possible to literally copy an entire drive (fresh install) and paste it, and it work? xD This computer is a HP laptop with Windows 7. The desktop is a dell with Windows Vista. I wish to put Ubuntu 11.04 on both (with dual boot) and on this one, Xubuntu/Kubuntu (triple/quad boot). 

PS, Any reccomendations for what I should DL today? I am a graphics artist and web coder. I code in PHP, HTML, CSS, and work with databases. I love to draw and I like to digitalize my drawings with my Wacom Bamboo tablet. I also enjoy racing games ;)

Thanks for all the help!<3

---

### Post by blazemore on 2011-08-15
Well I don't know if there's a better way to do it, but I've done this in the past.

Delete everything in /var/cache/apt/archives
then do
```
sudo apt-get -d package1 package2...
```

The -d flag means download the packages only and don't install them.
This will also get all dependencies.
Every .deb file downloaded will go in /var/cache/apt/archives.
You can copy them all out to a flash drive, then use the following to install them wherever:
```
sudo dpkg -i *.deb
```

---

### Post by JC Cheloven on 2011-08-15
Yes. For example from synaptic package manager, choose "download packages only". 

Also you may want to try [aptonCD]("https://help.ubuntu.com/community/APTonCD").

Or see [here]("https://help.ubuntu.com/10.04/add-applications/C/offline.html") for more general overview on how to install without net connection.

---

### Post by JC Cheloven on 2011-08-15
> **Lucypie said:**
> If I CAN'T download all dependancies for multiple use, is it possible to literally copy an entire drive (fresh install) and paste it, and it work? xD This computer is a HP laptop with Windows 7. The desktop is a dell with Windows Vista. I wish to put Ubuntu 11.04 on both (with dual boot) and on this one, Xubuntu/Kubuntu (triple/quad boot). 



Sorry I didn't noticed that bit. For that, you'll want to try [remastersys]("http://www.geekconnection.org/remastersys/ubuntu.html"). With that, you configure one ubuntu to your liking, make an image of that, and then you can install it to other pc's.

In short, in your case I'd go for aptoncd or remastersys, depending on whether you prefer to install some packages in an existing ubuntu, or install an "exact" copy of the system everywhere.

---

### Post by Lucypie on 2011-08-15
Whoohoo! That sounds great :) Thanks :D

---

### Post by ~!geek!~ on 2011-08-15
I don't know if it helps, but one of my friends wrote a blog for doing the same. You may want to give it a visit. [http://xperiencegnulinux.blogspot.com/2011/07/manage-ubuntu-without-active-internet.html](http://xperiencegnulinux.blogspot.com/2011/07/manage-ubuntu-without-active-internet.html)
and comment there  either in case,  you face any problem or it helps you!!!

---

### Post by oldos2er on 2011-08-15
Take a look at Keryx: [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by Lucypie on 2011-08-15
Keryx: Cannot install it. I don't know why. Just opens software center.

Remastersys: Cannot find the source, as says the sources list. 

I've got APTonCD installed and made a disk, but I was hoping to have at least one more system restore thing for safety.

---

### Post by JC Cheloven on 2011-08-15
> **Lucypie said:**
> 
Remastersys: Cannot find the source, as says the sources list. 


First, edit your sources.list as supersuser to add the repository. For that, please open a terminal and type ```
gksudo gedit /etc/apt/sources.list
```
Now please add this line to the end of the file:```
deb http://www.geekconnection.org/remastersys/repository karmic/
```
Save and exit from the editor.

Now, back at the terminal run ```
sudo apt-get update
```

Finally, install remastersys using your prefered method (may you prefer via via synaptic...), for example again from terminal ```
sudo apt-get install remastersys
```

I see [here]("http://www.geekconnection.org/remastersys/repository/karmic/") that version 2.0.18-1 is the latest (I'd expect this one to be installed; alternatively to all steps mentioned, you could simply grab the file remastersys_2.0.18-1_all.deb from the previous link and install it with gdebi or the ubuntu software center).

Hope to have made it clearer ;)

---

### Post by oldos2er on 2011-08-17
> **Lucypie said:**
> Keryx: Cannot install it. I don't know why. Just opens software center.


That's what it should do. Are you saying Software Center can't install it? Are there any error messages?

---

### Post by Lucypie on 2011-08-17
No, I mean, it opens the face page of the software center. It usually takes 10 sec to load, but it won't load it at all. Doesn't matter- I got what I wanted done. My father is pleased with his new programs and updated ubuntu. I am pleased aswell. Thanks all.

---

