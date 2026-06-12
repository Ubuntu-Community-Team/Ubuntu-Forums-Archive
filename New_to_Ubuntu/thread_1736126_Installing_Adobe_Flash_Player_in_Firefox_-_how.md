---
title: "Installing Adobe Flash Player in Firefox - how?"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by SandJ on 2011-04-22
I have just installed Ubuntu 10.04, loaded Firefox and gone to a BBC news site which needs the Flash Player to display a video.  So I have done a Google search to see how to do that and this has me well confused.  I thought this would be easy!

My assumption:
- go to 'Add-ons', select the Flash Player and install it.  But there is no such add-on for Firefox.  (plenty of Flash blockers, though!)

Some of the advice from the Google search is:
- go to the Adobe web site and download the APT version.  That tells me I need to run apturl using an application and there are none to choose from.
- use the Ubuntu Software Centre and install the Flash Plugin (NOT the viewer plugin) but there are a few to choose from.  Which is it?
- use a Terminal command "sudo apt-get install flashplugin-installer"; really?  Do we really need to use the command line to install a common thing like the Flash Player in Ubuntu?  If so I'm going back to Windows!
- exit Firefox and in the Terminal enter "sudo apt-get install flashplugin-nonfree" ; there are quite a few other suggestions made for command line installation too.
- edit /etc/aps/sources.lst and add 'universe multiverse' and ... nah, this can't be right!

(In a flash of inspiration I selected the Firefox option "Tools", "Add-ons", "Plugins", "Find Updates" which goes to a page telling me my Flash has been disabled because it is an outdated version which is clever since it is not even in the list of Plugins!)

---

### Post by TeoBigusGeekus on 2011-04-22
Simplest way:
Open a terminal (Applications>Accessories>Terminal), give
```
sudo apt-get install ubuntu-restricted-extras
```
press enter, give your password (nothing will be shown while typing it) and press enter.
This will install flash, restricted codecs, microsoft fonts, java, etc.

---

### Post by frup on 2011-04-22
It does seem confusing right now doesn't it. Don't worry, you will get used to doing things new ways eventually. Part of the problem you're experiencing is there are more ways than one to do many things and everyone has their preferred methods. The other problem you are experiencing is that while some of the information you are getting is correct, it is also old.

> use the Ubuntu Software Centre and install the Flash Plugin (NOT the viewer plugin) but there are a few to choose from. Which is it?

This is the method we want you to use because it is easy. 

In the search area just type "restricted" it will come up with a package called Ubuntu restricted extras. It will install Flash, Mp3 codecs and everything you probably are expecting to have running.

---

### Post by SandJ on 2011-04-22
> **TeoBigusGeekus said:**
> Simplest way:
Open a terminal (Applications>Accessories>Terminal), give
```
sudo apt-get install ubuntu-restricted-extras
```press enter, give your password (nothing will be shown while typing it) and press enter.
This will install flash, restricted codecs, microsoft fonts, java, etc.Please God, no.  I have had Ubuntu installed for five minutes and the first thing I need to do is drop down to the command line?  I thought the point of Ubuntu was that it was "the OS for the rest of us" and had moved on from the old Unix ways.  That's now how to compete with Windows!

> **frup said:**
> It does seem confusing right now doesn't it.Yes, it does.

> **frup said:**
>  Don't worry, you will get used to doing things new ways eventually. Part of the problem you're experiencing is there are more ways than one to do many thingsTell me about it!

> **frup said:**
> This is the method we want you to use because it is easy. That's the method I want too!

> **frup said:**
> In the search area just type "restricted" it will come up with a package called Ubuntu restricted extras. It will install Flash, Mp3 codecs and everything you probably are expecting to have running.Aha!  So, if I understand correctly - and this is NOT a criticism - the installation process for Ubuntu is:

- bung in the CD and install it; (this will give you the lovely free open source stuff)
- go into the Ubuntu Software Centre, click on "View" and change from "Canonical maintained software" to "All software" and search for "Ubuntu restricted extras" (this then finishes the installation by adding essential free software from 3rd parties)

It would be handy if that 2nd step was included on the installation instructions.

Thank you.

---

### Post by frup on 2011-04-22
There are some different philosophies in the Linux ecosystem some of us care a lot about.

