---
title: "Will Amarok 1.x be replaced with 2 when I upgrade to Jaunty?"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by diablo75 on 2009-03-29
I heard that Amarok 2 does not include all the shoutcast radiostations in its playlists (is this true?).  So I'm wondering if Amarok 1.x is going to be replaced by version two automatically when I upgrade to Jaunty... because I'd rather it didn't do that (I like my huge selection of radio stations).

---

### Post by snova on 2009-03-29
[http://packages.ubuntu.com/jaunty/amarok](http://packages.ubuntu.com/jaunty/amarok)

Yes, it is Amarok 2. I don't know about your other question, though, as I don't use that feature.

---

### Post by Bakon Jarser on 2009-03-29
> **diablo75 said:**
> I heard that Amarok 2 does not include all the shoutcast radiostations in its playlists (is this true?).  So I'm wondering if Amarok 1.x is going to be replaced by version two automatically when I upgrade to Jaunty... because I'd rather it didn't do that (I like my huge selection of radio stations).

I didn't do an upgrade, I did a clean install but I'm pretty sure it will be replaced.  But you can revert back to 1.4.

[http://ubuntuforums.org/showthread.php?t=1084971](http://ubuntuforums.org/showthread.php?t=1084971)

Check out post 75 for the solution.

---

### Post by 123456789123456789123456 on 2009-03-29
Is it included automatically with Ubuntu, or do you have to download it, through add programs?  I don't use that program.

If it is automatically included.  then the updates to it will appear in the update manager, along with the security updates.  If it is actually part of the Ubuntu system, which I doubt, it would be upgraded with the ubuntu release upgrade.

If it is the former. then you can simply tell ubuntu not to include that update.

---

### Post by InfectedWithDrew on 2009-03-29
It won't be included with Ubuntu since it is a KDE application.

----------------
Now playing: [Rush - Red Barchetta](http://www.foxytunes.com/artist/rush/track/red+barchetta)

---

### Post by alphacrucis2 on 2009-03-29
> **diablo75 said:**
> I heard that Amarok 2 does not include all the shoutcast radiostations in its playlists (is this true?).  So I'm wondering if Amarok 1.x is going to be replaced by version two automatically when I upgrade to Jaunty... because I'd rather it didn't do that (I like my huge selection of radio stations).


I didn't have Amarok already installed but I tried installing it under Jaunty via Add/Remove programs and it installed Amarok Version 2.02. I'm not really familiar with the program but I notice that when I click on the internet tab to the left, one of the options listed is Shoutcast Director, which is described as the biggest list of online radio stations on the internet. Maybe Amarok have restored the facility you are looking for in their latest version?

Edit: Just a note - I am running the Ubuntu version of Jaunty not Kubuntu. When I installed Amarok it also installed a bunch of KDE libraries that Amarok requires on but it still appears to work fine under Gnome as long as all the dependent libraries are available.

---

### Post by diablo75 on 2009-03-30
> **alphacrucis2 said:**
> I didn't have Amarok already installed but I tried installing it under Jaunty via Add/Remove programs and it installed Amarok Version 2.02. I'm not really familiar with the program but I notice that when I click on the internet tab to the left, one of the options listed is Shoutcast Director, which is described as the biggest list of online radio stations on the internet. Maybe Amarok have restored the facility you are looking for in their latest version?

If so, I'll be quite happy.  :)

---

### Post by SuperSonic4 on 2009-03-30
> **123456789123456789123456 said:**
> Is it included automatically with Ubuntu, or do you have to download it, through add programs?  I don't use that program.

If it is automatically included.  then the updates to it will appear in the update manager, along with the security updates.  If it is actually part of the Ubuntu system, which I doubt, it would be upgraded with the ubuntu release upgrade.

If it is the former. then you can simply tell ubuntu not to include that update.

not in Ubuntu but it will be in Kubuntu

---

### Post by LowSky on 2009-03-30
if you have the application installed then yes it will get upgraded to 2.0.2 (current verison in 9.04Beta)

---

### Post by txcrackers on 2009-03-30
I'm using 2.0.1 for Intrepid and, yes, it has all the Shoutcast servers. It appears to be constructing it's information tree dynamically, just like 1.4.x

---

### Post by Paqman on 2009-03-30
> **diablo75 said:**
> I'd rather it didn't do that (I like my huge selection of radio stations).

I can confirm that Shoutcast is ok on Amarok 2.

However, a couple of general points.
[LIST]
[*]When you upgrade from one release to the next you migrate from the old repos to the new ones. That means that any and all packages that have a newer version in the new repos will be upgraded. This is a lot like when you get updates normally.
[*]You don't *have* to use the newest version of an app. You can lock an app to any version through Synaptic. As long as it stays locked you won't receive any updates.
[/LIST]

---

### Post by Naz_Farooq on 2009-03-30
If I install Jaunty beta on my Ubuntu 8.10, will it automatically upgrade all my updates which I have installed on ubuntu 8.10 with connecting my laptop to the internet.
Is it possible?

---

### Post by Paqman on 2009-04-03
> **Naz_Farooq said:**
> If I install Jaunty beta on my Ubuntu 8.10, will it automatically upgrade all my updates which I have installed on ubuntu 8.10 with connecting my laptop to the internet.
Is it possible?

Everything you've installed from the repos will be upgraded, yes.

---

### Post by paul@cyberengel.com on 2009-04-19
I just installed Jaunty for my main laptop yesterday and I'm really frustrated with Amarok 2...
[LIST]
[*]First of all, the interface has become very congested and harder to user.
[*]There is NO documentation I can find, (everything on the web refers to 1.x)
[*]I can't sort a Dynamic Playlist
[*]I can't control how many songs are included with the dynamic playlist.
[*]My "usb_device" script installs, but doesn't show up in the Script Manager.
[*]The podcasts doesn't show the details of the podcast or the episode.
[/LIST]

Basically it's become useless for me... I'm currently looking at installing 1.4 so I at least have a usable music/podcast platform.

Ubuntu team, you may want to wait until KDE gets their act together before eliminating 1.x from the repos.

KDE team, I've been watching Amarok 2 for a while and it doesn't seem to be getting any better.

---

### Post by nickpick on 2009-04-25
I want to smack the person who removed 1.6 from the repos. Amarok 2.0 is not stable. For instance, there's no way I can remove songs from the "Various Artist" category without the entire thing.

---

### Post by Murwiz on 2009-05-01
For some reason, Amarok 2 seems to have lost all the podcast subscriptions I had in 1.x. Any hints on how to recover them?

---

