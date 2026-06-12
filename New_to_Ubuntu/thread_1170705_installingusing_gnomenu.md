---
title: "installing/using gnomenu?"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by cirabisi2009 on 2009-05-26
how? where? i am looking at this.. i want my task bar to be similar to a vista menu. seeing that im on a netbook and i dont like the NBR. i want all my stuff to be under 1 menu button. so i am choosing to go with [http://www.gnome-look.org/content/show.php/Linux+Broken+Vista?content=99593]("http://www.gnome-look.org/content/show.php/Linux+Broken+Vista?content=99593")
 and please spare me when it comes to the fact the some people believe "gnome isnt supposed to look like that" or "linux is not windows if you want that look go back to windows" . i just would like some help getting this menu to work properly on my machine. i dont even know how to get gnomenu. help please. thanks in advance :)

---

### Post by billgoldberg on 2009-05-26
> **cirabisi2009 said:**
> how? where? i am looking at this.. i want my task bar to be similar to a vista menu. seeing that im on a netbook and i dont like the NBR. i want all my stuff to be under 1 menu button. so i am choosing to go with [http://www.gnome-look.org/content/show.php/Linux+Broken+Vista?content=99593]("http://www.gnome-look.org/content/show.php/Linux+Broken+Vista?content=99593")
 and please spare me when it comes to the fact the some people believe "gnome isnt supposed to look like that" or "linux is not windows if you want that look go back to windows" . i just would like some help getting this menu to work properly on my machine. i dont even know how to get gnomenu. help please. thanks in advance :)

These are the instructions provided by the author.

> How to install:
Extract "Linux Broken Vista.tar.gz",
Copy the the content of the "Linux Broken Vista" output folder in:
/usr/share/gnomenu/Themes/
Remember that you have to be root to do this passage.
From terminal:
cd /root/of/the/extractedfolder/"Linux Broken Vista"
sudo mv * /usr/share/gnomenu/Themes
From nautilus:
Open a terminal:
sudo nautilus
You are now in nautilus but as root.
Copy as usual.

I'll break it down for you.

Press "alt+f2" and enter "gksu nautilus" in the run dialog.

You have now started nautilus as root.

Find the file you just downloaded, right-click it and choose "extract here".

Now copy the newly made folder to /usr/share/gnomenu/Themes/

I'm not on Linux atm, but I presume that folder already exists.

Now you'll have to add it to the panel. Right-click the panel and choose "add to panel".

It should be in the list.

It could be that it's a mod for one of the existing menu's in there (there are two by default).

---

### Post by hockeyhead019 on 2009-05-26
hey man,

here is a link to the site where you can download the .deb packages for the gnomenu...

as to how to get it to work well with different themes... well i'm still workin on that one myself because i just downloaded it as well and i'm working on getting it to work right with some themes haha

---

### Post by bowens44 on 2009-05-26
> **hockeyhead019 said:**
> hey man,

here is a link to the site where you can download the .deb packages for the gnomenu...



Did you forget to include the link? I don't see it.

---

### Post by hockeyhead019 on 2009-05-26
yup completely forgot to put the link in there haha my bad...

here's a link to the 1.6 .deb files but you can make the latest version (1.9.8) from this source

[Link To Source (1.9.8)]("https://code.launchpad.net/gnomenu/1.9/1.9.8")

[Link to the .deb packages]("https://launchpad.net/gnomenu/trunk/1.6")

---

### Post by blueridgedog on 2009-05-26
You should read the feedback on the posting that you linked to.  The author responds specifically to your question:

