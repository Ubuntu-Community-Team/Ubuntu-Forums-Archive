---
title: "Upgrading Intepid -&gt; Jaunty: what gets zapped?"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by ticket on 2009-06-27
I'm considering updating from 8.1 to 9.04, just to keep up with things.

I'm on an Intel 1.5GHz PC, nVidia gpu, using 32 bit OS version.

So far I have configured my 8.1 to my satisfaction.

But what will happen to these settings/packages on upgrading?  :
- metacity settings, gnome settings
- nautilus settings
- compiz settings
- firefox configuration, preferences, extensions, plugins
- adobe flash plugin (non-free)
- netbeans settings
- audio settings
- packages that provide codecs (e.g libavdevice-unstripped-52, etc) that allow me to play wmv, avi, etc
- desktop layout
- sensors applet & configuration
- Packages installed that were not part of standard Ubuntu, eg. rosegarden, pulse audio preferences, simple compiz config settings manager, Hex editor, Open Movie Editor
- Sun java (other javas uninstalled)
- Lots of dev packages installed (for s/w development)
- mttr settings
- Custom packages installed from Intrepid repos.


S[COLOR="Blue"]o a lot of work has gone into setting up 8.1 - does it all disappear and have to be redone when Jaunty gets installed?[/COLOR]

Presumably the synaptic package manager is modified to point to Jaunty packages instead of Intrepid ones. What problems could this cause?

[COLOR="Blue"]Just what gets zapped by the upgrade and then needs to be fixed?[/COLOR]

(Luckily I don't have an Intel graphics card, so I am spared that pain).

---

### Post by northern lights on 2009-06-27
> **ticket said:**
> But what will happen to these settings/packages on upgrading?  :
- metacity settings, gnome settings
- nautilus settings
- compiz settings
- firefox configuration, preferences, extensions, plugins
- adobe flash plugin (non-free)
- netbeans settings
- audio settings
- packages that provide codecs (e.g libavdevice-unstripped-52, etc) that allow me to play wmv, avi, etc
- desktop layout
- sensors applet & configuration
- Packages installed that were not part of standard Ubuntu, eg. rosegarden, pulse audio preferences, simple compiz config settings manager, Hex editor, Open Movie Editor
- Sun java (other javas uninstalled)
- Lots of dev packages installed (for s/w development)
- mttr settings
- Custom packages installed from Intrepid repos.

The update will remove some obsolete packages, that either are outdated and/or their tasks are taken up by newer ones. It however will not mess with your previously installed apps and their config files.

---

### Post by jward3010 on 2009-06-27
Unless the upgrade will install radically different upgrades of your current programs (which stable releases rarely do) then most likely everything will be fine, they will continue to use your exisiting .config files in your home directory and as far as I remember the upgrade from 8.10 to 9.04 was pretty placid and not hugely different.

---

### Post by ticket on 2009-06-27
Encouraging posts so far!
jward, your signature still says using 8.1 !

---

### Post by 45acp on 2009-06-27
If you have amarok 1.4 installed it gets replaced with 2.0

---

### Post by durand on 2009-06-27
User specific settings are never removed or changed, but if you changed something system wide, the upgrader will ask you whether you want to keep the settings or not. Custom programs will not be removed or affected unless they clash with the upgraded programs. You may also need to change the repository lines in /etc/apt/sources.list as they will be commented out if they are not official ubuntu ones.

---

### Post by ticket on 2009-08-15
Well I finally did the upgrade - and survived!

I must have left it rather late, as the upgrade ended up downloading about 1.2 Gb. Thank goodness my ISP connection kept going!

After the upgrade, I had a new OpenOffice and sound and video were fine, so was web flash video (apart from the usual slow performance in full screen).

I have to say that the Jaunty desktop is noticeably more responsive than Intrepid 8.1 (as well as booting faster).

And you guys were right - my custom settings were preserved.  Even my mtrr hack still works, and my temperature sensors are still there, etc.

I had to rebuild my mplayer and ffmpeg binaries for them to work again (the Ubuntu packages for these work fine - I just prefer newer versions).

It seems totem has got better as well - more responsive. Might even make it my firefox media player plug-in instead of gecko-mplayer ...

---

