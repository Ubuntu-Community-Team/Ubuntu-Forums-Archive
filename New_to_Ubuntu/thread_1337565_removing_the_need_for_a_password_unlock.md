---
title: "removing the need for a password unlock"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by pendulum101 on 2009-11-25
just wondering if there is any way that i can allow my user profile to carry out actions such as CPU frequency scaling and drive mounting without the need to enter a password i didn't have this problem with 9.04 but since upgrading to 9.10 this has become an issue if there is a way around it i would really like to hear about it 
thanks in advance

---

### Post by Paqman on 2009-11-26
Have you got all the latest updates installed in Karmic. There were some drive mounting permissions bugs during testing, but they should be sorted in the release or later versions.

---

### Post by 3rdalbum on 2009-11-26
Drive mounting is now handled through Policykit. In Gnome there's a utility that can edit Policykit settings so that your disk mounting can be done (or not done) by a particular user with/without a password.

CPU frequency scaling might also be handled by Policykit; I'm not sure. Sorry I can't be of more help there.

---

### Post by pendulum101 on 2009-11-26
> **3rdalbum said:**
> Drive mounting is now handled through Policykit. In Gnome there's a utility that can edit Policykit settings so that your disk mounting can be done (or not done) by a particular user with/without a password.

CPU frequency scaling might also be handled by Policykit; I'm not sure. Sorry I can't be of more help there.

I tried to locate Policykit but with no success where can i find it

---

### Post by mc4man on 2009-11-26
till such time as they provide a way to set authorizations you can do yourself.
Note that you shouldn't overdo this or unexpected behavior will result.

An update to devicekits may necessitate resetting ( or provide means

For cpu applet(s) (**read edits also**)
  [http://ubuntuforums.org/showthread.php?p=8158855#post8158855](http://ubuntuforums.org/showthread.php?p=8158855#post8158855)

If you can't find a utility to set auth. for mounting of internal drives then this is a bit clearer than from above thread, though same thing

[http://ubuntuforums.org/showthread.php?p=8203192#post8203192](http://ubuntuforums.org/showthread.php?p=8203192#post8203192)

---

### Post by pendulum101 on 2009-11-26
> **mc4man said:**
> till such time as they provide a way to set authorizations you can do yourself.
Note that you shouldn't overdo this or unexpected behavior will result.

An update to devicekits may necessitate resetting ( or provide means

For cpu applet(s) (**read edits also**)
  [http://ubuntuforums.org/showthread.php?p=8158855#post8158855](http://ubuntuforums.org/showthread.php?p=8158855#post8158855)

If you can't find a utility to set auth. for mounting of internal drives then this is a bit clearer than from above thread, though same thing

[http://ubuntuforums.org/showthread.php?p=8203192#post8203192](http://ubuntuforums.org/showthread.php?p=8203192#post8203192)

perfect that worked great i used the second link you provided just for anyone else's information [HTML]http://ubuntuforums.org/showthread.php?p=8203192#post8203192[/HTML]

---

