---
title: "Compiz Fusion HELP NEEDED!!"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by MaximoMilkman on 2009-01-07
Hey guys.. I dont seem to have compiz fusion?? BUT oddly enough when i go to my appfinder it says i have a thing called CompizCOnfig settings manager I ALSO downloaded this CompizFusion ICON for my toolbar but that does nothing.. SO where can i actually get Compiz Fusion from anyone have a repository code.. ALSO anyone know of a code to type into to see what type of graphics card or video card i have.. i know its an intel integrated but i dont know exact specs so is there a code that will show me more information?? I REALLY want wobbly windows =)

---

### Post by alphaakenny1 on 2009-01-07
In the terminal 'lspci' will tell you your hardware

also:

sudo apt-get install compiz compizconfig-settings-manager

---

### Post by detroit/zero on 2009-01-07
The command ```
lspci
```will give you a quick rundown of your hardware.

There are different ways to go about installing CF, with varying degrees of reliability and varying degrees of difficulty. Search around the forums or use Google to find a method that suits your abilities/needs.

---

### Post by Michael.Godawski on 2009-01-07
hi

perhaps you can have a look at this guide written by Bodsda. Might be of some help:


[LIST]
[*][http://godawski.oxyhost.com/compiz.html](http://godawski.oxyhost.com/compiz.html)
[/LIST]

---

### Post by MaximoMilkman on 2009-01-07
Hum for some reason the wobbly windows wont wobble and the cube wont cube.. actually nothing works for me that compiz has to offer anyone know why?? or am i just doing something wrong.. do you want me to post my graphics controller stats or something??

---

### Post by JBrehm on 2009-01-07
have you tried actually going through the compiz fusion manager and enabling all of those features and customizing them so that they work? have you even downloaded/installed compiz fusion manager like one of the other folks directed? i have nothing but integrated graphics on my computer and it works just fine. it's a little slow in 8.10 but 8.04 was fine.

---

### Post by MaximoMilkman on 2009-01-07
Actually no i dont have compiz fusion.. i didnt no it was a necassary download because i have the manager guess i gotta find the compiz fusion where did you get yours from my friend! =)

---

### Post by oldos2er on 2009-01-07
Compiz-fusion has been installed by default since v7.10. You activate via the menus System, Preferences, Appearance, Visual Effects.

---

### Post by MaximoMilkman on 2009-01-07
Unfortunatley since im using xubuntu i dont know how to access that i have no prefrences menu under my system tab do you know how to access this visual effects menu through terminal by any chance?

---

### Post by lswest on 2009-01-07
You will need to install the compiz package if you're running Xubuntu, as it's not included by default (to the best of my knowledge).

```
sudo apt-get install compiz
``` if that returns package not found, try compiz-core.  Not sure atm what the package is called.

Also, look here: [http://ubuntuforums.org/showpost.php?p=4375297&postcount=3](http://ubuntuforums.org/showpost.php?p=4375297&postcount=3)

---

### Post by MaximoMilkman on 2009-01-07
I read that but i cant find Advanced Desktop Effects Settings because its not there.. it may have been updated since last year.. now i guess my problem is i need to find out how i can access advanced desktop effects settings in xubuntu... anyone know how as of 8.10 intrepid ibex

go to Aplications -> Settings -> Advanced Desktop Effects Settings an select your plugins you want

---

### Post by MaximoMilkman on 2009-01-07
I have made a major breakthrough!!! i was fooling around with emerald and i needed some help so i was reading some forums and some guy said to install the fuizon icon which i had and hit reload windows manager and POOOOOOF now i have wobbly windows but now i oddly have a new theme with transparent bards probably some settings in Compiz i will check it out.. i think i may start making some xubuntu tutorials because not many people know what xubuntu is like. it has many less options then ubuntu and everyone has ubuntu so their directions always seem to have mistakes to us xubuntu users. this compiz does make my PC alot slower though my 256mb of ram is not holding up to well i need to upgrade to 2gb ram well thanks for the help if i have more questions i will post..

---

### Post by Tom--d on 2009-01-07
Post the outcome of compiz in the terminal. It will say the problems your having.

---

### Post by MaximoMilkman on 2009-01-07
A new problem has arised now my windows wobble and i have a cube but idk how to change my window decortion theme?? it be default is some white thing.. i want it to be black. also the results of my putting in compiz in the terminal are as follows.. what is XGL??

joseph@joseph-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present.

---

### Post by MaximoMilkman on 2009-01-07
bump.. sorry i really need this resolved plus wanna know what XGL is and why i dont have it..

---

### Post by bixejo on 2009-01-07
> **MaximoMilkman said:**
> bump.. sorry i really need this resolved plus wanna know what XGL is and why i dont have it..
Try to open a terminal and type there:

```

ccsm

```This should open the compiz-config settings manager which shall allow you to change your preferences and adding/removing plugins to/from the active plugins list.

As for the windows' bars appearance, that seems to be a matter of Xfce (the default desktop manager for Xubuntu). I've never tried Xubuntu, but I guess you should probably have somewhere in your menus an option for changing themes and windows' appearance.

Hope this helps,

---

