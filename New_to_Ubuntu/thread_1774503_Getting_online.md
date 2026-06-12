---
title: "Getting online"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by eeonz on 2011-06-03
I'm having a lot of trouble with ubuntu and my speedtouch 330 modem.

I'm following this guide:

[http://ubuntuforums.org/showpost.php?p=4813601&postcount=114](http://ubuntuforums.org/showpost.php?p=4813601&postcount=114)
And all the files for it can be found here:

[http://ubuntuforums.org/showthread.php?t=796697&page=2](http://ubuntuforums.org/showthread.php?t=796697&page=2)

Everything goes well until this message pops up:

**"Breaks existing package 'python-gtkspell' conflict: python-gnome2-extras (<2.191-4) "**

I know nothing about ubuntu, i've had it for about 3 hours now! Can somebody please explain what these means please in layman's terms. How do i fix this? Does it mean that python-gtkspell is something i already have and need rid of? If so, hows that done?

I'm hoping to use "usb adsl modem manager" to finally get online. Any help would be brilliant!

Thank you!

---

### Post by candtalan on 2011-06-03
> **eeonz said:**
> I'm having a lot of trouble with ubuntu and my speedtouch 330 modem.

I'm following this guide:
[http://ubuntuforums.org/showpost.php?p=4813601&postcount=114](http://ubuntuforums.org/showpost.php?p=4813601&postcount=114)
And all the files for it can be found here:
[http://ubuntuforums.org/showthread.php?t=796697&page=2](http://ubuntuforums.org/showthread.php?t=796697&page=2)

Everything goes well until this message pops up:
**"Breaks existing package 'python-gtkspell' conflict: python-gnome2-extras (<2.191-4) "**

I know nothing about ubuntu, i've had it for about 3 hours now! Can somebody please explain what these means please in layman's terms. How do i fix this? Does it mean that python-gtkspell is something i already have and need rid of? If so, hows that done?

I'm hoping to use "usb adsl modem manager" to finally get online. Any help would be brilliant!
Thank you!

Welcome to Ubuntu and Ubuntu forums!

Unfortunately I do not think I can offer you good news. These are usb modems and I believe have been poorly supported in Linux based systems. The reason I think is because they are quite bad news in that they (being usb devices) have no 'router' function, meaning that they are I believe essentially two way devices - making your machine unduly vulnerable to incoming attacks.

This very un attractive feature in my view has meant that pretty well no effort has been made to have them working in (say) Ubuntu.

I also note that the link you mention is about 3 years old. This is well past its probable 'use by' date, because linux based systems such as Ubuntu release new versions twice a year. There is a fast pace of development. So that specialist and rarely used stuff will get much more difficult to make work, if work at all, unless you are a total expert..

Apologies for the probable unwelcome opinion here.

When I saw a friend recently using one similar usb modem I helped him replace it asap with a modem router - these (basic ones) have at least one ethernet socket to connect to the PC, to a network card.

AFAIK pretty well anything with such a socket will work with Ubuntu, using the ethernet connection. Most can be found as discarded items, or used, at low cost.

hth

---

### Post by jtarin on 2011-06-03
> **eeonz said:**
> I'm having a lot of trouble with ubuntu and my speedtouch 330 modem.

I'm following this guide:

[http://ubuntuforums.org/showpost.php?p=4813601&postcount=114](http://ubuntuforums.org/showpost.php?p=4813601&postcount=114)
And all the files for it can be found here:

[http://ubuntuforums.org/showthread.php?t=796697&page=2](http://ubuntuforums.org/showthread.php?t=796697&page=2)

Everything goes well until this message pops up:

**"Breaks existing package 'python-gtkspell' conflict: python-gnome2-extras (<2.191-4) "**

I know nothing about ubuntu, i've had it for about 3 hours now! Can somebody please explain what these means please in layman's terms. How do i fix this? Does it mean that python-gtkspell is something i already have and need rid of? If so, hows that done?

I'm hoping to use "usb adsl modem manager" to finally get online. Any help would be brilliant!

Thank you!

The message is saying you already have that one installed only they conflict in version numbers. Try it without installing that one. Doesn't work??? Consider candtalan's post.

---

