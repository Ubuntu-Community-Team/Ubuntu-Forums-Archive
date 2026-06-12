---
title: "windows applications"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by wdbnv on 2009-11-17
Hi, 
 
I'm new to Ubuntu...
 
therefore maybe strange question: is it possible to run Win-apps on Ubuntu?
 
kind regards

---

### Post by emigrant on 2009-11-17
yes, you can run most of the applications.
go to terminal:
```

sudo apt-get install wine

```or if you are in jaunty, go to add/remove prog and search for wine.
or if you are in karmick go to software center and search for wine.

after you finish installing.
right click the .exe file you want to install and select install through wine (cant remember the exact wording)

---

### Post by fromthehill on 2009-11-17
[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)
here you can look if your windows program will work with or without some workaround

---

### Post by Paqman on 2009-11-17
> **emigrant said:**
> yes, you can run most of the applications.


Er, I wouldn't agree with that. Wine is fantastic, but if you assume that your Windows app *won't* run properly in it, you'll be less disappointed when it doesn't, and more pleasantly surprised when it does.

Wine is basically a massive kludge. A small percentage of Windows apps will run well on it, a lot more can be made to work acceptably well with some work, but a large amount just plain don't.

Did you have any particular apps in mind wdbnv?

---

### Post by emigrant on 2009-11-17
yes, sorry, i should not have said 'most of the apps'. personally i hate wine though i have it on my system. one reason the interface it gives is not nice for ex for photoshop.

---

### Post by 3rdalbum on 2009-11-17
> **Paqman said:**
> Er, I wouldn't agree with that. Wine is fantastic, but if you assume that your Windows app *won't* run properly in it, you'll be less disappointed when it doesn't, and more pleasantly surprised when it does.

Wine is basically a massive kludge. A small percentage of Windows apps will run well on it, a lot more can be made to work acceptably well with some work, but a large amount just plain don't.

+1. Great minds think alike; that's exactly what I always tell people :-)

---

### Post by wdbnv on 2009-11-23
> Did you have any particular apps in mind wdbnv?
 
 
Yes I do.
 
I'm using ETS (DOMOTICA sofware for EIB/KNX) in windows....

---

### Post by praveesh on 2009-11-23
You can run a lot of windows applications with the help of a compatibility layer named wine . Even though you can get it from Ubuntu repository (ie apt-get install wine) , it's better you go to their website [http://www.winehq.org/](http://www.winehq.org/) and download the latest wine since a lot more applications will be supported . From my experience, wine supports applications not in the appdb too.  

If you don't like the interface, you can theme it . You can install all the windows themes (<themename>.msstyles). To install theme , applications>wine>configure wine >desktop integration>browse . Browse to a .msstyles file . If you own a windows license, you can install original windows themes . Windows themes are located at c/windows/resources/themes

---

### Post by theozzlives on 2009-11-23
I hate wine, never been able to get a Windows app to run under it. Windows apps are for Windows, best idea is to run [VirtualBox]("http://www.virtualbox.org/") or dual boot.

---

### Post by praveesh on 2009-11-23
If you own a windows license, for even better performance, you can even replace the .dll files supplied by wine (which can be seen in .wine folder inside your home folder . You will need to enable viewing hidden files) with original windows .dll files . But you should not replace four specific .dll files . I don't remember the names . You can know the names from [www.winehq.org](www.winehq.org) .


There's a very easy way . Install 'playonlinux' . Some applications will require you to do some tweakings to make in run in wine . Playonlinux will automatically download all the required files and do all the required tweakings for an application . The result is that you will be able to run much more applications that won't run in mere wine . 
 

Do you know that microsoft office 2007 runs really fine in wine ?.

---

