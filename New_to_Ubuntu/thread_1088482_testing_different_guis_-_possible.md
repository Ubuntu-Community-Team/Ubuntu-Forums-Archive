---
title: "testing different guis - possible?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by longtom on 2009-03-06
Hi,

tried to do some research but wasn't able to find a definite answer.  

Is it possible for me in Ubuntu to load KDE (or any other GUI for that matter) and be abale to switch between my existing Gnome and whatever I installed additionally without loosing anything?

If yes - please kick me to the next possible documentation in order to get me there.

Thank you!

longtom

---

### Post by mikewhatever on 2009-03-06
Here you go.
[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)
[http://psychocats.net/ubuntu/xfce](http://psychocats.net/ubuntu/xfce)

---

### Post by JoshuaRL on 2009-03-06
> **longtom said:**
> Hi,

tried to do some research but wasn't able to find a definite answer.  

Is it possible for me in Ubuntu to load KDE (or any other GUI for that matter) and be abale to switch between my existing Gnome and whatever I installed additionally without loosing anything?

If yes - please kick me to the next possible documentation in order to get me there.

Thank you!

longtom

No problem, I do that on all my installs.  Just apt-get one of the desktops:
```

sudo apt-get install kubuntu-desktop

```
That's for KDE, but the full Kubuntu experience.  Here's for Xubuntu (XFCE):
```

sudo apt-get install xubuntu-desktop

```
Those are metapackages, so they are kind of a shell that pulls all the other packages the system needs to run those desktop environment.  APT can't delete metapackages, so if you ever decide you're short on disk space, just use aptitude like so:
```

sudo aptitude remove xubuntu-desktop

```

---

### Post by longtom on 2009-03-06
Psychocats - why didn't I think of that myself...(answers on a postcard...)

Thats great!

Also thank you very much for those short and powerfull terminal thingys..:P;)....
Seriously - a great way to get things going fast if you know what you are doing.

greetings

longtom

PS:  Might this possibly slow down my system as a whole?

---

### Post by longtom on 2009-03-06
Just to rewrite my above concern:

Might this possibly slow down my system as a whole?

And another one:

When I wnat to install with Synaptic it says:

To be removed:

Openoffice.org-debian-menus

What does that mean?  I don't want to have anything changed....

Please advise!

longtom

---

### Post by mcduck on 2009-03-06
Installing many desktop environments won't have any effect on your computer's speed, after all you only run one of them at a time. You can choose which one to use when you log in.

What comes to the message about removing that package, quite likely what you are trying to install provides same (or more) functionality than that package has, and therefore that package is removed and some other one installed in it's place.

---

### Post by longtom on 2009-03-06
> **mcduck said:**
> Installing many desktop environments won't have any effect on your computer's speed, after all you only run one of them at a time. You can choose which one to use when you log in.

What comes to the message about removing that package, quite likely what you are trying to install provides same (or more) functionality than that package has, and therefore that package is removed and some other one installed in it's place.

Yeah - you're probably right.  I'll have a go...what an adventure.:P

longtom

---

