---
title: "How do I completely replace gnome panel with AWN?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by maduranga on 2008-12-07
Can someone help me to completely replace the gnome panel with AWN? I still have problems with that. It seems like I'll miss notification area, network icon, windows list, a good menu system, if i'm gonna delete gnome panels.

Please someone help me

thanks

---

### Post by Joeb454 on 2008-12-07
I would recommend you keep the top panel, as this way you can keep your notification area etc.

That's how I have mine set up, AWN at the bottom, and a gnome panel at the top :)

---

### Post by kaivalagi on 2008-12-07
I no longer use a notification applet with gnome, I use pynot in awn..

I am using an alternative repo to install AWN which has all the nice applets...

To setup, the new package archive needs to be setup in sources.list. Do this as follows:

1) run the following in the terminal to "trust" the repo:

```
wget http://download.tuxfamily.org/syzygy42/F4ECF181.gpg -O- | sudo apt-key add -
```

2) Edit your sources.list file:

```
gksudo gedit /etc/apt/sources.list

```

3) Add this new ppa location for the packages to the bottom of your sources.list and save:

```
## +++ Reacocard's Ubuntu Repository +++
# wget http://download.tuxfamily.org/syzygy42/F4ECF181.gpg -O- | sudo apt-key add -
deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
```


4) Once this is done install the new awn packages from synaptic after an update. I have a couple more than normal and note the default awn packages are NOT installed, only *-bzr ones, see 1.jpg

5) start awn and add the pynot applet through dock preferences - see 2.jpg

The end result is something like 3.jpg

Hope that helps

---

### Post by milko on 2009-01-15
I badly want to do this but I'm not seeing the bzr packages in synaptic and the wget key thing is resulting in a 404. Has it all moved? Can't find pynot anywhere!

---

### Post by kaivalagi on 2009-01-15
> **milko said:**
> I badly want to do this but I'm not seeing the bzr packages in synaptic and the wget key thing is resulting in a 404. Has it all moved? Can't find pynot anywhere!

Yeah, it looks like the auth key has moved, not sure where to?

You can install without it though, you'll just need to authorise the install when synaptic asks...

So, put the following into your sources.list:

```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
```

And then reload in synaptic and search for the awn packages ending in "-bzr"

PyNot is included in the applets you install from these packages

Have fun :)

---

### Post by mc4man on 2009-01-15
If you continue to have no luck with that repo i use this one ( has 2 pynot's (awn-extras-applets-trunk

[https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive)

wiki
[http://wiki.awn-project.org/Installation:Ubuntu](http://wiki.awn-project.org/Installation:Ubuntu)

info on  Reacocard's repository
[http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

---

### Post by abn91c on 2009-01-15
try this guide is has step by step with screenshots [http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml](http://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml)

---

