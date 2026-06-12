---
title: "can not view certain web pages"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by hiffenscgaupher on 2009-01-10
I have recently updated from 6.06 LTS to 8.04 LTS. I have my Java installed and firestarter is active. I am using FF as my browser. The web page that I am having trouble with is on Pogo. I can get to the web site, I can go to the room select page. When I select a room, I get a white page, and it says the applet is stared. Could someone please help me with this problem.

---

### Post by handydan918 on 2009-01-10
Maybe, if you could provide some basics, like a URL...

---

### Post by hiffenscgaupher on 2009-01-10
This is the URL
[http://game3.pogo.com/room/game/frameset.jsp?site=pogop&scrn=hiffenschnaupher&rkey=sweeper-plsweepersf51997&anam=Temporary+Members+Room+1178&install=true&apid&rspt=16465&ahst=game3.pogo.com&vmtype=sun&rhst=www.pogo.com&vmver=1.6.0_07&game=sweeper&auto=PlayNow](http://game3.pogo.com/room/game/frameset.jsp?site=pogop&scrn=hiffenschnaupher&rkey=sweeper-plsweepersf51997&anam=Temporary+Members+Room+1178&install=true&apid&rspt=16465&ahst=game3.pogo.com&vmtype=sun&rhst=www.pogo.com&vmver=1.6.0_07&game=sweeper&auto=PlayNow)

---

### Post by SunnyRabbiera on 2009-01-10
well part of your issue might be there is no shockwave player for linux, I know some web games require shockwave as opposed to standard flash.
Also you need regular flashplayer too, do you have flashplayer installed?
Java is also needed, can you play flash videos or use java web apps?
By default java and flash are not preinstalled on Ubuntu but getting them is quite easy.

---

### Post by hiffenscgaupher on 2009-01-11
I do not have flash player installed. I will install that. Do I need to install shock wave also?

---

### Post by SunnyRabbiera on 2009-01-11
> **hiffenscgaupher said:**
> I do not have flash player installed. I will install that. Do I need to install shock wave also?

well flash is the easy part, heck you can get it from the adobe site:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

select the one for ubuntu hardy

as for shockwave thats a bit harder, but we will come to that if its needed.
To start off I suggest installing flashplayer and then java.

---

### Post by tuxxy on 2009-01-11
Yes that link works fine here also it is not recommended to install software manually its better to go with the supported versions provided in the repos.  Flash, Java, Codecs and much more can all be easily installed with one package called ubuntu-restricted-extras.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by kaibob on 2009-01-11
Is this how the page is supposed to appear?
EDIT: I had adblock enabled. New screenshot.

---

### Post by SunnyRabbiera on 2009-01-11
> **kaibob said:**
> Is this how the page is supposed to appear?

No, when installing flash you have to turn off firefox.
that way when you reload it the pages requesting flash will work.
The restricted extras package is another big help, it will install a large base of packages to get your ubuntu media ready.

---

### Post by tuxxy on 2009-01-11
> **kaibob said:**
> Is this how the page is supposed to appear?

Menus look a bit wierd, heres how it looks for me

---

### Post by SunnyRabbiera on 2009-01-11
> **tuxxy said:**
> Menus look a bit wierd, heres how it looks for me

make that a jpg please or something we all can read :D

---

### Post by hiffenscgaupher on 2009-01-11
I downloaded flash player, and I downloaded the Linux RPM (self extracting file). I started to install and the terminal stated   No such file or directory

---

### Post by tuxxy on 2009-01-11
> **SunnyRabbiera said:**
> make that a jpg please or something we all can read :D

hehe yes sorry, dont know what happened there :)

---

### Post by tuxxy on 2009-01-11
> **hiffenscgaupher said:**
> I downloaded flash player, and I downloaded the Linux RPM (self extracting file). I started to install and the terminal stated   No such file or directory

You dont need to download or install anything manually, as I said in my post above all you need is ubuntu-restricted-extras [FONT=monospace][FONT=Verdana]and it will install the lot for you.[/FONT]

[/FONT]```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SunnyRabbiera on 2009-01-11
> **hiffenscgaupher said:**
> I downloaded flash player, and I downloaded the Linux RPM (self extracting file). I started to install and the terminal stated   No such file or directory

No, not the RPM.
There is a pulldown menu, you want the .deb for UBUNTU not the .RPM for redhat.
We have more then one installer format here under linux so keep that in mind.

> **tuxxy said:**
> You dont need to download or install anything manually, as I said in my post above all you need is ubuntu-restricted-extras [FONT=monospace][FONT=Verdana]and it will install the lot for you.[/FONT]

[/FONT]```
sudo apt-get install ubuntu-restricted-extras
```

Yeh but might as well download the official flash installer, the rest is automatic

---

### Post by hiffenscgaupher on 2009-01-11
I used the pull down menu and I have the correct one. How do I install the java?

---

### Post by tuxxy on 2009-01-11
> **hiffenscgaupher said:**
> I used the pull down menu and I have the correct one. How do I install the java?

lol for gods sake the same way you should ahve installed Flash open a terminal and type

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SunnyRabbiera on 2009-01-11
> **hiffenscgaupher said:**
> I used the pull down menu and I have the correct one. How do I install the java?

Did flash install?
also it might help to know what kind of Ubuntu you are using, regular or a 64bit version.
To find out go to system> administration> Control center
click on the first tab, it should give you system information.
If flash gives you more errors this could be the reason why and the installation of ubuntu extras is more needed.

---

### Post by hiffenscgaupher on 2009-01-11
OK. Thats done. What should I do next.

---

### Post by SunnyRabbiera on 2009-01-11
> **hiffenscgaupher said:**
> OK. Thats done. What should I do next.

well assuming you got the extra packages installed you can try pogo again after a browser reset.
We will worry about Java if it comes

---

### Post by hiffenscgaupher on 2009-01-11
I tried to open the page again, and at the bottom of the page it said   applet game death, I have been getting that since the beginning

---

### Post by SunnyRabbiera on 2009-01-11
> **hiffenscgaupher said:**
> I tried to open the page again, and at the bottom of the page it said   applet game death, I have been getting that since the beginning

alright, lets try to install java.
Go up to system
then to administration
then to synaptic package manager
search for java runtime
MAKE SURE that you mark the packages labeled "Open JDK" for removal (do this with either the right or left mouse button)
after that search for java again
make sure to install the packages sun-java5-bin and sun-java6-bin
if they are not listed then go up to "settings"
and to "repositories"
click off all the boxes in the first and second tabs except the ones labeled source code
refresh
and again search for java
mark them for installation
restart firefox
done.

Now it may ask to install more packages, let it.

---

### Post by hiffenscgaupher on 2009-01-11
I tried one more time to get the page to load, the web site told me to clear the cache and restart the browser. I did that and I did a restart. I went to the web site, and everything came up as it is supposed to do.
Thank you very much for your help.

---

### Post by SunnyRabbiera on 2009-01-11
> **hiffenscgaupher said:**
> I tried one more time to get the page to load, the web site told me to clear the cache and restart the browser. I did that and I did a restart. I went to the web site, and everything came up as it is supposed to do.
Thank you very much for your help.

No prob, if anything else comes up just tell us.
I know I dont like using Pogo personally, and I know some of its games might not work nativly under linux.
Just be prepared :D

---

