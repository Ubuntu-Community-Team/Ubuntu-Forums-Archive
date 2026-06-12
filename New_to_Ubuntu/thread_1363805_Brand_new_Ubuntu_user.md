---
title: "Brand new Ubuntu user"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by bm14 on 2009-12-24
Well I got tired of using windows vista, so i decided to give Ubuntu a try. I'm currently using ubuntu 9.10 and i don't really have any clue on how to do pretty much anything. I have some questions about ubuntu,

Where should i look to find cool ways to personalize my desktop? 
What programs allow me to access my ipod, if there are any?(2nd gen ipod touch)
What is the easiest way to get music and pictures from vista to ubuntu if im using dual boot?
And this sounds dumb, but with vista i could put my laptop to sleep overnight and when i woke up the battery would be where it was, but if i put my laptop to sleep running ubuntu i wake up and its practically dead. Are there any ways to stop that?

---

### Post by Geoff918 on 2009-12-24
Well, if you're using Ubuntu you'll be on GNOME. You can go to gnome-look.org to customize things.

There are some ipod access programs. gtkpod for one. I have a ton of things come up for ipod, but I also have extra repositories. I definitely know gtkpod will be accessible to you.

Mount the Windows partition. Just click on the partition in the "Places" menu and when you select that partition it will prompt you to enter your password. If you're using a Wubi install then it will be in the /hosts directory.

You can powertune your laptop with the following:

powertop

Just sudo aptitude install powertop

then run

sudo powertop

It will figure out how to drop your power consumption.

---

### Post by bm14 on 2009-12-24
Sorry, i'm a complete noob. How would i sudo aptitude install powertop?

I just went to my battery preferences and made it so my laptop will hibernate when i close the lid. Hopefully this will fix the problem.

---

### Post by Geoff918 on 2009-12-24
No problem.

Applications -> Accessories -> Terminal

In the resulting box you can type the commands. :) Let me know if you need more help (I might be away for a bit getting some food, though)

---

### Post by spiderbatdad on 2009-12-24
A lot of the tools for personalizing the desktop are right at your finger tips. For example the top and bottom panels are totally customizable. They can be transparent, auto-hidden, you can have one or both, they can hold many icons, and on and on. You can install a mac like dock (cairo-dock) from synaptic package manager. (System>>Administration>>Synaptic Package Manager.) You can add conky and a conky config file to have all sort of really cool information displayed. You can customize the themes from the appearances menu, and combine icons from one theme with window decorations from another theme. You can get some really sweet themes from Bisigi ppa at Launchpad, and Gnomelook.org. Welcome to Ubuntu-Debian/Gnu/Linux, and the forums.

---

### Post by sandyd on 2009-12-24
> **bm14 said:**
> Well I got tired of using windows vista, so i decided to give Ubuntu a try. I'm currently using ubuntu 9.10 and i don't really have any clue on how to do pretty much anything. I have some questions about ubuntu,

1. Where should i look to find cool ways to personalize my desktop? 
2. What programs allow me to access my ipod, if there are any?(2nd gen ipod touch)
3. What is the easiest way to get music and pictures from vista to ubuntu if im using dual boot?
4. And this sounds dumb, but with vista i could put my laptop to sleep overnight and when i woke up the battery would be where it was, but if i put my laptop to sleep running ubuntu i wake up and its practically dead. Are there any ways to stop that?
1. what "cool ways" are you looking for?
for desktop eye candy, such as the famous desktop cube (millions on youtube), you will want to install compiz ```
sudo apt-get install compiz compiz-fusion-plugins* compizconfig-settings-manager
```
then, you can either right click on desktop, -> properties (or something like this)
select visual effects.
then you can fiddle with it as much as you want

or

run
```

compizconfig-settings-manager
```set the stuff you want, and run
```

compiz --replace

```to activate it

if your seriously looking for eye candy,
```

sudo apt-get install kubuntu-desktop
```and selecting KDE as your session (in the login window) 
is the way to go.
p.s. almost forgot.
when me or someone else types ```
sudo apt-get *packagename*
```you can alternatively install the application by searching for *packagename* in synaptic
p.p.s. installing graphics drivers if your using ati/nvidia card is recommended

and personalizing the desktop is easy.
you can go to gnome-art where there are millions of themes avalible for free.
download them, and drag and drop the file you just downloaded onto the themes window.

2. gtkpod. that is, providing youve got the non restricted itouch. which i think you do. you will need to jailbreak it if you do.
for more info, read here
[https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

3. mount your ntfs windows partition using ntfs-config
```

sudo apt-get install ntfs-config
gksudo ntfs-config

```4. is a currently a bug thats been running accross several releases now
unless, your talking about hibernate

oh, and have a merry christmas

---

### Post by Geoff918 on 2009-12-24
Kubuntu? Eww. Nice appearance, terrible applications. I vote 'no'. Konqueror 'nuff said.

---

### Post by sandyd on 2009-12-24
> **Geoff918 said:**
> Kubuntu? Eww. Nice appearance, terrible applications. I vote 'no'. Konqueror 'nuff said.
no problem.
run dolphin or natilus (actually still works in KDE) ;)

