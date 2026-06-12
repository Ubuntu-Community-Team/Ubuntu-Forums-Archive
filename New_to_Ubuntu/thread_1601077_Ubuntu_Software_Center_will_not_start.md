---
title: "Ubuntu Software Center will not start"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by hurt.david on 2010-10-19
I click on "software center" in the applications menu and nothing happens.   The circle appears and the window appears below with the application name.  But instead of opening it disappears.   There is no error message and I am not sure where to look.  I have not been able to locate info about this problem as I am beyond a newbie.  I just installed 10.10 somehow...

---

### Post by Paul820 on 2010-10-19
Try starting it through the terminal, if any errors are there it will show them.
Applications-Accessories->Terminal
Then enter this:
> software-center

---

### Post by robsoles on 2010-10-19
Welcome to UF.

Depending on what response you get from Paul820's suggestion in terminal you might try an update via terminal and let us know what error messages (if any) that causes.
```
sudo apt-get update
sudo apt-get upgrade
```
If no errors from updating but software-center didn't open for Paul820's command then you might just try uninstalling and reinstalling software-center
```
sudo aptitude purge software-center
sudo aptitude -f install software-center
```
That may mention removing 'ubuntu-desktop' and if that isn't restored by the install command you want to restore that so distro upgrades still work:
```
sudo apt-get install ubuntu-desktop
```

HTH, let us know please.

---

### Post by hurt.david on 2010-10-20
I tried the two suggestions and finally received this error message:  

SystemError: E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/archive.canonical.com_dists_maverick_partner_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

I am not sure if I should submit as a 'bug' or not.  I tried the 'purge' command and received a 'command not found' message, but no error message followed.  

Immediately after I installed maverick i added some of the educational programs including edubuntu.   Could this be a cause?

Thank you very much for the quick response and help!!!!!:)

---

