---
title: "Nubie Q: Why have Package installer?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by smileyguy on 2009-04-23
OK - I've just finished my first ever (successful) Linux installation of Ubunto 8.1 (then saw 9.04 released the next day!!!).

I'm fumbling around learning things and want t know why I need to install packages with the **package installer** (this is how I installed Open Office 3.1). Why can't I just download as an executable file and run?

Is this some sort of Linux philosophy or have I missed something?

I am getting around to reading the newbie documentation but like these forums:)

---

### Post by yeats on 2009-04-23
Ubuntu software is packaged in repositories, which only contain versions of the software that won't break your system.  You may, of course, go out on the web and install programs from source code or with binaries, but the repositories are almost always sufficient (depending on your needs).  I always recommend to new users (having recently been one :-) ) that using (or at least starting with) the repositories is the smartest way to go.

Also - do a few keyword searches for programs you might be interested in (music, games, utilities, whatever) - I think you'll be impressed with the massive amount of software that is literally a click away.

---

### Post by ugriffin on 2009-04-23
For a Ubuntu equivalent of Windows Installer .exe, always search for .deb files.

---

### Post by thesuperjman on 2009-04-23
soemtimes i download stuff from the add/remove under the appliations menu.

---

### Post by rhcm123 on 2009-04-23
there is no real such thing as an "executable" on linux. (technically there is, but not like a .exe file). On linux, programs are compiled into packages, which are diverse programs (they have directories all over the system), that rely on other programs, called dependancies.

Dependancies are like the .NET framework in windows, only in linux, the package manager sees that a package depends on another, and automatically installs it.

Yes, this is a linux philosophy, and it's been built that way since the begining of time. Technically windows is package-based as well, but it doesn't use a system wide recorder/manager (unless you count the registry).

It's complicated, and linux is very different than windows. You can't just grab a working-out-of-the-box program - this is actually very good virus protection!

