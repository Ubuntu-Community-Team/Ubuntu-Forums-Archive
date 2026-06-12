---
title: "/home not visible under Computer once Ubuntu starts"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by jal301 on 2009-01-03
I apologize if this is ridiculously elementary but I suppose that's why we're in beginner's talk....

Anyhow, I followed the directions from ([http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)) and modeled the very last pic showing Ubuntu / (Ext3) at 7gb, Ubuntu /home (Ext3) for 490gb, and a 3gb swap.  I imagined that once I booted that /home or some folder of the like would show up under Computer, but it doesn't.  So I booted with the CD and I can see it there.

How do I get this to show under Computer?  What I would like to do is have this home drive contain all documents (files, music, movies, etc) but I am not quite sure how to access it.

---

### Post by jal301 on 2009-01-03
Wow, this was incredibly simple.  I now see the "Home" folder as my user name.  Is there any way to make this appear under Computer or as a desktop shortcut icon?

---

### Post by civillian on 2009-01-03
it isn't visible under "computer" when you access it from nautilus, however if you click the "home" button from next to the computer button and it should take you to 
/home/jal301 (or whatever your username is).

/home won't show up but if you go into "file system" it will be there (just called home).
If you go into view menu and click the "side pane button) or just hit f9 and the sidepane will show up and your home will be the the first shortcut on the top of the menu.

Hope this is clear enough...

---

### Post by Paqman on 2009-01-03
You home will be listed under Places.

You can also find it at Places > Computer > Filesystem > home > username.

---

### Post by louieb on 2009-01-03
Isn't your home folder the 1st thing listed in the places menu? 

Under computer you will find /home in the file system folder.

If more questions please post the output of ```
df -h  
```

---

### Post by Paqman on 2009-01-03
> **jal301 said:**
> Is there any way to make this appear under Computer or as a desktop shortcut icon?

Technically your desktop is actually within your home folder, so a shortcut would kind of be going round in circles.

If you really want a shortcut on the desktop instead of in Places though, just drag and drop.

---

### Post by SonicSteve on 2009-01-03
If you want a desktop Icon do this.
Pres alt f2 this will load the run application window.
type gconf-editor and click run
expand apps
expand nautilus 
click on the desktop item
then put a checkmark in home icon visible. 
TA-DA! 
This would work for any linux version that uses Gnome and Nautilus


By the way,

Be careful what else you do in Gconf-editor unless you know what you are changing it's best not to. It's a bit like the windows registry in some ways.

---

### Post by SonicSteve on 2009-01-03
> **jal301 said:**
> I apologize if this is ridiculously elementary but I suppose that's why we're in beginner's talk....

Anyhow, I followed the directions from ([http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)) and modeled the very last pic showing Ubuntu / (Ext3) at 7gb, Ubuntu /home (Ext3) for 490gb, and a 3gb swap.  I imagined that once I booted that /home or some folder of the like would show up under Computer, but it doesn't.  So I booted with the CD and I can see it there.

How do I get this to show under Computer?  What I would like to do is have this home drive contain all documents (files, music, movies, etc) but I am not quite sure how to access it.


By the way this a very good way to partition the hard drive. I usually follow it as well. The only thing to keep in mind is that if you run into problems and want to re-install, often the problems stem from the settings from the home folder. It contains all the settings for each user of the computer. So if the problems are user settings based this partition needs to be formatted (after you back up documents) or else as soon as the installation is done all the old user settings will come back, both good and bad. 

For example. 
If you follow the gconf-editor advice then re-install ubuntu without formatting the /home partition this change you make to gconf-editor will still be there when the installation is done. This would be an example of good.

---

### Post by jal301 on 2009-01-04
Thank you all for the good words and great advice.  This gives me a lot to work with and great direction.  You are all very helpful and have gone above and beyond the call!

---

