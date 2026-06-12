---
title: "Flash video"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by bibleguy125 on 2009-11-24
I can't get flash videos to work on ubuntu. Is it because I booted off the CD, or is there something else I'm missing?

---

### Post by snowpine on 2009-11-24
Ubuntu does not ship with the Flash codec for legal reasons.

Open a terminal (under Applications->Accessories) and copy & paste the following:

```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

Good luck!

---

### Post by bibleguy125 on 2009-11-24
Okay I did that and the last line in the terminal says E: Couldn't find package flashplugin-installer

---

### Post by snowpine on 2009-11-24
Are you running Ubuntu 9.10? Are you connected to the internet?

---

### Post by McFarley on 2009-11-24
Which version of Ubuntu, and 32 or 64 bit?

---

### Post by bibleguy125 on 2009-11-24
yeah it's ubuntu 9.10 and i'm connected to the internet
The only thing I can think of is if it wouldn't do that from booting straight off the CD, but I don't know if that's the case or not

---

### Post by snowpine on 2009-11-24
Try:

```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

That is the package name for older versions, but I think it might still work for 9.10.

If not, cut and paste the output here (not just the last line).

---

### Post by Cheesemill on 2009-11-24
Copy and paste this into a terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update && sudo apt-get install flashplugin-installer
```

Ubuntu won't find the package flashplugin-installer until you add the medibuntu repository, see the following link for more information:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by julianb on 2009-11-24
Maybe it's just me, but here is how I'm interpreting this thread:

Bibleguy says: "i booted off of a CD and flash doesn't work"

everybody responds... "use this process to install flash" but IGNORES the fact that you can't install new software on to a liveCD.
=========================
Bibleguy - if you install Ubuntu to your hard drive, you will be able to install new software. And flash videos won't work unless you install a flash player. 

Am I missing something?

If you want a less-permanent install of Ubuntu, you can try using ubuntu through "Wubi", which sometimes does not work as well as the regular Ubuntu, but is also very easy to delete, if you want a short term temporary install of Ubuntu.

---

### Post by Cheesemill on 2009-11-24
You can install software on a Live CD, it just wont be there after you restart.

---

### Post by snowpine on 2009-11-24
> **julianb said:**
> Maybe it's just me, but here is how I'm interpreting this thread:

Bibleguy says: "i booted off of a CD and flash doesn't work"

everybody responds... "use this process to install flash" but IGNORES the fact that you can't install new software on to a liveCD.
=========================
Bibleguy - if you install Ubuntu to your hard drive, you will be able to install new software. And flash videos won't work unless you install a flash player. 

Am I missing something?

I think you can install anything you want in a Live CD session (so long as you have enough RAM).

---

### Post by bibleguy125 on 2009-11-24
Thanks guys. Snowpine, the older version worked, so I'm not sure what the problem was with the new version.
I do plan to install ubuntu on my harddrive at some point, but wanted to get it figured out first and maybe try some other versions of linux first and see what they are like too before I commit, which is why I'm just using the Live CD for now. Thanks again guys.

---

