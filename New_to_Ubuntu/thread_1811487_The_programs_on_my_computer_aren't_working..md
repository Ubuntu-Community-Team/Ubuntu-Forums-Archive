---
title: "The programs on my computer aren't working."
date: 2011-07-24
forum: New to Ubuntu
---

### Post by Mycomputersuckz on 2011-07-24
My brother some years ago uploaded ubuntu onto my computer, I know nothing about programming but I am trying to download utorrent, I pretty much don't know where to begin because it seems nothing on here works I've dowloaded it and I try and go into Wine then Browse C:\ Drive this wont open EVER. This is really frustrating me, all this computer seems to know is how to freeze and lagg and not open anything.

I am in some serious desperate need of help!

---

### Post by beew on 2011-07-24
> **Mycomputersuckz said:**
> My brother some years ago uploaded ubuntu onto my computer, I know nothing about programming but I am trying to download utorrent, I pretty much don't know where to begin because it seems nothing on here works I've dowloaded it and I try and go into Wine then Browse C:\ Drive this wont open EVER. This is really frustrating me, all this computer seems to know is how to freeze and lagg and not open anything.

I am in some serious desperate need of help!

There are many torrent clients native in Linux. Transmission is installed by default, if you find it too plain or lack options you can also use deluge, qbittorent and quite a few other excellent ones. You don't need utorrent. Some Windows programs run it WINE but many don't and others only partially, so WINE is really a last resort.

---

### Post by 23dornot23d on 2011-07-25
What version of Ubuntu is it ...... ?

if you are not sure - 

type in a terminal 

**uname -a**

Then post the results .... just to give us some idea of what you are working with .....

as said above by Beew there are many torrent programs for Linux

---

### Post by amjjawad on 2011-07-25
> **Mycomputersuckz said:**
> My brother some years ago uploaded ubuntu onto my computer, I know nothing about programming but I am trying to download utorrent, I pretty much don't know where to begin because it seems nothing on here works I've dowloaded it and I try and go into Wine then Browse C:\ Drive this wont open EVER. This is really frustrating me, all this computer seems to know is how to freeze and lagg and not open anything.

I am in some serious desperate need of help!

Hello and Welcome :)

You reminded me of my first day with Ubuntu 9.10 where nothing was clear and everything was hard to understand. Couldn't use it more than a few days and gave up.
After some time, I realized that was a mistake to give up so easily so I decided to start learning Linux and ... I just can't live WITHOUT it anymore :)

I understand how hard it could be but guess what? it will be very easy once you learn HOWTO DO it ;)

You don't have to be a programmer to use Linux. Linux nowadays is different that what it was before.

[**Here**]("http://linux.oneandoneis2.org/LNW.htm") is a good article that will enlighten your path :)


Accessories > Internet > Transmission BitTorrent Client

This is the default application for Torrent.

[http://torrentz.eu/](http://torrentz.eu/) ... search for what you want and download the torrent. Transmission will start once you open the torrent file.

As for C: drive, if you want to access your Windows Drives then go to 

Places > Computer 

Try to find your C: Drive.

I suggest to give a label to each drive so that it will be so easier for you to find what you are looking for.

Good luck!

---

### Post by amjjawad on 2011-07-25
> **23dornot23d said:**
> What version of Ubuntu is it ...... ?

if you are not sure - 

type in a terminal 

**uname -a**




This will NOT tell you what version/release of Ubuntu, this will tell you what version or Kernel the user is using ;)


```
cat /etc/issue

```

is the right command ;)

[http://www.howtogeek.com/howto/ubuntu/how-to-tell-what-version-of-ubuntu-you-are-running/](http://www.howtogeek.com/howto/ubuntu/how-to-tell-what-version-of-ubuntu-you-are-running/)

---

### Post by dirghrabadia on 2011-07-25
With plenty of help readily available on the forums, I am sure you would start loving Ubuntu :)

Give Transmission a try, works perfectly for me!

---

### Post by beew on 2011-07-25
> **amjjawad said:**
> This will NOT tell you what version/release of Ubuntu, this will tell you what version or Kernel the user is using ;)


```
cat /etc/issue

```is the right command ;)

