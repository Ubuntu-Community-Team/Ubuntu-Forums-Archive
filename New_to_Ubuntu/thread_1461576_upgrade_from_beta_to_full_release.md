---
title: "upgrade from beta to full release"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by crazyavery4444 on 2010-04-24
With the ubuntu 10.04 full release coming out in a few days, I was wondering if there was a way to upgrade from the beta to the full release? (via sudo update-manager -d)

---

### Post by akand074 on 2010-04-24
The update manager will give you new updates as they are released. So yes when Lucid is fully released, it will prompt you to update/install only the selected files your missing.

---

### Post by QIII on 2010-04-24
Your command will work.  Just don't do 

```
sudo apt-get upgrade -d
```in the terminal.

In that case, the "-d" switch tells the command to upgrade to the next development version, which Lucid will not be at that time.  You DON'T want to do that, because you don't really know when stuff for the next dev version will start appearing.

If you have been doing your updates

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```you should already essentially be at the RC.

Do it again a day or two after the release, since the servers will likely be busy for a couple of days.

NOTE:  BACK UP!  BACK UP!  BACK UP!

Did I mention that you should back up?

While this will not give you *exactly *a clean 10.04, the differences will amount to little more than just a few bits of chaff ... like a bit of unused DNA in your genes.  Won't hurt a thing.


NOTE:  Just wanted to dispel some rumors about dist-upgrade.  It will not automatically update you to the next distribution.  It will update you to the latest and greatest in your current distribution, as long as you don't change your sources list.

---

### Post by crazyavery4444 on 2010-04-24
> **akand074 said:**
> The update manager will give you new updates as they are released. So yes when Lucid is fully released, it will prompt you to update/install only the selected files your missing.
yes, but it seems that no matter how many new packages they release, it seems that my problem will always be there (I had no problems with this in 9.10) if I go to start a fullscreen game with rhythem box running or when my CPU is under load, the screen flashes, it displays 6 lines that say error, cannot write bytes, broken pipe. then it goes to say that ubuntu is running in low graphics mode, if i reboot it dosnt detect it as an error so there is no way to report the bug, and when I restart everything works fine. its a huge pain the ***.

---

### Post by crazyavery4444 on 2010-04-24
> **QIII said:**
> Your command will work.  Just don't do 

```
sudo apt-get upgrade -d
```in the terminal.

In that case, the "-d" switch tells the command to upgrade to the next development version, which Lucid will not be at that time.  You DON'T want to do that, because you don't really know when stuff for the next dev version will start appearing.

If you have been doing your updates

```
sudo apt-get update
``````
sudo apt-get upgrade
``````
sudo apt-get dist-upgrade
```you should already essentially be at the RC.

Do it again a day or two after the release, since the servers will likely be busy for a couple of days.

NOTE:  BACK UP!  BACK UP!  BACK UP!

Did I mention that you should back up?

While this will not give you *exactly *a clean 10.04, the differences will amount to little more than just a few bits of chaff ... like a bit of unused DNA in your genes.  Won't hurt a thing.


NOTE:  Just wanted to dispel some rumors about dist-upgrade.  It will not automatically update you to the next distribution.  It will update you to the latest and greatest in your current distribution, as long as you don't change your sources list.
hmm, im wondering whether or not to back up before doing this, well thanks! i'll do that now and next week when 10.04 comes out!

---

### Post by QIII on 2010-04-24
I would say that if you are having a persistent problem right now, a fresh install might be in order.

Be sure to save your /home directory and your applications installed via Synaptic or apt.

Before you save your /home, identify what you have installed,


```
sudo apt-get install deselect
```
```
sudo dpkg --get-selections > selections.txt
```

this will leave a text file in your home directory.

When you reinstall and put your home back where it belongs (you may have to fiddle around a bit with Firefox and email profiles to get your data under the new profiles that may be created, but you will at least have the data in the orginals), run

```
sudo dpkg --set-selections < selections.txt
```
```
sudo apt-get update
```
```
sudo apt-get dselect-upgrade
```

I also save some files like /etc/hosts (in case you have networking set up), a list of all third-party software I have and the installation files (I keep all of those in a folder), etc.   Think about those sorts of things and get them all in your /home folder you save before you reinstall.

---

### Post by Paqman on 2010-04-24
You don't need to do anything at all. The normal update process will bring you into line with the final release.

Labels like Beta 1, Beta 2, etc are really just a snapshot of the state of the repository on that particular day. Once you're on the development branch you can just keep updating like normal.

---

### Post by nhasian on 2010-04-24
I've been running lucid since alpha3 and i've done all the updates.  I still have encountered various glitches due to upgrading so i am planning on doing a fresh install when the official lucid comes out.  A few things that dont work for me:

cannot open links in firefox
missing notification area/volume control on taskbar
iphone isnt detected
toggling my touchpad on/off will stop mouse/keyboard input and requires reboot.

I hope that a fresh install will clear up most if not all these issues for me.

---

### Post by -humanaut- on 2010-04-24
In my opinion if your running from Beta1 or Beta2 I'd HIGHLY recommend doing a clean install to atleast the R.C. I'm paranoid but I've seen alot of problems creep up from Beta to R.C./Final updates.

---

### Post by QIII on 2010-04-24
> **Paqman said:**
> You don't need to do anything at all. The normal update process will bring you into line with the final release.

Labels like Beta 1, Beta 2, etc are really just a snapshot of the state of the repository on that particular day. Once you're on the development branch you can just keep updating like normal.

Generally, I would agree.

In this case, however, the OP is having problems that have persisted through updates.

I've been running Lucid as my primary since the first Beta without problems.  But not everyone has been so fortunate.

---

### Post by mick222 on 2010-04-24
I'd say just update I done a new install today and it wasn't a nice experiance. I had to install with nomodset  and am having a lot of trouble with my graphics card. I was running lucid from alpha withg very few problems.Have a look around the forums you'll see a lot of people with the saqme problem it will probably be fixed soon but if your ok with what you've got i'd wait a few weeks to reinstall.

---