> This is a theme for a menu Vista/Xp/etc Like and NOT for the WHOLE system.
If you want the menu for the whole system:
Theme:
[http://www.gnome-look.org/content/show.php/Windows+Vista+Inspired+Theme+?content=99252](http://www.gnome-look.org/content/show.php/Windows+Vista+Inspired+Theme+?content=99252)
Icon:
[http://www.gnome-look.org/content/show.php/Linux+Broken+Vista?content=99611](http://www.gnome-look.org/content/show.php/Linux+Broken+Vista?content=99611)
If you want a menu as the one in the pictures go to:
[https://launchpad.net/gnomenu/+download](https://launchpad.net/gnomenu/+download)
Install third link first, then second, then first one.
Right click on the traybar>add to panel>gnomenu.
Right Click on the Gnomenu Icon>Preferences>
And then customize it with my theme.
Of course first you have to follow the istructions in the description =)

So, the first task is the above, then you can download the theme he has supplied and install per the instructions listed.  Good luck.

---

### Post by albinootje on 2009-05-26
[https://launchpad.net/gnomenu/](https://launchpad.net/gnomenu/)

---

### Post by cirabisi2009 on 2009-05-26
ok thanks guys. i read the instructions the guy gave with the gnomenu theme but i didnt understand. maybe i shoulda included that. sorry for the lack of info. but thank you all. i got it working. i will post a screen shot in a little bit to show you all how it turned out :biggrin:

SOOO! what if i just happen to type this in a terminal. 

sudo apt-get install gnome menu

will this install the gnomenu? i came up with my self and i am quite a noob when it comes to using the terminal. i thought i'd give it a shot and its downloading right now. did i do it right?

---

### Post by cirabisi2009 on 2009-05-26
no help???

---

### Post by Viva on 2009-05-27
> **cirabisi2009 said:**
> ok thanks guys. i read the instructions the guy gave with the gnomenu theme but i didnt understand. maybe i shoulda included that. sorry for the lack of info. but thank you all. i got it working. i will post a screen shot in a little bit to show you all how it turned out :biggrin:

SOOO! what if i just happen to type this in a terminal. 

sudo apt-get install gnome menu

will this install the gnomenu? i came up with my self and i am quite a noob when it comes to using the terminal. i thought i'd give it a shot and its downloading right now. did i do it right?

No, it will install two different programs "Gnome and Menu". I think 'gnome' is a meta package that installs a lot of programs.

---

### Post by Viva on 2009-05-27
And I suggest that you don't experiment with apt-get or anything that remotely uses sudo until you get used to ubuntu

---

### Post by fluxlizard on 2009-05-27
I'm pretty sure this is in the repos.

Search for gnome menu in synaptic- I think I was fooling around using this menu a few months ago and installed it from synaptic. It might be called something else, so you may just want to search synpatic for menu and find it that way.

Then right click on the panel where you want to put the new menu, select add to panel, and choose it from the list.

---

### Post by WinterMadness on 2009-05-27
i wouldnt recommend using gnomenu on a netbook, its too big. i would recommend using the normal jaunty for your netbook like i do, works great.

anyway, i noticed gnomenu has troulbe installing its self correctly sometimes, so once you have ran everything (.debs, scripts etc) make sure the lib/bin/share folders that come with it are actually in your lib/bin/share folders and it will work

---

### Post by cirabisi2009 on 2009-05-28
> **Viva said:**
> And I suggest that you don't experiment with apt-get or anything that remotely uses sudo until you get used to ubuntu

gotta start somewhere dont ya? if it hurts anything then i can just do a fresh install. and i have " THE OFFICIAL UBUNTU BOOK THIRD EDITION " to guide me along the way.

---

### Post by Viva on 2009-05-28
> **cirabisi2009 said:**
> gotta start somewhere dont ya? if it hurts anything then i can just do a fresh install. and i have " THE OFFICIAL UBUNTU BOOK THIRD EDITION " to guide me along the way.

Thats the spirit;)

---

### Post by Whise on 2009-06-04
> **WinterMadness said:**
> i wouldnt recommend using gnomenu on a netbook, its too big. i would recommend using the normal jaunty for your netbook like i do, works great.

anyway, i noticed gnomenu has troulbe installing its self correctly sometimes, so once you have ran everything (.debs, scripts etc) make sure the lib/bin/share folders that come with it are actually in your lib/bin/share folders and it will work


since the power of gnomenu is its theming abilities , and there are a couple of themes speacially made for notebooks that shoulnt be the problem

---

### Post by jonnydopemsr on 2009-08-22
nvm

---

### Post by Rob@ThePCWiz.info on 2010-05-25
Ok so now I AM having an issue.
I installed GnoMenu just fine, the issue is that it's not coming up in the selection when i go to add it to my panel. Any comments? I added the repos below:
```

deb [http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu](http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu](http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu) jaunty main

```
then did
```

sudo apt-get update
sudo apt-get install gnomenu

```

Success.
but now, i can't add it to my Panel.

---

