---
title: "Updating Firefox"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by pearsonb on 2010-04-12
I downloaded the new version of firefox and I have the package firefox-3.6.3.tar.bz2 in a folder in my documents.  The problem is I can't figure out how to install the program.  I've tried a couple of avenues recommended on "Installing Software" in ubuntu documentation.

First I installed GDebi, and then I'm supposed to double click on the package and install it with GDebi.  The problem is, although I've installed GDebi, when I click on the package it opens with archive manager and I just get a folder and series of folders within that.  If I right click I get options to open it with various programs, however, none of the programs are GDebi.


So now I figure out how to unpacked it.  But I still can't figure out how to install it.  What is the easiest way to update firefox?  And you'll have to explain it to me like I don't know what I'm doing, because I'm lost.  


Thanks for any help you can provide.

---

### Post by kellemes on 2010-04-13
I assume you're on Ubuntu 9.10 Karmic?
If so.. open a terminal-window.. to be found somewhere in the menu, now start typing..
Add the repository where this FF 3.6 is to be found..
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```
Update the source list..
```
sudo apt-get update
```
Now install FF 3.6..
```
sudo apt-get install firefox-3.6
```

Let us know if it works..

---

### Post by lovinglinux on 2010-04-13
> **kellemes said:**
> I assume you're on Ubuntu 9.10 Karmic?
If so.. open a terminal-window.. to be found somewhere in the menu, now start typing..
Add the repository where this FF 3.6 is to be found..
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```
Update the source list..
```
sudo apt-get update
```
Now install FF 3.6..
```
sudo apt-get install firefox-3.6
```

Let us know if it works..

Please see quote below:

> **lovinglinux said:**
> **[SIZE="4"]Attention Firefox 3.6.4 [Namoroka] ubuntu-mozilla-daily users![/SIZE]**

It seems this is a bug affecting only Firefox 3.6.4 [Namoroka] installed using the *ubuntu-mozilla-daily* ppa. The browser crashes when viewing pages with flash content or content for other plugins.

This problem is due to a bad/old implementation of the new Lorentz technology that should prevent flash from crashing the browser. When opening a page with flash content using Namoroka 3.6.4, there is a new *firefox-bin* process loaded and the browser crashes. 

[Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) doesn't behave like this and instead of loading a new *firefox-bin* process, it loads a *mozilla-runtime* process, which takes care of the flash content. It works like a charm and the browser doesn't crash or lock, even if you are viewing a messed up flash video.

So you have 3 options to fix your problem:

