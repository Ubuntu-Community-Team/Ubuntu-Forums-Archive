---
title: "Disappearing panel icons"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by Robing Goodfellow on 2011-03-28
Using Ubuntu 64 10.10 on an HP G62 laptop.

I've been using Ubuntu (and loving it!) since mid December.  When I first installed, within a couple of days the little sound icon disappeared.  Did it again on a fresh install.  I just decided to live with it and added the "sound preferences" to the panel.

This afternoon the internet connection icon (4-5 bars, right side of the panel) disappeared.  I have made no changes to the system that I am aware of other than a restart (very occasionally when I open up the laptop I just get a black screen, no log in, have to do a hard reboot, as happened this afternoon).  All of my other icons are still there.  Researched the forums, found the suggestion to use "killall gnome-panel" tried that, no joy and my yellow sticky icon is now just a flashing dot.  Any ideas?

regards, Richard

---

### Post by matt_symes on 2011-03-28
Hi

First don't hard reboot. Press

```
alt + sysrq
``` 

at the same time and keep them depressed. Then hit each of these keys in turn

```
r e i s u b
```

That is busier backwards. Leave 3-5 seconds between each key press. As long as the kernel has not locked that will safely reboot your PC.

Kind regards

---

### Post by matt_symes on 2011-03-28
Hi

To get your sound icon back try right clicking on the panel, select add to panel, scroll down to indicator applet and select add.

Is NetworkManager running ? I assume your using network manager and not wicd.

Open a terminal and type

```
ps aux | grep [N]etworkManager
```

Post results back here.

Kind regards

---

### Post by vivek.pandey on 2011-03-28
i too have a similar problem. my applets are not dissapearing but my notification are has become random . when i boot sometimes i find it on top panel and some times bottom panel. its totally random

---

### Post by Robing Goodfellow on 2011-03-28
root      1052  0.0  0.1  88644  4980 ?        Ssl  16:15   0:00 NetworkManager
root      2152  0.0  0.0   6600  1092 ?        S    16:17   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-wlan0.pid -lf /var/lib/dhcp3/dhclient-ddf79181-3d94-40e3-942f-73f3f1fa993b-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0


And another noob question:
alt + sysrq - you mean while holding alt, type in + and s,y,s,r,q, right?

thanks for the help

---

### Post by matt_symes on 2011-03-28
Hi

> alt + sysrq - you mean while holding alt, type in + and s,y,s,r,q, right? 

No. On your keyboard there should (not every keyboard has one) be an Alt key and a key with Sysrq. On my keyboard it's above the backspace key. Have a scan of your keyboard.

You need to hold these two keys down while entering r e i s u b.

Kind regards

---

### Post by Robing Goodfellow on 2011-03-28
I forgot to mention also that at one point, about a month ago, the shutdown/restart etc icon (far upper right) disappeared as well.  I added a new one for that too.  The stuff that's disappearing is what ships with Ubuntu.  Nothing else has.  The stuff I'm replacing it with sticks (right click - add to panel - choose from the drop down list)

---

### Post by Robing Goodfellow on 2011-03-28
No, no sysrq key.  Above backspace is prt sc and pause.

I'll scan the keyboard later and figure out which it is.  Most likely one of the function keys I'm thinking.

regards, Richard

---

### Post by matt_symes on 2011-03-28
Hi

Open a terminal and type

```
nm-applet
```

or 

```
nm-applet --sm-disable
```

Post back the output. Try both.

Kind regards

---

### Post by matt_symes on 2011-03-28
Hi

> **Robing Goodfellow said:**
> No, no sysrq key.  Above backspace is prt sc and pause.

I'll scan the keyboard later and figure out which it is.  Most likely one of the function keys I'm thinking.

regards, Richard

What keyboard do you have ?

Try with print screen (PrtSc) key instead of sysrq.

Kind regards

---

### Post by matt_symes on 2011-03-28
Hi

