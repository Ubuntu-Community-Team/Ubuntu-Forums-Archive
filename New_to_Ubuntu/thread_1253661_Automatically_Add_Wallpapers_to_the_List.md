---
title: "Automatically Add Wallpapers to the List"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by Penguin Guy on 2009-08-30
Attached is a script I wrote which will add a single background to the list, now you just need to integrate that into your system with some kind of loop. You can access help by typing [COLOR="Green"]add-background.sh -?[/COLOR]; good luck!

Alternatively, there is the nautilus extension nautilus-wallpaper, which adds a right-click option to set a picture as the wallpaper. To get it [click here]("apt:nautilus-wallpaper"), run [COLOR="Green"]sudo apt-get install nautilus-wallpaper [/COLOR] or [search the repositories]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by fooman on 2009-08-30
not sure if this will help,  but there is an add-on to nautilus that will let you right-click on an image and have the option to "set as wallpaper"

in most cases,  this *will* add that image to the list you see when you go to system > preferences > appearance > backround

occasionally,  the image does not show up in the list...it will still be set as your wallpaper,  just doesn't show up in the choices of backround (sorry,  i don't know why).

anyways,  it is called "nautilus-wallpaper" and can be found in synaptic (system > administration > synaptic package manager) or open a terminal and type or copy/paste the following:
```

sudo apt-get install nautilus-wallpaper
```after installing,  you will need to logout and back in again....then  just right-click on an image (must be on your hard drive) and you should see the new option..."set as wallpaper"

hope that helps.

---

### Post by credobyte on 2009-08-30
Check this file:
```
/usr/share/gnome-wallpaper-properties/desktop-backgrounds-basic.xml
```

---

### Post by Penguin Guy on 2009-08-31
> **fooman said:**
> *On the subject of nautilus-wallpaper.*
Thinking about it, that's probably just as good as my solution, but I'm not going to give up just yet.

> **credobyte said:**
> Check this file:
```
/usr/share/gnome-wallpaper-properties/desktop-backgrounds-basic.xml
```
I think I found the file you meant at: [COLOR="Green"]/usr/share/gnome-background-properties/ubuntu-wallpapers.xml[/COLOR]. But it doesn't look like the file I'm looking for. What I want is something (probably a .xml file) that has a list of the users backgrounds in.

---

### Post by credobyte on 2009-08-31
> **Penguin Guy said:**
> Thinking about it, that's probably just as good as my solution, but I'm not going to give up just yet.


I think I found the file you meant at: [COLOR=Green]/usr/share/gnome-background-properties/ubuntu-wallpapers.xml[/COLOR]. But it doesn't look like the file I'm looking for. What I want is something (probably a .xml file) that has a list of the users backgrounds in.

I don't get it .. It is an XML file and you can append your own list of wallpapers. What I'm missing here ?

---

### Post by Cheezespread on 2009-08-31
> **Penguin Guy said:**
> Thinking about it, that's probably just as good as my solution, but I'm not going to give up just yet.


I think I found the file you meant at: [COLOR="Green"]/usr/share/gnome-background-properties/ubuntu-wallpapers.xml[/COLOR]. But it doesn't look like the file I'm looking for. What I want is something (probably a .xml file) that has a list of the users backgrounds in.

Aint that an xml file ?.. 
For me it does reference the wallpapers kept in this directory :
```
/usr/share/backgrounds/
```

Gedit shows :
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
  <wallpaper>
    <name>Ubuntu</name>
    <filename>/usr/share/backgrounds/warty-final-ubuntu.png</filename>
    <options>zoom</options>
    <pcolor>#b06840</pcolor>
    <scolor>#b06840</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
  <wallpaper>
    <name>Simple</name>
    <filename>/usr/share/backgrounds/simple-ubuntu.png</filename>
    <options>zoom</options>
    <pcolor>#c58357</pcolor>
    <scolor>#c58357</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
</wallpapers>
```

---

### Post by Penguin Guy on 2009-08-31
> **Cheezespread said:**
> Aint that an xml file ?.. 
For me it does reference the wallpapers kept in this directory :
```
/usr/share/backgrounds/
```

Gedit shows :
```
*<XML File Cut out to Save Space>*
```
Indeed it is an XML file, indeed it does have a list of backgrounds in, but it doesn't have **my** list of backgrounds in. By complete coincidence I have just found the file I am looking for, it is located at [COLOR="Green"]~/.gnome2/backgrounds.xml[/COLOR]. Now I just need to write a script to add the wallpapers to the XML file.

---

### Post by golroch on 2009-11-19
After reading this I found some useful information but the above does not show the proper solution, though I may be wrong. 
In the directory *[COLOR="Red"]/usr/share/backgrounds/cosmos/background-1.xml[/COLOR]*
This file has the file listing for pictures in the cosmos folder. Therefore your pictures that need to be added to the slide show of backgrounds is here. **SUDO** Edit the xml file and add the lines
    <from>/usr/share/backgrounds/cosmos/sombrero.jpg</from>
    <to>/usr/share/backgrounds/cosmos/whirlpool.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/whirlpool.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/whirlpool.jpg</from>
[I][COLOR="DarkGreen"]    <to>/usr/share/backgrounds/cosmos/bluemoon.jpg</to>
  </transition>
<static>
    <duration>1795.0</duration>
    <file>/usr/share/backgrounds/cosmos/bluemoon.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/usr/share/backgrounds/cosmos/bluemoon.jpg</from>
    <to>/usr/share/backgrounds/cosmos/cloud.jpg</to>[/COLOR][/I]
  </transition>
</background>

Note whirlpool was the last picture on my list  with a transition to cloud therefore bluemoon is the new one you want to add. At first it did not work until I realized the last 'cloud.jpg' had to be retransitioned. So I had to add bluemoon to the transition of whirlpool, meaning edit the last line of the existing file and then add a new set of transition lines. Save the file and go back to desktop changer and click on the slide show cosmos one, you will see a little play button where you can scroll through the pictures and viola you will see the newly added pics.

Enjoy!

Other useful links was this one where you can create a whole new xml file for different themes based on your mood for the day :-)
[http://ubuntuforums.org/showthread.php?t=1329147&page=2](http://ubuntuforums.org/showthread.php?t=1329147&page=2)

---

### Post by jaysscholar on 2012-01-20
I've been thinking of writing a script to write ubuntu-wallpapers.xml. Then I found one over at [http://askubuntu.com/questions/35759/how-do-i-set-another-search-directory-for-wallpapers](http://askubuntu.com/questions/35759/how-do-i-set-another-search-directory-for-wallpapers) . I do think I might implement it as a service so it monitors a particular folder.

However, does anybody know what the pcolor and scolor tags are for? In my file, most are just 000000 so that's got me thinking it's not very important. Anybody know that for sure?

---

