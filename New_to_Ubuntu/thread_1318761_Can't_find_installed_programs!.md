---
title: "Can't find installed programs?!?"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by ericmark4 on 2009-11-07
[SIZE=2]Hi all. This might be the ultimate newbie question; I just installed Xubuntu today. I am fairly savvy at the end-user level of a Windows PC....which might be the problem.

How do I find, then run, programs I installed through Synaptic Package Manager? It's not like Windows, to state the obvious. I installed a bunch of chess programs and VLC Media Player through Synaptic, but they do not appear under Applications. The programs added through Add/Remove Applications _do_ appear, but not the ones added via Synaptic.

I did a brief Google search on this topic and came up with confusing (to utter newbie me) suggestions about the Terminal.

All I want to do is launch the programs I just installed. I checked in Synaptic to see if I messed that up, but the programs are all checked off there as "installed." I re-installed them, too, but they still do not appear anywhere I can see. File manager could not find them, either.

I'm scratching my head and waiting to see just how obvious is the trick I'm missing here.

Thanks much for all advice,
Eric M
[/SIZE]

---

### Post by john.nicholls on 2009-11-08
Go to the main menu (click on the Xfce icon). You should see a list including Accessories, Games, Graphics, etc. Moving the cursor to each one should display a list of programs. For example, VLC should be under Multimedia.

---

### Post by SunnyRabbiera on 2009-11-08
VLC should be in the menus, but other apps might not appear in the menus, there are some apps that are commandline based.

---

### Post by Tyke91 on 2009-11-08
if you are in doubt, you should be able to start your program from ALT+F2 or the terminal, just type it's name. for instance, to start vlc you could just do ALT+F2 and type vlc, or open a terminal and type vlc.

all of programs you install should be under /usr/bin  if you wanna know where to find them :) 

if they aren't in /usr/bin they should be in /usr/sbin (which is for superusers to use... certain security programs are in there as well as things like synaptic and visudo)

very rarely will something be installed into /bin or /sbin . those are basic core commands for your shells. for instance, the shell that came installed by default (bash) lives in /bin while admin commands like fsck live in /sbin.

PS: here's the wiki on how the linux filesystem hierarchy works [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