Oh, and one last protip: I knew a guy who once tried to remove apt cause he got tired of it and just wanted to install by dpkg (manual installs). he ended up breaking his machine. Keep apt around - it is very helpful of fast software grabs (for instance, grab ubuntu-restricted extras and get 90% of the packages you'll ever need)

Wikipedia has some help for you:
[http://en.wikipedia.org/wiki/Software_package_(installation](http://en.wikipedia.org/wiki/Software_package_(installation))
[http://en.wikipedia.org/wiki/Dependency_(computer_science](http://en.wikipedia.org/wiki/Dependency_(computer_science))
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)
[http://en.wikipedia.org/wiki/Package_management_system](http://en.wikipedia.org/wiki/Package_management_system)

---

### Post by sgosnell on 2009-04-23
If you go out and find a .exe file and install it in Windows, what happens when you decide you don't need it?  You end up with lots of crap in your registry, clogging things up, and the only way to get rid of it is to do a complete reinstall of Windows.  With Synaptic, you can install anything, and if you decide to remove it, you tell Synaptic to delete it and it's gone.  You have the choice of keeping the config files if you want, but if you tell it to remove the app, then it's gone, completely.  A .deb file is very much like a setup.exe file in Windows, and you can certainly install one without using the package manager, but it's not efficient, and it's not the best way.  Sometimes you have to get something outside the repositories, but you should still use the package management tools to install it, so they can track it and remove it if necessary.  You're used to the Windows way, but that's not necessarily the best way.  Different is not always bad.

---

### Post by snova on 2009-04-23
It is simply the way we usually install things.

Windows's MSI files are actually similar in several ways.

As to downloading and running, it's not much different, except now it's download, right click, and select "Install" or whatever the option is.

---

### Post by Hospadar on 2009-04-23
There are so many reasons, for one, convenience, you don't need to hunt all around for different packages which may or may not need to be built with dependancies you may or may not have.

In the windows world, developers release pre-built installers, in the linux world, developers release source code that distributions compile for you and put into their package management system.  This gives you some level of assurance that the software will work (at least as well as it should given any bugs on the developer's side) and will have all the dependencies.  Also this means that the software will all get regularly updated.

The convenience factor is huge, but so is security, all of your software is coming from the same trusted source.  There's almost no chance that someone's website has been jacked and is now serving you bad software, because it's all coming from ubuntu servers and mirrors, which are the only machines which have the private encryption keys matching the public keys distributed on livecds.

It's just a better way to get software, even if it's totally different from what you may be used to.

---

### Post by smileyguy on 2009-04-23
That's awesome - thanks for all the answers guys! Starting to make sense:)

---

### Post by smileyguy on 2009-04-23
> **chrissharp123 said:**
> Ubuntu software is packaged in repositories, which only contain versions of the software that won't break your system.  You may, of course, go out on the web and install programs from source code or with binaries, but the repositories are almost always sufficient (depending on your needs).  I always recommend to new users (having recently been one :-) ) that using (or at least starting with) the repositories is the smartest way to go.

Also - do a few keyword searches for programs you might be interested in (music, games, utilities, whatever) - I think you'll be impressed with the massive amount of software that is literally a click away.
OK this may sound dumb - but I'm completely new to this! What is a **repository**? 

Simple question but I get the felling I'm gonna get the best answers outta these forums.

---

### Post by smileyguy on 2009-04-23
> **sgosnell said:**
> If you go out and find a .exe file and install it in Windows, what happens when you decide you don't need it?  You end up with lots of crap in your registry, clogging things up, and the only way to get rid of it is to do a complete reinstall of Windows.  With Synaptic, you can install anything, and if you decide to remove it, you tell Synaptic to delete it and it's gone.  You have the choice of keeping the config files if you want, but if you tell it to remove the app, then it's gone, completely.  A .deb file is very much like a setup.exe file in Windows, and you can certainly install one without using the package manager, but it's not efficient, and it's not the best way.  Sometimes you have to get something outside the repositories, but you should still use the package management tools to install it, so they can track it and remove it if necessary.  You're used to the Windows way, but that's not necessarily the best way.  Different is not always bad.
GDebi seems to be the default Package Manager for my installation but Synaptics seems to be installed. Is one better than the other?

---

### Post by Paqman on 2009-04-23
> **smileyguy said:**
> OK this may sound dumb - but I'm completely new to this! What is a **repository**? 


It's an online library of software.

Go to System > Admin > Software Sources and you'll see what repos you're currently connecting to.

There are a lot of awesome things about repos:
[LIST]
[*]Whenever the repo gets an updated version of a package, your system will update automatically. So every single app on your machine is always up to date. That's really important for security, and something Windows can't do
[*]All the software in the repos is tested, and 100% spyware and adware free
[*]Because of the way your package manager and the repos work, you only download the packages you don't already have. That means Linux apps tend to be smaller and faster downloads than Windows apps
[/LIST]

---

### Post by gfe on 2009-04-24
> **smileyguy said:**
> Why can't I just download as an executable file and run?
Something that hasn't been mentioned is that there are numerous variations (called distributions) of Linux. I use Ubuntu Linux on my main computer at home, but I use another variation, Puppy Linux on my 10-year-old decrepit laptop with only 192K RAM.

But without getting too technical, if I were to download a package for Ubuntu, it wouldn't work in my Puppy machine and vice versa because of differences in the way the two flavors of Linux are set up. One advantage of a repository is that it's made for a specific version of Linux. I can go to a Puppy repository to get software for my creaky laptop, or I can go to a Jaunty repository for my main computer. Everything "just works," usually.

---

### Post by Alterax on 2009-04-24
> **smileyguy said:**
> OK this may sound dumb - but I'm completely new to this! What is a **repository**? 

Simple question but I get the felling I'm gonna get the best answers outta these forums.

Repositories (commonly called "repos") are the equivalent of a store.  The difference is that it's full of software that is free, and in the case of the Ubuntu repositories, has usually had modifications made to help make sure it works correctly on your system.

They've got their advantages over randomly downloading .exe or .msi files on Windows.  For starters, with the Windows programs you find and download on the 'net, you just really don't know where it's been.  The file could be something totally different, could be infected, could be for a different version of Windows, and it may have everything in it that you need to run it--and then again it may not.

Repositories take a lot of guesswork out of the equation.  The repositories usually have different builds--say, for your pentium-class processor or my powerpc one.  We don't have to tell it what kind of processor we have; the package manager looks for itself at your system, then reaches out to the repository and picks the right one.  The packages also have instructions built into them, which tells the computer if it needs anything else like shared libraries (kind of like DLLs) or other programs to run--and it gets those too, usually without you having to tell it to.  And if you decide you don't want that program anymore, it has all the instructions to wipe out that program completely and cleanly, without sacrificing your data.

Then, what about if you want a program that does something--let's say a virus scanner--but you don't know what it's called?  Just search for Virus Scanner, and it tells you what your options are and which ones are the most popular.

It's weird at first, but bear with it--it's incredibly efficient.  Give it a month or so and you may find yourself wondering how you've gone so long without it!

---

### Post by Peter09 on 2009-04-24
In case you dont know, go to 
System->Administration->Synaptic Package Manager

to see the full contents of your repositories.

---

### Post by JoshuaRL on 2009-04-24
> **smileyguy said:**
> GDebi seems to be the default Package Manager for my installation but Synaptics seems to be installed. Is one better than the other?

GDebi is the manager to install .deb files on your computer.  As has been stated, those are the equivalent of MSI/EXE installer files.

Synaptics is the true package manager.  It searches both through the repositories that your computer is set to look to, and through the packages installed on your system.  It will let you manager all of that however you want, has search and filter capabilities, and even gives you helpful package information.  Really one of the greatest applications Linux has.

---

### Post by smileyguy on 2009-04-24
Thanks again - all wonderful answers. And yes I am already wondering why I've been without Linux for so long (although tried yonks ago but kept failing at install point - these more recent machines I've acquired (P4s seem to be fine with it).

---

### Post by smileyguy on 2009-04-24
So under **Software Sources** is where my repositories are it seems?

And looks like I can add more under the **Third Party Software** Tab?

Again - I know this may seem really dumb: Is the **Ubuntu Software** tab pointing somewhere on the Ubuntu website? 

AND - what's the difference between **gDebi** and **Synaptics? **Just 2 apps that do the same thing?

---

### Post by Sef on 2009-04-24
> OK this may sound dumb - but I'm completely new to this!

The only dumb question is one that is unasked.

---

### Post by El Zoido on 2009-04-24
JoshuaRL answered the GDebi-Synaptics question quite nicely a couple of posts earlier, I think ;)

The third party tab will indeed allow you to activate more repositories you can use for searching for software.

But you can manually add more, if necessary:
Say, e.g., you are using some program that is not offered in the newest version in the original repositories.
Sometimes the developer is providing a repository of his own that will contain the newest version (maybe containing additional features, bugfixes, etc.).
You could then add this repository to your sources.list and use it.
An example for this would be Wine or Virtualbox.

And then there are projects like Medibuntu that have their own repositories, too.

---

### Post by The Cog on 2009-04-24
> **smileyguy said:**
> So under **Software Sources** is where my repositories are it seems?
Yes. This tells synaptic where to look.
> And looks like I can add more under the **Third Party Software** Tab?
Yes. I sometimes add wine, virtualbox and wicd in there - these software makers make the effort to provide their latest and greatest online in a compatible format.
> Again - I know this may seem really dumb: Is the **Ubuntu Software** tab pointing somewhere on the Ubuntu website? 
Or one of its many mirrors. You have a choice of locations somewhere there.
> AND - what's the difference between **gDebi** and **Synaptics? **Just 2 apps that do the same thing?
Synaptics uses the online repositories. gDebi is (I think) a local installer utility for when you download a .deb file yourself, drop it on your desktop and double-click it to install it. Sometimes necessary when you want sw that is later then the Ununru repos, or is not there for some reason.

---

### Post by smileyguy on 2009-04-24
Thanks - this is one of the quickest and most useful forums i've ever used!

Great for newbies!

---

### Post by nandemonai on 2009-04-24
> **smileyguy said:**
> Thanks - this is one of the quickest and most useful forums i've ever used!

Great for newbies!

On a related issue, I notice you're in Sydney. Who is your Internet provider if you don't mind me asking? They may offer an unmetered mirror by which all application installs and updates would come down free of charge to yourself (In other words a local ISP mirror of the Ubuntu repositories.).:D

---

### Post by smileyguy on 2009-04-24
iinet

I know they have a bunch of other unmetered linux stuff for customers (me). They call it freezone but won't let you even look if you aint a customer:(

 It's how I got my first (successful) installation of Linux ever (yesterday)!

---

### Post by nandemonai on 2009-04-24
> **smileyguy said:**
> iinet

I know they have a bunch of other unmetered linux stuff for customers (me). They call it freezone but won't let you even look if you aint a customer:(

 It's how I got my first (successful) installation of Linux ever (yesterday)!

Looks like you're in luck:

[https://launchpad.net/ubuntu/+mirror/ftp.iinet.net.au-archive](https://launchpad.net/ubuntu/+mirror/ftp.iinet.net.au-archive)

You should be able to setup your repositories to use the iinet mirror hence free apps and updates ;)

---

### Post by smileyguy on 2009-04-24
HA HA - thanks - was browsing there site looking for stuff now. seems there's a bit of stuff just not sure exactly what i'm looking at!

Just learn how to punch a repository in so here goes . . .

---

### Post by sgosnell on 2009-04-24
> GDebi seems to be the default Package Manager for my installation but Synaptics seems to be installed. Is one better than the other?

Ubuntu has many ways of skinning cats.  You can install software via Synaptic, or the Add/Remove app, with apt-get on the command line, and a few more.  They all do the same thing, just with a different user interface.  They all use the same source list, and thus the same repositories.  It's just a matter of how you prefer to do it.  Gdebi is a gui frontend for dpkg, and they're used to install packages downloaded outside the package manager.

---

### Post by smileyguy on 2009-04-24
> **nandemonai said:**
> Looks like you're in luck:

[https://launchpad.net/ubuntu/+mirror/ftp.iinet.net.au-archive](https://launchpad.net/ubuntu/+mirror/ftp.iinet.net.au-archive)

You should be able to setup your repositories to use the iinet mirror hence free apps and updates ;)
When adding software sources, do I need to add both the **main** and the **source** ATP paths? What's the difference between the two?

---

### Post by snova on 2009-04-24
> **smileyguy said:**
> When adding software sources, do I need to add both the **main** and the **source** ATP paths? What's the difference between the two?

There are source packages, and binary packages. Binary ones are what you'll usually install; source packages are the source code that the binary packages are created from.

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
[http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components)

---

### Post by smileyguy on 2009-04-25
Thanks - so I don't need to add the **source** repository?

---

### Post by 3rdalbum on 2009-04-25
You don't need to add the Source repository, it's just there for people who want to grab the source code for the software if they want to study it or make modifications.

Also, it's a small thing: But the software is called Synaptic (or Synaptic Package Manager). A lot of people in this thread have been calling it "Synaptics" which is incorrect - Synaptics is something to do with touchpads.

---

### Post by smileyguy on 2009-04-25
Thanks:)

---

