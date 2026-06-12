---
title: "unique problem installing kde 4.1"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by standingchair on 2009-01-18
Hello Ubuntu Forums, 
I was following this tutorial on installing KDE
[http://www.ubuntugeek.com/how-to-install-kde-41-on-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-install-kde-41-on-ubuntu-810-intrepid-ibex.html)

I got up to this command:
sudo aptitude install kubuntu-kde4-desktop

And let it run, and everything was ok and going normally. I left my room to take a shower, came back and my computer was frozen on the screen saver. This has happened before. I am running Ubuntu 8.10 off of a USB flash drive and I think this may have something to do with it freezing up.

Now, I've turned my laptop on and off, and have signed into my desktop. How can I continued configuring KDE? Should I uninstall and start from scratch?

I'm a total noob, just started with Ubuntu 8.10 a couple of days ago. So what is your advice?
Please feel free to ask me any questions. 
Thanks
Jenn

---

### Post by jimmy the saint on 2009-01-18
You could try to start over and see if it works.  If the screensaver keeps locking up, I would start by disabling it, especially if you are going to be doing anything that takes a while.  If it locked up during the download, you should be alright.  If it locked up during the installation, you will have to see if it works.  Other than that, there is really no simple way to find out.

---

### Post by standingchair on 2009-01-18
I think I'd feel more comfortable just reinstalling it. It might have frozen during the download, but I can't be sure. I constantly get knocked offline, every couple of minutes if I'm downloading. 

When I search for KDE 374 files are found in my file system. But, if all of them aren't downloaded and there....what then?

Is this the correct command to uninstall?
sudo apt-get remove kde

Thank you for your advice, 
Jenn

---

### Post by snova on 2009-01-18
> **standingchair said:**
> sudo aptitude install kubuntu-kde4-desktop

> **standingchair said:**
> Is this the correct command to uninstall?
sudo apt-get remove kde

aptitude has this nice property where if you install something with it, it remembers what packages it had to install as dependencies. So rather than this, I suggest:

```
sudo aptitude remove kubuntu-kde4-desktop
```

Which will additionally remove all the other bits of KDE 4.1.

But be careful- make sure it's not removing anything else!

Also, the next time you go to install it, try installing it from outside of KDE, just in case. It might not agree with being updated while running. (I had a similar problem trying to get KDE 4.2 RC1.)

---

### Post by abn91c on 2009-01-18
All you [COLOR="Red"]need[/COLOR] to do was install kubuntu-desktop from synaptic or
```
sudo apt-get kubuntu-desktop
```

---

### Post by jimmy the saint on 2009-01-18
as previously noted, aptitude is better for such processes as it remembers all the additional things installed and will remove them as well.  
If I choose to install appA with aptitude, and it also installs b,c,d,e and f
aptitude remove appA will uninstall all of them as opposed to apt-get only removing appA and leaving the rest.  Very usefull for the *buntu-desktop meta-packages.

The things is, you have to have used aptitude, not apt-get to install it in the first place for it to work that way.

---

### Post by standingchair on 2009-01-18
This is what I got when running that command:
centurion@centurion-laptop:~$ sudo aptitude remove kubuntu-kde4-desktop
[sudo] password for centurion: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Note: selecting "kubuntu-desktop" instead of the
      virtual package "kubuntu-kde4-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done



Just noticed your post ab, that does make it easier. I  am new to this, I'll try that out once I uninstall. But, you see, I also want to get used to the terminal. I can operate fine under a GUI but I know that learning how to use the terminal will help me in the long run.


Will that uninstall KDE?
Thanks everyone-
Jenn

---

### Post by abn91c on 2009-01-18
you need to do **sudo apt-get autoremove** to uninstall packages no longer needed after removing KDE

---

### Post by standingchair on 2009-01-18
> **abn91c said:**
> you need to do **sudo apt-get autoremove** to uninstall packages no longer needed after removing KDE
Thanks abn.
J

---

### Post by EXCiD3 on 2009-01-24
Have you considered using [Keryx]("http://keryx.betaserver.org") to download the packages on a computer with a good consistent internet connection and take the packages back home for installation? Its very helpful for me being on dialup as I cant download much in a reasonable amount of time.

---

### Post by yeats on 2009-01-24
> you need to do sudo apt-get autoremove to uninstall packages no longer needed after removing KDE

This will remove unnecessary packages, but the problem with metapackages is that 

```
sudo apt-get remove kubuntu-desktop
```

does NOT remove the packages that were installed by the "sudo apt-get install" command.

You can do 

```
dpkg -l | grep KDE | awk '{print $2}' > installed.kde
```

to find all the packages related to KDE and create a file from those package names

then 
```
vim installed.kde
```

and inside vim type

```
:%s/\n/*space*/g  I typed *space* - you would use the spacebar there
```

You can select and copy that list, then you can type

```
sudo apt-get remove 
```

and then paste in your list.

voila!

---

