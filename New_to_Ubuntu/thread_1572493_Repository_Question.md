---
title: "Repository Question"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by ubunwhat on 2010-09-11
Entering my second week of Ubuntu and starting to get the hang of things.  I think.  I have encountered a bit of a snag, however.  I want to install the current version of Mysql Workbench.  The article on installing workbench here on the Ubuntu site is already out-dated as a newer version has been released and I have absolutely no idea what file name to substitute in the install instructions.  I tried simply using the newer version (5.2.27 as apposed to 5.2.25) but the installer could not find the .deb.  Since I lack the expertise to decipher what the .deb file name would be that I need to dpkg I am left with two alternatives.  First, I can download workbench from the mysql site in .tar.bz files and install them manually.  Not only does this seem dicey for my current level of experience, but there are several posts all over this site saying that one should install through the package manager rather than through the .tar method.  Ok, fine.  But workbench isn't in the Package Manager list, so I would need to add whatever repository that MySql uses and well, therein lies my problem.  How on earth would I find this out in order to add it to the Package Manager?

---

### Post by surfer on 2010-09-11
did you try [this]("https://help.ubuntu.com/community/MySqlWorkBench")?

---

### Post by coffeecat on 2010-09-11
> **ubunwhat said:**
> First, I can download workbench from the mysql site in .tar.bz files and install them manually.

You definitely don't want to be compiling from source! :)

I presume the tar.bz2 files were from this site:

[http://www.mysql.com/downloads/workbench/](http://www.mysql.com/downloads/workbench/)

If you click on 'Select Platform' and select Ubuntu, you get download options for DEB packages for Ubuntu. Select the version of Ubuntu you are using, download the DEB and simply double-click on it to install it.

---

### Post by ubunwhat on 2010-09-11
> **surfer said:**
> did you try [this]("https://help.ubuntu.com/community/MySqlWorkBench")?

This is exactly what I was referencing when I talked about the article on installing Workbench in Ubuntu on this site.  I will note again, for anyone stumbling upon this thread later in hopes of resolving a similar problem, that the description of the .deb in that article is no longer valid.

---

### Post by ubunwhat on 2010-09-11
> **coffeecat said:**
> You definitely don't want to be compiling from source! :)

I presume the tar.bz2 files were from this site:

[http://www.mysql.com/downloads/workbench/](http://www.mysql.com/downloads/workbench/)

If you click on 'Select Platform' and select Ubuntu, you get download options for DEB packages for Ubuntu. Select the version of Ubuntu you are using, download the DEB and simply double-click on it to install it.

Spot on!  Many thanks.

---

### Post by coffeecat on 2010-09-11
> **ubunwhat said:**
> I will note again, for anyone stumbling upon this thread later in hopes of resolving a similar problem, that the description of the .deb in that article is no longer valid.

If you look at that page again, it doesn indeed refer to an earlier version of MySql Workbench, but it links to the MySql download page that I posted. All you have to do is to substitute the package version that you downloaded into the 'sudo dpkg' command. (Which is just a terminal way of installing the package.)

I tell you this because with Community documentation, you do come across things slightly out of date, but you can often adapt the instructions to suit. Indeed, on that page, under 'Previous Ubuntu version', it says, "(adapt the name accordingly)" which is just as true for the current version.

Alternatively, you could register a Launchpad account and edit the page yourself. Welcome to the open source community! :wink:

---

### Post by MestreLion on 2011-01-03
The .DEB for the MySQL WorkBench is great, but... isnt a repository better?

This way we can configure Synaptics/Ubuntu Download Center/APT/Whatever to add a new package location (software source) and thus benefit from upgrades, bug fixes and new releases.

So... is there ANY repository / PPA / something / anything avaliable for MySQL WorkBench? 

I cant believe that the official GUI for administration of worlds most popular free and open database has NO repository yet...

---

### Post by patrickvdbemt on 2011-01-17
I am looking for the package as well for quite some time.
The only package that worked was the one that got installed on my 10.04.
After upgrading to 10.10 (latest and greatest ??) I haven't been able to get it working. :-k

As you state, how can it be that a package for such a major player in OS database in the latest version of Ubuntu simply does not work....  OR do we have to wait for 11.04  ?? :lolflag:

---

### Post by patrickvdbemt on 2011-01-17
fyi : I have noticed that mysql has provided a debian package for ubuntu10.10.
but although the installation process seems to succeed the program does not startup.
it is available in the menu structure, starting shows the initial "welcome" screen that disappears in a couple of seconds time.

---

### Post by Steve R. on 2011-02-01
MySQl Workbench will not load for me either.  I appear to be having the same problems as patrickvdbemt.  All I get is a flash of the splash screen. Program does not load. 

I have an AMD-64 and I download the 64 byte version ((mysql-workbench-gpl-5.2.31a-2ubu1010-amd64.deb).

---

### Post by MestreLion on 2011-02-11
Well, it works fine for me (Netbook 10.04). But it has the same bug as MySQL Admin: for  it to work, you must first start the service. Yes, using the terminal. (sudo service mysql start). And THEN you can use to manage the connections. Quite a dumb requirement for a tool thats supposed to manage a service, including its start/stop status.

And, additionally, i could not create user accounts when using mysql >= 5.2 Looks like the server changed the format of the SQL query needed for a new user to be created, and Workbench wasnt updated to use this new  query.  Works fine for 5.0 and 5.1 tough (the version in repository)

---

