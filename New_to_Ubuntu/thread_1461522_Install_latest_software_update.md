---
title: "Install latest software update"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by nickreserved on 2010-04-24
There are cases where I don't need the stable release of a software, but latest.
For instance, I don't want Firefox 3.5 but Firefox 3.6.

But there are cases where I don't need the latest release but the stable.
For instance, a server software.

How can I tell this to package manager?

I believe that package manager must have more than one packages for each program (like **stable**, **beta**, **alpha**, **nightly build** or like **Apache 1.x**, **Apache 2.0.x**, **Apache 2.2.x**)

If I tell bullshits, don't blame me. I am totally dummy on Linux.

And a last question:
For instance, Firefox has release 3.6 branch as stable. Why package manager doesn't drop Firefox 3.5 package?

---

### Post by cap10Ibraim on 2010-04-24
what I know is that  
Firefox 3.6 will be available in lucid 10.04

---

### Post by Linuxforall on 2010-04-24
Best way is to add ppa, in case of latest Firefox it is [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable) in case you are running Karmic or above, open up terminal and type sudo add-apt-repository ppa:mozillateam/firefox-stable and do a sudo apt-get update and apt-get upgrade and you will have latest FF 3.6.3

---

### Post by ajgreeny on 2010-04-24
As the ubuntu update cycle is only six months between versions, once a version is out as the final, the application main versions such as firefox stay the same, ie there is no update from 3.5 to 3.6. There are many ways to get the most recent versions of just about any software if you search, and the PPAs are the first place to search out what you want.

Otherwise just wait a week and you will get ubuntu 10.04 final version with just about the latest of all the standard software available for you to try.

There is no way to tell the package manager that you want particular versions of applications on a global scale, if that is the question you are asking, but you can add some PPA repositories if you want to, install a new version of one particular application available from it, and then disable that repo to avoid continual notification of updates to other applications also available but not wanted, also from that repo.

---

### Post by warfacegod on 2010-04-24
If you want to update just firefox, I think ubuntuzilla might be your best choice.

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page")

---

### Post by 2hot6ft2 on 2010-04-24
And to lock a version so it doesn't update go to
System > Administration > Synaptic Package Manager
find the package and click on
Package > Lock version

---

### Post by cap10Ibraim on 2010-04-24
> **2hot6ft2 said:**
> And to lock a version so it doesn't update go to
System > Administration > Synaptic Package Manager
find the package and click on
Package > Lock version
This is useful , thanks

---

### Post by Melotten on 2010-04-24
Basically should work in this way:
the repository you have ""by default" is providing you just few versions of the programs that are tested to work with the current version of Ubuntu you have.

as suggested by Linuxforall, if you add a different repository you will be able to install automatically all the vesion of FIrefox you want ;)

Same story is, to give you an example, with Chrome. is not in the ubuntu repositoy, but you add the ones of google and you are done :)

I hope this help :)

---

### Post by lovinglinux on 2010-04-25
See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

