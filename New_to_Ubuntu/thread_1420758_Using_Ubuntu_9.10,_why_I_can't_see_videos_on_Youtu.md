---
title: "Using Ubuntu 9.10, why I can't see videos on Youtube?"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by oingk on 2010-03-03
Hi

Using Ubuntu 9.10, why I can't see videos on Youtube?

It just shows me a black screen where the video should be playing.

---

### Post by seventhsamurai on 2010-03-03
You do not have flash installed. Open the Synaptics Package manager and install adobe flash plugin.

---

### Post by oingk on 2010-03-03
How do I do this? (I'm kind of clueless)

---

### Post by seventhsamurai on 2010-03-03
On the top of your screen, you will see the System menu. Go to System >> Administration >> Synaptics Package Manager.

In the Synaptics Package manager, under Quick Search, type in "flash". you will see "flashplugin-installer". Mark it for installation by clicking on the box to its left. Then click the "Apply" button. Make sure you have firefox closed when you do this. Or if you have firefox open, restart firefox. Your youtube videos should play fine.

---

### Post by Arijit_Kundu on 2010-03-03
may be simpler :

open system > administration > software sources
check every thing is checked in 'ubuntu software' (except cdrom)
go to the tab 'other software', tick the two option
close (and reload)
open a terminal
run 'apt-get install ubuntu-restricted-extras' (without quotes)

---

### Post by juancarlospaco on 2010-03-03
*For the same reason you can't see videos on Youtube on recent installed Windows/OsX.*

You need to install the Flash.

---

### Post by oingk on 2010-03-03
Thanks for your help, but there seems to be another problem now. As I was trying to do what you guys told me, Ubuntu gave me a warning that "You have 12 broken packages on your system! Use the Broken filter to locate them".

What's this about?

I haven't used my Ubuntu for a while, maybe this is important for you to understand.

---

### Post by DubyBreaks on 2010-03-03
[B][SIZE=1]Try this:[/SIZE]
[/B]

**How to fix broken packages**

 [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=warning.png[/IMG] 'Broken packages' are packages that have unsatisfied dependencies. If broken packages are detected, Synaptic will not allow any further changes to the system until all broken packages have been fixed. 
**To fix broken packages** 

[LIST]
[*]Choose **Edit** > **Fix Broken Packages** from the menu.
[*]Choose **Apply Marked Changes** from the **Edit** menu or press **Ctrl + P**.
[*]Confirm the summary of changes and click **Apply**.
[/LIST]
-taken from Ubuntu documentation, [HERE]("https://help.ubuntu.com/community/SynapticHowto")

---

### Post by oingk on 2010-03-08
ok I installed Ubuntu again dues to some other problems as well, and things are fine now.

So I still want to know what should I do to watch youtube vids. If I go here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) 
to download adobe flashplayer, there are several versions, which one should I download? the versions are:

-YUM for Linux
-.tar.gz for Linux
-.rpm for Linux
-.deb for Ubuntu 8.04+
-APT for Ubuntu 9.04+

---

### Post by 2hot6ft2 on 2010-03-08
> **oingk said:**
> 
-APT for Ubuntu 9.04+
But the recommended way is thru the repositories
Synaptic Package Manager or using apt-get in the terminal as was said above.

---

### Post by oingk on 2010-03-08
ok I did it the way the guys said above (through synaptic manager, etc).
It works now, thanks

---

### Post by sriny1512 on 2010-06-12
videos in youtube were working all these days, until installing updates in karmic koala made youtube videos not work. I use firefox browser. Anyone who know the solution, please help. I have flashplugin installed in synaptic and also flashplugin-nonfree.

---

