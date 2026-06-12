---
title: "ubuntu-restricted-extras not in Synaptic but on Software Center?"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by ALF102 on 2009-11-15
Oh, I've just realize recently I can't find Ubuntu-restricted-package in synaptic but I found it in Ubuntu Software Centre

---

### Post by aysiu on 2009-11-15
> **ALF102 said:**
> Oh, I've just realize recently I can't find Ubuntu-restricted-package in synaptic but I found it in Ubuntu Software Centre
That's weird.

I had a similar but opposite experience: I could find *ubuntu-restricted-extras* in both Synaptic and Software Center, but Software Center could not install it (Synaptic could).

More details here:
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/465031](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/465031)

---

### Post by ALF102 on 2009-11-15
I don't think this would be a big problem anyway cuz there are many ways to get software.

---

### Post by mc4man on 2009-11-16
Many times it's better not to be too specific when searching in synaptic, if you get the name wrong then nothing will show
if you used Ubuntu-restricted-package it would come up empty, while ubuntu-r would show. ( or even Ubuntu-r

Anyway in karmic the restricted extras package may or may not give you what you intended.

Atm it's installing the stripped ffmpeg libs instead of the unstripped 'extra' versions. If you had the 'extra' versions installed it would remove them in favor of the stripped ones. ( depending on your usage this may or may not matter.

This is what it will check for and install if not installed ( in a 32 bit install, 64 bit is slightly different

> gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
ttf-mscorefonts-installer
flashplugin-installer
unrar
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg
libavcodec52
libavformat52
libpostproc51
libswscale0
sun-java6-jre
gstreamer0.10-pitfdll
libmp4v2-0

As far as the ffmpeg libs these are usually what people expect to be installed

> libavcodec-extra-52
libavformat-extra-52
libpostproc-extra-51
libswscale-extra-0

---

### Post by ALF102 on 2009-11-16
Well, I did use "ubuntu-r" in the search but it won't, I tried to reload the package list and try again but still no luck, as if its not even in the list. Well, this is a very small problem and I don't think it does need any fixing.

---

### Post by mc4man on 2009-11-16
As you say doesn't matter, does seem odd... though if you are using the 'quick search' it can act oddly on occasion (vs. the search button.

There was a bug about the index not updating for synaptic right away, though that usually seemed confined to adding third party repo's.

The index is updated on a weekly basis anyway, you could run the command to see

```
sudo update-apt-xapian-index
```

---

### Post by ALF102 on 2009-11-16
Ah thanks, its just as you've said, I try using the search button instead of the quick search and I found the file I was looking for.

---

### Post by t0p on 2009-11-16
> **ALF102 said:**
> Ah thanks, its just as you've said, I try using the search button instead of the quick search and I found the file I was looking for.

Dude, that 'quick search' is crap.  It searches just through stuff you've already listed or some such nonsense.  Its utility has eluded me at every turn.  I use plain old 'search' now, which serves me well.

---

### Post by mikechant on 2009-11-16
> Dude, that 'quick search' is crap.

Seconded. *Never* use 'quick search' if you actually want to find anything!

---

### Post by aysiu on 2009-11-16
> **mikechant said:**
> Seconded. *Never* use 'quick search' if you actually want to find anything!
I've found this too. Is there a bug report on this yet?

Maybe this is it?
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/288797)

Supposedly it's fixed, though?

---

### Post by coffeecat on 2009-11-16
If you know the name of the package, or at least the first few letters, you don't even need to use Search.

Highlight any package in the centre pane and simply start typing: u b u n t u - r . You'll soon find it.

---

### Post by mc4man on 2009-11-16
The quick search tends to work fine as long as you stay on the "all" search and sections tab. If you move off of the "sections" to for example "custom filters" you'd need to re-click the "All"

In other words "All" needs to be highlighted

That be said I almost always use the regular search drop down.

---

