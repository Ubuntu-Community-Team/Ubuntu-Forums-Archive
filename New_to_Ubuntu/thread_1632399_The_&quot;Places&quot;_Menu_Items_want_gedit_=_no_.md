---
title: "The &quot;Places&quot; Menu Items want gedit = no access"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by Ricalsin on 2010-11-27
Newbie:  :D

Problem: Trying to open anything from the Places dropdown menu generates the attached screenshot.  I don't know why the default program to open anything under that menu is gedit - it would seem to me it should be nautilus, but I do not know how to check or fix that.

A week ago I installed 10.10 (Maverick) from CD, then about 10 programs from repositories - all good.  Even installed the CCSM and Emerald and that seemed great too. Then tried to chmod 777 some folders in order to install a website development framework (Concrete5) and to setup a local directory under the home folder for multiple websites to be under construction.  I'm not sure exactly when the above described problem started to occur.  I do think I may have accidentally changed something from within the terminal when I was struggling with the Apache server config settings.  (BTW: What is the difference between sudo and gkudo ??)

To be clear: I can go to the desktop and open anything I want.  However, if I try to access anything from the places menu I get the screenshot that I have attached (Desktop, Home, anything comes up the same).  I am not against a re-installation of Ubuntu but I would like to learn from my mistake if possible.

Any help is greatly appreciated.  (I found nothing on this issue by way of searching the forums.)

Thanks.

---

### Post by jmwilli25 on 2010-11-27
Give this a try

```
sudo debconf gnome-panel
```

Or you could right click on the panel and click 'add to panel...' then scroll down to '**menu bar**, a custom menu bar' and add it. See if the problem still persists.

---

### Post by mc4man on 2010-11-28
see here
[http://ubuntuforums.org/showthread.php?p=10098466#post10098466](http://ubuntuforums.org/showthread.php?p=10098466#post10098466)

---

### Post by Ricalsin on 2010-11-28
@jmwilli25: Here's the terminal response to sudo debconf gnome-panel:

```
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:2962): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name
```

Then, I tried to reinstall gnome-panel and got this error message:

```
E: man-db: subprocess installed post-installation script returned error exit status 1
```

RESOLVED: Strangely, at this point the folders from under the Places sub-menu opened normally; however, it also blew out the home folder and all of it's contents - which is not something I would want to repeat when I'm further down the line with Linux (dangerous!).  

**@mc4man: I followed your link (after the steps mentioned above) and that seemed a more reasonable response.  At this point I've lost my home folder and I'm not sure how to reset that.** 

In the future: Was jmwilli25's code suggestion the reason for my lost home folder and contents or was it due to my re-installation of the gnome-panel?  Can someone briefly explain what might have caused this original problem in order that I might learn from it?

Thank you!
:popcorn:

---

### Post by Ricalsin on 2010-11-28
Okay, simply logging out and rebooting re-established the original home folder.  That's a bit disconcerting though that an entire home folder can be so easily erased, as that is where I was planning on setting up my web development work - I guess it just takes getting used to.  

I really like the ubuntu OS though.  Awesome!

For newbs (like myself): I created this problem by opening a folder through the terminal with the gedit in the command line: Like "sudo gedit <some folder name>".  As noted above, Linux has a default selection that makes this choice the default program of choice for all future files or folders of this type.  If it happens to be the wrong choice (like mine was) then you've just set the wrong default program to be used.  How to correct it is best described in the link provided by mc4man.

Thanks again for you help!

---

