---
title: "Indicator-weather"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by pressko on 2011-03-21
Hi,

Installed indicator-weather from [http://www.omgubuntu.co.uk/2011/03/indicator-weather-adds-data-caching-extra-weather-providers-and-locations/](http://www.omgubuntu.co.uk/2011/03/indicator-weather-adds-data-caching-extra-weather-providers-and-locations/) 2 days ago.

Last night there was a update for it. After the update the indicator-weather is not starting anymore. So i removed it (sudo apt-get --purge remove indicator-weather) and installed it again... and again it's not starting by clicking the icon or starting it from alt+f2. When i type "indicator-weather" in terminal i got : 
Another instance of this program is already running :O 

There is no indicator-weather process in the process and i cant kill it ...

sudo ps -ef |grep indicator-weather
presian   3727  3636  0 12:57 pts/0    00:00:00 grep --color=auto indicator-weather


help ?! 

10x in advance :)

---

### Post by Frogs Hair on 2011-03-21
Try this and then try indicator-weather again.```
killall indicator-weather
```

---

### Post by pressko on 2011-03-22
indicator-weather: no process found

.... WTF

---

### Post by Dutch70 on 2011-03-22
I'm not real sure about this, but have an idea. 

 Try uninstalling it again, but this time, go to your .config folder and if you find a folder for indicator-weather, delete it, then re-install.

---

### Post by mc4man on 2011-03-22
I am (was) using it on natty - the latest version broke it 
I'd either wait for a fix or you could revert to the previous version you were using

This is one of the bugs resulting from the break - there is some suggestion that installing python-desktopcouch-application would fix, doesn't here, just creates a new error

[https://bugs.launchpad.net/ubuntu/+source/desktopcouch/+bug/738762](https://bugs.launchpad.net/ubuntu/+source/desktopcouch/+bug/738762)

---

### Post by pressko on 2011-03-22
> **Dutch70 said:**
> I'm not real sure about this, but have an idea. 

 Try uninstalling it again, but this time, go to your .config folder and if you find a folder for indicator-weather, delete it, then re-install.

where is this .config folder ?

---

### Post by Dutch70 on 2011-03-22
In your home folder, click view in the menu bar and select "show hidden files"

---

### Post by pressko on 2011-03-22
there is no indicator-weather files

---

### Post by Dutch70 on 2011-03-22
If there are none inside the .config folder, then a fresh install of the applet should give you the same thing you had when you first installed it. If you're sure there is nothing in there, maybe a different name? Then AFAIK reinstalling should work fine.

---

### Post by pressko on 2011-03-22
AFAIK ... ?
man i'm new in ubuntu  :(

---

### Post by Dutch70 on 2011-03-22
> **pressko said:**
> AFAIK ... ?
man i'm new in ubuntu  :(

Sorry, AFAIK is...

As Far As I Know. :)

---

### Post by mc4man on 2011-03-22
While nothing is getting the new version to work in natty, happened to log into maverick

Try running this in a terminal then restarting or logging out, then in
```
sudo apt-get install python-desktopcouch
```

---