> **vivek.pandey said:**
> i too have a similar problem. my applets are not dissapearing but my notification are has become random . when i boot sometimes i find it on top panel and some times bottom panel. its totally random

Did you right click on them and select 'Lock to Panel' ?

Kind regards

---

### Post by Robing Goodfellow on 2011-03-28
nm-applet
An instance of nm-applet is already running.

** (nm-applet:2841): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.


nm-applet --sm-disable
An instance of nm-applet is already running.

** (nm-applet:2850): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

---

### Post by matt_symes on 2011-03-28
Hi

> **Robing Goodfellow said:**
> nm-applet
An instance of nm-applet is already running.

** (nm-applet:2841): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

nm-applet --sm-disable
An instance of nm-applet is already running.

** (nm-applet:2850): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

Already running eh ? This is a chin stroking moment ;)

I'll get back to you. Did you get your sound icon back ?

Kind regards

---

### Post by matt_symes on 2011-03-28
Hi  

BTW. You can check to see if the magic key conbination is enabled in the kernel on your PC by typing (at the terminal)

```
cat /proc/sys/kernel/sysrq
```

If it returns 1 it is enabled. It should be.

```
matthew@matthew-laptop:$ cat /proc/sys/kernel/sysrq
1
matthew@matthew-laptop:$ 
```

Kind regards

---

### Post by Robing Goodfellow on 2011-03-28
No, never got the sound, nor the shutdown/restart icon back.  Replaced them with, well, replacements, from the add to panel menu.  Same functions, different icons from what ships with the OS.  I don't mind the different icons, I just have a really hard time with stuff indiscriminantly 'disappearing.'  I'm a math teacher and not even remotely computer illiterate, just new to ubuntu.  If something happens, it happens because (fill in the blank).  I'm just not strong enough in ubuntu or GNU/Linux yet to do any effective root cause analysis.  "It's a mystery" makes me a little crazy.  I learned to live with it with the first two as I was able to find suitable replacements.  No replacement for the net bars though, that I've been able to find, unless I use screenlets and those still mystify me.

Shouldn't have to find replacements though.  That tells me something changed, but durned if I can figure out what.

regards, Richard

---

### Post by Robing Goodfellow on 2011-03-28
re: sysrq

Thanks Matt!  On the G62 it's 0.

regards, Richard

---

### Post by matt_symes on 2011-03-28
Hi

I am a bit stumped by this one.

Have you considered reinstalling network manager and nm-applet. That may fix the problem. Open a terminal and type

```
sudo apt-get install --reinstall network-manager
sudo apt-get install --reinstall network-manager-gnome
```

Enter your password. It will not be echoed to the screen. Restart PC.

A disclaimer though. I am always wary of instructing people to reinstall network software. Wait to see if any body has any other idea's first. 

I will also do some more research for you.

Kind regards

---

### Post by Robing Goodfellow on 2011-03-28
Thanks Matt, I'll wait to see if there are other ideas or until you tell me to go with this one.  Not in a big hurry, I've found a workaround, though it's a bit of a pain.  I'm using the system>preferences>network connections for now.

regards, Richard

---

### Post by Robing Goodfellow on 2011-03-28
Now that the kids are in bed, I had the chance to reread all of this.  Regarding sysrq, I misread and thought something different.  So if I get 0 on

```
cat /proc/sys/kernel/sysrq
```

then I do not have a sysrq key enabled, correct?  How do I enable it?

regards, Richard

---

### Post by matt_symes on 2011-03-28
Hi

> **Robing Goodfellow said:**
> Now that the kids are in bed, I had the chance to reread all of this.  Regarding sysrq, I misread and thought something different.  So if I get 0 on

```
cat /proc/sys/kernel/sysrq
```

then I do not have a sysrq key enabled, correct?  How do I enable it?

regards, Richard

It's a compile option in the kernel so it has to be selected when the kernel is built. It should be enabled in Ubuntu by default i believe. The reason included it was because i try to avoid assumptions when it comes to computers.

