---
title: "'Restriced Extras' installation"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by newbie1000 on 2008-12-23
My Totem video player will not play many video files.
It says I need codecs for them, like for .mpg and .wmv files.

Will the Ubuntu 'Restricted Extra' package fix my problem and if so, how do I install it?

---

### Post by Duck2006 on 2008-12-23
Go to Synaptic Package Manager and you can install it from there, do a search for

Ubuntu-Restricted-Extras

---

### Post by newbie1000 on 2008-12-23
The Package Manager said I should install 'it directly'.
What does that mean?

---

### Post by SuperSonic4 on 2008-12-23
```
sudo apt-get install ubuntu-restricted-extras
```

I find [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) invaluable when dealing with multimedia

---

### Post by Duck2006 on 2008-12-23
From the terminal

sudo aptitude install ubuntu-restricted-extras

---

### Post by ugm6hr on 2008-12-23
> **supersonic4 said:**
> i find [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) invaluable when dealing with multimedia

+1

---

### Post by newbee70 on 2008-12-23
> **newbie1000 said:**
> My Totem video player will not play many video files.
It says I need codecs for them, like for .mpg and .wmv files.

Will the Ubuntu 'Restricted Extra' package fix my problem and if so, how do I install it?

goto applications "upper left toolbar".
add/remove

check ALL available packages at the top, in the search bar type in ubuntu
this first item will be the restricted click add.

---

### Post by newbie1000 on 2008-12-23
> **SuperSonic4 said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

I find [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) invaluable when dealing with multimedia

I get a Java agreement.   How do I 'OK' it?

---

### Post by SuperSonic4 on 2008-12-23
Press tab and then ok but Java is superfluous to video playing

---

### Post by newbie1000 on 2008-12-23
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


Do I need to type in anything before dpkg --configure -a?
:confused:

---

### Post by mikewhatever on 2008-12-23
Yes, run <sudo dpkg --configure -a>.

---

### Post by newbie1000 on 2008-12-23
It's still not working within Firefox.

How the heck do you **find** the correct files to set Firefox to use Gnome Mplayer (which will play the files)?

---

### Post by Duck2006 on 2008-12-23
In Synaptic Package Manager you will find it there. Just open Synaptic Package Manager and do a search for it, mark it and apply, it will load it for you.

---

### Post by oldos2er on 2008-12-23
> **newbie1000 said:**
> It's still not working within Firefox.

How the heck do you **find** the correct files to set Firefox to use Gnome Mplayer (which will play the files)?

 You probably need the mozilla-mplayer plugin.

---

### Post by newbie1000 on 2008-12-23
I'm talking about setting the preferences in Firefox to use another program besides Totem (others).

---

### Post by oldos2er on 2008-12-23
> **newbie1000 said:**
> I'm talking about setting the preferences in Firefox to use another program besides Totem (others).

 Edit, Preferences, Applications, double-click on the app you want to change.

---

