---
title: "Cairo Dock"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by thusspakeblixa on 2009-10-26
Hey there, I'm a noob. 
I'm trying to install Cairo Dock because AVN won't work (screen isn't composited). 
I can bring up the list, but what do I do then? I've read [this]("https://help.ubuntu.com/community/CairoDock") but I still can't get Cairo Dock.

---

### Post by phidia on 2009-10-26
> To add the Cairo-Dock repository to your sources open the sources.list file:


gksudo gedit /etc/apt/sources.list
and add the appropriate repository to the end of the file:


deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) jaunty cairo-dock  # For Ubuntu 9.04

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock  # For Ubuntu 8.10

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock  # For ubuntu 8.04
The signed GPG key for identification of the repository is:


wget -q [http://repository.cairo-dock.org/cairo-dock.gpg](http://repository.cairo-dock.org/cairo-dock.gpg) -O- | sudo apt-key add -
Then, to install Cairo-Dock, issue these two commands in the terminal:


sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins


Make sure you are following all of that. You need to add the specific repository for the ubuntu version that you're using. Let the thread know specifically what steps are failing and what the output is if you have problems with any of that. Hope that helps.

---

### Post by howefield on 2009-10-26
Try opening up a terminal, Applications > Accessories > Terminal and type

```
sudo apt-get update
```

Followed by your password when prompted. After that, type

```
sudo apt-get install cairo-dock
```

You can alternatively install with Synaptic Package Manager, System > Administration > Synaptic Package Manager. Search for cairo-dock, right click and select mark for installation. Then click the apply button, and apply again.

---

### Post by thusspakeblixa on 2009-10-26
> **howefield said:**
> Try opening up a terminal, Applications > Accessories > Terminal and type

```
sudo apt-get update
```Followed by your password when prompted. After that, type

```
sudo apt-get install cairo-dock
```You can alternatively install with Synaptic Package Manager, System > Administration > Synaptic Package Manager. Search for cairo-dock, right click and select mark for installation. Then click the apply button, and apply again.
That did it, thanks!
Hopefully my screen is OK now...

---

### Post by thusspakeblixa on 2009-10-26
One more thing here-
How do I make Cairo Dock stay up permanently? I have to hover over it to bring it up at the moment.

---

### Post by thusspakeblixa on 2009-10-26
I figured that one out. Never mind.

---

### Post by howefield on 2009-10-26
> **thusspakeblixa said:**
> That did it, thanks!

That's good, once you are happy that you want to keep it, and have figured it all out, you might want to follow phidias advice about adding the repository, which will make sure you have the most up to date version.

---

