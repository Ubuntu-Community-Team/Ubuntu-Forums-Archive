---
title: "ubuntu 9.04 firefox trouble"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by this is new york not l.a. on 2009-04-25
hey there, I just upgraded my computer from 8.04 to 9.04. I did a clean install and haven't done much except for installing compiz-fusion. but for some reason I can't watch any videos on youtube, dailymotion, or any site with flash videos. I tried "updating" adobe flash player but that didn't do anything. does anybody know ow to help me? it would be greatly appreciated

---

### Post by sports fan Matt on 2009-04-25
Have you gone into add/remove and searched for "ubuntu-restricted- extras

---

### Post by this is new york not l.a. on 2009-04-25
i have not... *searches*

---

### Post by this is new york not l.a. on 2009-04-25
nothing came up. this is very strange

---

### Post by Didius Falco on 2009-04-25
Go to System/Administration/Software Sources

Check all the boxes on the first page, do the same for the "Third Parties" tab.

Then open a Terminal window (Applications/Accessories/Terminal) and paste ```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

This will add the Medibuntu repository to your software sources list.

Then paste ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

This adds the GPG key for Medibuntu to your keyring. It'll throw up a y/n question about whether to accept it even though it can't be authenticated. Answer yes.

then paste
```
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs

```

in, one at a time. This will install the encrypted DVD playback and windows 32 codecs.

Then follow this guide for more multimedia goodness:

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

I hope this helps...

---

### Post by this is new york not l.a. on 2009-04-25
I tired but it really didn't help I keep getting this gray box that has a play emblem in it but when I click it it will either play the video or just freeze up and go to the adds after a video

---

### Post by this is new york not l.a. on 2009-04-25
the problem is fixed now.... I just restarted my computer and everything is fine so i'm assuming something I did worked but just needed to be restarted. thanks everybody who helped =]

---

