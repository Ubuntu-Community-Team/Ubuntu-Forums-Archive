---
title: "Install FireFox 3.5"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2009-06-30
Hey -
Super excited about the release of FF 3.5.  The download on their site is a .tar.bz2 and inside is a directory with a lot of files in it.  I'm new to installing software without using apt-get, has anyone installed FF 3.5 and could help me out w/ how it's done?

BTW: running 8.10x64

Thanks

---

### Post by mike555 on 2009-06-30
Until Ubuntu puts out the "offical" update you can just put that folder somewhere , like in your user folder , open it and click on the icon that says "Firefox" and run it ......

I have a fix for no close button on the last tab if anyone is interested ...

---

### Post by cariboo on 2009-06-30
3.5b4 has been in the Jaunty repositories since it's release, install it and wait a couple of days for the repositories to be updated to the 3.5 release.

---

### Post by heyyy on 2009-06-30
> **cariboo907 said:**
> 3.5b4 has been in the Jaunty repositories since it's release, install it and wait a couple of days for the repositories to be updated to the 3.5 release.

could you point me exactly where(im kind of new to linux) i can install it
and how to have the latest updates?

---

### Post by gjoellee on 2009-06-30
> **heyyy said:**
> could you point me exactly where(im kind of new to linux) i can install it
and how to have the latest updates?

You can find Synaptic Package Manager in the menu,open it and search for "firefox". Then lok at the version number and you should find firefox 3.5 quite quickly. Then right click on the package you want to install and select "Mark for installation". Then find the "Apply" button on the top of the window.

It is shown on this page: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
You just won't get the upgrade button.

---

### Post by heyyy on 2009-06-30
> **gjoellee said:**
> You can find Synaptic Package Manager in the menu,open it and search for "firefox". Then lok at the version number and you should find firefox 3.5 quite quickly. Then right click on the package you want to install and select "Mark for installation". Then find the "Apply" button on the top of the window.

It is shown on this page: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
You just won't get the upgrade button.

so that means that i'll have version 3.5 but i wont be able to have further notifications for upgrades?

---

### Post by lovinglinux on 2009-06-30
For instructions on how to install Firefox 3.5 or upgrade the 3.0.11 version, check the [color=#CC0000]**Firefox Alternatives & Newer Versions**[/color] section of the [**[color=#CC0000]Firefox optimization and troubleshooting thread[/color]**](http://ubuntuforums.org/showthread.php?t=1193567).

For a list of other threads talking about the same subject, visit [http://ubuntuforums.org/showthread.php?t=1200781](http://ubuntuforums.org/showthread.php?t=1200781)

---

### Post by heyyy on 2009-07-01
after some research i did on my own in order to install it from the official repositories ifound two solutions:

1)

> sudo sh -c "echo 'deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"
sudo sh -c "echo 'deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"


and then add the Launchpad PPA GPG key:

> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247510BE

2)

Copy the lines below and add them to your system's software sources.

> deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main 



and then add the pgp key: 1024R/247510BE

----------------

probably all these are simple and the same thing but i want to make sure this is the right thing to do ..so?

---

### Post by heyyy on 2009-07-01
i was looking on synaptic and found a lot of packages with this descriptions:
dummy upgrade package for firefox-3.1 -> firefox-3.5

could someone explain this to me a bit further

---

### Post by carml on 2009-07-01
As fas as I know the dummy packages are used for compatibility or as servant to others packages.

---

### Post by shailendra on 2009-07-01
The simplest way would be to enable the auto upgrade feature in Firefox. It will prompt you to download and upgrade to the new version. Synaptic Manager shall do the rest.

---

### Post by SJChip on 2009-07-01
It was like two clicks!  Help->About->Check for updates.  It downloaded it and everything.  Had to restart Firefox, though.

Oh, wait.  That was for Windows XP.  Sorry.  Still can't find a Ubunty Hardy update yet.  I guess a few months shouldn't matter.  Opera is pretty good too.

---

### Post by cariboo on 2009-07-01
Firefox will not be upgraded, as it is an LTS version, and the only updates will be for security. You can setup the ppa's in heyyy's post to get the newer version.

