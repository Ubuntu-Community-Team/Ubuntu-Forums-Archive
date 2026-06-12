---
title: "Mac/Linux desktop toolbar"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Gennn89 on 2010-08-10
Hey, new user to linux, saw a desktop toolbar that I believe first appeared on mac desktops. The one I'm referring to is the one that sits on the bottom of the screen on your desktop and has a "stage" for your favourite tools such as firefox and music and whatnot. I was hoping for the visual fx as well (meaning 3d and reflections) but Its not necessary. Ive seen this on mac linux and even windows vista and 7. Can anyone tell me how to get this tool? Im running ubuntu jaunty 9.04 i believe. thanks!

---

### Post by LowSky on 2010-08-10
avant-window-manager it is in the repos

---

### Post by dca on 2010-08-10
cairo-dock, as well

---

### Post by Temposs on 2010-08-10
Also:

Gnome-Do with the Docky extension. That's what I use :-)

---

### Post by Gennn89 on 2010-08-10
I searched for the gnome-do app but being slightly unfamiliar with this type of searching I was unable to figure out how to actually download the app. Can you tell me or give me a link to the site so i may download? Or do I need to look it up in the terminal or something? How do i put the 3d docky extension on the app?

---

### Post by Gennn89 on 2010-08-10
> **Gennn89 said:**
> I searched for the gnome-do app but being slightly unfamiliar with this type of searching I was unable to figure out how to actually download the app. Can you tell me or give me a link to the site so i may download? Or do I need to look it up in the terminal or something? How do i put the 3d docky extension on the app?

- May have figured it out as far as downloading the app goes, found it in the add/remove section, had to select all opensource... downloading now
Still need to figure out how to add the 3d docky extension..?

---

### Post by Gennn89 on 2010-08-10
For anyone else using jaunty 9.04 I also found this code useful
(gathered from [http://do.davebsd.com/wiki/index.php?title=Installing_Do#9.04_.28Jaunty.29](http://do.davebsd.com/wiki/index.php?title=Installing_Do#9.04_.28Jaunty.29))

> 9.04 (Jaunty)

Add the Gnome Do PPA Repository to your sources list. (See the Ubuntu Repositories).

deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main

Optional: Add key of repository

$ gpg --no-default-keyring --keyring /tmp/gnome-do.keyring --keyserver keyserver.ubuntu.com --recv A5D19FDCAA6ABB440CD3464628A8205077558DD0
$ gpg --no-default-keyring --keyring /tmp/gnome-do.keyring --export --armor  A5D19FDCAA6ABB440CD3464628A8205077558DD0 | sudo apt-key add -
$ rm /tmp/gnome-do.keyring

In Synaptic Package Manager, search 'gnome do' or install from the terminal:

$ sudo aptitude update && sudo aptitude install gnome-do


---

### Post by Gennn89 on 2010-08-10
Found the gnome-do app but it doesnt appear in the toolbar format as i was looking for. do i need the docky extension or did i find the wrong app?

---

### Post by yunone on 2010-08-10
i have used AWN and i like it.... give it a try

open synaptic>search for avant>Mark avant-window-navigator

follow install instructions

Start AWN by opening the main Ubuntu menu, move your cursor over "Accessories" and click on "Avant Window Navigator."



Right-click on the AWN bar that opens up. Select "Preferences" to change the default AWN settings. Select "Configure launchers" to add icons to the panel. Select "Close" to turn off AWN.



have fun!

---

### Post by qamelian on 2010-08-10
You need to select Docky as the theme in Gnome-do preferences.

---

### Post by Gennn89 on 2010-08-10
> **qamelian said:**
> You need to select Docky as the theme in Gnome-do preferences.

Got it thanks, found it on the same site posted earlier
([http://do.davebsd.com/wiki/Docky](http://do.davebsd.com/wiki/Docky))

Hard on the gfx card.. maybe better not until i get a new card. 
Thanks!

---

### Post by fabounet on 2010-08-13
you can try GLX-Dock, it's much lower on CPU.

---

### Post by cespinal on 2010-08-13
get in here 

[http://www.omgubuntu.co.uk/2010/08/omg-5-five-tips-hacks-and-tweaks-to-get.html](http://www.omgubuntu.co.uk/2010/08/omg-5-five-tips-hacks-and-tweaks-to-get.html)

you can thank me later :)

---

### Post by Nerflander on 2010-08-13
rocketdock ;'D i think


edit: my bad  windows only unless you do it on gnome but i looked to fast!

---

