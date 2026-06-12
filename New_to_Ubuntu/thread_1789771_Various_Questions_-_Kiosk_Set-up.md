---
title: "Various Questions - Kiosk Set-up"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by Cognitive_Dissonance on 2011-06-24
Hello community,

I'm opening this thread after doing quite some searching and not with a light heart :)
**A bit about me: **I'm not entirely PC illiterate and have been using linux for about a couple of years for my basic netbook needs. I can follow documentation and if providing an answer is too dificult, a pointer to a relevant section will suffice for me.

**What I want to achieve:** I'm making an Edubuntu-based kind of "activity kiosk" for my little boy of 2. I've seen those on kids corners' in several places and want to make a kiosk initially only running GCompris but as he grows I'll be adding more options. Here's something to give you an idea [http://www.protouchblog.co.uk/tag/interactive-kiosks/](http://www.protouchblog.co.uk/tag/interactive-kiosks/)

**My questions/problems so far:**

[LIST=1]
[*]How to customize a profile with showing only the programs I want and not the entire program list normally available. (I've made a restricted account for the little one and I need it to only be able to run GCompris and nothing else at all; not even volume controls).
[*]As the kiosk will run headless (there's a touchscreen for the activities) I am running teamviewer for remote access from my Winbox (lame, I know but spare me for now). I already have it as a startup program but I want it to run minimized and not even visible on a panel anywhere (that was trivial to do in Kubuntu, not quite so in Edubuntu). Is there a way to make it run "silently" or "as a service" as we'd say in Win-world?
[*]If anyone has experience administering GCompris I'd love to get a PM as the GCompris fora are a bit too quiet.
[/LIST]

I'm sure as I'm working through this set-up I'll get more questions, so I reserve the right to update the post with more queries :)

My system:

[LIST]
[*]Dell optiplex G620 (P4@3.80, yes they still exist)
[*]HP 2310ti touschscreen monitor
[*]Edubuntu 11.04 (almost virgin, installed a week ago)
[/LIST]

---

### Post by I&#9829;HTML5 on 2011-06-24
1. To edit the programs lists go to System > Preferences > Main Menu, and uncheck the programs you want to hide. To remove the volume controls and other panel items, right click the items on the panel and click "Remove From Panel".

2. I have absolutely no experience with TeamViewer, but many programs support being launched with a ```
-d
``` option which runs them in the background as a daemon. However, TeamViewer may or may not support this option.

---

### Post by Cognitive_Dissonance on 2011-06-24
Hello there and thanks for the pointers.

I'm afraid it's a straight 0 out of 2 on this one. 

First, there is no "Preferences" under "System" in Edubuntu. There is an "Edubuntu Profile Editor" but its documentation is abysmal. In the screenshot you can see what's available under "System".

Second, I added the -d handle on teamviewer but got an error message saying it could not parse the command. (TeamViewer as such, runs from within WINE as it's essentially a Win application ported to Linux).

I can live with the teamviewer being constantly there but, I can't get to actually tweak the available progs on the little one's profile which is my main concern.

Thanks for the help anyway :)

---

### Post by I&#9829;HTML5 on 2011-06-24
Try the Edubuntu Menu Editor

I use old Gnome on my computer, not Unity, so I am used to menus, not search, so sorry 'bout that

---

### Post by Cognitive_Dissonance on 2011-06-27
So far so good but many problems persist.

[B]Menu Editor
[/B]
[LIST]
[*]Regardless of what options are chosen all programs and options appear in Unity. It seems like the menu editor does not influence what Unity displays
[*]Switching to Classic (gnome) interface, *does* implement the changes
[/LIST]
So this brings up a new set of challenges:

[LIST]
[*]What is the equivalent of the Menu Editor for Unity?
[*]Assuming I keep gnome, is there a way to disable the top panel? (or remove **everything** from it, including the ubuntu 'start' button, the logoff/restart button and everything else that appears there). I tried customising it but those buttons can't be hidden/removed.
[/LIST]
**TeamViewer**

The -d handle did not work so I'm reduced to actually running it with its window on my desktop. Now, considering GCompris runs as a startup program it could 'cover' teamviewer's window. So here are my questions stemming from this:

[LIST]
[*]Is there a handle (equivalent to -d) to make a program run minimised?
[*]Failing the above, is there a way to queue the startup programs in such a way that TeamViewer runs **before** GCompris (thereby ensuring GCompris covers it)?
[/LIST]

---

### Post by grahammechanical on 2011-06-27
I have been thinking about what you are trying to do. I do not have the answers. I am using Edubuntu right now. I am using Ubuntu Classic without effects. In this user interface the bottom panel can be deleted and all the things in the top panel can also be removed from the panel. There is not one item in the right of the top panel that cannot be removed from the panel with a right click.

Also the menu items in the top right have gone. The Ubuntu icon is still there and it has a little triangle at the bottom left corner that gives you access to all the usual menu items. which can no doubt be edited by the Edubuntu Menu Editor. Note, this list includes a shutdown option which is useful if you remove shutdown from the top panel.

I tried to find a way to put GCompris into the startup applications but I could not located the binary (bin = program) file. I wanted to test to see if it would load GCompris from boot.

I have noticed that when GCompris does load it takes up all the screen. It hides the panels. There are also in Edubuntu various programs that give control over the computer. I have not tried these out.

I hope this helps a little bit.

Regards.

P.S. I was under the impression that Edubuntu was built on Kubuntu. It certainly has a lot of K type programs and utilities.

P.P.S. Found it! Use the browse button to go to file system usr/games/gcompris and put that as the command. Then GCompris will load at boot time. You will need to have automatic log in unless you want to control the ability of your son to start the kiosk. Are you going to build a flashy surround like in those photographs. It would look great.

It may also be possible to have a guess session as a startup application. I have not tried this out. This is in file system usr/bin

---

### Post by I&#9829;HTML5 on 2011-06-27
Either panel can be removed simply by right clicking it, and clicking "Delete Panel"

---

### Post by Cognitive_Dissonance on 2011-06-28
Hi guys,

you're right :)

All buttons removed and top panel made to hide. (This is extra helpful because i) it can be accessed by a mouse and ii) it's virtually impossible to pull it using a finger on the touchscreen which makes it toddler-safe)

**Re start-up apps.**
I may have confused you you both and apologise for this. I got GCompris to be a start up app and launch immediately and full screen. (which means that the lil one will immediately go in GCompris). I also dotted the desktop with about 15 shortcuts to GCompris in case he presses the quit button and returns to desktop. 

My issue is the GCompris in conjunction with TeamViewer. They're both start up apps. T-V does not get "closed" once it runs, it can only be minimised. However, as things are now, T-V starts after GCompris which sends its windows over the GCompris. 
So, I must either find a way to run T-V *prior* to GCompris or find a way to run it minimized.

If push comes to shove, I'll disable it altogether, although I'd favour this simple and easy remote access to remotely shut down the PC whenever the little one gets too stuck on it :)