---

### Post by alexcckll on 2009-07-01
> **cariboo907 said:**
> Firefox will not be upgraded, as it is an LTS version, and the only updates will be for security. You can setup the ppa's in heyyy's post to get the newer version.
Umm- so am I to understand that this is the equivalent of OpenOffice 3 in that respect?  us LTS-LTS users will get it (or the then-stable version) next October?

---

### Post by kansasnoob on 2009-07-01
Firefox 3.5 became available yesterday using Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Worked fine for me in Hardy, Jaunty, and Mint Gloria.

---

### Post by lovinglinux on 2009-07-01
> **kansasnoob said:**
> Firefox 3.5 became available yesterday using Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

Worked fine for me in Hardy, Jaunty, and Mint Gloria.

It worked for me too. Additionally, the semi-official *[ubuntu-mozilla-daily](https://help.ubuntu.com/community/FirefoxNewVersion)* PPA repository also worked. So I don't know which one to recommend :). Nevertheless, I decided to compile Firefox myself and got 30% performance boost ;)

Check my benchmarks:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=119664&stc=1&d=1246476466[/IMG]
> 
**[color=#CC0000]Note:[/color]** **Firefox 3.5 optimized **is the official final version from Mozilla, compiled from source with optimization flags. 

---

### Post by heyyy on 2009-07-01
> **shailendra said:**
> The simplest way would be to enable the auto upgrade feature in Firefox. It will prompt you to download and upgrade to the new version. Synaptic Manager shall do the rest.

...and how exactly am i going to do that?

---

### Post by steveneddy on 2009-07-01
I am on Hardy (an LTS) and just installed the ppa then apt-get install

it's very easy and keeps it up to date

---

### Post by treesurf on 2009-07-01
I'm a little confused.  Firefox 3.5 is now in the Jaunty repos.  If I install this will it politely replace my old Firefox install while still preserving all of my prefs, bookmarks, etc?  Or will it install it side by side with the old version?

---

### Post by lovinglinux on 2009-07-01
> **treesurf said:**
> I'm a little confused.  Firefox 3.5 is now in the Jaunty repos.  If I install this will it politely replace my old Firefox install while still preserving all of my prefs, bookmarks, etc?  Or will it install it side by side with the old version?

Side-by-side, but it will copy your profiles to ~/.mozilla/firefox-3.5, so you will be able to use your settings on both. Further modifications on a profile using FF 3.5 will not be saved on profiles using FF 3.

---

### Post by treesurf on 2009-07-01
Excellent. Thank you.

---

### Post by pickarooney on 2009-07-20
I just installed ff 3.5 from the repos and it's identifying itself as shiretoko instead of firefox. Is this normal?

---

### Post by Garyhans on 2009-07-20
Yes. By having a different name you can run the ealier FF side by side.

---

### Post by lovinglinux on 2009-07-21
> **pickarooney said:**
> I just installed ff 3.5 from the repos and it's identifying itself as shiretoko instead of firefox. Is this normal?

Yes. Look explanation at [http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html](http://www.asoftsite.org/s9y/archives/161-FAQ-Why-is-my-firefox-3.5-still-called-Shiretoko.html)

---

### Post by pickarooney on 2009-07-21
OK, I'll wat for karmic koala and just pick it up then; I don't see the need for two firefoxes.

---

### Post by bbrg548 on 2009-07-22
I've had the Ubuntuzilla setup for a while now, so I can run the 32 bit version of Firefox so Flash actually works (mostly) right. After I used "gksudo firefox" to run an upgrade from 3.0.11 to 3.5, Firefox wouldn't work. If I try to run "firefox" from the command line, I get:

```
/opt/firefox/firefox-bin: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory
```

If I run "firefox-3.0", I get the 64 bit version of 3.0.11, but Flash, YouTube, etc. don't work anymore (probably because it's 64 bit).

I've checked my /usr/lib/ directory, and libdbus-glib-1.so.2 is there (although it's a link to "libdbus-glib-1.so.2.1.0.bak" in the same directory).

Help?

---

