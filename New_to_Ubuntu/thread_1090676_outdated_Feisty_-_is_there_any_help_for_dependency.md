---
title: "outdated Feisty - is there any help for dependency error ?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by garyed on 2009-03-08
I have an older computer that I installed Feisty on since it was the last version of Ubuntu that supported a computer with no more than 256 meg of ram.Everything works O.K. except for Adobe Flash & when I try to install it I get all kinds of dependency errors.Since it's no longer supported is there any way to solve those dependency errors?

---

### Post by Temposs on 2009-03-08
You would have to go through each package that flash depends on and install the proper version until you satisfy all the dependencies...you can check package dependencies here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

If you're not sure how to do that, it may be more trouble than you want to go through.

What I'd recommend is upgrading to Xubuntu 8.04 or 8.10. You can run it with a machine that has low RAM like yours because it uses a lighter desktop manager called Xfce

EDIT:
[http://www.xubuntu.com/](http://www.xubuntu.com/)

---

### Post by whoop on 2009-03-08
*** Temposs said I also recommend updating to latest version (or latest LTS version).
Feisty is not supported anymore so it won't be updated and it is therefore a security risk to run it. Especially if your connected to the internet.

---

### Post by kansasnoob on 2009-03-08
I'd suggest a newer version of Xubuntu:

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

> You need 192 MB RAM to run the Live CD or 128 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time. To install Xubuntu, you need 1.5 GB of free space on your hard disk. Once installed, Xubuntu can run with starting from 192 (or even just 128) MB RAM, but it is strongly recommended to have at least 256 MB RAM. 

Still too heavy? Try UbuntuLite:

[http://u-lite.org/?q=node/2](http://u-lite.org/?q=node/2)

It uses the LXDE window manager.

Or check out Aysiu's guide:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by garyed on 2009-03-08
First I want to thank you guys because I really do appreciate the info.
Now for my rant.
Since about 2 years ago when I started with Ubuntu I have been totally blown away with the OS & have been trying to ween myself away from Windows to the point where I only use it for two or three applications.
I do run Hardy on the computers that can handle it.
I refused to upgrade to Vista so Ubuntu was the perfect alternative.
Now I find that the problem I'm having with Ubuntu Feisty is the very same
reason I was trying to get away from Windows. I'm not against updates & upgrades to improve the OS but being forced to in order to stay with an OS is what I am opposed to.  
I have another old computer running Feisty with Flash running perfectly so i know it can be done.
I'm still an Ubuntu fan but I'm just a little disappointed right now.

---

### Post by Temposs on 2009-03-08
First, no one is forcing you to upgrade. However, you must understand that the version of Ubuntu you are using has its limitations, and also security risks. It is also no longer supported by Canonical, the company that develops/organizes Ubuntu. They're the ones that normally take care of dependencies for you and prepare security and software updates that work smoothly on your system. This is not an easy thing to do...

It costs money and time to pay developers and for volunteers to fix bugs, develop new features, and keep the OS secure. The contributing developers cannot continue supporting each old version of Ubuntu they've ever released, with all its thousands of packages to keep working together properly and securely. There simply aren't the resources. 

You are welcome to continue using Feisty, but it is now your own responsibility to support software updates like Flash and keep the OS secure against the latest threats, rather than having someone else worry about dependencies and threats. But this is a potentially difficult and tedious thing to do, especially if you're not a programmer.

I pointed you to a way to update your dependencies in my first post, and you can use that if you can figure it out. It will work, but takes some time. It may turn out that the newer versions of Flash themselves require newer versions of Ubuntu/Linux at the kernel level, too(hypothetically possible), which would force you to upgrade anyway, if you wanted to use a newer version of Flash than is supported on Feisty.

It makes sense to have new versions on a regular basis because as newer and more advanced software is developed, older versions of various libraries that were supported in older versions have to be shed in order to keep the size of the OS down and to not force developers to make sure everything works well with dozens of versions of each of thousands of software libraries. 

As software advances, Ubuntu developers want to favor the newer versions of software over old because they offer better programming models, more features for more hardware, and better security, so the versions of Ubuntu are a convenient way to phase out old versions of software and their dependent libraries.

This is a necessary process. It is different from the Windows update process that tries to extract money from people through planned artificial obsolescence and lock-in. 

Ubuntu is free software and you are never forced to upgrade. We are simply recommending the easiest, safest and more progressive route for maintaining your computer.

---

### Post by kansasnoob on 2009-03-08
> **garyed said:**
> First I want to thank you guys because I really do appreciate the info.
Now for my rant.
Since about 2 years ago when I started with Ubuntu I have been totally blown away with the OS & have been trying to ween myself away from Windows to the point where I only use it for two or three applications.
I do run Hardy on the computers that can handle it.
I refused to upgrade to Vista so Ubuntu was the perfect alternative.
Now I find that the problem I'm having with Ubuntu Feisty is the very same
reason I was trying to get away from Windows. I'm not against updates & upgrades to improve the OS but being forced to in order to stay with an OS is what I am opposed to.  
I have another old computer running Feisty with Flash running perfectly so i know it can be done.
I'm still an Ubuntu fan but I'm just a little disappointed right now.

Well, I ran Win ME for a couple of years after support ended using Firefox browser ......... so, if you must, get the newest Firefox using Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

It really is as simple as downloading Ubuntuzilla to your Desktop (or wherever you choose) then double click it, which will install it to the repos, then just go to terminal and run:

```
ubuntuzilla.py -a install -p firefox

```

The script will ask you some simple questions, it's pretty straight forward.

For Flash I'm guessing you can install Flash 10 if Ubuntuzilla allows you to install Firefox 3.07. But I've tried Flash 9 in Dapper (which is still supported until June of this year) and it worked well with the newest Mozilla build of Flashblock - 1.5.8 (just don't download Flashblock from the repos - use the Get Add-ons tool in Firefox).

As far as installing the Flash tar.gz:

[http://www.psychocats.net/ubuntu/flashpre710](http://www.psychocats.net/ubuntu/flashpre710)

or the rpm (I did this in the old Freespire which was based on either Ubuntu 7.04 or 7.10):

[http://www.ubuntugeek.com/install-flash-player-9-in-ubuntu.html](http://www.ubuntugeek.com/install-flash-player-9-in-ubuntu.html)

---

### Post by kansasnoob on 2009-03-08
> It is different from the Windows update process that tries to extract money from people through planned artificial obsolescence and lock-in.

That would make a good sig!

---

### Post by garyed on 2009-03-09
I had to leave unexpectedly & just back to my computer so again i appreciate the ideas.
Temposs, I did try the page you referenced but again no packages were listed for Feisty since it is not supported any more. I'll try some more things tomorrow evening but its bed time now, work tomorrow.
If I only knew what dependencies I needed I could probably copy them from my other Feisty computer.

---

### Post by Temposs on 2009-03-09
garyed,
   You probably don't need to know the feisty dependencies, since what's on feisty obviously isn't working for what you want to install. Which version of Flash are you wanting to install, and where are you downloading it from(provide link)?

---

### Post by garyed on 2009-03-09
Well I kind of feel like an idiot now.
I was trying to install Flash Player 10 since that was what I was pointed to on the Adobe site. I just copied my Flash player 9 tar.gz file from my other Feisty computer & it installed fine with no dependency problems.
So all my ranting was out of my own ignorance.
Thanks again to all

---

