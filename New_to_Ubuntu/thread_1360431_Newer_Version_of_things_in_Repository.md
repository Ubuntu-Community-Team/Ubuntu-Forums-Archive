---
title: "Newer Version of things in Repository"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by bigaldizzler on 2009-12-20
Hi,

I did a search on google and a brief one here but dont know for certain so I am asking, sorry if this has been asked many times.

Ok so the problem, I have a dell mini10v netbook the touchpad is terrible if you ever used one, stupid design!!! #-o To my surprise on ubuntu 9.10 karmic koala the touchpad works fantastically compared to 9.04 BUT the internet is frustratingly slow!!!

What I want to do is install ubuntu 9.04 again but download a updated version of the synaptic mouse driver used in karmic koala...how do I go about doing that?

The driver that I want to update is 

xserver-xorg-input-synaptics touchpad driver

---

### Post by Chesamo on 2009-12-20
What you're talking about is using the Karmic repos in Jaunty. This is possible, but not recommended.

A better option is to use the Backports respository. Go to System > Administration > Software Sources and check all the boxes that say "Backports" next to them.

---

### Post by snowpine on 2009-12-20
Every package from every current Ubuntu release is available for download at packages.ubuntu.com, for example:

[http://packages.ubuntu.com/karmic/xserver-xorg-input-synaptics](http://packages.ubuntu.com/karmic/xserver-xorg-input-synaptics)

But beware! You can't just upgrade xserver-xorg-input-synaptics alone. It depends on some pretty important stuff. In other words, I don't recommend mixing Jaunty and Karmic.

ps As you can see from the link above, xserver-xorg-input-synaptics is not in jaunty-backports. Enabling the backports repo will not help you.

---

### Post by Chesamo on 2009-12-20
> **snowpine said:**
> ps As you can see from the link above, xserver-xorg-input-synaptics is not in jaunty-backports. Enabling the backports repo will not help you.
My mistake. Although, since it's not in jaunty-backports, that means it may not work in Jaunty at all. Keep that in mind.

---

### Post by bigaldizzler on 2009-12-21
OMG You guys are awesome! I should of asked earlier would of saved me alot of time reinstalling and tinkering around!

Thanks for the quick reply you guys are awesome!!! :KS

---

### Post by Yvan300 on 2009-12-21
Instead of using the backport repos which may potentially break your system why not fix your slow internet problem?

---

### Post by steveneddy on 2009-12-21
Here is the ppa for the synaptics touchpad:

[http://www.unblockade.com/index.php?____pgfa=aHR0cHM6Ly9sYXVuY2hwYWQubmV0L353Z3JhbnQvK2FyY2hpdmUvcHBh&field.series_filter=jaunty](http://www.unblockade.com/index.php?____pgfa=aHR0cHM6Ly9sYXVuY2hwYWQubmV0L353Z3JhbnQvK2FyY2hpdmUvcHBh&field.series_filter=jaunty)

check the listing to see if it is the version you want or newer.

You may experience issues by using non stable files in your new repo.

Many of us prefer to "fix" issues by running out of repo ppa's from the developer.

---