[http://www.howtogeek.com/howto/ubuntu/how-to-tell-what-version-of-ubuntu-you-are-running/](http://www.howtogeek.com/howto/ubuntu/how-to-tell-what-version-of-ubuntu-you-are-running/)

Or ```
lsb_release -a 
```I think that was what he meant.

---

### Post by kaldor on 2011-07-25
> **Mycomputersuckz said:**
> My brother some years ago uploaded ubuntu onto my computer, I know nothing about programming but I am trying to download utorrent, I pretty much don't know where to begin because it seems nothing on here works I've dowloaded it and I try and go into Wine then Browse C:\ Drive this wont open EVER. This is really frustrating me, all this computer seems to know is how to freeze and lagg and not open anything.

I am in some serious desperate need of help!

For one, you should really try to learn to do things the Linux way. I enjoy using Transmission and Deluge quite a lot, and prefer them to uTorrent. 

Secondly, Linux usually isn't unstable like you say it is. There seems to be something amiss, so post the information about your computer. Getting the version of Ubuntu you are using is needed. You don't need to be a programmer to use Linux.

---

### Post by 23dornot23d on 2011-07-25
@amjjawad and beew

You are both right the two commands you give are much better for finding out what the USER is using,

My main reason for asking for a feedback of any kind was to get the ball rolling so to speak ....

[B]uname -a
[/B] 
Was the simplest command that came to mind but the other commands will give the Ubuntu version rather than the kernel  version .... not that either of the commands given are difficult.

This is one I learned from Van-DSL for later releases will put it here as someone may find it useful

**date && lsb_release -sd || cat /etc/*release &&  uname   -s -r && unity --version &&   /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils**


So I stand corrected and have learned something new today ..... :D  I just hope the user comes back and
we can maybe go from there ...... after typing these or one of these at the command prompt or in a terminal
it may give us a better start point ..... we could even get the Linux upgraded to a version that makes it much
easier to use too ...... 

[B]cat /etc/issue

[/B] [B]lsb release -a

_________________________________


[/B]

---

### Post by sanderd17 on 2011-07-25
> **kaldor said:**
> For one, you should really try to learn to do things the Linux way. I enjoy using Transmission and Deluge quite a lot, and prefer them to uTorrent. 

Secondly, Linux usually isn't unstable like you say it is. There seems to be something amiss, so post the information about your computer. Getting the version of Ubuntu you are using is needed. You don't need to be a programmer to use Linux.

I second doing it the Linux way. Part of the Linux way is
**Not installing things from the internet**

We have a Software Center (or maybe it's called different if you have an older version) for a reason.

---

### Post by beew on 2011-07-25
> **sanderd17 said:**
> I second doing it the Linux way. Part of the Linux way is
**Not installing things from the internet**

We have a Software Center (or maybe it's called different if you have an older version) for a reason.

I would not put it in such absolute term. There are things that I either have to or prefer to install from the internet. Examples: the Gtalk plugin, Android emulator, Outrec, a datamining tool that called Weka,-- the version in the repository is old. There are a few other specialized programs which I can't find in the official repo. I also installed a few things from source and  installed some .rpm packages after converting them into .debs (for example stand alone blenderplayer, which is available in Fedora but not in Ubuntu or Debian) 

The SC without PPAs doesn't meet my needs, but probably good enough for most requirements of a new user.

---

### Post by sanderd17 on 2011-07-25
> **beew said:**
> I would not put it in such absolute term. There are things that I either have to or prefer to install from the internet. Examples: the Gtalk plugin, Android emulator, Outrec, a datamining tool that called Weka,-- the version in the repository is old. There are a few other specialized programs which I can't find in the official repo. I also installed a few things from source and  installed some .rpm packages after converting them into .debs (for example stand alone blenderplayer, which is available in Fedora but not in Ubuntu or Debian) 

The SC without PPAs doesn't meet my needs, but probably good enough for most requirements of a new user.

Those are exceptions that prove the rule (if they say it that way in English). :D

I also have some exceptions, I use JOSM from their site because the one in the SC is outdated, and gnome-shell with the GS extensions isn't in the 11.04 repo. But those are exceptions. In Windows it's a rule that you have to buy software in a shop or download it from the internet.

---

### Post by amjjawad on 2011-07-25
> **23dornot23d said:**
> have learned something new today 

```
 cat /etc/issue
``````
  lsb release -a
```

Same here. I searched on Google and Learned the first command. And when Beew posted, I learned the other one :)

---

### Post by amjjawad on 2011-07-25
> **sanderd17 said:**
> In Windows it's a rule that **you have to buy software in a shop** or *download it from the internet.*

Thank God, I had to buy one Software ONLY and that was the first and the last time :)

---

