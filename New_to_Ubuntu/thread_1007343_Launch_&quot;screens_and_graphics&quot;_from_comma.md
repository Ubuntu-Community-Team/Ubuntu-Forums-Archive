---
title: "Launch &quot;screens and graphics&quot; from command line"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by stevebond001 on 2008-12-10
Hi
Can anyone please give me the command to run the "screens and graphics" program, used to identify and set the monitor type (and associated resolutions).

I am stuck at a low resolution and can't add the "screens and graphics" icon to the menu ('cos it doesn't appear when setting up the main menu).

Many thanks

---

### Post by mc4man on 2008-12-10
```
gksu displayconfig-gtk
```

Not for intrepid

---

### Post by stevebond001 on 2008-12-10
mc4man
Thanks very much for the quick reply - much appreciated.

However, I am running Intrepid - Sorry, forgot to mention it in the original post

Any ideas?

---

### Post by stevebond001 on 2008-12-10
Anyone ????

---

### Post by anim on 2008-12-10
gnome-display-properties

?

---

### Post by stevebond001 on 2008-12-10
anim
Thanks for the advice.  However, this launches the screen resolution program.  Unfortunately this does not show the correct resolution for my monitor (I want 1280 x 1024).

The "Screens and Graphics" program, included in Hardy but for some reason missing in Intrepid, lets you select your monitor by manufacturer and configure the appropriate resolutions for it.

I find it hard to believe that something so useful has been removed from Intrepid - surely I'm not the only one with this problem??

---

### Post by oldsoundguy on 2008-12-10
No, you are not the only one with the problem.  It seems to have been totally ignored by the developers, by the card makers (I suspect you are running NVidia), and the people at Envy are up to their ears in the swamp that Intrepid/Gnome (note that a lot of the issues go away if you use KDE as the desktop!) created trying to figure out how to get things working PROPERLY.  You will find all sorts of threads all over these forums and the NVida forums concerning the issue you have along with all sorts of other issues with the "driver package from hell" that does not work properly.  Niceties like RandRotate do not work either!  AND problems with such as Compiz, you name it!  It has been 6 weeks since release and very little progress has been made other than page after page after page of code that has to be copied and pasted into terminal in HOPES of getting the display to work .. note the HOPES .. sometimes yes most times NO.

I used the legacy the drivers in synaptic and was able, at least, to finally get the proper resolutions (including a wide aspect monitor on one set up), but that is it.  No bells, whistles, OR eye candy!

---

### Post by anim on 2008-12-11
There is a way to manually add resolutions to xorg.conf if i'm not mistaken. Otherwise I'm afraid I'm at a loss.

---

### Post by mc4man on 2008-12-11
This was an interesting thread from the testing

[http://ubuntuforums.org/showthread.php?t=930166&highlight=screens+graphics](http://ubuntuforums.org/showthread.php?t=930166&highlight=screens+graphics)

---

### Post by Michael.Godawski on 2008-12-11
There is a project going on to replace the displayconfig-gtk
with X-kit:

[LIST]
[*][https://launchpad.net/x-kit](https://launchpad.net/x-kit)
[/LIST]

---

### Post by JoshuaRL on 2008-12-11
The issue here is displayconfig-gtk.  It is the GTK+ port of displayconfig for KDE.  Since the original is still in KDE, that is why you don't have the same issue in Kubuntu.  But I believe XrandR is the preferred way to deal with autodecect issues in Intrepid.

---

### Post by anim on 2008-12-18
I have a quick solution for you guys (hopefully!)
```
sudo apt-get install gnome-randr-applet
```

Logout of the session and log back in. You may have to restart the entire computer, I didn't though.

then rt click on the panel and add the applet screen resolution and orientation. Click on the applet and select new resolution. 

Let me know if that works

/pck
{Edit} - this is a graphical front-end for xrandr. By searching for more information on it (xrandr) you may find a more 'consoly(TM)' solution. The man page ($ man xrandr) is also quite useful.

---

