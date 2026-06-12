---
title: "add gui from live cd to fresh server install."
date: 2009-06-15
forum: New to Ubuntu
---

### Post by Black Kelpie on 2009-06-15
Hi guys, I just installed a 8.10 server but since I&#7743; still kinda new to the terminal I like to add a GUI for now. 
I know this can be done by "sudo apt-get install desktop" but the thing is : I live in Australia and I have to live with these @#$%^ download quota limits. 
I also have the desktop live cd here, version 8.10 as well, can I install the desktop GUI from the cd to the server via the terminal? If so, how?

---

### Post by ultratwo on 2009-06-15
Just do a reinstall with your livecd (that won't attempt any downloads).

It far easier to use 'Sudo apt-get install desktop' to add a desktop than it is from a livecd.

If you have any packages on the server that you want that are not on the live cd (which I doubt since you don't seem to have used it) you could manually copy them (/var/cache/apt/archives) and to another media with the livecd and then install after your desktop install.

---

### Post by Black Kelpie on 2009-06-15
Ok I had to read that twice and I still think I only partially understand. Are you saying I should do a reinstall of the desktop cd instead of the server and then later on add server packages to it?

---

### Post by Cheesemill on 2009-06-15
It's not possible to install packages from the Live CD because there aren't any on the disc. It's only the Alternate Install and Server CD's that have packages on them.

---

### Post by Nythain on 2009-06-15
the live cd doesnt have packages on it for reals? i mean, if it did, all the user would have to do is add thier cdrom to teh apt sources.list... but i was unaware livecd didnt have any of the packages it installs on it

---

### Post by twright on 2009-06-15
To add a gui to a server you do not need the whole Ubuntu desktop package, just install gnome and anything else you need as you go

---

### Post by Cheesemill on 2009-06-15
> **Nythain said:**
> the live cd doesnt have packages on it for reals? i mean, if it did, all the user would have to do is add thier cdrom to teh apt sources.list... but i was unaware livecd didnt have any of the packages it installs on it

The Live CD doesn't have any .deb packages because it contains a squashed filesystem of an installed version of Ubuntu that gets decompressed onto your drive when you install, the packages don't get installed one by one.

If you look at the Alternate Install CD then it contains all of the .deb packages that you would expect, there just isn't room on 1 CD for the squashed filesystem (which is what enables the Live CD to work) and the packages.

This is also the reason why you can only perform an upgrade from the Alternate CD and not the Live one (it's also why an install from the Live CD is quicker than any other method).

---

### Post by Black Kelpie on 2009-06-15
> **twright said:**
> To add a gui to a server you do not need the whole Ubuntu desktop package, just install gnome and anything else you need as you go

So how does that work? How can I add the cd to the resources list in the terminal? And how do I only get the gnome desktop to install?

---

### Post by Cheesemill on 2009-06-15
You're honestly much better off installing the Desktop version if you want a GUI and then adding any server packages you require.

Bear in mind that having a GUI installed on a server is not a good idea.

---

### Post by twright on 2009-06-15
> **Black Kelpie said:**
> So how does that work? How can I add the cd to the resources list in the terminal? And how do I only get the gnome desktop to install?
sudo apt-get install gnome should do the trick :-) You might also want to try webmin first which gives you a nice web-based control panel for your server.

---

### Post by Black Kelpie on 2009-06-15
> **Cheesemill said:**
> You're honestly much better off installing the Desktop version if you want a GUI and then adding any server packages you require.
Bear in mind that having a GUI installed on a server is not a good idea.

I know that, apparently, security wise it's better to have no GUI but I'm still getting used to the terminal and basically, at this stage, I'm only copying commands found for instance here in the forums, into the terminal. A GUI is, for me,  more helpful than a terminal to install and configure things needed for the server. 

But, in this case, you're saying I'm better off reinstalling the thing using the desktop cd?

---

### Post by Cheesemill on 2009-06-15
If you don't want to have to download all of the desktop packages because of your bandwidth, then yes, you may as well do a fresh install from the Desktop CD and add any server packages to that, it will save you alot of traffic.

---

### Post by twright on 2009-06-15
> **Black Kelpie said:**
> I know that, apparently, security wise it's better to have no GUI but I'm still getting used to the terminal and basically, at this stage, I'm only copying commands found for instance here in the forums, into the terminal. A GUI is, for me,  more helpful than a terminal to install and configure things needed for the server. 

But, in this case, you're saying I'm better off reinstalling the thing using the desktop cd?
you should have a look at [http://www.webmin.com/](http://www.webmin.com/) as an alternative then. It provides an online GUI/interface which is more suited to setting up server stuff whilst still being quite easy to use. You can do most things that you would with the standard Ubuntu UI and extra stuff like configuring apache without needing to use a command line.

---

### Post by Black Kelpie on 2009-06-15
ha that's quite eh...funny, in a way. I was about to mention Webmin as software that I used on a previous install on another machine. Do you mean I can use Webmin as a standalone web based GUI instead of installing desktop? That never occurred to me.

---

### Post by Celauran on 2009-06-15
Clearly it's not going to have everything a desktop GUI will have, but it should act as a suitable go-between.

---

### Post by theozzlives on 2009-06-15
The server software is mainly for REAL servers. My WWW/File/Print server is actually Desktop from the live CD. You can do LAMP, DHCP, DNS, Mail, FTP, etc from the desktop version. What you're calling "Terminal" is actually "Console".

---

### Post by rbueno on 2009-06-15
i don't know it is working but tyr this
sudo apt-get install "X Window System" "GNOME desktop environment"
it is working in dedicated server like centos. Just try it. there no harm to try.

---

### Post by Cheesemill on 2009-06-15
> **rbueno said:**
> i don't know it is working but tyr this
sudo apt-get install "X Window System" "GNOME desktop environment"
it is working in dedicated server like centos. Just try it. there no harm to try.

The actual commands to install a basic desktop environment would be:
```
apt-get update && apt-get -y install xorg && apt-get -y install gdm gnome-core ubuntu-artwork fast-user-switch-applet && shutdown now -r
```
Although I still don't recommend it :)

---

### Post by jamesrfla on 2009-06-15
> **Black Kelpie said:**
> I know that, apparently, security wise it's better to have no GUI but I'm still getting used to the terminal and basically, at this stage, I'm only copying commands found for instance here in the forums, into the terminal. A GUI is, for me,  more helpful than a terminal to install and configure things needed for the server. 

But, in this case, you're saying I'm better off reinstalling the thing using the desktop cd?

There is no problem with having a GUI for beginners. When I first started configuring my server I installed the desktop edition since I was going to use it as a desktop and server. I also did it since I needed access to forums and the internet for help configuring my server. The desktop edition can do everything that the server edition can as far as server services. The only problem is the GUI slows down the server but you won't notice it that much depending on your system.

---

### Post by twright on 2009-06-16
> **Black Kelpie said:**
> ha that's quite eh...funny, in a way. I was about to mention Webmin as software that I used on a previous install on another machine. Do you mean I can use Webmin as a standalone web based GUI instead of installing desktop? That never occurred to me.
Well I don't have any GUI on most of the servers I have setup and use webmin and the commandline almost excursively but it really depends what you want to use it for. If you actually want to desktop stuff as well with it then you might want to install gnome/the GUI but otherwise I'm not sure how much use it would be (it is really not designed for configuring servers) compared to something like webmin.

---

