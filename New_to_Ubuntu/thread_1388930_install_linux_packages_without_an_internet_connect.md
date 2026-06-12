---
title: "install linux packages without an internet connection, is it possible?"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by computerguts on 2010-01-23
Hi, I am realtivy new to linux, and I was wondering is their any way to download and transfer software packages to a flash drive to install them to a ubuntu linux 9.10 computer without an internet connection. 

Thanks

---

### Post by rogue_0111 on 2010-01-23
I don't believe so!

---

### Post by Yvan300 on 2010-01-23
Yeah through deb packages which are like the equivalent of .exe files. Google the packages you want and you may or may not find them. But this method of installation is not recommended for security reasons.

---

### Post by warfacegod on 2010-01-23
Are you talking about updates or just any software. You can install packages from the install disc. Synaptic has the option of downloading packages only. As for normal apps any compressed application file can be put onto a jump drive and be installed later.

---

### Post by Bartender on 2010-01-23
I've been experimenting with that recently.  Well, not off-line, but dial-up.  Completely off-line is a bigger challenge.  Take a read thru the two threads linked below.  Updating via thumb drive isn't discussed until several pages into the wvdial thread.

In a nutshell, I'm trying to maintain two dial-up desktop PC's using our laptop and a thumb drive.  One desktop PC is running 9.10, the other's running 9.04.  Broadband is available at the library, which is where I take the laptop.

The process that I try to explain in both of those threads relies on being able to get online with the two desktop PC's in order to have Synaptic "Reload" the package lists.  If you can't get online at all, it gets more complicated.  

You'll see some references to truly off-line PC's scattered between the two threads, and some of the links that are in the threads, but I haven't tried to figure it out.

So, are you completely off-line or at least able to do some work via dial-up?

---

### Post by egalvan on 2010-01-23
three project that may or may not be useful...
the first seems to be closer to what you want...

