---
title: "installing applications"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by mhilinski on 2009-03-14
I would like to know how do i install appications that ihave downloaded?


I am new to ubuntu so please forgive me 


thanks

mch

---

### Post by overdrank on 2009-03-15
Hi and welcome, You may look [[COLOR="Blue"]here[/COLOR]]("http://www.psychocats.net/ubuntu/installingsoftware")

Moved and bumped :)

---

### Post by got_milk? on 2009-03-15
> **overdrank said:**
> Hi and welcome, You may look [[COLOR="Blue"]here[/COLOR]]("http://www.psychocats.net/ubuntu/installingsoftware")

Moved and bumped :)

While this is a great way of installing applications I much prefer the command line way.

You can use:

```
sudo apt-get install [name]
```

(where [name] is replaced with the package you wish to install)

and to uninstall:

```
sudo apt-get remove [name]
```

(where [name] is replaced with the package you wish to remove)

So, for example, if I wanted to install Adobe Flash Player:

```
sudo apt-get install flashplayer-nonfree
```

and if I wanted to remove it:

```
sudo apt-get remove flashplayer-nonfree
```

HTH.

---

### Post by sgosnell on 2009-03-16
The only trouble with that is that you have to know the **exact** name of the package you want, and it's not always obvious.  Using Synaptic or Add/Remove is by far the easiest way for beginners to install things.  You get to see a description of the package before you commit to anything, and a typo won't hurt anything.

---

### Post by ramjet_1953 on 2009-03-16
For a new user, the command line can be daunting.

My advice is navigate to [COLOR="Blue"]Applictions>Add/Remove[/COLOR].

When the window opens, you will notice at the top centre a drop-down menu, called [COLOR="Blue"]Show[/COLOR].

Click on the drop-down and select [COLOR="Blue"]All Available Applications[/COLOR].

Once this is done, you will have bucket loads of available applications that can be installed with just a couple of clicks.

Once you have become comfortable with this, you can then start to use the full=blown Synaptic Package Manager ([COLOR="Blue"]System>Administration>Synaptic Package Manager.
[/COLOR])
I do not advise you to attempt to compile packages from source yourself at this stage, as it can be quite complex when you run into dependency issues. It also requires you to have a knowledge of the command line.

Regards,
Roger :o

---

### Post by mvalviar on 2009-03-16
If it is something you downloaded and and its a *.deb file simply double-click it. If its an installation file you have to give it execute permission if it doesn't have it.

```
chmod a+x filename
```
then run it with
```
./filename
```
assuming you are in the directory where your file resides.

---

