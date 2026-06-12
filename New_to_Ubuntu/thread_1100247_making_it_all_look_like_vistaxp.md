---
title: "making it all look like vista/xp"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by cirabisi2009 on 2009-03-19
yeah. i am trying to change the desktop to look/operate like vist ( who really wants that,,, really!! )  well i have a friend thats converting to ubuntu and i want to make it a simple transition. so what do i do to switch it over? put menu bar on bottom and have the windows on the same bar? i want to basically convert it all to vista style menus.

what things might i have to download?

 thanx in advance!!





0

---

### Post by blackened on 2009-03-19
Check out some of the GnoMenu themes on gnome-look. Some are very similar to Vista.

---

### Post by cirabisi2009 on 2009-03-19
> **blackened said:**
> Check out some of the GnoMenu themes on gnome-look. Some are very similar to Vista.

i've looked and the things i try and get like linux broken vista it says i need to download some GTK file and i've downloaded all i could find in the synaptics and it still says it wont look the way it should cause of it.

---

### Post by cirabisi2009 on 2009-03-19
[http://www.gnome-look.org/content/show.php/Linux+Broken+Vista?content=99593]("http://www.gnome-look.org/content/show.php/Linux+Broken+Vista?content=99593")

like this.. this is the exact one i try and get but i dont know how to do it and what special apps i need to make it work?!?

---

### Post by sonu 1807 on 2009-03-19
Go to [http://ubuntu.online02.com/node/14](http://ubuntu.online02.com/node/14) and follow the instructions to get a complete XP (not vista) look.I checked it and it worked on my laptop

---

### Post by blackened on 2009-03-19
> **cirabisi2009 said:**
> i've looked and the things i try and get like linux broken vista it says i need to download some GTK file and i've downloaded all i could find in the synaptics and it still says it wont look the way it should cause of it.

GnoMenu is just a panel applet that replaces the Applications/Places/System style menus with one that mimics Vista's start menu.

I can't speak to the quality of Vista-ish GTK themes. I've never used any of them.

---

### Post by cirabisi2009 on 2009-03-19
> **blackened said:**
> GnoMenu is just a panel applet that replaces the Applications/Places/System style menus with one that mimics Vista's start menu.

I can't speak to the quality of Vista-ish GTK themes. I've never used any of them.

how do i get GnoMenu? i cant find a place to download it? can i find it in synaaptic?

---

### Post by cirabisi2009 on 2009-03-19
im guessing not](*,)

---

### Post by blackened on 2009-03-19
> **cirabisi2009 said:**
> how do i get GnoMenu? i cant find a place to download it? can i find it in synaaptic?

Nope, but there are debs for it here ->[https://launchpad.net/gnomenu/trunk/1.6]("https://launchpad.net/gnomenu/trunk/1.6").

---

### Post by cirabisi2009 on 2009-03-19
> **blackened said:**
> Nope, but there are debs for it here ->[https://launchpad.net/gnomenu/trunk/1.6]("https://launchpad.net/gnomenu/trunk/1.6").

how do i use .deb files?

---

### Post by blackened on 2009-03-19
> **cirabisi2009 said:**
> how do i use .deb files?

```
sudo dpkg -i */path/to/deb/file*
```

---

### Post by 73ckn797 on 2009-03-19
> **cirabisi2009 said:**
> how do i use .deb files?

Go to System/Administration/Synaptic Package Manager. There you will find "gdebi" which is a "deb" package manager. It will make it easy to install "debs". It is a graphical interface.

---

### Post by gandaran on 2009-03-19
> **cirabisi2009 said:**
> how do i use .deb files?
you just double click the package to install like in windows, simple!

---

### Post by abn91c on 2009-03-19
just install ```
sudo apt-get install kubuntu-desktop
```  and you get the attached screenshot

---

### Post by blackened on 2009-03-19
> **gandaran said:**
> you just double click the package to install like in windows, simple!

Guess it would've been helpful if I'd have mentioned gdebi from the start. Sorry about that.

---

### Post by cirabisi2009 on 2009-03-19
ook. got the Gdebi file.. so when i download the gnomenu package from launchpad it auto matically opens in gdebi. but after that i cannot find the program for the life of me.

---

### Post by gandaran on 2009-03-19
> **cirabisi2009 said:**
> ook. got the Gdebi file.. so when i download the gnomenu package from launchpad it auto matically opens in gdebi. but after that i cannot find the program for the life of me.
right click the panel » add to panel » gnomenu

---

### Post by linux6994 on 2009-03-19
.deb files are package files that will install with the deb package installer. It will bring in the package and install it if the proper dependencies are present.

---

### Post by cirabisi2009 on 2009-03-19
> **gandaran said:**
> right click the panel » add to panel » gnomenu

tried. i dont find any gnome menu :(

---

### Post by gandaran on 2009-03-19
> **cirabisi2009 said:**
> tried. i dont find any gnome menu :(

it's not gnome menu it's gnomenu , are you sure you installed the package, try rebooting the computer.

---

### Post by gandaran on 2009-03-19
exactly what did you install, theres another similar package called advanced gnome menu, which one?

---

### Post by cirabisi2009 on 2009-03-19
> **gandaran said:**
> it's not gnome menu it's gnomenu , are you sure you installed the package, try rebooting the computer.

im pretty sure. and i just rebooted. and theres still no gnomenu. 

packages: gnomemenuthemes
status: all dependancies are satisfied

im going here [https://launchpad.net/gnomenu/trunk/1.6]("https://launchpad.net/gnomenu/trunk/1.6")
and i download the 3rd link. its the only one where the dependancies are satisfied?!

---

### Post by gandaran on 2009-03-19
> **cirabisi2009 said:**
> im pretty sure. and i just rebooted. and theres still no gnomenu. 

packages: gnomemenuthemes
status: all dependancies are satisfied

im going here [https://launchpad.net/gnomenu/trunk/1.6]("https://launchpad.net/gnomenu/trunk/1.6")
and i download the 3rd link. its the only one where the dependancies are satisfied?!
I believe you just download the themes package, you have to install the gnomenu package too!
it's the second one.

---

### Post by cirabisi2009 on 2009-03-19
when i download the second package it says 

package: gnomenu
  ERROR: Dependancy is not satisfiable: gnomemenuthemes
status:

---

### Post by gandaran on 2009-03-19
> **cirabisi2009 said:**
> when i download the second package it says 

package: gnomenu
  ERROR: Dependancy is not satisfiable: gnomemenuthemes
status:
you have to install gnomemenuthemes first then gnomenu, you only need these two packages.

---

### Post by cirabisi2009 on 2009-03-19
idk.. still not working .. im a just give up i think.. :(

---

### Post by SunnyRabbiera on 2009-03-19
A way I made my system vista/XP like in the past is to install Mint Menu:
[http://packages.linuxmint.com/](http://packages.linuxmint.com/)

Can be found on this page, Mint menu can give you a XP like menu

---

### Post by gandaran on 2009-03-19
> **cirabisi2009 said:**
> idk.. still not working .. im a just give up i think.. :(
then you are doing something wrong! are you downloading the right packages?

---

### Post by cirabisi2009 on 2009-03-19
> **gandaran said:**
> then you are doing something wrong! are you downloading the right packages?

no matter which package except the 3rd link i get missing dependencies

---

### Post by gandaran on 2009-03-19
> **cirabisi2009 said:**
> no matter which package except the 3rd link i get missing dependencies
so the third link package is installed and you still get dependencies error installing the second link package? this should't be, try reinstalling the third link package again and then the gnomenu package.

---

### Post by [tke]PB506 on 2009-05-03
Just go to [Gnomenu download home]("https://launchpad.net/gnomenu/trunk/1.6")


Download 3 deb files, gnomenuthemes gnomenu gnomenu-themes-gnomelook and install them
 After all the nessesary software installed, you can add a GnoMenu to your panel. Finally, you&#8217;ll have a Vista&#8217;s like menu, like my own.


Download them in the order listed above.  Go to the desired panel, select "add to panel," scroll down to Gnomenu, push OK.  You should now have the Gnome Icon on your panel which contains the contents of the standard Gnome menu bar




*I found this info at [http://abz89.wordpress.com/tag/how-to-install-gnomenu/](http://abz89.wordpress.com/tag/how-to-install-gnomenu/) and would like to thank the author of said information for their assistance

---