[http://apt-proxy.sourceforge.net/](http://apt-proxy.sourceforge.net/)

[http://packages.debian.org/lenny/apt-cacher](http://packages.debian.org/lenny/apt-cacher)

[http://sourceforge.net/projects/debproxy/](http://sourceforge.net/projects/debproxy/)

---

### Post by sandyd on 2010-01-23
[-> aptoncd <-]("https://help.ubuntu.com/community/AptGet/Offline/Repository")
its the last post on [http://ubuntuforums.org/showthread.php?p=6159111](http://ubuntuforums.org/showthread.php?p=6159111) btw

---

### Post by computerguts on 2010-01-23
I have a computer with a high speed internet connection that is operating windows vista, but the computer that I am operating ubuntu which is a desktop does not have an internet connection at all

---

### Post by Bartender on 2010-01-23
> **computerguts said:**
> I have a computer with a high speed internet connection that is operating windows vista, but the computer that I am operating ubuntu which is a desktop does not have an internet connection at all

I don't get it.  Where's the Ubuntu desktop in relation to the connected Vista PC?  Is it in the same house, and you just can't figure out how to get online with it?  Or is the Ubuntu PC someplace far away?  Without understanding more about your situation, I'd say the easiest thing would be to set up the Ubuntu desktop next to the vista rig! :)

I just posted a PDS for Karmic in the Dial-up Redux thread.  Pretty sure all you'd have to do is create a blank PDS as described previously, paste the entire list of packages into a PDS, then go get all the packages with a Linux PC that has wget installed, or a Windows PC with - um - let me check...OK, [here's]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript") the link that describes what to do in Windows.  I've never tried it in Windows, just Linux, but using Firefox and DownThemAll doesn't sound too complicated.  If you do this in Windows don't forget to remove the first line from the PDS, the one that says, [COLOR="Blue"]#!/bin/sh[/COLOR]

---

### Post by warfacegod on 2010-01-23
> **computerguts said:**
> I have a computer with a high speed internet connection that is operating windows vista, but the computer that I am operating ubuntu which is a desktop does not have an internet connection at all

Is this because of a hardware issue or simply because it's not connected to the router? And you still haven't answered the question as to whether you want update packages or normal application packages.

---

### Post by cascade9 on 2010-01-24
> **computerguts said:**
> Hi, I am realtivy new to linux, and I was wondering is their any way to download and transfer software packages to a flash drive to install them to a ubuntu linux 9.10 computer without an internet connection. 

Thanks

It can be done..but IMO its easier to use debian for this. Its much more offline friendly than ubuntu is.

---

### Post by bobin on 2010-01-24
try out the keryx project (google it). You can download packages on the vista and transfer to the ubuntu using a thumb

---

### Post by YosefKaro on 2010-01-24
Yes, it is very possible and Nigel Babu goes into great lengths on his blog explaining exactly how to do this.  Check it out [here.]("http://justanothertriager.wordpress.com/")

-Yos

---

### Post by Bartender on 2010-01-24
Mr. Babu's blog merely parrots the instructions in the link I provided from the Ubuntu Community Docs.  

And his description of Keryx makes me wonder if he's actually tried to use it?  The crashsystems tutorial has a few serious holes in it, like neglecting to explain some terminal-based work that needs to be done.

I've spent several hours figuring out how to use Keryx.  After invoking the "force" command (described in the tutorial) apt-get locked up and refused to do anything until it was allowed to connect to the internet and figure out what was wrong.

---

### Post by computerguts on 2010-01-24
I am trying to install full applications, the computer that has ubuntu does not have an internet connection and is far away from the router that is close to the vista pc

---

### Post by warfacegod on 2010-01-24
> **computerguts said:**
> I am trying to install full applications, the computer that has ubuntu does not have an internet connection and is far away from the router that is close to the vista pc

Using a flash drive is no problem then. Find an app with a .deb file. They behave basically like Windows .exe files. Tar files are good too, if a little more difficult to install. Here's Softpedia's Linux site. There are all kinds of downloadable packages there.

[http://linux.softpedia.com/]("http://linux.softpedia.com/")

If your router has wireless capability, I would consider getting a wireless card for your Ubuntu machine. If it doesn't, you can ask your ISP for one that does.

---

### Post by Bartender on 2010-01-24
Any possibility you might be interested in installing Linux to the vista PC as a dual-boot?  That would make things much easier.  You could generate Package Download Scripts with all the packages you needed for the offline PC.  You'd want to install the same Linux distro to the vista PC as the offline PC.

It's often not as easy as warface describes.  Just about every package you want to install relies on other packages.  For instance, Handbrake is available bundled up in a .deb package ready to go.  But it requires a smattering of dependencies (well, at least one that I know of) in order to get it to work.

If the softpedia website offers applications with all dependencies as a single download, that would be great and I'd gladly admit to being wrong! :)

---

### Post by warfacegod on 2010-01-24
> **Bartender said:**
> Any possibility you might be interested in installing Linux to the vista PC as a dual-boot?  That would make things much easier.  You could generate Package Download Scripts with all the packages you needed for the offline PC.  You'd want to install the same Linux distro to the vista PC as the offline PC.

It's often not as easy as warface describes.  Just about every package you want to install relies on other packages.  For instance, Handbrake is available bundled up in a .deb package ready to go.  But it requires a smattering of dependencies (well, at least one that I know of) in order to get it to work.

If the softpedia website offers applications with all dependencies as a single download, that would be great and I'd gladly admit to being wrong! :)

When my wireless card was shaky at best, I would install .debs all the time with out the internet connected and never had a problem with anything needing dependencies.

---

### Post by j002 on 2010-01-24
Well I have Ubuntu and I have never had an internet connection, am I doing something wrong ?

Google "ubuntu packagename.deb" and you will find the Ubuntu repository.

Make sure you get the files and packages that fit YOUR distribution (e.g. Ubuntu 9.04), otherwise you can completely wreck your system (well I have anyway).
Don't use .deb files for another distro (e.g. Debian) - they won't work.

Of course, you need to find out what packages you need, which will require a bit of searcing and you need to get all the dependencies you don't have, that's why it's easier on the internet.

After that you just double click on the .deb file in Nautilus (the window manager) in any directory and it will install itself.

Sometimes you can't get .deb files, only source or binary files.
Don't bother with tar - it's too complicated.
Just double click on the icon in Nautilus to decompact the file.
If you need root permission to do that, open a terminal and type :

sudo bash

then :

nautilus --browser.

and then double click on the icon in the new window.

(Does anyone else know how to become root user on Nautilus ?  I can't find any way).

---

### Post by qyot27 on 2010-01-24
> **j002 said:**
> (Does anyone else know how to become root user on Nautilus ?  I can't find any way).
sudo nautilus /location/is/optional

---

### Post by warfacegod on 2010-01-25
> **qyot27 said:**
> sudo nautilus /location/is/optional


The best/safest way is:
```
gksudo nautilus
```

Using sudo has the potential to corrupt the filesystem, from what I understand.

---

### Post by egalvan on 2010-01-25
The link that ***Bartender *** gave  (msg #9) seems to have the solution.
How about ***Carlee's*** link (msg #7)?
Has the OP checked them?


Another "solution" is to obtain the repositories.
It's possible to download the repo's...
there was a "how-to" on these forums in 2008 on this.

And here is one example being sold by *osdisc.com*
[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html)

[i]""Product Description
The Complete Ubuntu Software Repository, as of Nov 14, 2009. Includes the entire main, restricted, multiverse, and universe repositories -- over 28GB of software.

Compatible with any Ubuntu 9.10 based distribution, including Ubuntu 9.10, Kubuntu 9.10, Xubuntu 9.10, Edubuntu 9.10, Ubuntu 9.10 Server, Ubuntu Studio 9.10, Mythbuntu 9.10, and Ultimate Edition 2.4.

This DVD set allows you to install thousands of applications directly from the DVDs using Add/Remove Applications.

[B][COLOR="Red"]This is perfect for those with slower internet connections, or no connection at all.
[/COLOR][/B]
Complete step-by-step setup instructions included on DVD #1.

Note: This DVD set will not install Ubuntu on your computer. An install CD or DVD is required if Ubuntu is not already installed.""[/I]

---

### Post by Bartender on 2010-01-25
The last we heard from the OP was back at post #15, yet the thread is marked as 'Solved'.
computerguts, what did you end up doing?  If you found a good solution please share.  Offline/dial-up has been a real sticky problem for many folks!
The Package Download Script process has worked pretty well for me but I've got dial-up at home, a Linux laptop, and broadband is available.  Except on Sundays and Mondays :)
Take away those three things and I'd be lost...

---

### Post by qyot27 on 2010-01-26
> **warfacegod said:**
> The best/safest way is:
```
gksudo nautilus
```

Using sudo has the potential to corrupt the filesystem, from what I understand.
The difference between sudo and gksudo is the fact that gksudo prevents text spoofing attacks by locking the screen and sudo doesn't (so it's rather an issue of security against hacking than stability).  Either one has the same disadvantage - being that you can royally muck up your system if you go around deleting stuff randomly while logged in as root.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

While it talks about the issues with profiles changing with sudo, I've personally never experienced that, or the deficiency of profile was only experienced in the root-ed app, and remained the same otherwise.  Overall, using sudo is fine, except those rare cases where it isn't.  And of course, gksudo is the one needed if you want to avoid using the Terminal altogether.

---

