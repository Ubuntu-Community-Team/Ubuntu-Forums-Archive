---
title: "Flash : youtube,hulu Puzzle."
date: 2011-02-26
forum: New to Ubuntu
---

### Post by pallukucchu on 2011-02-26
I am using chrome browser.
I can watch youtube videos on this site.

I use mozilla browser.
I cannot see youtube video.
I enable flash player. Everytime I have to clear cache and refresh the link for seeing another video after having watched one.
Can anybody solve this puzzle?

---

### Post by I8NY on 2011-02-27
Make sure you have the latest version and don't get the one from the software center it never worked for me.  Do a manual install of flash and if you have 64bit ubuntu, get the 64bit version of flash, it fixes a couple problems.

---

### Post by tgm4883 on 2011-02-27
> **pallukucchu said:**
> I am using chrome browser.
I can watch youtube videos on this site.

I use mozilla browser.
I cannot see youtube video.
I enable flash player. Everytime I have to clear cache and refresh the link for seeing another video after having watched one.
Can anybody solve this puzzle?

It's possible that youtube detects you are using the chrome browser and you actually are getting the HTML5 version rather than the flash site.

---

### Post by gandaran on 2011-02-27
> **pallukucchu said:**
> I am using chrome browser.
I can watch youtube videos on this site.

I use mozilla browser.
I cannot see youtube video.
I enable flash player. Everytime I have to clear cache and refresh the link for seeing another video after having watched one.
Can anybody solve this puzzle?
chrome browser uses built in adobe flash, firefox uses the system installed flash so the question is what have you installed for system flash or have more than one conflicting plugins installed?
there are many options for flash so open synaptic package manager, type flash in search box, that should show which packages are installed.
also the question ubuntu 32-bits or 64-bits?

---

### Post by TechWiz2100 on 2011-02-27
if you are getting audio from the flash video or frozen video try running firefox from terminal like this:```
env XLIB_SKIP_ARGB_VISUALS=1 firefox
```
if this fixes your issue then its Compiz/ desktop effects related
I have the same issue with 64bit flash on both chrome and firefox
Also, Chrome will not use its own plugin if the system specifies one or there is one in mozilla's plugin folder.

---

