---
title: "What are the differences between Gnome and KDE?"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by Newbez on 2009-11-14
I'm wondering whether to download Kubuntu or Ubuntu. All I know is that they look different, I actually prefer the look of Kubuntu because it's interface is more similar to Windows (yes, I have been a Windows user all my life). So can someone tell me the differences without typing an essay, a paragraph will do.

---

### Post by SuperSonic4 on 2009-11-14
Never used gnome so this will be no way balanced


KDE is largely written in Qt and so any non-native programs (such as gtk) will look out of place unless you install a package to do so: *gtk-qt-engine-svn*

KWin does away with the need for any additional composting (such as compiz) and the KDE desktop is well connected and integrated while having become more modular in KDE 4.x. KDE 4.3 is now a stable system and it is very pretty.

Amarok and K3B are two excellent programs for music and disc burning/ripping/copying respecitvely which many gnome users also use.

---

### Post by Paqman on 2009-11-14
Psychocats has a good article on this:

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

---

### Post by Newbez on 2009-11-14
> **SuperSonic4 said:**
> Never used gnome so this will be no way balanced


KDE is largely written in Qt and so any non-native programs (such as gtk) will look out of place unless you install a package to do so: *gtk-qt-engine-svn*ing/ripping/copying respecitvely which many gnome users also use.
I don't have a clue what that means... I'm a total Ubuntu n00b. I've been using Windows for too long :p.

---

### Post by SuperSonic4 on 2009-11-14
Essentially Qt and Gtk are different styles used by programmers to give the code a graphical interface. 

KDE largely uses Qt and Gnome Gtk. 

Gtk will work on KDE but it won't look as nice as native Qt apps. On KDE you can force Gtk apps to use a Qt style with the following command

```
sudo apt-get install gtk-qt-engine-svn
```

---

### Post by yeats on 2009-11-14
Both have advantages and both are worth learning how to live in.  SuperSonic4 has described the main differences and a Google search of "KDE Gnome comparison" will bring up many links worth reading.  On a really basic level, though, GNOME is more user-configurable - you can basically make it look completely different.  Compiz (which works on KDE - though Kwin is better in that environment IMHO) makes GNOME an eye candy paradise.  GNOME will also get better support in Ubuntu - especially on these forums.  I'm currently in a GNOME phase, but I tend to prefer KDE myself :-).

You'll find that the preferences toward one environment for another are entirely about personal opinion in the end.

---

### Post by Ji Ruo on 2009-11-14
I've found that there is more help around for GNOME than for KDE. There are more GNOME users in Ubuntu than KDE, and so there are more people on the forums who can provide help. And most of the advice, how-to's and tutorials are geared towards GNOME. I found it was just that bit harder to accomplish things in KDE, like getting the graphics card driver to work, to enable compiz effects, get a network set up etc because of this.

Kubuntu looks nicer with its default settings and I prefer the look and function of the desktop, but I have found Compiz easier to get working on Ubuntu (the attachment is a screenshot of compiz working on my desktop - sphere ftw) so this might also be a consideration for you.

The quality can go up and down between versions. Kubuntu Jaunty (9.04) had a couple of bugs with the network manager and the package management software that Ubuntu just didn't have, so Ubuntu edged ahead. These have probably been fixed for the latest release (Karmic).

And it must be pointed out that you don't have to choose only one or the other. If you're keen on trying both, you can install one on top of the other. Then at the login screen, before entering your username and password click on 'Options' and select the Desktop you wish to use for that session. Search for 'kubuntu-desktop' in Synaptic, or 'ubuntu-desktop' in K PackageKit then download, install, and restart your computer for it to take effect. You may end up downloading the libraries for both GNOME and KDE anyway if you are using say firefox, GIMP, VLC and Pidgin on your Kubuntu system (all GNOME based) or programs like K3b in Ubuntu. So it's worth considering.

---

