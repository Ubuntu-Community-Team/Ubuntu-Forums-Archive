---
title: "Site problem"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2011-01-22
I do not know if this is a problem with Ubuntu or something else. All i know is that if i do the same with Windows it works fine, though slowly loading, but i think that is the PC.

I installed Ubuntu 10.10 this morning, i have played about with ubuntu in the past, but decided i would give it a proper go along side XP on one of my computers. Everything seems to of gone fine with the install and the Updates (using Update Manager).

I have been surfing about the site i use most, and hit a problem. On [www.pogo.com]("http://www.pogo.com") something very odd happens. Basically when you have decided what game you wish to play, and click on it, a pop-up appears, and the game loads in there, no problem. Well that is what should happen. Trying it today (within Ubuntu) the pop-up appears, and it says game loading for a few minutes, then goes blank, then either closes the pop-up OR crashes Firefox. I have only managed to get one thing to load, and that was a little played fruit machine which is very basic.

A couple of times i have got a error screen from pogo explaining what could be causing this problem, BUT of cause these are Windows related. This has happened in Windows before (every few weeks it may happen, when Pogo is extremely busy i may get the error screen), and i think in the past it has been put down to either Java OR there is something within about:config in Firefox that can be changed to help the problem BUT Windows has never closed the pop-up before or crashed Firefox.
 
Any help would be great :)

---

### Post by Daveth on 2011-01-22
crashes with Opera 11 as well!

---

### Post by MadMonkey1966 on 2011-01-22
> **Daveth said:**
> crashes with Opera 11 as well!
Thanks for your reply, so this is known about then ? Is there anything i can do to make it work. I know there is something in about:config (in Firefox) that does help the problem, but i can not find the info on it any more, and of course i do not know if would work in ubuntu.

I dont want to have to keep XP just to play pogo.com games..... I just tried Chrome and got the error page again that starts off 
> [COLOR=#000000][FONT=Times New Roman][LEFT][COLOR=#555555][FONT=Arial]**The Applet Encountered a Programming Error (Cripes!)**

[COLOR=#70BF49]**Explanation:**[/COLOR]
This error usually indicates one of the following; the applet has been corrupted in your cache, there's a bug in your browser or there's a bug in our applet.
[/FONT][/COLOR][/LEFT][/FONT][/COLOR]

As it is doing it with all browsers, i am guessing there is something within the site (Java maybe) that is conflicting somewhere.

---

### Post by mick222 on 2011-01-22
It could  require sun java which is not installed by defaukt you have to enable the partner repositories. you can install them by opening synaptic going to settings repositories in the pop up go to the second tab and check the box next to canonical partners. Then remove open java and icedtea plugin and install sun java and the mozzilla plugin.

---

### Post by sammiev on 2011-01-22
Your problem is your java. You need [Sun's Java]("http://ubuntuforums.org/showthread.php?t=1634220&highlight=java") and when you install it and it ask you to accept the lic by clicking <Ok>, just tab over to it to accept and press enter. GL :)

---

### Post by MadMonkey1966 on 2011-01-22
> **mick222 said:**
> It could  require sun java which is not installed by defaukt you have to enable the partner repositories. you can install them by opening synaptic going to settings repositories in the pop up go to the second tab and check the box next to canonical partners. Then remove open java and icedtea plugin and install sun java and the mozzilla plugin.
Is that the same as what it told me to do here ?

[http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html](http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html)

I did that, BUT i never removed anything, it just said enable the second canonical partner one, then reload etc....

---

### Post by MadMonkey1966 on 2011-01-22
> **sammiev said:**
> Your problem is your java. You need [Sun's Java]("http://ubuntuforums.org/showthread.php?t=1634220&highlight=java") and when you install it and it ask you to accept the lic by clicking <Ok>, just tab over to it to accept and press enter. GL :)
ah, i will read through that.....

Many thanks :)

---

### Post by mick222 on 2011-01-22
yes it's the same i usualy use synapic as i find it easier but terminal can be faster to remove paste the following into terminal.```
sudo apt-get purge openjdk-6-jre openjdk-6-jre-headles
```
 Though i don't think it will solve the problem some game sites have problems with linux hope this isn't a showstopper for you.

---

### Post by MadMonkey1966 on 2011-01-22
> **sammiev said:**
> Your problem is your java. You need [Sun's Java]("http://ubuntuforums.org/showthread.php?t=1634220&highlight=java") and when you install it and it ask you to accept the lic by clicking <Ok>, just tab over to it to accept and press enter. GL :)
Thanks, that sorted it :)

One thing, at the bottom of that thread you sent me to is a place to go to check if your Java Plugin is up to date.

this one : [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

If i go there, it says there is a newer version BUT if i go into Tools-->Add-ons-->Find Updates it says the one i have is up to date lol 

So, if anyone comes across this thread, just follow this:

> The key package to use Java-based applet is indeed sun-java6-plugin .

If you have IcedTea installed, you can try and uninstall it: I noticed that sometimes the two packages conflict with each other.
So, just open a terminal and type in:

sudo apt-get remove icedtea*

After that, go to System > Administration > Synaptic Package Manager and, when Synaptic is open, click on Settings > Repositories ; chose the "Other software" tab and select the entry called "Canonical Partners" (Synaptic is the graphical package manager that provides a frontend to apt-get commands and can make things easier: you just search for a package, select it and install it). This whole procedure enables the repository where the Sun Java packages are kept.

Now just install sun-java6-plugin from Synaptic or command line and you should be set to go: just restart Firefox and you should be able to enjoy Java-based content.

You can check if the plugin is operational by opening Firefox and typing about: plugins in the address bar: Firefox will open a page with a breakdown of all active plugins.


OR goto this thread [http://ubuntuforums.org/showthread.php?t=1634220&highlight=java](http://ubuntuforums.org/showthread.php?t=1634220&highlight=java) 

Thanks again everyone

---

### Post by sammiev on 2011-01-22
> **MadMonkey1966 said:**
> Thanks, that sorted it :)

One thing, at the bottom of that thread you sent me to is a place to go to check if your Java Plugin is up to date.

this one : [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

If i go there, it says there is a newer version BUT if i go into Tools-->Add-ons-->Find Updates it says the one i have is up to date lol 

So, if anyone comes across this thread, just follow this:



OR goto this thread [http://ubuntuforums.org/showthread.php?t=1634220&highlight=java](http://ubuntuforums.org/showthread.php?t=1634220&highlight=java) 

Thanks again everyone

Great to see you have it going. GL :)

---

