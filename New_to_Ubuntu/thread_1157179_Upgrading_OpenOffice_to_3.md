---
title: "Upgrading OpenOffice to 3?"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by newbie.poster on 2009-05-12
Two quick questions:

1. When I was on 7.10, I was alerted to the possibility of upgrading to 8.04 by update manager.  Now that I am on 8.04, why do I not get this same alert for Ubuntu 9.xx?

2. My OpenOffice is only 2.4 and update manager does not detect it as out of date.  I'd like to be on OO 3.xx.  How does one upgrade their OO version _easily_ on ubunutu 8.04?

Thanks!

---

### Post by gjoellee on 2009-05-12
If you upgrade to Ubuntu 9.04 you will get OpenOffice 3.0.

OpenOffice 3.0 is not included in the Intrepid repositories and will probably never enter them either, but you can install OpenOffice 3.0 anyway. Look here: [http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by newbie.poster on 2009-05-12
> **gjoellee said:**
> If you upgrade to Ubuntu 9.04 you will get OpenOffice 3.0.

What's the recommended method for upgrading from 8.04 to 9.04?  Doesn't seem to be an option in Update Manager.

---

### Post by philinux on 2009-05-12
> **newbie.poster said:**
> What's the recommended method for upgrading from 8.04 to 9.04?  Doesn't seem to be an option in Update Manager.

You would have to upgrade to 8.10 first then to 9.04 major bandwidth exercise. Easier to reinstall 9.04 especially if home is on it's own partition.

Also see this.
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by abn91c on 2009-05-12
> **newbie.poster said:**
> What's the recommended method for upgrading from 8.04 to 9.04?  Doesn't seem to be an option in Update Manager.
look here [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
and here for office 3.xx  [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

---

### Post by Cheesemill on 2009-05-12
You can only upgrade by one release at a time, so you would have to upgrade from 8.04 to 8.10, then upgrade from 8.10 to 9.04

By default 8.04 wont give you the option to upgrade to 8.10 because 8.04 is an LTS version (Long Term Support), it will only give you the option to upgrade when the next LTS version is released (10.04 I think).

You can get round this by following the instructions:

[https://help.ubuntu.com/community/IntrepidUpgrades#Network%20Upgrade%20for%20Ubuntu%20Desktops%20(Recommended](https://help.ubuntu.com/community/IntrepidUpgrades#Network%20Upgrade%20for%20Ubuntu%20Desktops%20(Recommended))

Once upgraded to 8.10 the option to upgrade to 9.04 should appear.

As always there is **no guarantee** of a successful upgrade so make sure you back up any important data before trying this.

In fact I think that in your situation I would back up my /home folder and re-install from scratch, you'll end up with a much leaner install (plus you'll be able to format your partitions as ext4 to gain more of a speed increase).

Hope some of this helps,

Cheesemill

(That's what you get when typing a long reply, I've just been beaten twice :))

---

### Post by newbie.poster on 2009-05-12
I'm actually thinking about trying CentOS for a while.  Not sure if I am keen on ubuntu.

---

### Post by Jon Monreal on 2009-05-12
> **newbie.poster said:**
> I'm actually thinking about trying CentOS for a while.  Not sure if I am keen on ubuntu.

As stated above, upgrade is easily possible by going the route of 8.04 first. If you are thinking about changing because of the upgrade, you might as well at least try to upgrade first. It's not like either of the upgrades are that large when compared to downloading an entire new system.

But it's your system, and your call. Just know that it's not as bad as it sounds, and if you need someone to help walk you through, I would be more than happy.

---

### Post by newbie.poster on 2009-05-12
> **Jon Monreal said:**
> But it's your system, and your call. Just know that it's not as bad as it sounds, and if you need someone to help walk you through, I would be more than happy.

It's not the upgrade fear so much as wanting to try something a little diff
I'll try the upgrade anyway. Thanks for the help offer!

---

### Post by Jon Monreal on 2009-05-12
> **newbie.poster said:**
> It's not the upgrade fear so much as wanting to try something a little diff
I'll try the upgrade anyway. Thanks for the help offer!

I can understand that; after all, it's the desire to try something different that drives many to Linux in the first place.

I hope everything goes well for you, and remember to back up your important files.

-Jon

---

### Post by newbie.poster on 2009-05-12
> **Jon Monreal said:**
> I hope everything goes well for you, and remember to back up your important files.

As it happens I did back up my important files but not everything went well :(

I have a myriad of issues but the most important one to me is the display issues I am having now.  One of the reasons I switched from fedora to ubuntu last year was because every time I rebooted my machine under fedora I would lose my display settings, the xserver would crash and I'd have to spend an hour rebuilding it each time.

It blew.

A buddy showed me 'Envy' on ubuntu which corrected everything for him and he never had issues so I switched.  Now I am having the same problems I had under fedora.  For starters, I have two monitors, and they both work, but one is a replica of the other (so everything I do on one screen happens on the other).  What I'd like is for the two screens to be one big desktop.

I also just uninstalled and then reinstalled EnvyNG, which seems to be fine, and reports that the recommended driver is the one which is enabled.

But when I choose System --> Preferences --> Display, I get the warning that:

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

And when I do, I am given the warning that:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Which I do, and then the who cycle repeats itself.

Any pointers on how to get my second monitor back?

I also have a few other minor issues that seem more like annoyances than anything, such as a "The greeter application appears to be crashing" and also "There was an error while performing indexing".  But those can wait until the display issues are handled.

---

### Post by Jon Monreal on 2009-05-13
> **newbie.poster said:**
> As it happens I did back up my important files but not everything went well :(

I have a myriad of issues but the most important one to me is the display issues I am having now.  One of the reasons I switched from fedora to ubuntu last year was because every time I rebooted my machine under fedora I would lose my display settings, the xserver would crash and I'd have to spend an hour rebuilding it each time.

It blew.

A buddy showed me 'Envy' on ubuntu which corrected everything for him and he never had issues so I switched.  Now I am having the same problems I had under fedora.  For starters, I have two monitors, and they both work, but one is a replica of the other (so everything I do on one screen happens on the other).  What I'd like is for the two screens to be one big desktop.

I also just uninstalled and then reinstalled EnvyNG, which seems to be fine, and reports that the recommended driver is the one which is enabled.

But when I choose System --> Preferences --> Display, I get the warning that:

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

And when I do, I am given the warning that:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Which I do, and then the who cycle repeats itself.

Any pointers on how to get my second monitor back?

I also have a few other minor issues that seem more like annoyances than anything, such as a "The greeter application appears to be crashing" and also "There was an error while performing indexing".  But those can wait until the display issues are handled.

Do you have any system specs on hand? That might help.

I'll see if I can dig anything up, but I've never used Envy, so I don't know how much I can help you with that.

If you have a fast enough internet connection, you may want to see if the latest LiveCD gives better results. If it does, you could install that. I know that would be disappointing after the update, but it might be worth it.

At any rate, I personally don't believe you would have a better time with another flavor of Linux from upgrade to upgrade. I think we should keep perspective, however, that Windows users have also faced a myriad of problems when upgrading, especially with their more recent versions.

---

