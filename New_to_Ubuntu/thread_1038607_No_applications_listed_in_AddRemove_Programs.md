---
title: "No applications listed in Add/Remove Programs"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by DaveKlynch615 on 2009-01-12
Hello,

A strange thing happened with my installation of Ubuntu 8.10.  I went to add a certain application today only to find out that no applications are being listed in Add/Remove Applications (not even the applications that are currently installed on my system).  I thus decided to reboot, but that did not change anything.

Yesterday everything was working fine, I was able to add/remove applications.  I cannot remember anything that I would have done that would of caused this to happen.

Recently, I:
- installed Adobe Air to use TweetDeck, but I don't think doing that would have effected anything since Adobe Air does not come through any of the repositories.

- I allowed certain updates to be installed earlier today when I was prompted by the update icon.  I do not remember what installed since I didn't pay much attention to it.  I assume that this could have caused some kind of conflict but I don't know where to start.

When I go to Add/Remove applications, this is the screen I get:
[IMG]http://farm4.static.flickr.com/3256/3192467615_5c176fb3f9_o.png[/IMG]

---

### Post by drs305 on 2009-01-13
Adobe Air has caused this problem for several users.

Try reinstalling this:
```

sudo apt-get remove gnome-app-install
sudo apt-get install gnome-app-install

```

---

### Post by Partyboi2 on 2009-01-13
To reinstall  gnome-app-install you can open a terminal (Applications>Accessories>Terminal) and ```
sudo apt-get --reinstall install gnome-app-install
```

---

### Post by DaveKlynch615 on 2009-01-13
Thanks everyone!  That fixed it.  

It does not seem to be letting me mark this as solved right now.  I'll try again later.

---

### Post by chuuk on 2009-01-25
Yep, just to confirm this solution does work flawlessly.

---

### Post by loud_monkey on 2009-02-03
Had the same problem after installing adobe air.  This also fixed it for me.  Thank you!

---

### Post by ymk on 2009-02-06
Cheers worked for me too

---

