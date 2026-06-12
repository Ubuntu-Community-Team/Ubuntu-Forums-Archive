---
title: "Basic Questions about Installing Software"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by T C on 2010-07-06
I'm a Linux novice with some basic questions about installing software.

First, I've encountered four ways to install software: Synaptic Package Manager, Ubuntu Software Center, packages that can be downloaded and installed manually, and applications (usually open source) which need to be compiled before they can be run. Here are my questions:

1. Synaptic Package Manager and Ubuntu Software Center seem very similar to each other. In fact, they seem redundant. What are the functional differences? Why is Ubuntu installed with both? Should I prefer one over the other?

2. I feel that I must do a lot of guessing when I use Synaptic Package Manager or Ubuntu Software Center. I must guess at which packages I want and/or need as prerequisites for others, and I must guess at how packages will manifest on my system after they are installed (e.g. Where will application files be stored? Will the applications add menu items under Applications? Will they integrate with other applications, run at startup, etc.?). Is it always like that, or am I doing something wrong?

3. When I use Synaptic Package Manager to install an application, it sometimes notifies me that I must install several prerequisites. When I uninstall the same application, however, it doesn't suggest that I uninstall the now unnecessary prerequisites. Does that mean I'm accumulating unused stuff on my computer? For example, I just tried to install ClamAV, then I tried to uninstall it. I'm certain that Synaptic installed a lot more packages than it uninstalled. Do I now have a lot of unused clutter as a result?

4. If I have the option to install an application manually, or to install that same application with Synaptic Package Manager or Ubuntu Software Center, which option should I choose? Do Synaptic Package Manager or Ubuntu Software Center give me any benefits regarding updates and/or integration with Ubuntu?

-TC

---

### Post by RiceMonster on 2010-07-06
> **T C said:**
> 1. Synaptic Package Manager and Ubuntu Software Center seem very similar to each other. In fact, they seem redundant. What are the functional differences? Why is Ubuntu installed with both? Should I prefer one over the other?

Think of synaptic as a more "advanced" version. I believe there's a few things it can do that software center cannot yet. However, last I heard they are looking to remove synaptic in future releases (someone can correct me if I am wrong about this). You're free to use whichever you prefer.

> **T C said:**
> 2. I feel that I must do a lot of guessing when I use Synaptic Package Manager or Ubuntu Software Center. I must guess at which packages I want and/or need as prerequisites for others, and I must guess at how packages will manifest on my system after they are installed (e.g. Where will application files be stored? Will the applications add menu items under Applications? Will they integrate with other applications, run at startup, etc.?). Is it always like that, or am I doing something wrong?

Most applications will add a menu item. It's mostly console specific applications that don't.

> **T C said:**
> 3. When I use Synaptic Package Manager to install an application, it sometimes notifies me that I must install several prerequisites. When I uninstall the same application, however, it doesn't suggest that I uninstall the now unnecessary prerequisites. Does that mean I'm accumulating unused stuff on my computer? For example, I just tried to install ClamAV, then I tried to uninstall it. I'm certain that Synaptic installed a lot more packages than it uninstalled. Do I now have a lot of unused clutter as a result?

If you want to clean unwanted dependencies, open up a terminal and type:
```
sudo apt-get autoremove
```

> **T C said:**
> 4. If I have the option to install an application manually, or to install that same application with Synaptic Package Manager or Ubuntu Software Center, which option should I choose? Do Synaptic Package Manager or Ubuntu Software Center give me any benefits regarding updates and/or integration with Ubuntu?

-TC

I'm not sure what you mean by manually. Do you mean install a .deb package? It really depends on a number of things. Generally. you may as well go through software center of synaptic unless you want to install a newer version than the one in the repositories.

---

### Post by kvarley on 2010-07-06
1.) Synaptic has more complexity to it and is more advanced. Ubuntu Software Centre is for all users and presents a nice catalogue of stable applications to install. (Synaptic shows all packages.) USC is for day to day use, Synaptic is for more complex issues.