P.S. Big thanks and kudos to you guys. It's appreciated massively :)
----

**@Graham**: For the last 3 days I've been struggling less on the software than the hardware :) I don't have the space or tools to do a proper job (can't use a circular saw in the apartment). So, I'm going with a basic IKEA cube unit on rollers, a VESA base screwed on the top, holding the monitor in place. And a couple of doors to access the desktop which will be locked inside. I'm posting a picture of the basic unit. 
My main focus is safety (hence all cables will be hidden inside and only on power lead will be on the outside going to the plug. I'll post a pic of the final set-up later tonight.

It's a learning process, much as it is setting up the edubuntu thing. GCompris for example, allows for a massive amount of customization which I took full advantage to filter out the games aimed at higher ages.

Next step, will be to add a shuffler app on the desktop for him to choose among 3-4 cartoons that he could watch. [Need to choose them on single-click and program VLC or equivalent to actually close upon playback completion; but this is for stage 2]

---

### Post by I&#9829;HTML5 on 2011-06-28
Are you possibly willing to switch from TeamViewer to VNC? I know that in the Software Center there are many VNC servers that can be started in the background. Ubuntu even has one built in, though I'm not sure about Edubuntu

---

### Post by Cognitive_Dissonance on 2011-06-28
If I wasn't willing to experiment, I wouldn't embark on the project :)

Edubuntu does have VNC too apparently.
I'm toying with now from the Winbox to see what I can do with it. It seems pretty straightforward from within the LAN but not sure how it would work on remote access from outside locations (work etc.).

---

### Post by I&#9829;HTML5 on 2011-06-29
To access from another location:

If your computer is connected directly to the internet (i.e. not through a router), you can access it from your external IP address, viewable [here (http://www.whatsmyip.org/)](http://www.whatsmyip.org/).

If you use a router (wired or wireless), you will need to forward port **5900** from your router to your computer's private/internal IP address (viewable by entering ```
ifconfig
``` and finding the section that says ```
inet addr:
```) by using your router's configuration page (instructions for many routers are available [here (http://portforward.com/)](http://portforward.com/))

---

### Post by grahammechanical on 2011-06-29
The problem of team viewer might be solved if some nice but clever person on this forum was to write for you a script that would run as a startup application and load GCompris after a delay of a certain number of seconds. How many seconds? To be worked out by trial and error.

Do not forget to enjoy watching your son grow and develop.

Regards.

---

