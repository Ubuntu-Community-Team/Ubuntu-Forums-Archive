---
title: "Please hold my hand while while I'm trying to update firefox"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by completely new on 2010-04-22
I installed ubuntu two or three days ago so, as my name says, I'm completely new. I searched the internet for a way to update Firefox and all the stuff that was written was written not to well. Anyway, I finally managed to install 3.6 version, but I don't know how to run it now because I don't know where it is. :frown: The shortcut on the bar on top and the shortcut in the menu just run the old version. Please tell me how to run the new firefox and get rid of the old one, or even better, upgrade this version to keep all the settings and plugins. Thanks.

---

### Post by nhasian on 2010-04-22
the easiest way would probably be upgrading to Ubuntu 10.04 Lucid Lynx when it comes out on april 29th.  or you could upgrade to the release candidate now

> To upgrade from Ubuntu 9.10 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '10.04' is available. Click Upgrade and follow the on-screen instructions. 

---

### Post by snowpine on 2010-04-22
Hi Completely New, it is impossible to help you because we don't know what you've done so far. We also don't know which version of Ubuntu you're running and which version of Firefox you want. :)

First ask yourself: do I really need a new Firefox? You should get Firefox updates through the Ubuntu Update Manager; there is no need to install a different Firefox from the Interweb as long as you keep current with your Update Manager. The version number will not change, but you will get all the important security updates and bug fixes. This is the easiest, stablest, and recommended method in my opinion.

If you do really want the latest Firefox for whatever reason, one easy way is by using Ubuntuzilla. I find that their instructions are very clear and easy to follow: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by gethighprlinks on 2010-04-22
Please clarify your points with - what version of Ubuntu you are using and waht version of firefox you want to get. Hope we can help you positively.

---

### Post by P4man on 2010-04-22
Its important to understand a fundamental difference here between ubuntu and windows. Ubuntu comes with a lot of supported applications, but these applications are only updated to a new version once every 6 months  along witht he operating system itself (bug fixes and security updates are constantly provided). Applications like firefox and openoffice really are part of an ubuntu release.

In general the ubuntu philosophy is to keep using the same versions of software, until the next ubuntu release gives you newer ones. That way its possible to test OS + apps without having endless combinations.

Anyway, in some cases you may not want to wait for the next ubuntu and get a newer OpenOffice, firefox or whatever. In that case, I would first check backport repository:
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

(please read their explanation)

Enabling that repository will allow you to upgrade selected applications to newer versions in an easy way.

If you must, you can go outside the repositories and manually install apps (or add third party repositories), but I would not recommend that to a new user. Its surprisingly difficult to manually install OO or firefox properly.

---

### Post by completely new on 2010-04-22
> **nhasian said:**
> the easiest way would probably be upgrading to Ubuntu 10.04 Lucid Lynx when it comes out on april 29th.  or you could upgrade to the release candidate now

Normally, I'd wait for a few weeks after the inital release to download the new version.

> **snowpine said:**
> Hi Completely New, it is impossible to help you because we don't know what you've done so far. We also don't know which version of Ubuntu you're running and which version of Firefox you want. :)

First ask yourself: do I really need a new Firefox? You should get Firefox updates through the Ubuntu Update Manager; there is no need to install a different Firefox from the Interweb as long as you keep current with your Update Manager. The version number will not change, but you will get all the important security updates and bug fixes. This is the easiest, stablest, and recommended method in my opinion.

If you do really want the latest Firefox for whatever reason, one easy way is by using Ubuntuzilla. I find that their instructions are very clear and easy to follow: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)
I have 9.10 version, forgot to mention that. Firefox 3.6 is available since january and it's the end of april now, so I figured what are they waiting for with the new Firefox and decided to do it myself. With the method on the link you provided, it seems that I'll end up with two firefoxes installed and I'm unsure about that.

edit: 

> **P4man said:**
> Its important to understand a fundamental difference here between ubuntu and windows. Ubuntu comes with a lot of supported applications, but these applications are only updated to a new version once every 6 months along witht he operating system itself (bug fixes and security updates are constantly provided). Applications like firefox and openoffice really are part of an ubuntu release.

In general the ubuntu philosophy is to keep using the same versions of software, until the next ubuntu release gives you newer ones. That way its possible to test OS + apps without having endless combinations.

Anyway, in some cases you may not want to wait for the next ubuntu and get a newer OpenOffice, firefox or whatever. In that case, I would first check backport repository:
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

(please read their explanation)

Enabling that repository will allow you to upgrade selected applications to newer versions in an easy way.

If you must, you can go outside the repositories and manually install apps (or add third party repositories), but I would not recommend that to a new user. Its surprisingly difficult to manually install OO or firefox properly.
Ok, this is getting more and more complicated. I think it would be best not to do anything for now, at least until I get the hang of things. Thanks everyone for the replies. :)

---

### Post by snowpine on 2010-04-22
I agree 99% with P4man, with an important 1% exception: Firefox is not in backports, so enabling the backports repository will not help you get a newer Firefox.

If you are coming to Linux from Windows, you are probably used to surfing the web and hunting down updates for each application individually. The Linux way is much nicer--all updates come through a central repository with the Update Manager--so give the Linux way a try first before you fall back on old habits is my advice. :)

---

### Post by completely new on 2010-04-22
> **snowpine said:**
> I agree 99% with P4man, with an important 1% exception: Firefox is not in backports, so enabling the backports repository will not help you get a newer Firefox.

If you are coming to Linux from Windows, you are probably used to surfing the web and hunting down updates for each application individually. The Linux way is much nicer--all updates come through a central repository with the Update Manager--so give the Linux way a try first before you fall back on old habits is my advice. :)Does this include applications that didn't come with it, but I installed myself later?

---

### Post by ed-koala on 2010-04-22
Yes, if you installed them through Synaptic.

---

### Post by snowpine on 2010-04-22
> **completely new said:**
> Does this include applications that didn't come with it, but I installed myself later?

Yup, Ubuntu is easy-peasy like that. So long as you stick to applications from the repositories (installed using Synaptic, Ubuntu Software Center, or terminal commands like apt-get) you should have a stable and secure system. :)

---

### Post by P4man on 2010-04-22
> **snowpine said:**
> I agree 99% with P4man, with an important 1% exception: Firefox is not in backports, so enabling the backports repository will not help you get a newer Firefox.

Ah, didnt know that. Is there an easy way to see what is in the backports repo?

---

### Post by snowpine on 2010-04-22
> **P4man said:**
> Ah, didnt know that. Is there an easy way to see what is in the backports repo?

[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by lovinglinux on 2010-04-22
As already stated, there is usually no need to download any application other then from the official repositories. Nevertheless, if you want the latest features see the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