You probably know that Ubuntu is open source. Part of that means that it is kind of not proper to ship closed source software in the box.

Mp3 codecs are patent encumbered too, so there are legal issues in some countries to ship with them out of the box. This is why it is done like that.

Of the repositories, you have main where all the software is supported by the company behind Ubuntu. This software will always run the best.
Restricted is supported too, but is non-free (as in freedom, not cost). Then you have the universe and multiverse. These are run by the community and are very large.

There is a fork of Ubuntu called Linux Mint, which comes with all this stuff pre-installed. It makes things easier, but I've explained the reason why things are the way they are.

---

### Post by el_koraco on 2011-04-22
you should probably stick with windows, you'll save yourself a lot of trouble.

---

### Post by coffeecat on 2011-04-22
> **SandJ said:**
> It would be handy if that 2nd step was included on the installation instructions.

There are licensing issues in some jurisdictions that prevent that. That is why much of what comes with the ubuntu-restricted-extras is in the restricted repository.

---

### Post by frup on 2011-04-22
> **el_koraco said:**
> you should probably stick with windows, you'll save yourself a lot of trouble.

I don't think that's necessarily true. His concerns and outlook are very similar to what a lot of new users experience I think. It's easy to forget just how different things are at times. 

Lucky for new users, app stores, market places etc. are becoming entrenched in computer usage through iphones, androids, itunes etc. so more and more users are going to understand the concept of repositories.

---

### Post by SandJ on 2011-04-22
Fixed by following advice from frup.  :D

