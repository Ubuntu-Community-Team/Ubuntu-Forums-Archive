---
title: "Latest Firefox and Open Office"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by luckydeveloper on 2010-01-25
Hi,

I use Ubuntu 8.10 now. It has older versions of Firefox and Open office which are maintained by ubuntu developers. 

I want to use latest version of firefox and Open office which are maintained by the respective original authors of those two products. I dont want to switch to ubuntu 9.04 or 9.10 just for these two products. 

How can I **_install and Use_** the latest versions of Firefox and Open office in ubuntu 8.10 ?

---

### Post by mikewhatever on 2010-01-25
The latest Open Office is available in from openoffice.org Not sure what language you want, so not linking directly. You'll need to unpack it and install with <sudo -i package-name> command. 
Following the release of Firefox 3.6, the forum is full of guide on how to install it. I'd recommend ubuntuzilla.

A word of caution, I doubt the latest OO and Firefox had been tested by anyone on 8.10, so whatever problems you encounter, you are on your own.
Furthermore, support for 8.10 is ending in April, just three month away, so that you might want to start thinking about migrating.

---

### Post by lovinglinux on 2010-01-25
For Firefox, see the [COLOR="Sienna"]**Install Other Version**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). I explains several methods and diferences between them.

---

### Post by nanotube on 2010-01-26
> **mikewhatever said:**
> The latest Open Office is available in from openoffice.org Not sure what language you want, so not linking directly. You'll need to unpack it and install with <sudo -i package-name> command. 
Following the release of Firefox 3.6, the forum is full of guide on how to install it. I'd recommend ubuntuzilla.

A word of caution, I doubt the latest OO and Firefox had been tested by anyone on 8.10, so whatever problems you encounter, you are on your own.
Furthermore, support for 8.10 is ending in April, just three month away, so that you might want to start thinking about migrating.

well, fwiw, i'm on ubuntu intrepid (8.10), and using firefox 3.6 (through ubuntuzilla) and OOo 3.0 (through openoffice.org) (i know this one's not the latest... but it's newer than the 2.4 which comes in the repos), with nary a problem. so should work, unless you have done something weird with your system.

---

### Post by luckydeveloper on 2010-01-26
> **nanotube said:**
> well, fwiw, i'm on ubuntu intrepid (8.10), and using firefox 3.6 (through ubuntuzilla) and OOo 3.0 (through openoffice.org) (i know this one's not the latest... but it's newer than the 2.4 which comes in the repos), with nary a problem. so should work, unless you have done something weird with your system.

Thank you !

---

### Post by gradinaruvasile on 2010-01-26
Openoffice 3.1.1 from the site works on Intrepid just fine. I installed it on 2 Intrepids, there are no problens.
Also, Firefox from mozilla's site (the generic linux build) works fine in Intrepid. These generic builds have everything bundled so no need for separate packages such as xulrunner etc.

---

### Post by luckydeveloper on 2010-01-26
I have installed Firefox from ubuntuZilla repo. But When i click Applications -> Internet -> Mozilla Build of Firefox,   the same firefox 3.0 opens up. what could be the problem ?

---

### Post by speedwell68 on 2010-01-26
Instead of using Ubuntuzilla, why not try Swiftfox.  It is a optimised build of the latest Firefox and updates from it's own repository...


[http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by Paqman on 2010-01-26
> **mikewhatever said:**
> The latest Open Office is available in from openoffice.org Not sure what language you want, so not linking directly. You'll need to unpack it and install with <sudo -i package-name> command. 


Actually [Open Office has .debs available]("http://download.openoffice.org/other.html#tested-full"), so all you need to do is download and click.

---

### Post by okkadiroglu on 2010-01-26
Hi,

I am using Kubuntu 9.10 on a AMD64 computer. I had no problem with OpenOffice but since two days when I try to open it I get a message:

Could not start process Cannot talk to klauncher: Not connected to D-Bus server.

What am I suppose to do?

Many thanks for the help.

Best Regards

---

### Post by mikewhatever on 2010-01-26
> **Paqman said:**
> Actually [Open Office has .debs available]("http://download.openoffice.org/other.html#tested-full"), so all you need to do is download and click.

The debs are packed into tar.gz archives, which probably means there are more then one. Something like <sudo dpkg -i *.deb> should install them all, while with clicking, you'll need to work hard. Not saying it wouldn't work though.

---

### Post by nanotube on 2010-01-26
> **luckydeveloper said:**
> I have installed Firefox from ubuntuZilla repo. But When i click Applications -> Internet -> Mozilla Build of Firefox,   the same firefox 3.0 opens up. what could be the problem ?

did you make sure to /quit/ all existing running instances of firefox3.0?

---

### Post by okkadiroglu on 2010-01-28
Hi,

I have to answer my own post! :D I reinstalled all the OpenOffice packages that I used and the problem disappeared. The owner of some of the files in ~/.openoffice.org directory became root but after changing the ownership all problems are solved for the time being.

---

### Post by Hagar Delest on 2010-01-30
To install the latest version of OOo, see [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

For FF, I always download the tarball from the Mozilla site, put it in the /opt folder and change the shortcuts to that one. I can keep several versions and then downgrade if the latest version is not compatible with my extensions.

---

