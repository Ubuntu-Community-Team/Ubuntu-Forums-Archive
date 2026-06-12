---
title: "Installed new software, but were is it?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by fareforce on 2009-03-19
Complete newbie here, but I went to the Synaptic Package manager, and found 3 programs for my APC battery backup. They are:

apcupsd
apcupsd-cgi
apcupsd-doc

I marked all three for install, then clicked apply. It downloaded them, then installed them and said it was done. How do I get to the program to configure the battery backup? Also, how do I open the doc file?

Thanks in advance!

---

### Post by Therion on 2009-03-19
I don't know, but I did find the online Users Manual here:

[http://www.apcupsd.com/manual/manual.html#Building-and-Installing-apcupsd](http://www.apcupsd.com/manual/manual.html#Building-and-Installing-apcupsd)

---

### Post by fareforce on 2009-03-19
I guess I don't understand what the manual is talking about. I tried to use some of the configure commands, but terminal says it can't find it.

---

### Post by arapa on 2009-03-19
what is the output of this command?

```
whereis apcupsd

```

---

### Post by fareforce on 2009-03-19
> **arapa said:**
> what is the output of this command?

```
whereis apcupsd

```

apcupsd: /sbin/apcupsd /etc/apcupsd /usr/share/man/man8/apcupsd.8.gz

---

### Post by Paqman on 2009-03-19
> **fareforce said:**
> Complete newbie here, but I went to the Synaptic Package manager, and found 3 programs for my APC battery backup. They are:

apcupsd
apcupsd-cgi
apcupsd-doc

I marked all three for install, then clicked apply. It downloaded them, then installed them and said it was done. How do I get to the program to configure the battery backup? Also, how do I open the doc file?

Thanks in advance!

The first is a daemon. That's basically a service that runs in the background. The second looks like some kind of cgi thing (I don't know too much about cgi scripts, but it's not going to be a GUI you can run) To find out where the files installed by the doc package are, go to Synaptic and in the details of the package it should tell you what files it installs and where.

Or just check their [website]("http://www.apcupsd.org/").

---

### Post by ufuxlinux on 2009-03-19
I dont't know if you need to configure /etc/apcupsd/apcupsd.conf file, but if you have to, you need to read the "After installation" section of this manual carefully.

Probably it is like a service. You can use:

```
sudo /etc/init.d/apcupsd start
``` command to start it. I suggest you to install sysv-rc-conf to configure the services that starts at boot (or different run levels).

```
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf
```

Look for apcupsd. If it is there and have checks on some runlevels, then it is automatically configured to start at boot. Then you don't need to change it. (be careful when you use this program, do not change anything you don't know).

Again, manual is long but explanatory.

---

### Post by yeats on 2009-03-19
This looks pretty involved for a beginner (though it looks like a great program with really useful functionality).  If I were you I might start simpler than this, which looks like it's going to involve a lot of command line work and knowledge of Linux configuration files...

Just my opinion :-).

---

### Post by fareforce on 2009-03-19
> **chrissharp123 said:**
> This looks pretty involved for a beginner (though it looks like a great program with really useful functionality).  If I were you I might start simpler than this, which looks like it's going to involve a lot of command line work and knowledge of Linux configuration files...

Just my opinion :-).


Is there a different package to control APC battery backups that is easier? This is for a server, but after reading up on ubuntu, I decided to load the desktop version, and then load the server stuff. The server is only going to hold photos for my photography studio, and I will occasionally need to burn DVD's, and do minor photo edits on it. So I really wanted the graphical GUI. 

I will play with it some more tomorrow when I get to work.

---

### Post by yeats on 2009-03-20
> 
Is there a different package to control APC battery backups that is easier? 

I haven't used this sort of thing before, so I don't know.  I'm just suggesting that you start using the command line for less complex programs in general, then move towards this program you want.  If this is something you need now, then perhaps people here can walk you through the steps...

> 
This is for a server, but after reading up on ubuntu, I decided to load the desktop version, and then load the server stuff. The server is only going to hold photos for my photography studio, and I will occasionally need to burn DVD's, and do minor photo edits on it. So I really wanted the graphical GUI.

I will play with it some more tomorrow when I get to work. 

The GUI is a good idea for starters, especially if you've got the resources for it.  I would suggest reading up on some introductory Linux skills.  This might be a good guide to orient yourself:

[http://www.ubuntupocketguide.com/]("http://www.ubuntupocketguide.com/")

There are others worth reading as well.  One that focuses on the command line exclusively is:

[http://books.google.com/books?id=wOGUuoHUyAEC]("http://books.google.com/books?id=wOGUuoHUyAEC")

---

### Post by fareforce on 2009-03-20
> **chrissharp123 said:**
> 
The GUI is a good idea for starters, especially if you've got the resources for it.  I would suggest reading up on some introductory Linux skills.  This might be a good guide to orient yourself:


Resources aren't a problem. There are only two computers that connect to the server. But the server itself (Dell Power Edge T300) has 2GB RAM, 1.5TB HDD (Raid 5), Core2 Duo 2 ghz. It should handle file storage fine.

I will try the command line stuff and see if I can get it working.

---

