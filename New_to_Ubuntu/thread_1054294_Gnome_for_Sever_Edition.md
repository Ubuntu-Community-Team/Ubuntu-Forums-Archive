---
title: "Gnome for Sever Edition?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by dphirschler on 2009-01-29
I want to have a Gnome desktop for my server (Ubuntu Server 8.10).  When I first tried it, whenever I went into Gnome, my network connections were all screwed up.  I don't mind installing the whole desktop (complete with Open Office), I just don't want the network stuff to get screwed up.

So I guess what I am looking for is:

a) What is the command line to set up Gnome for my server.  I want it installed, but I want to boot up in command line.  I just want to be able to enter the gui when I want to (like if I want to use Gedit or something).

b) Why were the network settings all screwed up under Gnome?  Why were they altered at all?  

c) How do you exit Gnome and go back to the command line without rebooting?


Darryl

---

### Post by slinkey1981 on 2009-01-29
1. This installs most of the Ubuntu goodies. I don't know how much will be skipped by having Server pre-installed....

```
sudo apt-get install ubuntu-desktop
```

After install, goto System > Administration > Services, and uncheck "Graphical login manager.

2. Don't know, shouldn't have been.

3. I think the command is....
```

sudo /etc/init.d/gdm stop
```


This does leave it to where you will be entering your login info two times. Once to boot into the command line, and once to boot into gnome.

And the command to start gnome is 
```

sudo /etc/init.d/gdm start
```

---

### Post by BDNiner on 2009-01-29
You can also press Ctrl+Alt+F1 though F7. F1 through F6 are terminal windows and F7 is where your desktop GUI is loaded. That way you can stay logged into the gnome desktop and log into a completely different session on F1 through F6. you can also start another gnome session on any of them.

---

### Post by dphirschler on 2009-01-29
Sounds good.  Now how about if I want to save time by installing ubuntu-desktop from the CD.  Possible?


Darryl

---

### Post by slinkey1981 on 2009-01-29
> **dphirschler said:**
> Sounds good.  Now how about if I want to save time by installing ubuntu-desktop from the CD.  Possible?


Darryl

Oh wow, I was just about to run you through how to switch it to do that under gnome... But you don't have gnome yet...

You can edit your 

```
/etc/apt/sources.list 
```

and comment (#) out all of the lines, while uncommenting the cdrom....

make this
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/
```

look like this
```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/
```

And then running through the process....
```

sudo apt-get update
```

Sorry, your "deb cdrom" may or may not say amd64, but it SHOULD be the first source listed in sources.list

---

### Post by egalvan on 2009-01-29
> **dphirschler said:**
> Sounds good.  Now how about if I want to save time by installing ubuntu-desktop from the CD.  Possible?
Darryl


oops, never mind..
you don't have the GUI yet. so this will not work.
yet

---

