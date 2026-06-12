---
title: "Can't get Firefox 3.5 to run in default desktop"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by RobHK on 2009-07-07
I installed Firefox 3.5 but I still only have the old orange icon for FF and when I run it 3.0 starts. Likewise if I type firefox in a terminal.

For entirely unrelated reasons, I installed the FluxBox desktop. In FluxBox, Firefox 3.0 is there with its orange icon, but so is 3.5 with its blue icon.

I'm on 3.5 now, in FluxBox, but when I go back to Gnome I can't find Firefox 3.5 anywhere.

---

### Post by taurus on 2009-07-07
Where did you install firefox 3.5?  You can create a shortcut on the top panel for version 3.5.

---

### Post by RobHK on 2009-07-07
> **taurus said:**
> Where did you install firefox 3.5?  You can create a shortcut on the top panel for version 3.5.

Synaptic installed it for me, but after reading your post I opened my home folder and found it in the .mozilla folder, alongside 3.0. But I'm afraid I still don't know how to run it, or to create an icon for it.

---

### Post by superprash2003 on 2009-07-07
there is usually a firefox launcher type icon in the folder when you download firefox

---

### Post by philinux on 2009-07-07
> **RobHK said:**
> Synaptic installed it for me, but after reading your post I opened my home folder and found it in the .mozilla folder, alongside 3.0. But I'm afraid I still don't know how to run it, or to create an icon for it.

In that case. Applications>Internet>Shiretoko WebBrowser:- aka FF3.5

---

### Post by lovinglinux on 2009-07-07
> **RobHK said:**
> Synaptic installed it for me, but after reading your post I opened my home folder and found it in the .mozilla folder, alongside 3.0. But I'm afraid I still don't know how to run it, or to create an icon for it.

That it's not the program, that's just you profile folder, where firefox-3.5 stores user related files, like cookies, passwords, extensions and so on.

You have installed Shiretoko 3.5, which just the codename for Firefox 3.5 without the branding. It can be found from the Internet menu ( "Applications >> Internet >> Shiretoko Web Browser")

---

### Post by scrooge_74 on 2009-07-07
Shouldn't it even run from a terminal typing firefox-3.5  ?

---

### Post by RobHK on 2009-07-07
> **superprash2003 said:**
> there is usually a firefox launcher type icon in the folder when you download firefox

In which folder?

---

### Post by RobHK on 2009-07-07
> **scrooge_74 said:**
> Shouldn't it even run from a terminal typing firefox-3.5  ?

Thank you. Yes, it does.

I should be able to add it to the menu in the right place now.

---

### Post by philinux on 2009-07-07
> **RobHK said:**
> Thank you. Yes, it does.

I should be able to add it to the menu in the right place now.

See posts #5 and #6

---

### Post by RobHK on 2009-07-07
It was there all the time. 

But for some reason it was labelled "Minefield Web Browser 3.5"! Not Firefox or Shiretoko.

---

### Post by scrooge_74 on 2009-07-07
Yep, Shiretoko if you followed a set of instructions a few days before there was a package in synaptic (at least for use in Hardy) now in Hardy ut has that Minefield name

---

### Post by lovinglinux on 2009-07-07
> **RobHK said:**
> It was there all the time. 

But for some reason it was labelled "Minefield Web Browser 3.5"! Not Firefox or Shiretoko.

Minefield is the codename for the next version of Firefox, currently under development. If you used the ubuntu-mozilla-daily PPA repository to update Shiretoko 3.5b4pre to 3.5 final, then you probably got Minefield instead, because this PPA doesn't stop. It keeps updating firefox-3.5 with alpha, beta and rc releases.

If you don't use an extra PPA repository, then the current available version is Shiretoko 3.5. I'm not sure if it will stop at this version, but probably not.

Read the "Install Other Version" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). It explains all of this and offers other methods of installation. I personally prefer the method #1, which installs Firefox 3.5 form Mozilla official release and don't update to unstable versions unless you download and install them manually.

---

### Post by RobHK on 2009-07-08
Thanks, that must be it. And, in fact I have had the odd instability. I'll uninstall it and get rid of the problem repository before reinstalling. Hope I manage to remove everything.

---

### Post by suresnjain on 2009-07-08
But why does it say-Minefield 3.5 browser.and some add-ons do not work here-like PDF download 2.2.02.This is creating problems for a PDF opening.Any solution to this?

---

### Post by scrooge_74 on 2009-07-08
Remember 3.5 work in progress, plugins may fail

---

### Post by lovinglinux on 2009-07-08
> **suresnjain said:**
> But why does it say-Minefield 3.5 browser.and some add-ons do not work here-like PDF download 2.2.02.This is creating problems for a PDF opening.Any solution to this?

You can disable extension compatibility check temporarily. See how to do this in the  [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004). Scroll down until you find "**[COLOR="Red"]Extension Compatibility[/COLOR]**", under the "[COLOR="Red"]**Installing Other Versions**[/COLOR]" section.

---

