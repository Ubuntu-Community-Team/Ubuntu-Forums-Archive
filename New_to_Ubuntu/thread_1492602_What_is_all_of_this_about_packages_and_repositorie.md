---
title: "What is all of this about packages and repositories?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by adamk918 on 2010-05-24
Can someone please explain the idea of packages, repositories, and all of that stuff? As a Windows 7 convert (and I still use it on my production machine), this is all new to me.

---

### Post by SRST Technologies on 2010-05-24
Packages - just that, a package.  Consider it to be like the mail.  You get packages in the mail.  In this case, the mailman is apt-get or Synaptics (whatever program you like to find packages), and the package is new software.  Another way to see it is the package (which is actually a .deb file) is something like setup.exe on Windows for whatever program you want to install.

Repository - That's the Post Office.  A Repository is a server on the net that your computer is going to to get the Package.

So, what it is, you open Synaptics or apt-get and search for a package.  When you are done selecting new packages, you click apply, and Synaptics or apt-get fetches the Package from the Repository and installs it for you automatically, usually without ever asking you any confusing questions or for your serial key.

It sure beats the crap out of searching the net or pirating stuff on Windows, doesn't it?  It's all free, it's easy as pie, and it's pretty fast, too.

---

### Post by laffinet on 2010-05-24
In Ubuntu (and other Linux distributions) software is installed via packages, which are found in repositories.

Instead of searching the net for software you'd like to install and then download an installation file, you do that via Synaptic, the package manager in Ubuntu.

These packages are organised in repositories. 

For example, open Synaptic Package Manager in System, type e.g. neverball (a game) in the search field. This should bring up a result. You can now right click and select install.
Once you apply, this will automatically download the required files and install them.

One of the advantages of this system is that repositories get updated constantly. Therefore, you can update all the installed software on your system with one simple command. Well, two to be precise.

---

### Post by ronnielsen1 on 2010-05-25
It's great once it sinks in

---

### Post by alphacrucis2 on 2010-05-25
Another thing that the package manager does is to keep a local database of what (and the version of what) you have installed. Ubuntu will by default, periodically check the repository server indexes to see if any installed packages have changed.

---

### Post by k3lt01 on 2010-05-25
In Ubuntu a package is a .deb file, the Windows equivalent is an .exe installer file. They are simply files that contain the application and various things needed to help install it.

Repositories are the location where you download the packages from. e.g. archive.ubuntu.com is a repository archive, archive.canonical.com is a repository archive that Canonical (Ubuntu's parent company) keeps, packages.medibuntu.org is a repository archive that contains many packages that may not be legal in many jurisdictions or have other "issues" regarding patents etc, that are useful for media type packages.

These 3, in the above paragraph, are kept up to date (within the bounds of sensibility that is) during the life of the distribution you are using, i.e. 10.04 has a support life of 3 years for the desktop and 5 years for the server.

The absolute beauty of this system is that you, the user, do not have to search high and low over the internet for what you want. As each new distribution comes out the repository archives get bigger and better containing more and more new applications. If it isn't in the repositories it generally means it hasn't been fully tested on Ubuntu. It also means that you do not have to worry about any unknown nasties being installed on your system such as can and does happen with Windows .exe files.

---

### Post by SRST Technologies on 2010-05-25
> **ronnielsen1 said:**
> It's great once it sinks in

Wow, dude, that was so helpful to the person that asked the question that they've not logged back into the forum since you answered it for them.  You taught them so much about computers and Linux in general and Ubuntu in specific that they've gone and wrote their own version of Linux by now.

You should be proud!

---

### Post by flyfishingphil on 2010-05-25
> **k3lt01 said:**
> In Ubuntu a package is a .deb file, the Windows equivalent is an .exe installer file. They are simply files that contain the application and various things needed to help install it.

Repositories are the location where you download the packages from. e.g. archive.ubuntu.com is a repository archive, archive.canonical.com is a repository archive that Canonical (Ubuntu's parent company) keeps, packages.medibuntu.org is a repository archive that contains many packages that may not be legal in many jurisdictions or have other "issues" regarding patents etc, that are useful for media type packages.

These 3, in the above paragraph, are kept up to date (within the bounds of sensibility that is) during the life of the distribution you are using, i.e. 10.04 has a support life of 3 years for the desktop and 5 years for the server.

The absolute beauty of this system is that you, the user, do not have to search high and low over the internet for what you want. As each new distribution comes out the repository archives get bigger and better containing more and more new applications. If it isn't in the repositories it generally means it hasn't been fully tested on Ubuntu. It also means that you do not have to worry about any unknown nasties being installed on your system such as can and does happen with Windows .exe files.
Was just looking at the list of repositories in the Ubuntu Karmic Koala Bible and wondering about adding them to my repository list.

Would anybody know if that list is current and the keys listed are up to date?

Thanks.

---

### Post by aysiu on 2010-05-25
A really easy way to think of package management and repositories is as similar to the iTunes App Store or the Android Market.

Instead of manually downloading apps, you go through an app management program that looks online to see what's available and then installs the apps for you.

That's how software installation in Ubuntu (and most Linux distros) works as well. Synaptic Package Manager or Ubuntu Software Center is just an interface to install apps (which come as package files with a .deb extension, which you don't have to see) off of app host servers (repositories).

---

### Post by ronnielsen1 on 2010-05-25
You know SRST Technologies (whatever that is)
 I'd look at all your posts and make sure that all of your posts were directly helpful to the people but I guess you hide your posts. It seemed like his questions were getting answered appropriately and I was trying to offer encouragement. (Something a user trying to learn a new OS can use) I have posted here solving questions where I have been thanked and I haven't posted new polls on how many b's can we type in a forum. So lighten up dude, go correct some spelling errors in some forum

---

### Post by coldfinger on 2010-05-26
I recently loaded Lucid.  When I tried to install the build-essential package, I got "file not found" errors for the packages and its dependencies.  Does this mean that the  repository is missing or not enabled?

---

### Post by k3lt01 on 2010-05-26
> **coldfinger said:**
> I recently loaded Lucid.  When I tried to install the build-essential package, I got "file not found" errors for the packages and its dependencies.  Does this mean that the  repository is missing or not enabled?Try refreshing your repository lists.

---

