---
title: "Trash Dekstop Icon"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by InfectedWithDrew on 2010-07-16
I'm trying to get a trash desktop icon in 10.04. I set the value for it in gconf-editor to true but it still isn't showing, even after a reboot.

Why won't this work?

edit: SOLVED. Kids, remember, sudo and gksudo aren't just "override" commands, they do other funny things.

---

### Post by AndyP79 on 2010-07-16
Easiest way...install UbuntuTweak, then go to desktop icon settings. get the deb at their website.[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

---

### Post by InfectedWithDrew on 2010-07-16
> **AndyP79 said:**
> Easiest way...install UbuntuTweak, then go to desktop icon settings. get the deb at their website.[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

I'd rather not install anything to do something that is supposed to be supported in Nautilus already.

---

### Post by AndyP79 on 2010-07-16
Tweak is so much more then just adding something. It has PPAs, icons settings, quick tweaks, applications, it's an all in one stop for many many things. If anything, you can just un-install it out of Synap afterwards.

---

### Post by InfectedWithDrew on 2010-07-16
> **AndyP79 said:**
> Tweak is so much more then just adding something. It has PPAs, icons settings, quick tweaks, applications, it's an all in one stop for many many things. If anything, you can just un-install it out of Synap afterwards.

If I uninstall it, will my settings revert? It depends on whether or not Tweak will edit config files I don't know about, or whether it runs a daemon.

---

### Post by v1ad on 2010-07-16
no your settings wont revert. 
but why wont u right click on the bottom panel and add the trash can to it?

---

### Post by InfectedWithDrew on 2010-07-16
> **v1ad said:**
> no your settings wont revert. 
but why wont u right click on the bottom panel and add the trash can to it?

It's already there. Why can't I have a desktop icon too if I want?

---

### Post by InfectedWithDrew on 2010-07-16
Solved. Was running gconf-editor with root permissions. Running it normally fixed things.

---

