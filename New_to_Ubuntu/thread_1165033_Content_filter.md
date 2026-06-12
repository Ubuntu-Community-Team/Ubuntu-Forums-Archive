---
title: "Content filter"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by trinidadflores on 2009-05-20
can anyone help me i installed the content filter through the add/remove applications, but i cannot configure it.  i need help doing that.  I get a dialog box that pops up and says **"Content filter not running! Start content filter?"** when i click on yes the same box pops up again no matter how many times i click it.

---

### Post by oldos2er on 2009-05-20
Which content filter are you referring to?

---

### Post by eragon100 on 2009-05-20
> **oldos2er said:**
> Which content filter are you referring to?

the one called "Content Filter" probably :wink:

There are two of them, but they're the same. One for gnome, one for KDE.

@OP: I am sorry, I can't comment on this, because I like my internet uncensored for violence etc... :lolflag:

---

### Post by albinootje on 2009-05-20
> **trinidadflores said:**
> can anyone help me i installed the content filter through the add/remove applications, but i cannot configure it.  i need help doing that. 

You need to restart dbus first, then run the config tool :
```

sudo /etc/init.d/dbus restart
sudo /usr/bin/willowng-config

```
Restarting dbus is a little weird looking, as it will restart a couple of services, you might want to reboot if you prefer a "cleaner" way of restarting all of that.

---

### Post by ultratwo on 2009-05-20
This is clearly a bug

I have reported it to launchpad (the ubuntu bugtracking system), [URL="https://bugs.launchpad.net/ubuntu/+source/willowng/+bug/378762"]https://bugs.launchpad.net/ubuntu/+source/willowng/+bug/378762
[/URL]

---

### Post by albinootje on 2009-05-20
> **ultratwo said:**
> This is clearly a bug

Indeed.
> 
I have reported it to launchpad (the ubuntu bugtracking system), [URL="https://bugs.launchpad.net/ubuntu/+source/willowng/+bug/378762"]https://bugs.launchpad.net/ubuntu/+source/willowng/+bug/378762
[/URL]

Thanks for the effort. It was already reported, though.

---

### Post by trinidadflores on 2009-05-20
> **albinootje said:**
> You need to restart dbus first, then run the config tool :
```

sudo /etc/init.d/dbus restart
sudo /usr/bin/willowng-config

```
Restarting dbus is a little weird looking, as it will restart a couple of services, you might want to reboot if you prefer a "cleaner" way of restarting all of that.


when i ran the sudo /ect/init.d/dbus restart everything was fine until it restarted now i cannot get connected to the wireless  as it says that the wireless module is no longer managing the connection.  currently i am in winblows so i can get online.

HELP!!!! please

---

### Post by albinootje on 2009-05-20
> **trinidadflores said:**
> when i ran the sudo /ect/init.d/dbus restart everything was fine until it restarted now i cannot get connected to the wireless  as it says that the wireless module is no longer managing the connection. 

Did you try booting in Ubuntu again, and test whether the wireless was back ? 
It is likely to be temporary just because of the dbus restart.
Sorry for the inconvenience, please report back about this.

---

### Post by trinidadflores on 2009-05-20
> **albinootje said:**
> Did you try booting in Ubuntu again, and test whether the wireless was back ? 
It is likely to be temporary just because of the dbus restart.
Sorry for the inconvenience, please report back about this.
I restarted several times and still nothing when it comes to wireless.

---

### Post by albinootje on 2009-05-20
> **trinidadflores said:**
> I restarted several times and still nothing when it comes to wireless.

hmmm :(

Can you remove the content filter with this :
```

sudo apt-get remove --purge willowng willowng-config-gnome

```
And then reboot.

---

### Post by trinidadflores on 2009-05-20
> **albinootje said:**
> hmmm :(

Can you remove the content filter with this :
```

sudo apt-get remove --purge willowng willowng-config-gnome

```
And then reboot.

I finally got my wireless connection back after shutting down and restarting several thousand times.  now back to trying to get this content filter to start.  It still does not want to do anything.

---

### Post by ronaldo1 on 2009-06-30
is there a workaround to get this running?
i have restarted dbus several times
and restarted the computer
but it just loops thru that the "Content filter not running! Start content filter?" message over and over

---

### Post by pckolog on 2009-11-05
> **trinidadflores said:**
> can anyone help me i installed the content filter through the add/remove applications, but i cannot configure it.  i need help doing that.  I get a dialog box that pops up and says **"Content filter not running! Start content filter?"** when i click on yes the same box pops up again no matter how many times i click it.

hi i have the same problem on ubuntu karmic and is there a solution for this problem this program is important for me i will wait for your ideas

---

### Post by glenstewart on 2010-05-16
WillowNG has an important technical improvement over the previous Willow filtering proxy, whose home is now at [https://sourceforge.net/projects/willow-proxy/](https://sourceforge.net/projects/willow-proxy/)

This Next Generation tool uses a pre-existent, independently-maintained proxy engine which has decent performance and solves a problem in the old version with "chunking" used when retrieving files over 5Mb in size.  The chunking problems prevented use of the old proxy for more than simple web browsing.

Unfortunately, WillowNG was not fully developed - the bayesian filter in the NG tool is reliant on a SQLite database which encounters significant performance problems as the database grows through addition of more sample Good and Bad sites, to improve its filtering accuracy.  There appear to be other code problems as well, and I consider the NG tool inferior due to absence of a web-based admin tool, as the original tool had.

In short, both Willow and WillowNG have issues.  If you turn off the filtering of WillowNG, it works nicely - but then why not just use TinyProxy ?

I am looking at merging the best features of Willow and WillowNG.  I have already released an update to the old Willow (link at top) bringing it as far as I can for now.  And I'm placing fixes to WillowNG at [http://welovegod.org/innovative/glen_stewart/willowng_0.5.tar.gz](http://welovegod.org/innovative/glen_stewart/willowng_0.5.tar.gz) which will overlay a broken WillowNG install and make it work again.  That patch is also attached here.

Enjoy,

Glen

---

