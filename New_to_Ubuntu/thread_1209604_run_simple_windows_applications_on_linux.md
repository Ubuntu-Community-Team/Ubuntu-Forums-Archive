---
title: "run simple windows applications on linux"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by vagelism on 2009-07-10
Hello to all I want to run some simple windows applications like dictionaries etc to a EEE pc with UBUNTU on it. 
Is there any kind of emulator?
Thank you all for your time!

---

### Post by Tibuda on 2009-07-10
[Wine]("apt:wine"). It's available from ubuntu package manager (Applications > Add/remove if you are using the default installation).

You should browse the [Wine Application Databse]("http://appdb.winehq.org/") to see other user experiences about the applications you want to run.

---

### Post by SaaTeeVaaGreen on 2009-07-10
the best way to do this is probably through wine. install it by typing ```
sudo apt-get install wine
``` into a terminal

---

### Post by LewRockwell on 2009-07-10
System > Administration > Synaptic Package Manager

search term: dictionary

perhaps?

.

---

### Post by clonne4crw on 2009-07-10
> **danielrmt said:**
> [Wine]("apt:wine"). It's available from ubuntu package manager (Applications > Add/remove if you are using the default installation).

You should browse the [Wine Application Databse]("http://appdb.winehq.org/") to see other user experiences about the applications you want to run.

+1. It can do more than simple applications. I've been able to get DirectX games working in it. Wine interperets and translates Windows API calls into things that Linux can work with. Works surprisingly well.

---

### Post by vagelism on 2009-07-10
Ok wine is ready...but when I run an application I can not even click on it..seem it is running but I can not interact with the application...
Do I do something wrong?

---

### Post by earthpigg on 2009-07-10
did you look for your application on the Wine Application Database, linked above?

that will have specific information on the specific program you are trying to run.

---

### Post by vagelism on 2009-07-10
no I will do it now...but even iexplorer is not working
is there any problem with compiz?

---

### Post by earthpigg on 2009-07-10
> **vagelism said:**
> no I will do it now...but even _**iexplorer**_ is not working

????

you mean firefox, right? :D

even if you dont, information on internet explorer can be found on the Wine Application Database:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4195&iTestingId=42329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4195&iTestingId=42329)

---

### Post by vagelism on 2009-07-10
No I mean that it has preinstalled the iexplorer, I suppose it has to work. But not.... I manage to open a really simple application... magenta polylexicon...and after 3 seconds the application disappears of the desktop!!

---

### Post by jerome1232 on 2009-07-10
> **danielrmt said:**
> 
You should browse the [Wine Application Databse]("http://appdb.winehq.org/") to see other user experiences about the applications you want to run.

You really do need to look up the program in their database, it will tell you if the program works and if there are any tricks/adjustments you have to make to get the program running.

It's not really a matter of 'simple' program vs 'complicated' program. Internet Explorer for example has always been a pain to get working (maybe that's changed) while the game World of Warcraft works flawlessly.

---

### Post by zetman on 2009-07-10
Wine is great, but it's not perfect.  If you just want it for applets and widgets, and what not, you're probably better of finding a native solution.  Spend some time searching the repositories with the Synaptic Package Manager.  (like LewRockwell suggested)  If you're only used to Windows, this is a whole new way of thinking about software installation.  It took me some time to get used to, but now when I'm looking for something new, the first thing I do is check the repositories.  You can kindda think of it like a search engine for software.

---

### Post by Mark Phelps on 2009-07-10
+1 BIG TIME on the checking the Wine App Database!

The op's program is not even listed in the supported apps, so it's very likely that it will NOT work.

Even when we provide folks with a link, they can't spend 30 seconds clicking the link and entering the name of their app -- to see if it's supported in Wine!

---

### Post by Mornedhel on 2009-07-10
> **Mark Phelps said:**
> +1 BIG TIME on the checking the Wine App Database!

The op's program is not even listed in the supported apps, so it's very likely that it will NOT work.

You never know. Unlisted applications have never been tested ; if they've been written well enough, they have a chance of working anyway.

Of course, the correct thing to do is to write an entry if there isn't one, whether you rate it Garbage or Platinum.

---