It's three in the  morning here so i will not  be up much longer. Check this thread again tomorrow. Post any more question you have and either i (tomorrow) or someone else will attempt to answer them.

Kind regards

---

### Post by Robing Goodfellow on 2011-03-29
A night to sleep on it has brought more to light, unfortunately, more problems, not solutions.  Some things that had not occurred to me, all within the 36 hours preceding my original post.

I use banshee.  One of the things I liked about it was I could close the GUI and the music would still play.  Less clutter on the desktop.  Now, when I close the GUI, the music stops.  (I installed the banshee update when it came out a few days ago.  never occured to me the problems might be related, and maybe they're not).

I use Liferea.  Before all all this new and unhappy change, Liferea would leave a grey dot or moon looking icon in my panel.  Click and Liferea instantly starts.  No longer.  I have pinned the app icon to the panel, so I have functionality back, but it is as slow (which is not very, just not instantaeous) as if I did Applications>Internet>Liferea

Back when I installed Ubuntu, I played the blockdrop game (can't remember what it was called) but it stopped working, ie the screen would flash off and on when I tried to play.  No big deal, I don't do a lot of games anyway, but it was odd.  I researched a bit and it seems there is some conflict between compiz and the game, as far as I knew (I had only been on Ubuntu a coupla weeks mind you) I didn't use or need compiz, so I removed it.  No change.  Last week I tried to reinstall compiz.  According to the software center I have it, but it doesn't show up in any menu.  Also, I'm pretty sure related, the extra visual effects no longer work, even after reinstalling compiz.

I dunno if all or any of this is related.  Dumping Maverick when Natty goes stable anyway, but it's curious, and the lack of net monitor and concurrent ability to easily change which network I'm on is annoying.

regards, Richard

ps Which begs another question.  When I switch to Natty, does the stuff I have installed in Maverick migrate over, is it just like an update, or is a fresh reinstall recommended?

---

### Post by Robing Goodfellow on 2011-03-31
Problem (1 of them) solved!  I reinstalled the notifications area, (right click the panel, add to panel, scroll down to notifications area, nail it) and the nm-applet and its icon are back and working.  Still no joy on the old sound or shut down/restart switch.

regards, Richard

---

### Post by safarin on 2011-03-31
> **Robing Goodfellow said:**
> Problem (1 of them) solved!  I reinstalled the notifications area, (right click the panel, add to panel, scroll down to notifications area, nail it) and the nm-applet and its icon are back and working.  Still no joy on the old sound or shut down/restart switch.

regards, Richard

Hi Richard,

Try download and run this program.
[ATTACH]187684[/ATTACH]

This could solved all your sound and shutdown/restart switch

to run
```

$ sh PanelRestore.sh

```

Credit goes to
```

# GNOME Panel Save / Restore
# Writen by PhrankDaChicken
#
# http://ubuntu.online02.com
#
#
# Updated to add restore defaults by jimjimovich
# http://www.starryhope.com

```

---

### Post by spillage2 on 2011-03-31
HMMMMM Safarin you beat me to it...

As soon as you have your task bar sorted run the .sh folder. 

I have come to rely on this little gem especially as my young kids are always mucking around with system.

Spill.

---

### Post by matt_symes on 2011-03-31
@safarin

Nice :popcorn:

---

### Post by safarin on 2011-03-31
> **spillage2 said:**
> HMMMMM Safarin you beat me to it...

As soon as you have your task bar sorted run the .sh folder. 

I have come to rely on this little gem especially as my young kids are always mucking around with system.

Spill.

hahaha.. nobody is lose here. Win-win situation because we are ubunturian.. :D

---

### Post by Robing Goodfellow on 2011-03-31
Thank you all, I'll try it!

regards, Richard

---

### Post by Robing Goodfellow on 2011-03-31
Nice!  Worked like a champ.  

regards, Richard

---

