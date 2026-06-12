---
title: "Installing Wine..."
date: 2009-01-10
forum: New to Ubuntu
---

### Post by triFeral on 2009-01-10
I just got my Ubuntu Live CD of 8.04 (Way to go, UPS), and I was wondering how to put Wine.
I've heard of it before and I'm a complete noob to Ubuntu.
I googled it and got no progress :confused:

The only things I know to do is pretty much just how to open up a terminal and type random 'sudo' things in. :(

So, something a little bit simple might help.
Thanks :D

---

### Post by taurus on 2009-01-10
Have you installed it on your machine?  If you want to install wine, just look for it in System -> Administration -> Synaptic Package Manager or install it from a terminal.

```
sudo apt-get update
sudo apt-get install wine
```

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by cwsnyder on 2009-01-10
Go to your System menu, then select Administration >> Synaptic Package Manager.  Enter your password when requested.  When Synaptic opens, in the search box, type WINE and press Enter.  Right click the box to the left of the wine entry and select Mark for Installation from the context menu, then select the Apply check mark button.  Now answer any questions which pop up.

This should install WINE.

Sorry Taurus, I'm slow.

---

### Post by Hangwire on 2009-01-10
Be sure to get 1.1.11 , not 1.1.12 - there is a nasty bug which makes wine unusable, some winecfg errors.

---

### Post by triFeral on 2009-01-10
Ah thanks, but I search in the box for the Synaptic Package Manager wine and WINE (Case sensitivity?) and I got three results...

kde-guidance
libdscaler
pptview

And for the first way to do it, I put in both codes but got:

"E: Package Wine has no installation candidate"

---

### Post by Hangwire on 2009-01-10
> **triFeral said:**
> Ah thanks, but I search in the box for the Synaptic Package Manager wine and WINE (Case sensitivity?) and I got three results...

kde-guidance
libdscaler
pptview

Hm.. weird...

Try what taurus said.

```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by taurus on 2009-01-10
Make sure you have all the repos (universe & multiverse) enable in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.

---

### Post by triFeral on 2009-01-10
> **taurus said:**
> Make sure you have all the repos (universe & multiverse) enable in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.

THANK YOU!
I was sitting here. wondering...

hehe

---

