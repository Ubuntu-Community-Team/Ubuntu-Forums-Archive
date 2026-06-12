---
title: "Rhythmbox in tray SUCKS"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Zopiac on 2009-12-27
The only thing I truly HATE so far about Ubuntu is that there is NO WAY to get Rhythmbox to not show up in the tray only! I can't stand having to use the stupid tray to open the player window. Is there ANY WAY I can stop this stupid thing??? I've looked for answers for months!!!!

inb4 Amarok, etc. :P They suck.

---

### Post by wesleybailey on 2009-12-27
Press **Alt+F2** and run *gconf-editor*

Find this key
/apps/rhythmbox/plugins/status-icon/notification-mode

set it to 2.

Latest Tutorial : [Convert FLAC to MP3 in Ubuntu]("http://wesleybailey.com/articles/convert-flac-mp3")

---

### Post by Merk42 on 2009-12-28
Um, doesn't just minimizing it put it in the window list as well?

---

### Post by MelDJ on 2009-12-28
get songbird

---

### Post by wesleybailey on 2009-12-28
I might have misunderstood the question. 

Do you want to hide the hide from the notification area or from the window list?

---

### Post by stinkeye on 2009-12-28
Rhythmbox > edit > plugins > status icon > configure box
and set it up to whatever makes you happy.
](*,)#-o

---

### Post by Zopiac on 2009-12-28
> **stinkeye said:**
> Rhythmbox > edit > plugins > status icon > configure box
and set it up to whatever makes you happy.
](*,)#-o

I do not have that as a plugin option...

> **wesleybailey said:**
> I might have misunderstood the question. 

Do you want to hide the hide from the notification area or from the window list?

Hide it from the notification area/make always show in window list.

> **MelDJ said:**
> get songbird

Already covered that base; falls under etc.:

> **Zopiac said:**
> inb4 Amarok, etc. :P They suck.

> **wesleybailey said:**
> Press **Alt+F2** and run *gconf-editor*

Find this key
/apps/rhythmbox/plugins/status-icon/notification-mode

set it to 2.

I don't run gnome, so alt+f2 is obsolete, but I got gconf-editor another way. However, since I do not have that plugin, this option is moot.

And finally,
> **Merk42 said:**
> Um, doesn't just minimizing it put it in the window list as well?

No, it often goes to only the notification area, hiding the button in the window list.

---

### Post by patchwork on 2009-12-28
I am also interested in finding an automated way to do this.  So far, all I have been able to do is to close rhythmbox from the tray, not the player.  On the next start-up, the player window opens.  It's still a hassle, but it's better than it was.

---

### Post by phillw on 2009-12-28
Hi, I just right-clicked it --> clicked on remove from panel & it's gone ?  Music is still playing .. Is this not available in 9.10 (If it is not, I'll boot back into 9.10 and take a look at it for you.)

Regards,

Phill.

---

### Post by patchwork on 2009-12-28
Maybe I'm reading the OP wrong, but I believe the problem is that when RB opens, it immediately opens into the tray, not into the windowed player.

---

### Post by stinkeye on 2009-12-28
> **Zopiac said:**
> I do not have that as a plugin option...




I'm using Rhythmbox 0.12.5 and I'm pretty sure the plugin was included in the
rhythmbox package.(/usr/lib/rhythmbox/plugins/status-icon)
If you really want that functionality install 0.12.5

---

### Post by Dragonbite on 2009-12-28
> **Zopiac said:**
> 
I don't run gnome, so alt+f2 is obsolete, but I got gconf-editor another way. However, since I do not have that plugin, this option is moot.

What environment are you running? I've found Alt+F2 to work in all of my environments (Gnome, Xfce, Fluxbox, KDE).

> **Zopiac said:**
> No, it often goes to only the notification area, hiding the button in the window list.

In Jaunty, my Rythmbox did not remove itself from the Task List until I applied the plug-in which was in the list.  I prefered it coming out of the task list and only being in the system tray so I was happy to find it.

