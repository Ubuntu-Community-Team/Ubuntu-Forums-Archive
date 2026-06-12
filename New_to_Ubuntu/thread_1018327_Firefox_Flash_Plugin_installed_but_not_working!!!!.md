---
title: "Firefox Flash Plugin installed but not working!!!!!!!"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Art3mis on 2008-12-22
Hi everyone,

I installed some plugin (not macromedia), in order to watch youtube.


It doeas not work what to do?

---

### Post by beno1990 on 2008-12-22
Firstly, what's the name of the plugin you installed, and where did you get it from?

Secondly, before you post that, just try going to tools -> addons -> plugins, and see if it's listed there and enable it if it is.

---

### Post by nhasian on 2008-12-22
it should be flashplugin-nonfree

if you dont have it installed you can install it with

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by treepolitik on 2008-12-22
> **beno1990 said:**
> Firstly, what's the name of the plugin you installed, and where did you get it from?

Secondly, before you post that, just try going to tools -> addons -> plugins, and see if it's listed there and enable it if it is.

I did what you said and it turns out I've more than five different ones all meant to play videos(Lol).  Needless to say, I can't play videos on any site.  I could uninstall the lot save Gnash/Shockwave Flash and see if this fixes the problem.  

I've the following: Shockwave Flash/Gnash, Totem Web Browser Plugin 2.22.1, VLC Multimedia (Compatible Totem 2.22.1), Windows Media Player Plugin 10 (compatible; Totem), QuickTime Plug-in 7.2.0, Helix DNA Plugin: Real Player G2 Plug-In (Compatible; Totem), Default Plugin(for mimetypes and extensions), DivX Web Player 1.4.0.233, and iTunes Application Detector.

Addendum: I am experimenting with the right-click Disable function to test which ones work before uninstalling.

---

### Post by Tomatz on 2008-12-22
Do this:

**Open a terminal and type:**

```
sudo apt-get remove --purge flashplugin-nonfree gnash* 
```

**Restart firefox**

Go here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Dropdown the (errr) dropdown. And select ***".deb for ubuntu 8.04"***.

**Download to desktop then double click it to install it.**

**Restart firefox** and wallah, Done!



The reason for this is that the flashplugin in the repositorys is broken. Also you had GNASH installed allongside abdobe flash plugin.

---

