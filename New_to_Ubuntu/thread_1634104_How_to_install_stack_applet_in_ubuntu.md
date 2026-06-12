---
title: "How to install stack applet in ubuntu?"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by karthick87 on 2010-11-30
I am using ubuntu 10.04.How to install stack applet?
[IMG]http://i.imgur.com/pzFTN.png[/IMG]

---

### Post by kerry_s on 2010-11-30
what? you need to be more specific.

---

### Post by karthick87 on 2010-11-30
How to install **StackApplet**?

---

### Post by kerry_s on 2010-11-30
is this it->
[http://stackapps.com/questions/83/stackapplet-stackoverflow-meets-the-gnome-desktop-v1-4-beta-1-available-for-te](http://stackapps.com/questions/83/stackapplet-stackoverflow-meets-the-gnome-desktop-v1-4-beta-1-available-for-te)


if so, just download the deb & double click on it.
[http://launchpad.net/stackapplet/1.4/1.4/+download/stackapplet_1.4.0_all.deb](http://launchpad.net/stackapplet/1.4/1.4/+download/stackapplet_1.4.0_all.deb)

---

### Post by karthick87 on 2010-11-30
I have installed stack applet from your link.Now i can find stackapplet under **Applications>>Accessories>>StackApplet**

But when i click StackApplet nothing happens.It's not opening.

---

### Post by kerry_s on 2010-11-30
> **karthick87 said:**
> I have installed stack applet from your link.Now i can find stackapplet under **Applications>>Accessories>>StackApplet**

But when i click StackApplet nothing happens.It's not opening.

if it's an applet, don't you need to right click the panel to add it ?
my guess would be the 1 in menus is for settings.

---

### Post by karthick87 on 2010-12-01
Now the applet is appeared in my panel.But everytime i have to start it manually by clicking the icon under** Applications>>Accessories>>StackApplet** Is there a way to start it automatically?But the applet is not found in Add to Panel list.

---

### Post by George Edison on 2011-11-16
As the author of the application, I will attempt to answer your question.

StackApplet can currently be installed using three different methods:

[LIST=1]
[*]**Directly through the archive:** simply open a terminal and run the following command:
```
sudo apt-get install stackapplet
```
Keep in mind that the version in the archive is quite outdated and is missing a lot of the newer features.


[*]**Use the StackApplet PPA:** StackApplet has a daily build recipe over on Launchpad that builds it from source each day and places the resulting builds in its PPA. You can add the PPA using the following command:
```
sudo apt-add-repository ppa:stackapplet-dev/stackapplet
```
This version is much more up to date.


[*]**Download the source and install it:** if you head on over to StackApplet's Launchpad page, you can grab the latest source archive and extract that to a folder. Then run:
```
sudo python setup.py install
```
...to install the application.
[/LIST]

---