### Post by robsoles on 2010-10-20
Would you please look at [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode) and find the [noparse]```
[/noparse] example and try to use code tags to show us the results of the commands, like example:
[code]rob@example:~$ sudo apt-get update
[sudo] password for rob:
Hit http://au.archive.ubuntu.com lucid Release.gpg
Get:1 http://au.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_AU [1,813B]
Get:2 http://au.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_AU [2,407B]
Ign http://au.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_AU
Get:3 http://au.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_AU [91.6kB]
Get:4 http://au.archive.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com lucid Release
Get:5 http://au.archive.ubuntu.com lucid-updates Release [44.7kB]
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_AU
Hit http://download.webmin.com sarge Release.gpg
Hit http://au.archive.ubuntu.com lucid/main Packages
Hit http://au.archive.ubuntu.com lucid/restricted Packages
Hit http://au.archive.ubuntu.com lucid/main Sources
Hit http://au.archive.ubuntu.com lucid/restricted Sources
Hit http://au.archive.ubuntu.com lucid/universe Packages
Hit http://au.archive.ubuntu.com lucid/universe Sources
Hit http://au.archive.ubuntu.com lucid/multiverse Packages
Hit http://au.archive.ubuntu.com lucid/multiverse Sources
Get:6 http://au.archive.ubuntu.com lucid-updates/main Packages [333kB]
Get:7 http://security.ubuntu.com lucid-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_AU
Hit http://archive.canonical.com lucid Release
Hit http://archive.canonical.com lucid/partner Packages
Get:8 http://au.archive.ubuntu.com lucid-updates/restricted Packages [3,267B]
Get:9 http://au.archive.ubuntu.com lucid-updates/main Sources [130kB]
Ign http://download.webmin.com/download/repository/ sarge/contrib Translation-en_AU
Get:10 http://au.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]
Get:11 http://au.archive.ubuntu.com lucid-updates/universe Packages [141kB]

Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_AU
Hit http://download.webmin.com sarge Release
Get:12 http://au.archive.ubuntu.com lucid-updates/universe Sources [54.7kB]
Get:13 http://au.archive.ubuntu.com lucid-updates/multiverse Packages [7,072B]
Get:14 http://au.archive.ubuntu.com lucid-updates/multiverse Sources [3,678B]
Ign http://download.webmin.com sarge/contrib Packages
Ign http://download.webmin.com sarge/contrib Packages
Hit http://download.webmin.com sarge/contrib Packages
Get:15 http://security.ubuntu.com lucid-security Release [38.5kB]
Get:16 http://security.ubuntu.com lucid-security/main Packages [93.0kB]
Get:17 http://security.ubuntu.com lucid-security/restricted Packages [14B]
Get:18 http://security.ubuntu.com lucid-security/main Sources [33.4kB]
Get:19 http://security.ubuntu.com lucid-security/restricted Sources [14B]
Get:20 http://security.ubuntu.com lucid-security/universe Packages [45.9kB]
Get:21 http://security.ubuntu.com lucid-security/universe Sources [11.8kB]
Get:22 http://security.ubuntu.com lucid-security/multiverse Packages [1,869B]
Get:23 http://security.ubuntu.com lucid-security/multiverse Sources [656B]
Fetched 1,040kB in 10s (95.7kB/s)
Reading package lists... Done
rob@example:~$
```
Only, please do Paul820's one first, please show us the verbatim output from your system:```
software-center
```(If that output doesn't look very interesting to you then please show us anyway but also show us the verbatim output from 'sudo apt-get update' as well).

---

### Post by hurt.david on 2010-10-20
Robsoles - thank you  for helping.

I ran 'software center' and this is this error message.  I am going to follow your other message now.

Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 105, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 88, in __init__
    self.open(progress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 126, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_dists_maverick_partner_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 316, in __init__
    self.view_switcher = ViewSwitcher(self.view_manager, datadir, self.db, self.cache, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 59, in __init__
    store = ViewSwitcherList(view_manager, datadir, db, cache, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 321, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 395, in _update_channel_list
    self._update_channel_list_installed_view()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 448, in _update_channel_list_installed_view
    if (pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 128, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'

---

### Post by hurt.david on 2010-10-20
Here is message from 'sudo .... update'

middletown@mid:~$ 
middletown@mid:~$ sudo apt-get update
[sudo] password for middletown: 
E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
middletown@mid:~$ 


This looks identical to the terminal formatting.

Thank you :)

---

### Post by Paul820 on 2010-10-20
Did some digging for you. Here is a link that will remove corrupted files.
[http://www.go2linux.org/problem-upgrading-debian-Couldnt-rebuild-package-cache]("http://www.go2linux.org/problem-upgrading-debian-Couldnt-rebuild-package-cache")
After that run
> sudo apt-get update
To get your sources again, then run
> sudo apt-get upgrade

---

### Post by hurt.david on 2010-10-22
I ran the 'go2linux' command and then entered the command to update and then upgrade.  I received the same error message.

E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)

This is a recurring error message that I think is related to the software center problem I am having.   I tried to search in the forum for this error, but I am sure I am looking for the wrong item.   I have entered variations of 'malformed line, line 61, the entire line' and cannot find anything.   

Any suggestion on how to look up this error?

---

### Post by Paul820 on 2010-10-22
Then you need to show us the contents of your sources.list. Open a terminal and enter this
> gksudo gedit /etc/apt/sources.list

Then copy and paste the contents on here.

---

### Post by robsoles on 2010-10-22
If interested to see if you can recognize the problem on the line yourself, go to 'edit'->'preferences' in gedit and turn on 'Line Numbers'-'Display line numbers', while you have the file open by using Paul820's command.

Scroll down to line 61 and compare it to lines above it, it is well worth your while to paste the contents of the file here if you can't see the problem or if the problem is that the file is empty from partway through line 61 - it will help a fair deal if you use

[noparse]```
<paste file content here>
```[/noparse]

to post it, when you 'submit reply' it will come out like this```
<pasted file content here>
```

---

### Post by hurt.david on 2010-10-28
Sorry -  have been out of town last week.....

Here is what I get from pulling code.

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
##deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb hppt://blognux.free.fr/ubuntu hardy main
deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardymain
deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardymain
deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main

---

### Post by n0obie on 2011-02-04
exactly same problem.

here is my source.list

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick main restricted
deb-src [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-updates main restricted
deb-src [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick universe
deb-src [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick universe
deb [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-updates universe
deb-src [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick multiverse
deb-src [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick multiverse
deb [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-updates multiverse
deb-src [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-security main restricted
deb-src [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-security main restricted
deb [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-security universe
deb-src [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-security universe
deb [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-security multiverse
deb-src [http://ubuntuarchive.hnsdc.com/ubuntu/](http://ubuntuarchive.hnsdc.com/ubuntu/) maverick-security multiverse
deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) maverick main
deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) maverick main non-free
deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) maverick main non-free
Reading package lists...
Building dependency tree...
Reading state information...
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) maverick main non-free
# deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
# deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) maverick main non-free

----------------------

installed ubuntu four times in 2 days.
I would really appreciate some help before i did clean install again :/

-n00bie thanks you ):P
:lolflag: me

---

### Post by robsoles on 2011-02-04
> **n0obie said:**
> exactly same problem.

...

<edited-in>Welcome to UF!</edited-in>

I don't think so. I wish I had spotted it before but the OP's problem was that they had '##deb-src' at the start of what comes to line 58 if you copy and paste their text into gedit.

I remember copy and pasting it 'back then' but line 61 in gedit looked perfectly good so I decided I didn't know enough to post back at the time.

Your file does not appear malformed. When you run the commands given, from post #2 down, what error messages do you get?

The line in OP's copy of the file is malformed because the '#' marks aren't interpreted as a comment until they are followed by a space and then everything after them, on that line, is ignored and process goes on to the next line.

Seriously, run the command given in post #2 above and consider starting a new thread when you identify your problem properly.

Also, please pay attention to where I talk about [noparse][code][/noparse] tags because it really does help when working on such problems.

---

### Post by robsoles on 2011-02-04
If the stuff I've made bold below in my quote is actually in the file at /etc/apt/sources.list then you need to delete the bold stuff for sure (and your problem is practically exactly the same, sorry about that :))

> **n0obie said:**
> ...

deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) maverick main non-free
[B]Reading package lists...
Building dependency tree...
Reading state information...
[/B]deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) maverick main non-free
# deb [http://buc.billera.eu/ubuntu/](http://buc.billera.eu/ubuntu/) binary/
# deb [http://www.sourceslist.eu/repo/ubuntu](http://www.sourceslist.eu/repo/ubuntu) maverick main non-free

...

---