---

### Post by Geoff918 on 2009-12-24
> **carlee said:**
> no problem.
run dolphin or natilus (actually still works in KDE) ;)

True Carlee. I greatly prefer the appearance of KDE. It's more sleak and prettier. But it's not just one of the apps. It's pretty much *ALL* of the apps I don't like.

It's all a matter of tastes and preferences. I have tweaked out my desktop where it seems everyone always stops and asks me how my system looks so good (yes, I can brag a little). But, I've stuck with GNOME.

Actually, I really like the look of OpenGEU, but I never kept up with it. They're too slow and too small to exist long term, too.

---

### Post by thomashw on 2009-12-25
For your iPod, try Songbird 1.2. It's pretty similar to iTunes.

I think Songbird has up to 1.6 out, but the iPod support is lacking. It works 100% in 1.2 so I went back to that.

---

### Post by Locke_99GS on 2009-12-25
Compiz is installed by default, I thought, (could be wrong) though you will need 3d drivers installed before you can use it. If you're using nVidia or ATI, you'll likely prefer their proprietary drivers, which jockey will install for you. *ccsm* or another manager is required if you wish to tweak it.

Cairo is, IMO, outdated. Try the 0.4 trunk of AWN, or even Docky; they're looking pretty slick these days.

I thought most music players had ipod support, including Rhythmbox, which is installed by default.

Full NTFS support has been out-of-box for quite some time now. Can be mounted directly with *mount* or in fstab, or via fuse in GNOME/KDE.

---

### Post by thomashw on 2009-12-25
> **Locke_99GS said:**
> I thought most music players had ipod support, including Rhythmbox, which is installed by default.
I've tried Rhythmbox, Amarok, gtkpod, yamipod, Banshee, and Songbird.

The one I liked the best was Songbird - the other's I literally hated.

---

### Post by spiderbatdad on 2009-12-25
> **Locke_99GS said:**
> 
Cairo is, IMO, outdated. Try the 0.4 trunk of AWN, or even Docky; they're looking pretty slick these days.


That's an odd statement considering cairo-dock [[COLOR="Blue"]team[/COLOR]]("http://translate.google.com/translate?hl=en&sl=fr&u=http://cairo-dock.org/&ei=Ta80S5e0F8e1lAfrhtyeBw&sa=X&oi=translate&ct=result&resnum=2&ved=0CAwQ7gEwAQ&prev=/search%3Fq%3Dcairo-dock%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3Dkk9") is alive and well. In fact the dock is looking better and better, with more themes and mac like display options. I've tried awn and docky and found both very buggy.

---

### Post by Anuovis on 2009-12-25
There is a sticky post in *Absolute Beginner Talk* that will lead you to a .pdf guide. This might be helpful to learn more about Ubuntu in general.
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

Ubuntu has many desktop environments, Gnome, KDE, Xfce. Right now you have Gnome since it comes as a default one, but you can change it later. Do not worry too much now, play around with Gnome for a while. Once you get more used to Linux, search about the other two. People (dis)like them for different reasons, none is ultimately the best. Be sure to check KDE later on.

People mentioned docks in this thread as well. They might help you to customize the desktop and make it "cooler". Be sure to check the Gnome *panels* as well, you can change their size, make them transparent, auto-hide, etc. It is also possible to add new useful objects there.

---

### Post by mutex023 on 2009-12-25
@bm14 I think you might want to try this - 
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)
As for making your desktop look cool try this - 
[http://sourceforge.net/projects/mac4lin/](http://sourceforge.net/projects/mac4lin/)
And about the commands, instead of 'sudo apt-get install whatever',
Its better you try : System > Administration > Synaptic Package Manager and search for 'whatever'.

---

### Post by Norm24 on 2009-12-25
The PocketGuide that mutex023 mentioned is an excellent suggestion.Before I post here I go to it first whenever I have a problem.

---

### Post by KajuNM on 2009-12-28
I just moved to Ubuntu from Windoze Xp a few weeks ago and never looked back. If you stay with Linux you'll like it a lot better. So here are a few web-sites that will help you make the switch from the other OS.

[http://www.youtube.com/user/gotbletu](http://www.youtube.com/user/gotbletu)
[http://book.opensourceproject.org.cn/distrib/ubuntu/movingtoubuntu/](http://book.opensourceproject.org.cn/distrib/ubuntu/movingtoubuntu/)
[http://book.opensourceproject.org.cn/distrib/ubuntu/official/](http://book.opensourceproject.org.cn/distrib/ubuntu/official/)

Enjoy.......

---