What version/distro version are you running this on?

---

### Post by theozzlives on 2009-12-28
Rhythm Box is not my player of choice. I like Amarok14, and don't mind the notification icon. I can do my work and listen to music without the player window hogging up space. If you want just a player, might I suggest a stereo, or MP3 player instead of a computer.

---

### Post by Zopiac on 2009-12-28
> **patchwork said:**
> Maybe I'm reading the OP wrong, but I believe the problem is that when RB opens, it immediately opens into the tray, not into the windowed player.

No, it usually opens in the window, but I don't want it to ever show up or minimise to tray.

> **phillw said:**
> Hi, I just right-clicked it --> clicked on remove from panel & it's gone ?  Music is still playing .. Is this not available in 9.10 (If it is not, I'll boot back into 9.10 and take a look at it for you.)

Regards,

Phill.

This is also only applicable to the plugin listed earlier :\ I'm not sure how to get the plugin... It seems like it might be standard to some versions, but not mine? Running 9.04

> **Dragonbite said:**
> What environment are you running? I've found Alt+F2 to work in all of my environments (Gnome, Xfce, Fluxbox, KDE).



In Jaunty, my Rythmbox did not remove itself from the Task List until I applied the plug-in which was in the list.  I prefered it coming out of the task list and only being in the system tray so I was happy to find it.

What version/distro version are you running this on?

IceWM :\ meta+space is used (and, IMHO, a whole lot better as it pops up instantly and is located in the panel and not in a seperate window)

> **theozzlives said:**
> Rhythm Box is not my player of choice. I like Amarok14, and don't mind the notification icon. I can do my work and listen to music without the player window hogging up space. If you want just a player, might I suggest a stereo, or MP3 player instead of a computer.

Well that would mean I'd need to get one of those things, and I would want full functionality from my computer. I could hardly get Amarok to find my songs... not to mention making a bunch of playlists and smart playlists. Anyways, that is not the problem. Rhythmbox fulfills everything I have asked for, except for this minor annoyance. And apparently there is a plugin to fix it, I just don't have it [yet].

---

### Post by phillw on 2009-12-28
You could be right !!

I'm not fully understanding this > I can't stand having to use the stupid tray to open the player window

What tray ? - I can

1) Add Launcher to Panel
2) Add Launcher to Desktop
3) Entire Menu --> Add this as drawer to panel
                         Add this as menu to panel

Like I say, I may have to pop into 9.10 to see what options are available there.

Regards,

Phill.

---

### Post by Zopiac on 2009-12-28
> **phillw said:**
> You could be right !!

I'm not fully understanding this 

What tray ? - I can

1) Add Launcher to Panel
2) Add Launcher to Desktop
3) Entire Menu --> Add this as drawer to panel
                         Add this as menu to panel

Like I say, I may have to pop into 9.10 to see what options are available there.

Regards,

Phill.

IceWM does not have these capabilities; those are gnome-panel (and maybe the Kde and/or Xfce variant) specific.

---

### Post by Zopiac on 2009-12-28
> **stinkeye said:**
> I'm using Rhythmbox 0.12.5 and I'm pretty sure the plugin was included in the
rhythmbox package.(/usr/lib/rhythmbox/plugins/status-icon)
If you really want that functionality install 0.12.5

Well I have 0.12.6...

---

### Post by phillw on 2009-12-28
> **Zopiac said:**
> Well I have 0.12.6...

+1

TBH, with running 10.04 nearly all the time - I'm losing track a bit 9.10. It's looking *REALLY* good - and it's only on its 1st alpha release :popcorn:

They're doing stuff to notifications - so, if they're currently a bane of your life, be patient - There's a bit squealing going on - But, so far - they're looking pretty darn good !!!

Phill.

---