2.)USC installs applications so that they appear in the same category as they are found in the Software Centre. USC installs all dependencies for you, in synaptic it will mark dependencies for you, however you can pick individual packages - not just applications.

3.) Yes, sort of. It does leave stuff behind. Use "sudo apt-get autoremove" to clear these or Ubuntu Tweak.

4.)Synaptic and Ubuntu Software Centre use the same software sources. (Repositories or PPA's.) These are found in System>Administration>Software Sources. Applications installed via both methods will come through update-manager.

Hope this helps, if you need anymore help - just post a reply! :)

---

### Post by QIII on 2010-07-06
My emphatic two cents:

If it is available in the repositories, install from there (Synaptic,  Software Center or terminal).

There is a very simple reason for this.  (This is not absolute, but only  general.  Absolute statements are generally wrong...)

Say you installed XYZApp from a .deb file you download XYZ.org.  We are going to assume you can trust XYZ.org, because the same package is in the Ubuntu repositories.  At some point,  XYZ.org will update XYZApp.  Then, you'll have to do whatever XYZ.org  says to uninstall XYZApp, download the new .deb and reinstall it.

The benefit of using the repositories (or a PPA -- but be careful with  PPAs because they may have unstable daily builds and fun things like  that going on) is that when an update to XYZApp reaches the  repositories, XYZApp will be updated along with the periodic updates you  do.  There will be little to no effort on your part.   That update will  not happen the very instant XYZ.org makes the update available, because  someone needs to get the update, package it, check the package, check  to make sure it won't break your OS, etc.  That takes a bit of time.  But that extra step also means that the update will be less likely to break your system.

---

### Post by Penguin Guy on 2010-07-06
> **T C said:**
> 1. Synaptic Package Manager and Ubuntu Software Center seem very similar to each other. In fact, they seem redundant. What are the functional differences? Why is Ubuntu installed with both? Should I prefer one over the other?
Software Center and Synaptic Package Manager are both front-ends for a program called [FONT="Courier New"]apt[/FONT] - meaning that they both look different but will achieve the exact same result. Synaptic is generally used by more advanced users because it's slightly more complex, but feel free to use whatever you want.

> **T C said:**
> 2. I feel that I must do a lot of guessing when I use Synaptic Package Manager or Ubuntu Software Center. I must guess at which packages I want and/or need as prerequisites for others, and I must guess at how packages will manifest on my system after they are installed (e.g. Where will application files be stored? Will the applications add menu items under Applications? Will they integrate with other applications, run at startup, etc.?). Is it always like that, or am I doing something wrong?
I'm not exactly sure what you mean, perhaps it would help if you gave some examples?

> **T C said:**
> 3. When I use Synaptic Package Manager to install an application, it sometimes notifies me that I must install several prerequisites. When I uninstall the same application, however, it doesn't suggest that I uninstall the now unnecessary prerequisites. Does that mean I'm accumulating unused stuff on my computer? For example, I just tried to install ClamAV, then I tried to uninstall it. I'm certain that Synaptic installed a lot more packages than it uninstalled. Do I now have a lot of unused clutter as a result?
Yes, you can see what 'clutter' you have and delete it using [COLOR="Green"]System -> Administration -> Computer Janitor[/COLOR] (which, on a side note, also uses [FONT="Courier New"]apt[/FONT]).

> **T C said:**
> 4. If I have the option to install an application manually, or to install that same application with Synaptic Package Manager or Ubuntu Software Center, which option should I choose? Do Synaptic Package Manager or Ubuntu Software Center give me any benefits regarding updates and/or integration with Ubuntu?
Installing manually is a bad idea unless you know what you're doing. Use Synaptic or Software Center (see #1) instead.

---

