---
title: "Updating Software?"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by Whisp3r on 2010-02-28
I'm running 9.04 on my desktop. I would like to update my some of my programs (IE, NetBeans 6.5, OpenOffice 3.0, etc). Even my Firefox's update is grayed out and I'm stuck on 3.0. :( How do I do this? For example, my drop down in NetBeans says no updates available, however, my 9.10 laptop has no problem upgrading. I assume I need to add certain sources or something? Thanks!

When I install a fresh version from Add/Remove applications, it reinstalls VirtualBox version 2... Any help would be greatly appreciated.

---

### Post by MelDJ on 2010-02-28
you may want to add the repos for your software from launchpad.
for example for firefox: [https://launchpad.net/ubuntu/+source/firefox/](https://launchpad.net/ubuntu/+source/firefox/)

---

### Post by snowpine on 2010-02-28
```
sudo apt-get install firefox-3.5
```

You might consider upgrading to 9.10 Karmic. This will make all of your applications 6 months newer. (9.04= April 2009; 9.10 = October 2009)

---

### Post by laptoplinux on 2010-02-28
Ok, well, typically, the program updates come through your package manager, so they will show up in the Update Manager along with any other system updates.  

That said, Ubuntu's policy is to freeze the software versions on each Ubuntu release, only issuing security updates and not updating to a new version of the programs until the next Ubuntu release.  So, if you update to the next Ubuntu version, you are usually never more than 6 months behind the latest software.  The downside is, sometimes you wait 6 months or so for the latest software, especially if a program had a new release just after an Ubuntu release.  

There's at least two ways to upgrade program versions within an Ubuntu release:

1.)  Search for a PPA (Personal Package Archive) for the program you are interested in.  These are 3rd party repositories maintained by members of the Ubuntu community.  They might have more up to date versions of the programs you are looking for.  one you add the PPA and refresh your software sources, you should be able to update the program.

2)  The other way is to find a newer .deb package for the program, usually from the program's website or possibly from somewhere like GetDeb.  Download the .deb file and you should be able to install it just by double-clicking on it.

3)  For open office in particular, I suggest you google for how to install the newer version on your version of Ubuntu.  It isn't hard, but the process doesn't quite fit either of the above methods.

<i> <b>A word of warning </i></b>: Upgrading programs outside of the package manager, done correctly, shouldn't cause problems in your system, but you may or may not run into things later when you decide to upgrade in place to the next release of Ubuntu.  It depends largely on which programs and which method was used to upgrade them.  Since OpenOffice is tied to the ubuntu-desktop metapackage, you may want to revert to the version that came with your Ubuntu release before upgrading to the next Ubuntu release.  Gotta run for now, but I hope that helps some.

---

### Post by Merk42 on 2010-02-28
> **snowpine said:**
> ```
sudo apt-get install firefox-3.5
```


Do not do this. You'll end up with "Shiretoko", which has [a bug that won't be fixed](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211)

Instead, look [here](http://ubuntuforums.org/showthread.php?t=1193567)
Firefox does have a PPA like most, if not all, of the software you wish to update

---

### Post by Whisp3r on 2010-02-28
Thank you all for your assistance. Karmic shot my laptop when I upgraded, so I am a firm believer in fresh installs. I'm just hanging on to a working 9.04 for now, until the next LTS comes out. 

Thanks!

---

### Post by snowpine on 2010-02-28
Personally I would upgrade to the current release (9.10), rather than use an older release (9.04) and then enabling lots of 3rd party repositories in an attempt to make it less outdated. That seems like kind of a "band aid" solution to me.

My 9.04 machines have no PPAs or other 3rd party software sources enabled. I enjoy the stability of using older and well-tested applications. I use Firefox 3.0 every day, and it is functional and reliable. You do not need the latest and greatest software to post on Ubuntu Forums. :)

---

### Post by Paddy Landau on 2010-02-28
I still use 8.04 because it's an LTS. Using FF 3.0 is fine, really.

The only program that I felt really necessary to upgrade is OpenOffice. Read the semi-official [how to install OpenOffice on Ubuntu]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68") from Hagar (it has a link to the official documentation).

---

### Post by laptoplinux on 2010-02-28
One more thing, Whisp3r.  You are aware that you can partition your hard drive to have a separate partition for /home and / (the root system partition), right?

This way, you only reformat the / partition during a fresh install, and all of your files remain intact in the /home partition, which remains untouched.  Bear in mind that the files will just belong to your old user name and will be stored in /home/<your old user name> after the install, so if you switch user names, you may need to copy the files over, change permissions, etc.

This can be a good way to get the benefits of a fresh install with minimal disruption to your system.  Though, being paranoid, I'd still always recommend backups for important files before any major system change, just in case.

---

