---
title: "My Main Panel Has Disappeared!!"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Roger Allott on 2011-04-03
I've just booted up Ubuntu (maverick) and to my horror, there's no main panel!! Where did it go? Why did it go?? How do I get it back???

More by luck than judgement, I hit Alt-F1 to bring up my Applications list so I can at least do some stuff, but without my panel I'm .... well, just a bit lost really.

Any help would be very gratefully received!

---

### Post by Thijk on 2011-04-03
Open a terminal and enter

```
sudo debconf gnome-panel 
```
That gives you the basic functionalities, if you had other things on there, you'll have to add them manually

---

### Post by Thijk on 2011-04-03
If that doesn't work, you can right click on the bottom panel (if you still have that one) right click and select "new panel"

And then you can add everything manualy, with "add to panel"

---

### Post by Roger Allott on 2011-04-03
Oddly, my panel reappeared, almost as mysteriously as it vanished!

It seemed to reappear just as Update Manager did an auto kick-in.

---

### Post by ashhab2010 on 2011-04-03
you might have kept it on auto hide...

---

### Post by Roger Allott on 2011-04-16
I've just booted up Ubuntu again and got exactly the same problem.

Anyone got any ideas:
a) how I can get my panel back?
b) how I can prevent this non-appearance of the panel from happening on subsequent boots?

---

### Post by Roger Allott on 2011-05-08
> **Thijk said:**
> Open a terminal and enter

```
sudo debconf gnome-panel 
```
That gives you the basic functionalities, if you had other things on there, you'll have to add them manually

Im still getting this problem every so often, so I just tried your suggestion and got this response:

```
stuart@stuart-laptop:~$ sudo debconf gnome-panel
[sudo] password for stuart: 
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:3590): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name
```

---

### Post by keroman on 2011-05-08
try this, worked for me


[http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/](http://www.starryhope.com/linux/ubuntu/2010/restore-the-default-panels-in-ubuntu/)

---

