---
title: "panel missing"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by blessedatheist on 2010-06-09
Hi,
Yesterday I tried moving the bottom panel to the top panel. As soon as I did that the system is irresponsive. I'm new, so I've been trying all sorts of commands suggested by help, but nothing seems to work. I don't have access to system, applications...nothing! All I can start is cttrl+l, ctrl+s and a few other things...any suggestions?
Sorry for the trouble and thanks a lot.l

---

### Post by blessedatheist on 2010-06-09
...and of course, I can't just drag the panel bars...

---

### Post by nick_goodfate on 2010-06-09
how did you move the bottom panel to the top ? the panel which was at the top ,is now under the panel you moved ?

---

### Post by roger_1960 on 2010-06-09
Hi

Have you tried Alt-F2 (together) and then type gnome-panel in the box and Return?

This should reinstate panels.

(If you type nautilus instead, you should get the file manager.)

---

### Post by blessedatheist on 2010-06-09
> **nick_goodfate said:**
> how did you move the bottom panel to the top ? the panel which was at the top ,is now under the panel you moved ?
I just dragged the bottom panel to the top wondering that if I could insert it there and save some space...

---

### Post by blessedatheist on 2010-06-09
> **roger_1960 said:**
> Hi

Have you tried Alt-F2 (together) and then type gnome-panel in the box and Return?

This should reinstate panels.

(If you type nautilus instead, you should get the file manager.)
alt+F2 doesn't respond. What should it do?

---

### Post by nick_goodfate on 2010-06-09
if you right click on the panel you moved and select delete this panel ? if i understand right the original top panel is under the moved one . so try to delete it and then add a new one at the bottom.

---

### Post by blessedatheist on 2010-06-09
> **nick_goodfate said:**
> if you right click on the panel you moved and select delete this panel ? if i understand right the original top panel is under the moved one . so try to delete it and then add a new one at the bottom.
I don't get any reaction when I right-click the panel!! :s I can only right-click the desktop...the panels are together and they have "crashed" and don't respond to anything :S

---

### Post by gandaran on 2010-06-09
have you rebooted the computer?

---

### Post by blessedatheist on 2010-06-09
> **gandaran said:**
> have you rebooted the computer?
It was the first thing I did and have done it several times since :(

---

### Post by nick_goodfate on 2010-06-09
im trying to add a second panel on my desktop , so i can drag on the other to see what happened to you . But i just realized that the add new panel doesnt work :p

---

### Post by blessedatheist on 2010-06-09
> **nick_goodfate said:**
> im trying to add a second panel on my desktop , so i can drag on the other to see what happened to you . But i just realized that the add new panel doesnt work :p
really?! crazy stuff...
I mean, I'm a bit new to ubuntu, but I've always been able to solve glitches when I used windows...I'm guessing the installation is corrupted...or something? Do you think I could just reinstall the panel or?
I managed to search "gnome-panel" and got many results. I've tried double-clicking on the executables, but nothing happened..so, I'm running out of ideas.

---

### Post by gandaran on 2010-06-09
well, I know of one way to fix it, delete the hidden home user .gconf folder and reboot, I don't recommend this as you will loose every desktop and applications user settings, unless you don't mind starting all over again do it or wait until someone else can help you.

---

### Post by roger_1960 on 2010-06-09
Hi

You could try this:

Boot into recovery mode ie hold down shift key while booting.  You should get a choice of boot configurations - go for the latest kernel in recovery mode( usually second option down)  Then select "drop to root shell prompt" and you should have a text cursor.  Be careful - you now have full priveledges over everything!

Then

> apt-get purge gnome-panel

apt-get install gnome-panel


(One line at a time folling each with return)

Then reboot normally ( you can type "shutdown now" at the prompt to do this)

---

### Post by pete_m on 2010-06-10
apt-get Purging software seems well over the top . . .

if your other user accounts and gnome fail-safe works then it shouldn't be necessary i think.

wouldn't simply deleting all the /gconf n similar files in one's home do the trick n force gnome back to its( /etc/skeleton ? ) defauls.

i think that if you use gconf-editor iin a shell you may well be able to re-instate panels as well as many other desktop features.

hope this helps . .

[screenshots  ]("http://www.youtube.com/watch?v=YoI4wRVVjBs")__of my ( presntly interrupted ) work in progress on a flexible ubuntu-based desktop - 
with apps, system tools and status on the top bar, 
active windows n workspaces in the bottom bar 
n cairo-dock/ compiz effects and nautilus or nbr/ une desktop

---

### Post by keroman on 2010-06-11
this worked for me, I had no panels.
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by pete_m on 2010-06-11
thanks keroman- that's a fine link..much  clearer than my late-night mutterings -while trying to get over upgraade worsening woes...

strikes me that posts on this thread n more generally hereon the forums - specially from newbies ( like myself with a grand total of 5 months Ubuntu n not yet 18 months on my Linux netbook )
tend to go for drastic solutions to perceived 

my woes started after developing probs with nautilus desktop prompted me to upgrade - and i thought i'd lokked before the leap by successfully upgrading kernel and extensively previewing forthcoming changes with apt-get -s upgrade n dist-upgrade.
used aptitude safe-upgrade when i actually ran it... nothing broke .. butt on reboot... no joy n all ni can do is get a root shell by editing grub commans. from there at a loss how to get network..
init 2 socket fails to connect - com/ubuntu/upstart : Connection refused



btw where you in n. yrks ? i've family in ripon...!

---

### Post by keroman on 2010-06-11
hi pete_m

sounds like you're having a rough time, I am fairly new to this myself, I  am sure someone with greater knowledge will be along shortly, they really are helpful here, also found this which may be of use for panels,    [http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

  am nearer heartbeat country, but was in London to see Oliver at Theatre Royal on Monday

---

### Post by blessedatheist on 2010-06-18
> **keroman said:**
> hi pete_m

sounds like you're having a rough time, I am fairly new to this myself, I  am sure someone with greater knowledge will be along shortly, they really are helpful here, also found this which may be of use for panels,    [http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

  am nearer heartbeat country, but was in London to see Oliver at Theatre Royal on Monday

Hello Keroman!!! IT WORKED!!! very easy and quick! I had tried everything else with no avail whatsoever. Thanks so much!
And thanks a lot to everybody who has replied to this thread - I really appreciate it :)

---

### Post by keroman on 2010-06-18
you're welcome

---

