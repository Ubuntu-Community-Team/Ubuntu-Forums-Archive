---
title: "How to get Add Remove Applications in Kubuntu (not KpackageEdit)"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by dasme on 2009-04-08
[IMG]http://files.fosswire.com/2007/04/arappsmainscreen.png[/IMG]

How to get this in Kubuntu 9.04 64bit?

---

### Post by kpkeerthi on 2009-04-08
Press ALT+F2 and type **adept**

---

### Post by dasme on 2009-04-08
> **kpkeerthi said:**
> Press ALT+F2 and type **adept**

I am using Kubuntu 9.04 Jaunty beta and the adept isn't thr on my computer.

For kubuntu we have Kpackage edit. But i like the graphical interface of adept i thr anyway to install it on kubuntu?

---

### Post by kpkeerthi on 2009-04-08
```
sudo apt-get install [adept]("http://packages.ubuntu.com/jaunty/adept")
```

---

### Post by dasme on 2009-04-08
> **kpkeerthi said:**
> ```
sudo apt-get install [adept]("http://packages.ubuntu.com/jaunty/adept")
```

I get this after ur command :(

[[img=http://img9.imageshack.us/img9/5697/snapshot1luk.jpg]](http://img9.imageshack.us/my.php?image=snapshot1luk.jpg)

---

### Post by kpkeerthi on 2009-04-08
> **dasme said:**
> I get this after ur command :(

[[img=http://img9.imageshack.us/img9/5697/snapshot1luk.jpg]](http://img9.imageshack.us/my.php?image=snapshot1luk.jpg)

Sorry. I'm not able to view the pic. The proxy at work blocks. If possible, attach the screen to the post instead of an external website.

---

### Post by tarps87 on 2009-04-08
> **kpkeerthi said:**
> Sorry. I'm not able to view the pic. The proxy at work blocks. If possible, attach the screen to the post instead of an external website.

[ATTACH]109078[/ATTACH]

I can't see an error message though, did you try installing it using the command line?

---

### Post by dasme on 2009-04-08
> **tarps87 said:**
> [ATTACH]109078[/ATTACH]

I can't see an error message though, did you try installing it using the command line?

Yes i installed it using above given command.

---

### Post by tarps87 on 2009-04-08
I think I see what you're getting at, this will install the gnome add remove thing, be warn it will probably bring along several gnome libraries.
```
sudo apt-get install gnome-app-install
```

---

### Post by dasme on 2009-04-08
> **tarps87 said:**
> I think I see what you're getting at, this will install the gnome add remove thing, be warn it will probably bring along several gnome libraries.
```
sudo apt-get install gnome-app-install
```

Thanks tarps it worked using above command.  :)

Thx once again

---

