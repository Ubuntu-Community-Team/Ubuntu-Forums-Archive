---
title: "Can't install anything. says there's other installers when there isn't"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by esotericguy on 2008-12-27
I've got Ubuntu 8.10 running with the modified eee pc kernel on my (obviously) eee pc 1000ha. It's installed via Wubi. Now that the intro is out of the way.

I'm trying to install Opera, themes, etc., but it won't let me. It will allow installations from the add/remove... but not from downloaded debs.

This is the message i get:

[IMG]http://img383.imageshack.us/my.php?image=thisismyproblemqv6.png[/IMG]

so what's the verdict/advice?

---

### Post by Kosimo on 2008-12-27
> **esotericguy said:**
> I've got Ubuntu 8.10 running with the modified eee pc kernel on my (obviously) eee pc 1000ha. It's installed via Wubi. Now that the intro is out of the way.

I'm trying to install Opera, themes, etc., but it won't let me. It will allow installations from the add/remove... but not from downloaded debs.

This is the message i get:

[IMG]http://img383.imageshack.us/my.php?image=thisismyproblemqv6.png[/IMG]

so what's the verdict/advice?

Could you please write the message? :)

---

### Post by ercferret18 on 2008-12-27
what is the message you get?

have you tried restarting?

---

### Post by 2hot6ft2 on 2008-12-27
You can't have 2 installation managers working at the same time. Close one.

---

### Post by snova on 2008-12-27
Having the message would be helpful, but I'll take a guess from the thread title. ;)

If you're certain there are no package management applications running, try removing the lock file:

```
sudo rm /var/lib/dpkg/lock
```

---

### Post by esotericguy on 2008-12-28
> **Kosimo said:**
> Could you please write the message? :)


thought for sure i had attached it!
[[IMG]http://img411.imageshack.us/img411/5803/screenshotxg8.th.png[/IMG]](http://img411.imageshack.us/my.php?image=screenshotxg8.png)
[[IMG]http://img411.imageshack.us/img411/5803/screenshotxg8.png[/IMG]](http://imageshack.us)
[[IMG]http://img411.imageshack.us/img411/screenshotxg8.png/1/w1024.png[/IMG]](http://g.imageshack.us/img411/screenshotxg8.png/1/)

---

