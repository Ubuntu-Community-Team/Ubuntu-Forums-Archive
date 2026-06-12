---
title: "Synaptic Package Manager or Add/Remove?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Wackjob on 2009-05-16
I tried to load a video in Movie Player, and it tells me that I need to install some gstreamer files for mpeg 4 support.   I noticed that the gstreamer packages are available in both the Add/Remove area and also in the Synaptic Package Manager. What are the differences between Synaptic and Add/Remove? Is installing through one more preferable than the other?    Also, is it safe to install software that isn't maintained by Canonical in the Add/Remove section?  Thanks in advance!

---

### Post by Joeb454 on 2009-05-16
Add/Remove and Synaptic are basically the same thing. One just has a prettier interface than the other ;)

If the software isn't maintained by canonical, but is in the repo's, then it will have been tested to make sure it is safe :)

For codecs, I simply install [libxine1-all-plugins](apt://libxine1-all-plugins)

---

### Post by lovinglinux on 2009-05-16
> **Joeb454 said:**
> Add/Remove and Synaptic are basically the same thing. One just has a prettier interface than the other ;)

If the software isn't maintained by canonical, but is in the repo's, then it will have been tested to make sure it is safe :)

For codecs, I simply install [libxine1-all-plugins](apt://libxine1-all-plugins)

Additionally, the Add/Remove manager only display the applications list, while Synaptic shows every single package available, including those necessary to compile programs from source. I think the "Add/Remove" manager exists to be a easy method for newcomers. 

About the codecs, follow [this tutorial](http://ubuntuforums.org/showthread.php?t=766683) and you will be able to play almost everything.

---

### Post by goldblattster on 2009-05-16
Yes. The content in Add/Remove and Synaptic are the exact same. ;)

---

### Post by snova on 2009-05-16
> **Wackjob said:**
> I noticed that the gstreamer packages are available in both the Add/Remove area and also in the Synaptic Package Manager. What are the differences between Synaptic and Add/Remove?

Interface. They do the same thing.

> Is installing through one more preferable than the other?

Only to the person using them.

> Also, is it safe to install software that isn't maintained by Canonical in the Add/Remove section?  Thanks in advance!

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you're referring to the universe/multiverse repos, I would say they're pretty safe.

---

### Post by WinterMadness on 2009-05-16
pretty much the same, I never use add or remove. Synaptic or apt-get for me

---

### Post by juancarlospaco on 2009-05-16
*or apt-get?, or aptitude, or apt:/url?, or ...*

---

### Post by SunnyRabbiera on 2009-05-16
Both do the same basic job though synaptic loads more packages and is a little more "advanced" in its settings.
Sometimes using pure add/remove might cause issues though, as sometimes its not as good with managing the packages.

---

### Post by zvacet on 2009-05-17
```
sudo apt-get install ubuntu-restricted-extras
```

If you want more codecs then add [Medibuntu.]("https://help.ubuntu.com/community/Medibuntu")

---