[LIST]
[*]disable *ubuntu-mozilla-daily* and reinstall Firefox to downgrade it to the default browser version
[*]temporarily turn off the flash process isolation following [these instructions](http://ubuntuforums.org/showpost.php?p=9104945&postcount=19)
[*]download [Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) and follow [these instructions](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3) to install it.
[/LIST]

There are some considerations about using a ppa repository for Firefox that I would like to highlight:
[LIST]
[*]some ppa repositories like *ubuntu-mozilla-daily* update not only Firefox, but also other Mozilla applications, like Thunderbird.
[*]some ppa repositories like ubuntu-mozilla-daily install development versions of Firefox which does not have the official branding (logo and name). Although they use essentially the same source code, the browser could be called Shiretoko, Namoroka or something else.
[*] some repositories like *mozillateam/firefox-stable* doesn&#8217;t seem to be updated frequently, thus missing important security patches.
[*]some repositories like *ubuntu-mozilla-daily* upgrade Firefox with unstable releases, sometimes causing issues, like crashing the browser in specific conditions or preventing it from starting.
[/LIST]

Please Before adding a ppa repository for Firefox, please make sure you understand how the repository works, which version it will install and how often it will provide updates.[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: Firefox optimization and troubleshooting thread[/color]]("http://ubuntuforums.org/showpost.php?p=9112875")

[*]**Tags:** [[color="DarkSlateGray"]Firefox optimization and troubleshooting thread[/color]]("http://www.google.com/search?q=Firefox+optimization+and+troubleshooting+thread+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by mk1w86 on 2010-04-13
> **pearsonb said:**
> I downloaded the new version of firefox and I have the package firefox-3.6.3.tar.bz2 in a folder in my documents.  The problem is I can't figure out how to install the program.  I've tried a couple of avenues recommended on "Installing Software" in ubuntu documentation.

First I installed GDebi, and then I'm supposed to double click on the package and install it with GDebi.  The problem is, although I've installed GDebi, when I click on the package it opens with archive manager and I just get a folder and series of folders within that.  If I right click I get options to open it with various programs, however, none of the programs are GDebi.


So now I figure out how to unpacked it.  But I still can't figure out how to install it.  What is the easiest way to update firefox?  And you'll have to explain it to me like I don't know what I'm doing, because I'm lost.  


Thanks for any help you can provide.

I would recommend you follow the suggestion posted by kellemes (EDIT:After seeing lovinglinux's post you might want to reconsider), but to run the file you currently have after extracting it double click on the file named firefox and click Run.  The Firefox version you downloaded from the Firefox website does not have to be installed because it runs straight from the directory.  You would normally place the Firefox directory in /opt so it can be used system wide, although you can run it from anywhere. ;)

---

### Post by lovinglinux on 2010-04-13
@pearsonb

You just need to extract the file and execute the firefox file inside it. Actually, there is no installation when you download it from Mozilla. See [method #1](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3) of the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for instructions.

If you are running a 32bit system, then I recommend using [Ubuntuzilla](http://ubuntuzilla.wiki.sourceforge.net/) instead of the ubuntu-mozilla-daily ppa suggested by kellemes. See why on my previous post.

---

### Post by snowpine on 2010-04-13
ubuntu-mozilla-daily will give you the current *testing* build of Firefox. If you are not an experienced Linux problem-solver, you might want to stick with the stable version: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

Another popular method to get the latest stable Firefox is Ubuntuzilla: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

A third and final method is to extract the "tarball" you've already downloaded with Archive Manager, then just double-click the Firefox executable to run it. It does not need to be "installed" and will not uninstall your current Firefox. I find this method clumsy, personally, but it is your computer. :)

edit: I also should mention, you do not *need* the latest Firefox from an outside source. The Ubuntu Update Manager will keep your Firefox up to date with security patches and bug fixes. Even though the version number never changes, the Firefox in the repositories does get important updates, for the lifespan of the release. This is true for all applications in Ubuntu, not just Firefox: they get bug fixes and security patches up until the release hits end-of-life. A common beginner mistake in Ubuntu is to add tons of 3rd party software sources, repositories, downloads, and PPAs they don't really need, ending up with a very unstable system. I am not accusing you of this, of course :) just something you should be cautious of.

---

### Post by philinux on 2010-04-13
One other problem with the daily ppa is the daily updates, no pun intended.

---

### Post by pearsonb on 2010-04-13
Excellent.  Thank you all for your trenchant advice and insight.  Given the options, I'll stick with my current version of firefox as long as it's supported, but now, once I make the plunge, I'll be ready.  Although I'm going to do more research next time I see some software trying to lure me into updating the version.  I appreciate all the help.

---

### Post by Otis Spunkmiyer on 2010-04-13
So, let me understand this.  When ever we see 'new updates' for this and that, it's not for some 'new' feature, but simply a security or bug fix  ?

---

### Post by mk1w86 on 2010-04-13
> **Otis Spunkmiyer said:**
> So, let me understand this.  When ever we see 'new updates' for this and that, it's not for some 'new' feature, but simply a security or bug fix  ?

Usually, but I think it depends on the application and what the update is.  Most updates though, are minor revisions e.g. Firefox 3.5.8 to 3.5.9 which are bugfixes and secuity fixes.

This assumes, of course, you are not upgrading to a later Ubuntu version where you would get updates that are major revisions e.g. Firefox 3.5 to 3.6.

The reason updates for a Ubuntu release throughout its life are not major revisions of software is for stability. ;)

---

### Post by snowpine on 2010-04-13
> **Otis Spunkmiyer said:**
> So, let me understand this.  When ever we see 'new updates' for this and that, it's not for some 'new' feature, but simply a security or bug fix  ?

Correct; any updates that would result in new features (such as from 3.5 to 3.6 or 3.6 to 4.0) are "lumped" together every 6 months into a new Ubuntu release. Most Linux distributions work this way; it means all the parts can be tested to work together, creating a stable release, as opposed to the "Windows Way" where applications are upgraded individually and separately from the operating system. :)

---

### Post by Steven_S on 2010-04-13
Thank you for these interesting notes! I was wondering why I didn't have Firefox 3.6 installed and where the "find updates" option went, but now I know :-).

In other words: if I want the latest versions, but not the beta's, I should add Ubuntuzilla to the repositories. It will be in the sources and will then tell me if there is a new stable version available (?).

If I want to not fix what ain't broken, I should just do nothing and let the Ubuntu update manager handle it. 

Did I get all that right?

---

### Post by lovinglinux on 2010-04-13
> **Steven_S said:**
> Thank you for these interesting notes! I was wondering why I didn't have Firefox 3.6 installed and where the "find updates" option went, but now I know :-).

In other words: if I want the latest versions, but not the beta's, I should add Ubuntuzilla to the repositories. It will be in the sources and will then tell me if there is a new stable version available (?).

If I want to not fix what ain't broken, I should just do nothing and let the Ubuntu update manager handle it. 

Did I get all that right?

Pretty much. Please note that Ubuntuzilla in particular, will not upgrade your current Firefox, but install a second version that runs independently. Other ppa repositories behavior is usually to upgrade your software, instead of installing another version. Nevertheless, the opposite might happen depending on the software and the ppa.

---

### Post by snowpine on 2010-04-13
> **lovinglinux said:**
> Pretty much. Please note that Ubuntuzilla in particular, will not upgrade your current Firefox, but install a second version that runs independently. Other ppa repositories behavior is usually to upgrade your software, instead of installing another version. Nevertheless, the opposite might happen depending on the software and the ppa.

For me, on my machine, Ubuntuzilla replaced my existing Firefox.

---

### Post by lovinglinux on 2010-04-13
> **snowpine said:**
> For me, on my machine, Ubuntuzilla replaced my existing Firefox.

No, it doesn't. 

> From [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Technical_Details](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Technical_Details)

The packages are named firefox-mozilla-build, thunderbird-mozilla-build, and seamonkey-mozilla-build.Upon installation, the actual binaries are installed into /opt/(firefox|thunderbird|seamonkey), a link is placed into /usr/bin/(firefox|thunderbird|seamonkey), and the same link from the Ubuntu-repositories version of these packages is diverted to /usr/bin/(firefox|thunderbird|seamonkey).ubuntu.A menu shortcut is also created, which places an item named Mozilla Build of (Firefox|Thunderbird|Seamonkey) into the Applications -> Internet menu.

---

### Post by snowpine on 2010-04-13
> **lovinglinux said:**
> No, it doesn't.

Maybe "replaced" is the wrong word, but typing 'firefox' at the command line definitely launches the new Ubuntuzilla version, not the Ubuntu repository version, for me, on my computer. :) If the old Firefox is still there somewhere, I do not know how to launch it.

---

### Post by lovinglinux on 2010-04-13
> **snowpine said:**
> Maybe "replaced" is the wrong word, but typing 'firefox' at the command line definitely launches the new Ubuntuzilla version, not the Ubuntu repository version, for me, on my computer. :)

Yes. It does "replace" the default Firefox in your system , but does not upgrade the existing packages :)

---