### Post by ajgreeny on 2010-07-06
> Yes, you can see what 'clutter' you have and delete it using [COLOR=Green]System -> Administration -> Computer Janitor[/COLOR]  (which, on a side note, also uses [FONT=Courier New]apt[/FONT]).I would suggest you use Computer Janitor very carefully as it will probably tell you to uninstall a lot of things you may want to keep, eg skype, compiz-switch, and several other things that you may have decided you needed to install manually.

You can use synaptic to remove those packages that are simply dependencies of others that you have now removed, by using the **Status** button on the left hand pane and choosing **Installed (auto-removable)**

You see, as many have said, synaptic is more complex than the other gui package managers, and in my opinion is undoubtedly the best.

There is, however, little need to worry about those auto-removable packages as they do not generally make ubuntu slower, as they probably would do in windows.  They do take up space on the drive, but seldom in these days of big hard drives is that of great consequence.  Linux does not have a single, huge registry file like windows but keeps its configurations separate for each package, thus removing a terrible bottleneck that is often talked about in windows circles.

---

### Post by T C on 2010-07-06
You guys rock. Thanks for the replies. In addition to answering my questions, you've helped me put things in context (which is what beginners really need).

QIII, what is a PPA?

Penguin Guy, as an example of guessing in Synaptic, consider installing ClamAV. When I search for ClamAV, I get a long list of packages and I don't know which ones to choose. If I choose the command-line interface, the rest of the necessary packages come along as prerequisites, but if I choose a GUI interface like ClamTK, they don't. clamav-data, which would seem necessary, is incompatible with clamav-freshclam. Also, ClamTK installs a menu item into a menu I wouldn't expect (Accessories) with a name I wouldn't expect (Virus Scanner). None of this is obvious behavior; I feel like I have to figure it out by trial-and-error.

-TC

---

### Post by philinux on 2010-07-06
At this point I would not recommend JANITOR at all.

---

### Post by ajgreeny on 2010-07-06
> **philinux said:**
> At this point I would not recommend JANITOR at all.
I'm with you there!  Use with great care or preferably not at all.  It simply does not seem well integrated with the overall system if you have anything at all outside the repos installed.

---

### Post by bance on 2010-07-06
without wishing to hi-jack this thread, how does one remove the configuration files that are created, such as with mythbuntu?

---

### Post by warfacegod on 2010-07-06
I'll second that. Avoid Computer Janitor like the plague. Among its many flaws, the most memorable for me where:

.01 It wanted to remove FireFox. While I was using it.

.02 It wanted to remove my active video driver. The keyword here is "active".

---

### Post by warfacegod on 2010-07-06
> **bance said:**
> without wishing to hi-jack this thread, how does one remove the configuration files that are created, such as with mythbuntu?

```
sudo apt-get autoclean
```

If my memory serves.

---

### Post by m_kelly on 2010-07-06
> without wishing to hi-jack this thread, how does one remove the configuration files that are created, such as with mythbuntu?

I believe what you are looking for is

```
sudo apt-get remove --purge *package-you-do-not-want*
```

---

### Post by alphacrucis2 on 2010-07-06
> **T C said:**
> You guys rock. Thanks for the replies. In addition to answering my questions, you've helped me put things in context (which is what beginners really need).

QIII, what is a PPA?



-TC

PPA stands for Personal Package Archive. You can think of them as a mini repository mostly hosted by [Launchpad]("https://launchpad.net/"). They are used to make new versions of applications or even brand new applications that haven't yet made it to the main repositories. You have to be a bit careful as they are often at the "bleeding edge" intended for testing. Sometimes though they are the best way to get an update you really need. An example I used this ppa below to install the latest version of VLC:

[URL="https://launchpad.net/~c-korn/+archive/vlc"]https://launchpad.net/~c-korn/+archive/vlc
[/URL]

If you are going to use ppa's it is a good idea to first install the package called ppa-purge. If the ppa gets you into trouble you can use ppa-purge to eliminate the offending ppa and restore packages to the standard ones.

---

