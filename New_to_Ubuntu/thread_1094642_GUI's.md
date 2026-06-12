---
title: "GUI's"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by barbz127 on 2009-03-12
Hi all,

Im setting up a server running lamp for ntop.

I need a gui to be able to run etherape to get good real time monitoring.

I dont need all the office tools,etc which i would get if i just install ubuntu-desktop...

so what the easiest and smallest gui that i can install that is part of the ubuntu repositories.

Cheers
Paul

---

### Post by spcwingo on 2009-03-12
The smallest would be jwm directly on top of X.  The easiest of the smaller in my opinion would be lxde, but you have to add a repo to get it.  To add the repo in Hardy, do this:

```
sudo nano /etc/apt/sources.list
```

Scroll to the bottom and add:

```
deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main
```

then press CTRL+O (capital "O", not a zero), then CTRL+X.

after that enter this:

```
sudo apt-get update && sudo apt-get install xorg lxde
```

after that just type:

```
startx
```

to enter your new lxde desktop.  :)

Keep in mind you will still have to log in textually and enter startx every time you boot this way.  If you would like a lite graphical login you could install slim.

```
sudo apt-get install slim
```

BTW, I'm not sure if there's a lxde ppa for intrepid or jaunty, so you might want to do some googling if your on those versions.

---