Summary of how to get Flash Player (and other stuff) working in Firefox in a new Ubuntu installation:
- I went into the Ubuntu Software Centre
- clicked on "View" and changed from  "Canonical maintained software" to "All software"
- searched for "Ubuntu  restricted extras" and installed it (ignoring the Xubuntu and Kubuntu because they weren't for my distro)
- rebooted (probably unnecessary but I'm used to Windows...)
- restarted Firefox and the Flash thingy started playing!

At no time did I need to use the command line, nor use the Firefox add-ons.  Dead easy.

Thank you also for the philosophy explanation.  I get the impression that once a new user has absorbed the philosophy of their chosen distro, the rest becomes fairly intuitive.

---

### Post by SandJ on 2011-04-22
> **el_koraco said:**
> you should probably stick with windows, you'll save yourself a lot of trouble.I'm trying to get away from Windows to save myself a lot of trouble.

I'm looking forward to the day I too can hang around in a brand new newbie forum and abuse people that have been using Linux for a couple of hours.  That will be so life-fulfilling for me.  You must be so happy in your l33tness.

---

### Post by frup on 2011-04-22
The philosophy is similar for all free software, though some distributions are more strict than others. Ubuntu is actually one of the more lenient distributions.

You don't need to restart. If after doing updates or installations you do need to restart Ubuntu will tell you and the power icon in the top right of the screen will go red.

I think the key thing for you to remember is just that there is more than one way of doing things, so be a little patient. It can actually be really hard to teach others things. Think that some of the very very best and smartest linux users around won't know the easy ways to do things because they do it the fast and efficient way. Being polite will always get you the most help. 

Good luck.

---

### Post by el_koraco on 2011-04-22
> **SandJ said:**
> I'm trying to get away from Windows to save myself a lot of trouble.



Well, then you should embrace the fact that the command line is not your enemy. In most cases, the GUI is. I'm just saying this, because during your Linux time, sooner rather than later you'll find yourself in a situation when the GUI doesn't work, or you just don't get to the GUI. 

The only way to fix it will be through a black screen with white text. If you freak out as much as you did when trying to install flash, you'll probably put your fist through the screen, which will be painful and unpleasant. 

Call it a heads up rather than abuse.

---

### Post by oldos2er on 2011-04-22
> **SandJ said:**
> I have just installed Ubuntu 10.04, loaded Firefox and gone to a BBC news site which needs the Flash Player to display a video.  So I have done a Google search to see how to do that and this has me well confused.  I thought this would be easy!

My assumption:
- go to 'Add-ons', select the Flash Player and install it.  But there is no such add-on for Firefox.

Try FlashAid instead (see my sig).

---

### Post by lovinglinux on 2011-04-22
A lot of people here that are using Linux for some time love the command-line. It is so easy, specially to install applications.

Anyway, to solve your problem, get my [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") extension. It removes conflicting plugins, install the latest version o flash from Adobe and even apply some performance tweaks.

Once you install the extension and restart Firefox, click the extension icon in the toolbar, then click "Execute" in the extension dialog. It will generate a script and launch it on a terminal, which will do everything for you, automatically.

---

### Post by Raan03 on 2011-04-22
Like the others said, don't be shy of the command line. Sooner or later, you'll encounter it anyway. e.g. I'm coding C++ programs in gEdit and compile them with g++ through the command line. It's easy & smooth. 

What you might not know; the synaptic is just a "shell" and in fact used the command line to download and install the ubuntu-restricted-extras. When using a GUI (graphical user interface), lots of (sometimes essential) info will be "hidden".

---

### Post by beew on 2011-04-22
Use the flash-aid addon for Firefox like Lovinglinux says.

---

### Post by collisionystm on 2011-04-22
Note to users using 64 bit Linux

You need 64 bit Flash to avoid having any problems. The software center will install a 32 bit version that is know to cause issues.

```

http://labs.adobe.com/downloads/flashplayer10_square.html

```

Download the tar.gz for Linux
Open the file with Archive Manager, browse the archive and extract the libflash.so to your Desktop or home folder.
Open a terminal
```

sudo nautilus

```
Browse to your libflash.so file in the Root Nautilus Window
Right click, hit CUT or COPY
Browse to 
```

/usr/lib/firefox-addons/plugins

```
Paste the file there
Close Firefox and  open again.
You now have 64 bit flash.

---

### Post by beew on 2011-04-22
> **collisionystm said:**
> Note to users using 64 bit Linux

You need 64 bit Flash to avoid having any problems. The software center will install a 32 bit version that is know to cause issues.

```

http://labs.adobe.com/downloads/flashplayer10_square.html

```Download the tar.gz for Linux
Open the file with Archive Manager, browse the archive and extract the libflash.so to your Desktop or home folder.
Open a terminal
```

sudo nautilus

```Browse to your libflash.so file in the Root Nautilus Window
Right click, hit CUT or COPY
Browse to 
```

/usr/lib/firefox-addons/plugins

```Paste the file there
Close Firefox and  open again.
You now have 64 bit flash.

????

Use Flash-Aid!

---

### Post by collisionystm on 2011-04-22
Well Now there are 2 ways to do it that WORK =)

---

### Post by Vaphell on 2011-04-22
> - use a Terminal command "sudo apt-get install flashplugin-installer"; really? Do we really need to use the command line to install a common thing like the Flash Player in Ubuntu? If so I'm going back to Windows!

As it was already explained, you don't have to do that - you can run package manager if that floats your boat. The reason for why it's beneficial to use terminal is that commands are pretty much consistent across many distros, gui on the other hand not so much (you can customize the sh%% out of graphical interface, so expect using at least hundred words to describe even the simpliest procedure while still risking not being precise enough). Copy-paste of 1 line verbatim, enter, done vs dozen clicks and 20 seconds to achieve the same thing using GUI - the choice is yours.
Besides when you know your way around command line interface you have much bigger knowledge base to draw from, because you are not limited to online resources related to a single distro.

---

### Post by beew on 2011-04-23
> **Vaphell said:**
>  Copy-paste of 1 line verbatim, enter, done vs dozen clicks and 20 seconds to achieve the same thing using GUI - the choice is yours.
Besides when you know your way around command line interface you have much bigger knowledge base to draw from, because you are not limited to online resources related to a single distro.

Well if all you do is copy and paste how are you going to increase your knowledge base? I haven't learned anything by cutting and pasting commands into the terminal just in order to get things done. In fact I learn less that way than by using the gui because I don't see the logic of those commands, they are like magical incantations that one forgets in no time.

The command line is powerful but to get the power out of it you have to sit down and learn bash script. If you are not prepared to do so I can see no advantage of the command line in terms of learning. With the gui you can often find your way through intuition and there is a logical process to it, but there is no way for the command line unless you actually know the syntax.

---

