---
title: "[SOLVED] ATI 3D acceleration"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by HavocXphere on 2008-12-03
Hi

I'm slightly confused regarding the whole ATI drivers situation & hope someone can clarify this for me.

I've got a Radeon HD 3850 (RV670).

Is the fglrx driver in the repositories (kubuntu) identical to the drivers on the ATI website? Do they both support 3D acceleration?

If I do install additional drivers will that affect the radeonhd driver or can I always go back by just changing the driver line in xorg.conf?

At the moment the login screen appears to be using a different driver/setup than the desktop (Refresh rate differs). How do I control the settings for the login screen?

At the moment I've got it running on the radeonhd driver with the correct Resolution & refresh rate. Two problems though: No 3D acceleration and sometimes it falls back onto (I think) the Vesa driver when booting up. 

The driver being used in a LiveCD environment doesn't work (Black screen). Which driver is that?...cause I'd like to avoid it.

Thanks:KS

---

### Post by Titan8990 on 2008-12-03
Use the restricted driver manager to install your graphics drivers. Installing graphics drivers isn't as easy as just downloading it from the repositories.


> The driver being used in a LiveCD environment doesn't work (Black screen). Which driver is that?...cause I'd like to avoid it.


Most likely Vesa, the fail safe default drivers.

---

### Post by Michael.Godawski on 2008-12-03
> **ATI (fglrx)**

 If you have an ATI Radeon 9500 or newer (including thx X-series, such as x300, x1600, etc, an Xpress 200, or a Radeon HD card), then you can use the restricted fglrx drivers: _**[BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). **_

[LIST]
[*]Radeon HD support is currently limited, but rapidly improving.
[/LIST]
[IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=IconNote.png[/IMG] If you are using an ATI Radeon card that is *older than above*, you need the open source drivers:_** [RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")**_ (**NOT** fglrx). Hope that helps.

---

### Post by HavocXphere on 2008-12-04
> **Titan8990 said:**
> Use the restricted driver manager to install your graphics drivers. Installing graphics drivers isn't as easy as just downloading it from the repositories.

Yaaa....worked on the second try.:guitar:

Tried doing that a week ago and nothing happened. This time, it caused Kmix to crash...but the driver is now activated & 3D acceleration appears to be ON. Not ideal from a user experience PoV...but the end result appears to be Good.

Thanks:KS

---

