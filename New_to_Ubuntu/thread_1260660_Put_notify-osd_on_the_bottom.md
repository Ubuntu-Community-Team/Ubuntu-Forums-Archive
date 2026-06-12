---
title: "Put notify-osd on the bottom?"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by Jimleko211 on 2009-09-07
I changed my configuration so I only have on panel, on the bottom.  However, notify-osd still appears at the top.  How I do change it to go to the bottom-right?

---

### Post by alienclone on 2009-09-07
i would also like to know the answer, and also can you turn off the notify osd completely?

---

### Post by CatKiller on 2009-09-08
I think it's just broken. It is rather new, after all. Hopefully it will be fixed by the end of next month.

---

### Post by Paqman on 2009-09-08
> **Jimleko211 said:**
> How I do change it to go to the bottom-right?

You can't. Notify-osd is still a work-in-progress though, the ability to pick where you want it to appear may be added as a feature later in the design process.

---

### Post by CatKiller on 2009-09-08
> **Paqman said:**
> You can't. Notify-osd is still a work-in-progress though, the ability to pick where you want it to appear may be added as a feature later in the design process.

That's why I said it's broken. The ability to pick the location is already there. It just doesn't do anything.

---

### Post by philinux on 2009-09-08
> **alienclone said:**
> i would also like to know the answer, and also can you turn off the notify osd completely?

If you want it gone look here.

[http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/](http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/)

---

### Post by alienclone on 2009-09-08
> **CatKiller said:**
> That's why I said it's broken. The ability to pick the location is already there. It just doesn't do anything.

can you tell us where the option is so that when it is fixed we will know how to change it?

---

### Post by alienclone on 2009-09-08
> **philinux said:**
> If you want it gone look here.

[http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/](http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/)

thankyou philinux, very nice find.

---

### Post by detroit/zero on 2009-09-08
It is possible to move the notifications to the bottom right of the screen.

[http://dagus.org/2009/06/09/ubuntu-notification-dirty-hack-por-displaying-notifications-on-the-bottom/](http://dagus.org/2009/06/09/ubuntu-notification-dirty-hack-por-displaying-notifications-on-the-bottom/)

---

### Post by CatKiller on 2009-09-08
> **alienclone said:**
> can you tell us where the option is so that when it is fixed we will know how to change it?

```
notification-properties
```

I have no idea if it normally gets a menu entry.

---

### Post by tim71 on 2009-09-20
```
$ notification-properties
The program 'notification-properties' is currently not installed.  You can install it by typing:
sudo apt-get install notification-daemon
bash: notification-properties: command not found
```

notification-properties is related to old notification-daemon and would not help with notify-osd.

I keep the notification area at the lower end of the screen and find the default behaviour - "North-East" - just incompatible...

I think that if there is a need to one non-configurable positioning option, then the positioning should honour the position of notification area on the desktop - plain and simple! Current (on-configurable) default option just makes whole configurability of GNOME panels totally useless...

P.S. This non-configurability-problem is somehow related with the "simplicity-concept" that is propagated by some people at Canonical, but sometimes it just feels, like they mean this "simplicity" from the standpoint of the programmer and/or developer, because all configurability options will need more code for implementing.

---

