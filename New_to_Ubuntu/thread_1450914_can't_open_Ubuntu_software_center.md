---
title: "can't open Ubuntu software center"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by telltom on 2010-04-09
When i try to open it, it closes immediately. This just started happening today. I wanted to download Alarm-clock, so i got it from the synoptic package manager instead.

---

### Post by tom.swartz07 on 2010-04-09
> **telltom said:**
> When i try to open it, it closes immediately. This just started happening today. I wanted to download Alarm-clock, so i got it from the synoptic package manager instead.

Try opening it from the terminal and see what prints out.

Open the terminal from Applications>Accessories>Terminal

then type
```
gksudo software-center
```

If it does the same thing, you will at least have a text output of the error. Post it back here.

---

### Post by telltom on 2010-04-11
I turned off the computer this morning, later i was able to open it without a problem. It must have needed a reboot for some strange reason. thanks..

---

### Post by Razor338 on 2010-12-29
i have the same problem,here's what i get when open i open it from the terminal!


 self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 88, in __init__
    self.open(progress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 130, in open
    self._list.read_main_list()
SystemError: E:Type '&#8206;eb' is not known on line 60 in source list /etc/apt/sources.list
2010-12-29 01:39:05,533 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 96, 'open')'
2010-12-29 01:39:05,532 - root - WARNING - failed to add sca db Couldn't detect type of database
Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 316, in __init__
    self.view_switcher = ViewSwitcher(self.view_manager, datadir, self.db, self.cache, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 59, in __init__
    store = ViewSwitcherList(view_manager, datadir, db, cache, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 321, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 399, in _update_channel_list
    self._update_channel_list_installed_view()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 452, in _update_channel_list_installed_view
    if (pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 128, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'

---

### Post by matt_symes on 2010-12-29
Hi

Open a terminal and type

```
cat /etc/apt/sources.list
```

Post the output back here.

Kind regards

---

### Post by Razor338 on 2010-12-29
herez what i got!!


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
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) maverick main ## Cairo-Dock-PPA-Stable
eb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator

---

### Post by Razor338 on 2010-12-29
i can't even update ubuntu,and wine is not working either!!(i can't open any exe files)

---

### Post by matt_symes on 2010-12-29
Hi

Have a look at your post where you posted /etc/apt/sources.list.
Look at the bottom and see the lines..

```
deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu maverick main ## Cairo-Dock-PPA-Stable
eb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```

Well the second one

```
eb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```

wants to be

```
**d**eb http://download.tuxfamily.org/syzygy42/ gutsy avant-window-navigator
```

To fix open a terminal and type

```
sudo nano /etc/apt/sources.list
```

Enter your password. Use the down arrow keys to get to the line and add the **d**

Press ctrl + o to save and ctrl + x to exit. (that is small O)

**EDIT:** deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) **gutsy** avant-window-navigator
That is for gusty. Not what you want to be using anyhow.

Have a look at this