### Post by mc4man on 2009-12-28
If the status icon plug-in is **not enabled**, then rhythmbox will never go to the notification area (what you're calling 'system tray'..?

If you're running 0.12.6 in 9.04 then how did you install it? (build, take from lucid, whatever...?

The plug-in is in most recent versions of rhythmbox (even though you want it not enabled

filelist of 0.12.6
[http://packages.ubuntu.com/en/lucid/rhythmbox/filelist](http://packages.ubuntu.com/en/lucid/rhythmbox/filelist)

---

### Post by phillw on 2009-12-28
Hi,

Just to update my previous posting ..

The stuff going on for the Notification Area can be found here --> [https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

So, if, you've got a bit of time & 10GB of hard drive space, come along and have a play with 10.04 - It's still a bit rough round the edges for some video drivers - But, as ever, you can have a play with the LiveCD and the "fix its" for 9.10 seem to work.

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)  Is the area to head for. Please note, it IS a development release - So don't be replacing your current install with it !!!

If you'd like any help setting up / questions - please feel free to pop over and ask.


Regards,

Phill.

---

### Post by Zopiac on 2009-12-28
> **mc4man said:**
> If the status icon plug-in is **not enabled**, then rhythmbox will never go to the notification area (what you're calling 'system tray'..?

If you're running 0.12.6 in 9.04 then how did you install it? (build, take from lucid, whatever...?

The plug-in is in most recent versions of rhythmbox (even though you want it not enabled

filelist of 0.12.6
[http://packages.ubuntu.com/en/lucid/rhythmbox/filelist](http://packages.ubuntu.com/en/lucid/rhythmbox/filelist)

Idk, I just know that I have 0.12.6... and that I don't have the plugin.
And yes I mean notification area by saying system tray. I am still calling it what Windows does, since I hardly ever deal with it and am therefore not up-to-date on what it is called.

> **phillw said:**
> Hi,

Just to update my previous posting ..

The stuff going on for the Notification Area can be found here --> [https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

So, if, you've got a bit of time & 10GB of hard drive space, come along and have a play with 10.04 - It's still a bit rough round the edges for some video drivers - But, as ever, you can have a play with the LiveCD and the "fix its" for 9.10 seem to work.

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)  Is the area to head for. Please note, it IS a development release - So don't be replacing your current install with it !!!

If you'd like any help setting up / questions - please feel free to pop over and ask.


Regards,

Phill.

All right, I get it, you like 10.04. Not helping me though to say that again and again, however >_>

---

### Post by mc4man on 2009-12-28
> Idk, I just know that I have 0.12.6... and that I don't have the plugin.

If you wish to then post your sources and third pary repos
or these should suffice

 ```
cat /etc/apt/sources.list

```
```
ls /etc/apt/sources.list.d/
```

Though the odds are 0.12.6 is not going to act totally as expected in 9.04

---

### Post by Zopiac on 2009-12-28
> **mc4man said:**
> If you wish to then post your sources and third pary repos
or these should suffice

 ```
cat /etc/apt/sources.list

```
```
ls /etc/apt/sources.list.d/
```

Though the odds are 0.12.6 is not going to act totally as expected in 9.04

```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Jahshaka
deb http://repo.jahshaka.org/ubuntu/dapper/ binary-i386/

# Miro
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu karmic/

# Cairo
# deb http://repository.cairo-dock.org/ubuntu jaunty cairo-dock  # For Ubuntu 9.04

# Gnome-do
# deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

deb http://ppa.launchpad.net/spring/ubuntu jaunty main
deb-src http://ppa.launchpad.net/spring/ubuntu jaunty main

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner
```

and

```

$ ls /etc/apt/sources.list.d/
akirad.list     opera.list    winehq.list
medibuntu.list  playdeb.list  winehq.list.save

```

---

### Post by mc4man on 2009-12-28
Don't particularly see where you aquired it. I guess you could searh rhythmbox in synaptic, right click on the package -> properties and there should be a line that provides more info.

Otherwise, ...
there is a jaunty 0.12.5 version here that does contain all the plugins. If desired then remove your current rhythmbox and dl and install this one. ( it may be just as good as the .6  - don't really know

[http://old.getdeb.net/search.php?keywords=rhythmbox](http://old.getdeb.net/search.php?keywords=rhythmbox)

If this is the one you installed ( seems unlikely), and want to keep, then you'll have to put up with it ( I can't dl without adding repo to ck. for plugin, though I'd think it has it

[http://www.getdeb.net/software/Rhythmbox](http://www.getdeb.net/software/Rhythmbox)

finally this would show if the plug-in was installed in current install ( unless rhythmbox is in /usr/local/
```
ls /usr/lib/rhythmbox/plugins/

```
and or
```
ls /usr/lib/rhythmbox/plugins/status-icon/
```

---

### Post by brookie on 2009-12-28
mc4man, i got it [here]("https://launchpad.net/%7Ejmatthew/+archive/ppa") and it works in karmic. it comes with the status icon plugin as well.

---

### Post by mc4man on 2009-12-28
> ....it works in karmic.
Our op is running jaunty (fortunately or unfortunately depending on your viewpoint), and atm the source of his is  unknown. Though I'd think any rhythmbox meant for recent ubuntu releases would include the plug-in, like you've seen in the ppa you're using.
 
( which ironically needs to be disabled for what I'm thinking he wishes.

---

### Post by Zopiac on 2009-12-28
Well right now I can't do anything, as I am experiencing [tgis problem.]("http://ubuntuforums.org/showthread.php?p=8574a081#post8574081") It has rendered me sound-less, so I'm not sure what all I can do about Rhythmbox successfully...just going to switch to my Arch installation until the problem gets resolved.

Thanks for all the help guys, though!

---

### Post by gnimsh on 2010-05-20
To make rhythmbox open when you click the icon, open up the plugins and find status icon. Click configure. For notifications, choose "show when main windows is hidden" and for status icon choose "always visible." That solved this issue for me.

---

### Post by awi on 2010-05-21
Trayicon sucks because:
- Single click brings the context menu (secondary is widely used all over the gnome desktop)
- Double click does nothing (It would be nice to bring the app window or even a single click and let the secondary button shows the context menu)
- Lack of tooltip (It could for instance show you what is being played, or "Stopped" if nothing is playing).
- A checkbox for play/pause (how intuitive is that!)
- You have to guess (try/error) to figure it out in plugin's configuration what combination lets you send the window to the tray icon and not minimize it or close it

---

### Post by Hreinsi on 2010-05-21
I would try this [http://ubuntuforums.org/showthread.php?t=1380811](http://ubuntuforums.org/showthread.php?t=1380811)
The best player i have tested

---

### Post by jrothwell97 on 2010-05-21
> **gnimsh said:**
> To make rhythmbox open when you click the icon, open up the plugins and find status icon. Click configure. For notifications, choose "show when main windows is hidden" and for status icon choose "always visible." That solved this issue for me.
[IMG]http://blogs.warwick.ac.uk/images/lblackwell/2005/03/01/thread_necromancer.png[/IMG]

> **awi said:**
> Trayicon sucks because:
- Single click brings the context menu (secondary is widely used all over the gnome desktop)
- Double click does nothing (It would be nice to bring the app window or even a single click and let the secondary button shows the context menu)
- Lack of tooltip (It could for instance show you what is being played, or "Stopped" if nothing is playing).
- A checkbox for play/pause (how intuitive is that!)
- You have to guess (try/error) to figure it out in plugin's configuration what combination lets you send the window to the tray icon and not minimize it or close it
Please read [this]("http://www.markshuttleworth.com/archives/347"). The old notifications are being deprecated due to wild inconsistency and inflexibility, and Rhythmbox is an app that takes advantage of the new indicator styles. The move to the new indicators should be all but complete by Maverick+1

---

### Post by philinux on 2010-05-21
Thread closed Necromonger. Check the thread date.

---