[http://www.unixmen.com/linux-distributions/4/1200-install-cairo-dockawn-and-docky-in-ubuntu1010-maverick-meerkat](http://www.unixmen.com/linux-distributions/4/1200-install-cairo-dockawn-and-docky-in-ubuntu1010-maverick-meerkat)

Kind regards

---

### Post by matt_symes on 2010-12-29
Hi

To run wine programs make sure the exe file has executable permissions.

Kind regards

---

### Post by Razor338 on 2010-12-29
I did exactly as you said,but the problem still exist,i'll restart my pc and tell you whether the problem has been solved or not.

---

### Post by Razor338 on 2010-12-29
the problem is not solved,and when i try to update i get this error!

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '&#8206;deb' is not known on line 60 in source list /etc/apt/sources.list'

> E: Type '&#8206;deb' is not known on line 60 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.




---

### Post by matt_symes on 2010-12-29
Hi

> EDIT: deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
That is for gusty. Not what you want to be using anyhow.

Have a look at this

[http://www.unixmen.com/linux-distrib...verick-meerkat](http://www.unixmen.com/linux-distrib...verick-meerkat)

Above quote is my edit to my post and i don't think i made myself clear. Plus it is a malformed source.

Gusty is old, very old, and is no longer supported.

Use nano again to _remove_ that line from /etc/apt/sources.list (line 60 the one with gusty in it) and save the file as before.

Use the above link to install docky, cairo or awn the correct way in maverick.

Kind regards

---

### Post by Razor338 on 2010-12-29
i'll try it and inform you the results!

---

### Post by Razor338 on 2010-12-29
it worked,thanx for your help!

once i deleted gusty source line and tried to open software centre,but it didnt work.after that, i deleted the  cairo source line which  is the 60th line as your mentioned,then it worked.anyway thanx for your great help!

---

### Post by matt_symes on 2010-12-29
Hi

No worries. Remember what is said about wine and exe files.

Also, mark the thread as solved to help others searching for a solution.

Kind regards

---

### Post by Razor338 on 2010-12-29
dude,im not the one who started this thread,so i think,im not allowed to mark it as solved,right?

---

### Post by matt_symes on 2010-12-29
> **Razor338 said:**
> dude,im not the one who started this thread,so i think,im not allowed to mark it as solved,right?

Blimy. I have just noticed that (well it is 8.00 in the morning here)

---

### Post by Aznpope on 2011-03-10
Hi, I seem to be having a similar problem but my computer never was ale to open the software center. I installed the YLMF OS

rom softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 34, in <module>
    from softwarecenter.backend.channel import SoftwareChannel
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 22, in <module>
    from softwarecenter.distro import get_distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 88, in <module>
    distro_instance=_get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 77, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named Ylmf_OS
aznpope@aznpope-laptop:~$ ^C
 canbu help? thanks alot

---

### Post by matt_symes on 2011-03-11
Hi

> **Aznpope said:**
> Hi, I seem to be having a similar problem but my computer never was ale to open the software center. I installed the YLMF OS

rom softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 34, in <module>
    from softwarecenter.backend.channel import SoftwareChannel
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 22, in <module>
    from softwarecenter.distro import get_distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 88, in <module>
    distro_instance=_get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 77, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named Ylmf_OS
aznpope@aznpope-laptop:~$ ^C
 canbu help? thanks alot

Blimy. It's window XP !!!!!!!!

Next time it's probably best to start a new thread. 

I know absolutely nothing about the UI on this distro.

Can you get to a terminal ? If so open it and type

```
sudo apt-get update
```

Post back results.

Understand i am only assuming that will work as it's based on Ubuntu.

Kind regards

---

### Post by Alarmist on 2011-03-16
hi there,

im very new in ubuntu
i just use this lovely 10.10 version 2 weeks ago
pretty nice!!

now i just finish install docky
but get error in software center and update manager

here the result when i do 
> sudo apt-get update

E: Type '.net/tualatrix/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
E: The list of sources could not be read.

this is the source for cat /etc/apt/sources.list

> # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
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

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse


anyone can help, very love to hear any response
TQ

---

### Post by matt_symes on 2011-03-16
Hi

Post the output of

```
cat /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
```

Kind regards

---

### Post by Alarmist on 2011-03-17
> root@ubuntu:/home/alarmist# cat /etc/apt/sources.list.d/tualatrix-ppa-maverick.list

deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) maverick main #Ubuntu Tweak Stable Source
.net/tualatrix/ppa/ubuntu maverick main

this is the result
thanks for ur response matt

---

### Post by matt_symes on 2011-03-17
Hi

```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu maverick main #Ubuntu Tweak Stable Source
.net/tualatrix/ppa/ubuntu maverick main
```

That second line is what is causing you the problem.

Open a terminal and type 

```
sudo nano /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
```

Put a # in front of the bottom line so it becomes

```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu maverick main #Ubuntu Tweak Stable Source
#.net/tualatrix/ppa/ubuntu maverick main
```

Press Ctrl + o to save the file and ctrl + x to exit nano.

Then try the software centre again

Kind regards

---

### Post by Alarmist on 2011-03-17
thanks matt_symes
its work now
thanks a lot for ur help, really appreciate!

---

### Post by Ireallyneedhelp on 2011-03-27
I have just downloaded Ubuntu a few days ago and am having mega problems knowing what to do once I've downloaded a program. I extracted the file but then what? I had a look at "Ubuntu Software Center" and it won't open. I tried accessing it using details from one of the earlier posts with no joy.

(Apart from the hassle of not being able to do a Skype video call or access my Voipcheap account (I've tried to do this by reading other posts) I am enjoying the somewhat steep learning curve.

Thanks in advance:D

---

### Post by matt_symes on 2011-03-27
Hi

> **Ireallyneedhelp said:**
> I have just downloaded Ubuntu a few days ago and am having mega problems knowing what to do once I've downloaded a program. I extracted the file but then what? I had a look at "Ubuntu Software Center" and it won't open. I tried accessing it using details from one of the earlier posts with no joy.

What software are you trying to install ? What happens when you open the software centre ? What error messages are displayed ?

Open a terminal and type 

```
sudo apt-get update
```

Enter your password.It will not be echoed to the screen. This is normal. Use copy and paste to post your results back here.

> 
(Apart from the hassle of not being able to do a Skype video call or access my Voipcheap account (I've tried to do this by reading other posts) I am enjoying the somewhat steep learning curve.

Thanks in advance:D

What have you done so far regarding Skype ?

I will not be able to look at this until tomorrow as i have guest here.

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-27
1 Thanks for the response. I don't get an error message. The software centre just won't open. I have the spinning disc then nada.

2 I typed the code and got the following:-
nerja@ubuntu:~$ sudo apt-get update
[sudo] password for nerja: 
E: Type ‘--2011-03-27’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

3 I downloaded the Skype beta - latest version. It works but without video.

4 The program I tried to download was a version of Skype mentioned on another thread here.
I downloaded it ... extracted it ... then I'm at a loss. The Skype version I have is still the same as the program that came with Ubuntu.

5 Thanks again for your post but please don't feel you have to dedicate your time! I am in Spain and probably a different time zone, so there's no rush. Enjoy your guests.

(I am a complete novice with Linux. I'm OK with Windows but I'm cheesed off waiting as my boot time with windows  is over 2 minutes. Security check is another 2 minutes. I then click Firefox and wait another couple of minutes. I'm impressed with Ubuntu as I'm up and running in under 30 seconds).

---

### Post by Christopher V. on 2011-03-28
Hello everyone! Normally I am able to find a solution to my Ubuntu related problems by referencing existing material, but I was unable to do so in this case. I will try and provide as much information as possible to assist you all in helping me to solve my problem.

I'm a relatively new Ubuntu user who is having some trouble with Ubuntu 10.10 64bit and the following three programs:

Update Manager

Synaptic Package Manager

Ubuntu Software Center



Some basic system details:
[Asus G73JW-A1]("http://www.amazon.com/G73JW-A1-Republic-Gamers-17-3-Inch-Gaming/dp/B0041RRS0I/ref=sr_1_2?ie=UTF8&qid=1301294246&sr=8-2")
Intel Core i7-740QM
Nvidia GTX 460M Graphics with 1.5GB GDDR5
8GB DDR3 1333MHz
TB Hybrid HDD/SSD (2x 500G 7200RPM/4GB SSD)


When I first installed 10.10, I had no troubles getting any of the above mentioned programs to work. I was able to successfully download and install the Nvidia drivers with no problem. 

However, after a few more days of using my Ubuntu installation with no problems I found that Ubuntu Software Center had ceased to work. When I attempt to click on it, it shows on the bottom bar as loading, but never actually does and eventually completely disappears from the bottom bar without any error notice. 

Both Update Manager and Synaptic Package Manager ceased to work at the same time.

Attempting to run Synaptic Package Manager returns this message:
 E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)  
 E: The list of sources could not be read.  
 Go to the repository dialog to correct the problem.  
 E: _cache->open() failed, please report
 

 Attempting to run Update Manager returns this message:
 

 Could not initialize the package information  
 An unresolvable problem occurred while initializing the package information.  
 Please report this bug against the 'update-manager' package and include the following error message:  
 'E:Malformed line 61 in source list /etc/apt/sources.list (dist parse)'
 

 Running 'sudo apt-get update' returns this message:
 

 E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)  
 E: The list of sources could not be read."
 

And since there's been a lot of:
 


 cat /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
 


 going around, here's the output from my terminal:
 


 cat: /etc/apt/sources.list.d/tualatrix-ppa-maverick.list: No such file or directory
 


 The closest other mention I could find to my issue was in [this thread.]("http://ubuntuforums.org/showthread.php?p=8654075")

Although the bug in question didn't seem close enough to my own issue to allow me to find a solution from that thread, I did run the same script that was suggested. I don't know if it will help, but it certainly can't hurt:
 more /etc/apt/sources.list
 

 Which returns:
 

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
 

 ## Uncomment the following two lines to add software from Ubuntu's  
 ## 'extras' repository.  
 ## This software is not part of Ubuntu, but is offered by third-party  
 ## developers who want to ship their latest software.  
 # deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main  
 # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main  
 

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted  
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe  
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse  
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse  
 deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) main  
 deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) main  
 

 

 

 I would be very appreciative if anyone could help me with my issue.


And separately, if someone could tell me how to post terminal output in the code boxes, I would also appreciate it.

---

### Post by matt_symes on 2011-03-28
Hi

> **Ireallyneedhelp said:**
> 1 Thanks for the response. I don't get an error message. The software centre just won't open. I have the spinning disc then nada.

2 I typed the code and got the following:-
nerja@ubuntu:~$ sudo apt-get update
[sudo] password for nerja: 
E: Type ‘--2011-03-27’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

3 I downloaded the Skype beta - latest version. It works but without video.

4 The program I tried to download was a version of Skype mentioned on another thread here.
I downloaded it ... extracted it ... then I'm at a loss. The Skype version I have is still the same as the program that came with Ubuntu.

5 Thanks again for your post but please don't feel you have to dedicate your time! I am in Spain and probably a different time zone, so there's no rush. Enjoy your guests.

(I am a complete novice with Linux. I'm OK with Windows but I'm cheesed off waiting as my boot time with windows  is over 2 minutes. Security check is another 2 minutes. I then click Firefox and wait another couple of minutes. I'm impressed with Ubuntu as I'm up and running in under 30 seconds).

Sorry for the late reply. As i said, i have had friends around over the weekend.

First things first. Please post the output of (copy and paste from a terminal)

```
cat /etc/apt/sources.list.d/medibuntu.list
```

It is in that file where the problem lies.

Second, could you post a link to the Skype beta you downloaded. I will install it on my machine and tell you how i did it.

Could you also post the output of 

```
xinput --list
```

for the web cam. Is the web can a built in web cam ?

Kind  regards

---

### Post by matt_symes on 2011-03-28
Hi

> **Christopher V. said:**
> Hello everyone! Normally I am able to find a solution to my Ubuntu related problems by referencing existing material, but I was unable to do so in this case. I will try and provide as much information as possible to assist you all in helping me to solve my problem.

I'm a relatively new Ubuntu user who is having some trouble with Ubuntu 10.10 64bit and the following three programs:

Update Manager

Synaptic Package Manager

Ubuntu Software Center  

...

And separately, if someone could tell me how to post terminal output in the code boxes, I would also appreciate it.

Open a terminal and type 

```
sudo nano /etc/apt/sources.list
```

Scroll right down to the bottom where you will see.

```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu main 
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu main
```

These are the 2 lines causing you problems. You can either remove them, comment them out by putting a hash in front of them as in

```
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu main 
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu main
```

or you can fix them

```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu maverick main
```

Press ctrl + o to save the file and ctrl + x to exit.

after that type

```
sudo apt-get update
```

To use code blocks on the forums highlight the text you want to appear in code blocks and hit the # button on the screen above where you type. It's next to the quote button.

Failing that you can type the tags themselves

```
 text goes here [/code**}** 

The last bracket must also be a square bracket.

To copy and paste from the terminal, hightlight the text and use 

[code]shift + ctrl + c
``` 

to copy and 

```
shift + ctrl+ v
``` 

to paste into the terminal..The terminal requires the shift and ctrl keys to be pressed at the same time. For everything else it's just ctrl + c and ctrl + v.

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-28
Thanks Matt. Here's the error I got-
nerja@ubuntu:~$ cat /etc/apt/sources.list.d/medibuntu.list
--2011-03-27 12:10:37--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 88.191.127.22
Connecting to [www.medibuntu.org|88.191.127.22|:80](www.medibuntu.org|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-03-27 12:10:38 ERROR 404: Not Found.

---

### Post by Ireallyneedhelp on 2011-03-28
X-input list shows ...

nerja@ubuntu:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; zc3xx                                       id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]


Regarding the SKYPE, it was the one with Ubuntu. It works fine but without video.
To expand this a bit further, I use Voipcheap to phone certain landlines (family without computers). I contacted Voipcheap to ask if I could use their service wit Ubuntu. They suggested I download "Linphone" but in order to use the Voipcheap service, I also had to download X-lite. The trouble here is that the X-lit page only shows downloads for Windows and MAC.

Should I give up and buy Windows 7?:confused:

PS ... Linphone said I had to change from IPv6 to IPv4. Would there be problems with this?

---

### Post by matt_symes on 2011-03-28
Hi

> **Ireallyneedhelp said:**
> Thanks Matt. Here's the error I got-
nerja@ubuntu:~$ cat /etc/apt/sources.list.d/medibuntu.list
--2011-03-27 12:10:37--  [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 88.191.127.22
Connecting to [www.medibuntu.org|88.191.127.22|:80](www.medibuntu.org|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-03-27 12:10:38 ERROR 404: Not Found.

I'll tackle your first post first.

That file is completely broken and contains no valid data so we might as well delete it. Open a terminal and type

```
sudo mv /etc/apt/sources.list.d/medibuntu.list ~/
sudo apt-get update
```

Enter you password.It will not be echoed to the screen. This is normal. If you get no errors type

```
sudo rm ~/medibuntu.list
```

I  will have a look at you second post a bit later.

Kind regards

---

### Post by matt_symes on 2011-03-28
Hi

> **Ireallyneedhelp said:**
> X-input list shows ...

nerja@ubuntu:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                  id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; zc3xx                                       id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]


Regarding the SKYPE, it was the one with Ubuntu. It works fine but without video.
To expand this a bit further, I use Voipcheap to phone certain landlines (family without computers). I contacted Voipcheap to ask if I could use their service wit Ubuntu. They suggested I download "Linphone" but in order to use the Voipcheap service, I also had to download X-lite. The trouble here is that the X-lit page only shows downloads for Windows and MAC.

Should I give up and buy Windows 7?:confused:

PS ... Linphone said I had to change from IPv6 to IPv4. Would there be problems with this?

Is your web cam built in or is it USB ? What is the make and model ?

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-28
Matt. You're a star.:KS Software back. I'm now reading one of the recommended books about Ubuntu.
I'll plough my way through it and try to solve my own problems - eventually.

Re Skype ... My camera is a "Creative" with a USB. No idea of the model but it cost around &#8364;25.
 (around $35)

(That's around 20 pounds - I just noticed you're in Bristol)

---

### Post by matt_symes on 2011-03-28
Hi

Plug in your usb web cam. Open a terminal and type

```
lsusb
```

Post the results back here.

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-28
> **matt_symes said:**
> Hi

Plug in your usb web cam. Open a terminal and type

```
lsusb
```Post the results back here.

Kind regards

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 041e:4034 Creative Technology, Ltd Webcam Instant
Bus 002 Device 002: ID 03f0:7e04 Hewlett-Packard DeskJet F4100 Printer series
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by matt_symes on 2011-03-28
Hi

The web cam hardware is being recognised so that is good. 

I did expect to see it mentioned using xinput --list and it's not. That may or may not be good. My laptop has a built in webcam so maybe built in webcams are handled differently.

I think the first thing i would do is to install Cheese and see if that recognises the web cam. That way we can narrow down what the  problem might be. If cheese recognises your web cam then it's a Skype issue. If not it's probably an issue with Ubuntu and the web cam and we can check that out.

```
sudo apt-get install cheese
```

You will find it under "sound and video" menu.

Kind regards

---

### Post by Christopher V. on 2011-03-28
```
Thank you Matt, problem solved.
```

---

### Post by matt_symes on 2011-03-29
Hi

> **Christopher V. said:**
> ```
Thank you Matt, problem solved.
```

That's good news :D. 

How did you solve it ?

Kind regards

---

### Post by Christopher V. on 2011-03-29
I decided to manually enter 'maverick' into the last few lines in the terminal. All three programs now open and do their thing which allowed me to update. 

Now I'm having trouble getting WINE to download and install correctly despite having followed the instructions provided on their site for installing WINE onto Ubuntu. 

After adding the source that the WINE website instructed, I attempted to install WINE through Software Center. I received this message in return:

Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?

Which doesn't do anything except bring up the same window again a few seconds later. 

I then tried to use the terminal.

```
viveros@viveros-G73Jw:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
 [sudo] password for [---]: password
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```I'm not exactly sure what to do with this...but WINE still isn't installed. I can't seem to find a simple .deb download location anywhere. 

If this isn't related to my previous Software Center problem, I will start another thread instead of making this one too OT.

---

### Post by matt_symes on 2011-03-29
Hi

Is it only wine that will not install ? Are other programs now installing correctly ?

What version of wine are you trying to install ?

Can you post the link you have been following.

Kind regards

---

### Post by Christopher V. on 2011-03-29
To test if it was just WINE, I failed to install Python 3.1 through Software Center.

Just to double check, I restarted the computer and attempted to reinstall both programs.

And success! Apparently I needed a simple restart after updating (which isn't something I thought you needed to do with Linux, but I'm a newb so eh).

Thanks for your help!

Oh, and it was the WINE 1.3 beta package. Instructions for which I got [here]("http://www.winehq.org/download/deb").

---

### Post by Ireallyneedhelp on 2011-03-29
Matt
Good morning sir. Cheese works fine - as does Linphone. Both show my big ugly  baw heid. 
Skype is fine for audio calls and for seeing other people when I'm on a call. They of course can't see me.
Perhaps Skype is the problem in Ubuntu.

I'm really trying to get Voipcheap to work. According to Voipcheap, if I download Linphone (I have and it works) I should be able to use my Voipcheap account once I've downloaded X-lite. When I go to the X-lite page there doesn't appear to be a download for Ubuntu - only windows or Mac. Aaargh!

---

### Post by matt_symes on 2011-03-29
Hi

> **Christopher V. said:**
> To test if it was just WINE, I failed to install Python 3.1 through Software Center.

Just to double check, I restarted the computer and attempted to reinstall both programs.

And success! Apparently I needed a simple restart after updating (which isn't something I thought you needed to do with Linux, but I'm a newb so eh).

Thanks for your help!

Oh, and it was the WINE 1.3 beta package. Instructions for which I got [here]("http://www.winehq.org/download/deb").

That is great news. I'm glad it's fixed. :D

Occasionally Ubuntu does need rebooting. Well saying that it is generally a quick way to fix some problems. Mostly they can be fixed without a reboot.

Kind regards

---

### Post by matt_symes on 2011-03-29
Hi

> **Ireallyneedhelp said:**
> Matt
Good morning sir.

Good morning to you to :D

> Cheese works fine - as does Linphone. Both show my big ugly  baw heid. 
Skype is fine for audio calls and for seeing other people when I'm on a call. They of course can't see me.
Perhaps Skype is the problem in Ubuntu.

Yes. That does rather point to an issue with skype. What version of skype are you using ?

> I'm really trying to get Voipcheap to work. According to Voipcheap, if I download Linphone (I have and it works) I should be able to use my Voipcheap account once I've downloaded X-lite. When I go to the X-lite page there doesn't appear to be a download for Ubuntu - only windows or Mac. Aaargh!

I don't know much about voipcheap but it may be possible to run  X-lite through wine.

I will do some research for you.

[B]EDIT:

Can you post a link to the site you are trying to download the  software from ?[/B]

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-29
I'm using the latest Beta version of Skype for Ubuntu.
(No rush Matt to solve my ever-growing problems! I'm off for a walk along the coast to get rid of the cobwebs. Looks like 22ºF today).

---

### Post by matt_symes on 2011-03-29
Hi

Well according to this site

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

your web cam...

> Bus 002 Device 003: ID 041e:4034 Creative Technology, Ltd Webcam Instant

should work out the box on 8.04. I assume you are not using that any more. There may be a tweek we can use.

> Creative Instant P0620 8.04 041e:4034 gspca Works out of the box Skype Version 2.0.0.68

This is the driver you need. gspca.

Lets check the driver first. Open a terminal and type

```
lsmod | grep videodev
```

Post the results back here.

Can you also post a screen shot of the video page on the configuration dialog. You can get to that by hitting the button on the very bottom left of skype.

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-30
Morning Matt. I was out all day yesterday and didn't get in till this morning. I'll post the results in a minute. The main question is ... when you use Skype Are you able to do a video call both ways? When I use it with Ubuntu, I can see the caller but my camera doesn't work. I know the camera is fine but Skype appears to say that video calls aren't possible. Hey ho. Here's the result ... 

lsmod | grep videodev
videodev               43098  1 gspca_main
v4l1_compat            13359  1 videodev

Regarding screenshot of configuration page. wtf? Unlike Skype for windows I don't see any edit, help or other tags. All I have is my list of contacts. I'll scratch around and see if I'm being thicker than usual.

(ps . I had an extra beer yesterday just for you)

---

### Post by Ireallyneedhelp on 2011-03-30
Weird! I just did a skype test call. I hear it OK, but when I record I get zilch!

When I click on -System then on Preferences, and then on volume control-... there is nothing saying "volume control".
[B]
[/B]

.

---

### Post by matt_symes on 2011-03-30
Hi

> The main question is ... when you use Skype Are you able to do a video call both ways?

Yes i believe so. I don't really use it myself but when i have used it, it's both ways.

Ubuntu 9.04 needed a tweek to get it working and i am wondering if that same tweek will work in your version. 

From that web site i referenced above....

> Creative Webcam Instant
9.04
041e:4034
gspca
Skype 2.0.0.72: Works fine after running skype like this from the command prompt: "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" without the double quotes. If you don't have that library already installed, install it with "apt-get install libv4l-0" first. The same trick also works for Camorama, and mplayer. Cheese works out the box!

Open a terminal and type 

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

(that is /USR/LIB/LIBV4L/V4L1COMPAT.SO in lower case. The lower case L looks like a 1 in the code block font)

If that does not work because v4l1compat is not installed type

```
apt-get install libv4l-0
```

(that is LIBV4L-0 inlower case)

to install it and then try the above command again.

Hopefully that will give you video. If it works add that command as a launcher.

Regarding the configuration for Skype, when you have logged onto Skype if you look at the very bottom left in the status bar you will see 2 small icons. The one on the very left is the configuration icon.

Do you have that link to Voipcheep so i can check out the site ?

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-30
> **Ireallyneedhelp said:**
> Weird! I just did a skype test call. I hear it OK, but when I record I get zilch!

When I click on -System then on Preferences, and then on volume control-... there is nothing saying "volume control".


.
Skype audio now fine. It helped when I noticed the microphone was set far too low.
Still no video - and no further forward with getting Voipcheap to work.

(other anomaly ... when I power up I used to get the option of Windows or Ubuntu. This option has disappeared. I have to guess when the screen would be showing and press the down arrow and "enter" to select Ubuntu).

---

### Post by matt_symes on 2011-03-30
Hi

> **Ireallyneedhelp said:**
> Weird! I just did a skype test call. I hear it OK, but when I record I get zilch!

When I click on -System then on Preferences, and then on volume control-... there is nothing saying "volume control".
[B]
[/B]

.

Look at system->preferences->sound ;)

The recording might be a different issue.

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-30
Thanks Matt! Video and audio working perfectly. I tried to close the terminal after I had done this but it said **"There is still a process running in this terminal. Closing the terminal will kill it."** 

I then thought I had to ensure the code was installed and ran it again but I then got the message **"There is still a process running in this terminal. Closing the terminal will kill it.**

I'll leave it just now (maybe even kill process later tonight?) and try skype again. If it works - great. If not I'll enter the code again.

Thanks a million. Off now to check [http://www.voipcheap.com/en/index.html](http://www.voipcheap.com/en/index.html)

:KS:KS:KS

---

### Post by matt_symes on 2011-03-30
Hi

We can continue this tomorrow. We will create a script and launcher for Skype so you can start it through that. And then we can look at voipcheap.

I am off out tonight though  :D :D :D

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-31
> **matt_symes said:**
> Hi

We can continue this tomorrow. We will create a script and launcher for Skype so you can start it through that. And then we can look at voipcheap.

I am off out tonight though  :D :D :D

Kind regards

Skype is now working a treat. Thanks Matt. People at the other end are saying the sound & video quality is much better. It's a simple click & go ... amazing.

No luck with Voipcheap. They got in touch again saying they only support windows. I directed them to their page that said they support Linux! I found something on another forum (Astalavista) about voipcheap, but no joy. I downloaded it - extracted it but nada. Any suggestions for a Voip system that works in Linux?

---

### Post by matt_symes on 2011-03-31
Hi

Have you tried running it through wine ?

Kind regards

---

### Post by matt_symes on 2011-03-31
Hi

> (other anomaly ... when I power up I used to get the option of Windows or Ubuntu. This option has disappeared. I have to guess when the screen would be showing and press the down arrow and "enter" to select Ubuntu).

Please post the output of

```
sudo fdisk -l
```

Small L above. 

Try pressing the shift key at boot up. You could also try

```
sudo update-grub
```

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-31
Good evening Matt. Skype OK. Thanks a lot for all your help. Regarding above, I get
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x19d619d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

---

### Post by Ireallyneedhelp on 2011-03-31
Regarding sudo upgrade grub, I get
Generating grub.cfg ...
cat: /boot/grub/video.lst: No such file or directory
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found Microsoft Windows XP Home Edition on /dev/sda1
done

I assume it will be OK as it says "done". I'll try tomorrow. Off along the coast tomorrow  to meet up with friends who are here for a fortnight. I may be late.
Thanks again for all your help. Doesn't it annoy you?

---

### Post by matt_symes on 2011-03-31
Hi

Is this a Wubi install ? I see no Linux partitions.

> Thanks again for all your help. Doesn't it annoy you?

No. I just like to help.

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-31
While you're her (arf), I keep getting asked for my password. Fair enough, but if I'm downloading things and it takes a while, if I'm not at the computer it's a drag. Is there any way I can set the password manager to ony ask for a password every hour or so?
(btw ... if you're ever over here I'll treat you to a dinner and copious amounts of drink)

---

### Post by Ireallyneedhelp on 2011-03-31
> **matt_symes said:**
> Hi

Is this a Wubi install ? I see no Linux partitions.



No. I just like to help.

Kind regards
  It's a Wubi! Assuming I get Voipcheap up and runing I'll be dumping windows.
(I note there''s a beta version of 11)

---

### Post by matt_symes on 2011-03-31
Hi

> **Ireallyneedhelp said:**
> While you're her (arf), I keep getting asked for my password. Fair enough, but if I'm downloading things and it takes a while, if I'm not at the computer it's a drag. Is there any way I can set the password manager to ony ask for a password every hour or so?

When are you being asked for a password ? Post a screen shot.

> (btw ... if you're ever over here I'll treat you to a dinner and copious amounts of drink)

Thanks. That's nice :D but i would  prefer i you could help others when you're up to speed or spread the word about open source software.

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-31
When I said I keep getting asked for my password, I've an old "useless" laptop that I'm trying to revive (I'm using my desktop just now). I've dumped Vista and am currently downloading the Beta version of Ubuntu. THAT'S why I was asking if there's a way to delay asking for a password (I should really start another thread). I've to keep dotting back & forward.

---

### Post by Ireallyneedhelp on 2011-03-31
> **matt_symes said:**
> Hi



When are you being asked for a password ? Post a screen shot. 
I can do screenshots. How do I post it?
(Re previous question, I've already got three people trying it out)

---

### Post by matt_symes on 2011-03-31
Hi

> It's a Wubi! Assuming I get Voipcheap up and runing I'll be dumping windows.

We will tackle this one either tomorrow or the day after. 

Bump this thread so it's in my User_CP area. 

Kind regards

---

### Post by matt_symes on 2011-03-31
Hi

We are cross posting :)

> I can do screenshots. How do I post it?

Take your screen shot. Select reply to reply to my post, type your reply and then scroll down to the manage attachments button. You can attach a screen shot from there.

I have subscribed to a couple of thousand threads. It takes me ages to look through them. When you reply it gets bumped up to my user control panel area. Then i can see.

Kind regards

---

### Post by Ireallyneedhelp on 2011-03-31
bump

---

### Post by Ireallyneedhelp on 2011-03-31
> **Ireallyneedhelp said:**
> bump
Screenshot test

---

### Post by Ireallyneedhelp on 2011-03-31
> **Ireallyneedhelp said:**
> Screenshot test

Try again ...

---

### Post by matt_symes on 2011-04-01
Hi

Your screen shot looks fine. Did you create a launcher for Skype ? Do you need instructions on how to do that ?

Do you have Wine installed ? I will have a good look at the Voipcheap web site later today. Today i have to fix a neighbours WinXP box.

Kind regards

---

### Post by guruvigneshwaran on 2011-04-27
> **telltom said:**
> When i try to open it, it closes immediately. This just started happening today. I wanted to download Alarm-clock, so i got it from the synoptic package manager instead.
Whenever i open my update manager it shows the following error:
Could not initialize the package information  An unresolvable problem occurred while initializing the package information.  Please report this bug against the 'update-manager' package and include the following error message:  'E:Malformed line 63 in source list /etc/apt/sources.list (dist parse)'

Software center is also not opening..

---

### Post by matt_symes on 2011-04-29
Hi

> **guruvigneshwaran said:**
> Whenever i open my update manager it shows the following error:
Could not initialize the package information  An unresolvable problem occurred while initializing the package information.  Please report this bug against the 'update-manager' package and include the following error message:  'E:Malformed line 63 in source list /etc/apt/sources.list (dist parse)'

Software center is also not opening..

Applications->Accessories->gedit.

Open the file 

```
/etc/apt/sources.list
```

Copy and paste the contents back here. Please post the between code tags to make it easier to read.

[noparse] ```
 sources copy and paste text 
``` [/noparse]

Kind regards

---

### Post by Detroit_Bad_Boy on 2011-07-20
> **Razor338 said:**
> i can't even update ubuntu,and wine is not working either!!(i can't open any exe files)


Linux does not work like that. It NEVER opens .exe extensions. That way it helps cut down on viruses and malware :guitar:

---

### Post by matt_symes on 2011-07-21
Hi

> **Detroit_Bad_Boy said:**
> Linux does not work like that. It NEVER opens .exe extensions. That way it helps cut down on viruses and malware :guitar:
Errr. The poster is talking about using wine to open .exe files and wine can if you have it installed.

Kind regards

---

### Post by pintsie on 2011-10-15
Hey! 
I have ubuntu 10.10 (I did format yesterday) and I can't open the software center and any of the chat programs. 
Can you help me? 

I tried to open from the terminal and it says this: 

from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 48, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 33, in <module>
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 50, in <module>
    from  appdetailsview_gtk import AppDetailsViewGtk as AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py", line 45, in <module>
    from appdetailsview import AppDetailsViewBase
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 30, in <module>
    from purchasedialog import PurchaseDialog
  File "/usr/share/software-center/softwarecenter/view/purchasedialog.py", line 25, in <module>
    import webkit
  File "/usr/lib/pymodules/python2.6/webkit/__init__.py", line 19, in <module>
    import webkit
ImportError: libjpeg.so.62: cannot open shared object file: No such file or directory

---

### Post by stuartlarsen on 2012-09-22
I'm also having trouble opening the software center. This is what I got when I tried using terminal

stu@stu-Satellite-L750:~$ gksudo software-center
2012-09-23 14:21:45,640 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-09-23 14:21:45,897 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-09-23 14:21:45,999 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-09-23 14:21:46,003 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 146, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.
2012-09-23 14:21:47,086 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1422, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1352, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 171, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 238, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 511, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 271, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 450, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 439, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
stu@stu-Satellite-L750:

Many thanks for any advice with this
Stu

---

### Post by matt_symes on 2012-09-24
Hi

This is an error from the last trace back.

> 
SystemError: E:The package ttf-mscorefonts-installer needs to be reinstalled, but I can't find an archive for it.

Open a terminal and type

```
sudo apt-get install ttf-mscorefonts-installer
```

Enter your password. It will not be echoed to the screen.

Post back any errors by copying and pasting from the terminal into your next post.

Do you have the multiverse repo enabled ?

Please post the output of

```
grep multiverse /etc/apt/sources.list
```

Kind regards

---

### Post by rwharper on 2012-09-24
Software-center stopped working today.  Upgraded to 12.04 previously, and had no problems with any of the software including software-center.  Now - when I click on the software-center icon, it just pulsates a few times, then stops.  Nothing else happens.  If I try to start it from a terminal window I get:

rwharper@RWH-netbook:~$ software-center
  File "/usr/bin/software-center", line 152
    print time.time()
             ^
SyntaxError: invalid syntax

Help!!

****

---

### Post by matt_symes on 2012-09-26
Hi

> **rwharper said:**
> Software-center stopped working today.  Upgraded to 12.04 previously, and had no problems with any of the software including software-center.  Now - when I click on the software-center icon, it just pulsates a few times, then stops.  Nothing else happens.  If I try to start it from a terminal window I get:

rwharper@RWH-netbook:~$ software-center
  File "/usr/bin/software-center", line 152
    print time.time()
             ^
SyntaxError: invalid syntax

Help!!

****

This is not an error i have come across.

You could try reinstalling software-center from the command line.

```
sudo apt-get install --reinstall software-center
```

Kind regards

---

### Post by isa saids on 2013-01-05
I got the same problem. It is happened because i was ignore the software problem notification and leave it closed. Maybe i have different way for getting the problem. Bad.
I try to solve the problem by this way :
```
1. isa@isa-NEON-MNW:~$ sudo apt-get autoclean
2. isa@isa-NEON-MNW:~$ sudo apt-get update
3. when i do that update i find error and note the error then i look for article for it's cause the error is same like this :
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages
4. I found a solution to fix my problem up in this [**[COLOR="Blue"]link[/COLOR]**]("http://ubuntuforums.org/archive/index.php/t-1764781.html")
5. From that link I do this :
isa@isa-NEON-MNW:~$ sudo su
[sudo] password for isa: 
root@isa-NEON-MNW:/home/isa# 
root@isa-NEON-MNW:/home/isa# cd /var/lib/apt
root@isa-NEON-MNW:/var/lib/apt# 
root@isa-NEON-MNW:/var/lib/apt# mv lists lists.old
root@isa-NEON-MNW:/var/lib/apt# mkdir -p lists/partial/
root@isa-NEON-MNW:/var/lib/apt# apt-get clean
root@isa-NEON-MNW:/var/lib/apt# update
6. Then I can open the software center again, And got the same notification as usual but i send the report but no problem.
```
I should share my problem but thank you.

---

