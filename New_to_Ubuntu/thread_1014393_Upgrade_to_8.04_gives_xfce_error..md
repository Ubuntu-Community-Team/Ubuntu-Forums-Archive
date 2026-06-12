---
title: "Upgrade to 8.04 gives xfce error."
date: 2008-12-17
forum: New to Ubuntu
---

### Post by memullen on 2008-12-17
I tried to upgrade 7.10 to 8.04 three times.  Each time, I get a blue screen (Not a BSOD) with an xfce message about not having thunar installed.  No panels, no heron, nothing familiar, and only a few icons, all broken.  As far as I can tell, it has upgraded the system to Xubuntu, but I am no expert, or I wouldn't be posting here.  I have spent over 6 hours on the forums, and can't find anything relevant.

The only reason I am trying to upgrade via net is that my Broadcomm wireless can't be made to work with 7.10 (It installs, but kwifi whatever says there are no networks), and the disk upgrade can't recognize 8.04 iso cdrom (burnt errorfree and checked by two systems on two brands of disk with two different burner packages)
I am beginning to wonder if anything in linux really works--every step I take leads me to new failures.

---

### Post by evilkastel on 2008-12-17
ok let's not get cranky. that particular upgrade is really strange. And upgrades can get messy, you'll be better backing up your data and performing a fresh install of 8.10 or 8.04.

---

### Post by memullen on 2008-12-17
> **evilkastel said:**
> ok let's not get cranky. that particular upgrade is really strange. And upgrades can get messy, you'll be better backing up your data and performing a fresh install of 8.10 or 8.04.

Well, I've done it three times.  How many more times should I try? 
 There isn't any data to back up.  It was a fresh install of 7.10 from a Linux magazine, and I liked the s/w that came with it, but it's rather usless without a wireless link.  And I don't even know if the upgrade will fix the problem, but two weeks of following links for wireless problems with 7.10 is more time wasted than I want.

---

### Post by evilkastel on 2008-12-17
ohh thats easier. I am sorry for your bad experience. 7.10 is an merely outdated version and wifi support is better on hardy (8.04) or Intrepid (8.10). I'll recommend you download an 8.10 iso and do a fresh install, wiping the disk. if you want xfce, get xubuntu here: [http://www.xubuntu.org/news/intrepid/release](http://www.xubuntu.org/news/intrepid/release) 
please consider too Gnome, as in ubuntu regular flavor. Xfce is a less consuming DE.

---

### Post by memullen on 2008-12-17
I _don't_ want xfce -- it showed up uninvited after the upgrade.  I want the same desktop I had before the 'upgrade', complete with the nice program collection that I will lose if I do a new install.  Everything I read indicates that the upgrade to 8.04 seems to have effectively done an upgrade to xubuntu -- I thought I had clicked on the wrong link the first time.
The stuff seems to be there.  The Heron desktop is visible, and the gnome panel across the top, until I 'complete the install by rebooting'.  Then I get what seems to be teh xfce desktop, but none of the icons work, and there is a message on the screen complaining about no file handler being there.

If I call up nautilus from the command line, a few things show up, but not all, and and it doesn't hang around after a reboot.

---

### Post by evilkastel on 2008-12-17
see, To replicate your packages selection on another machine (or restore it if re-installing), you can type ```
aptitude --disable-columns --display-format '%p' search '?installed!?automatic' > ~/my-packages », move the file "my-packages" to the other machine, and there type « sudo xargs aptitude --schedule-only install < my-packages ; sudo aptitude install
```

so, what's stopping you from doing a fresh install? ;) your upgrade is messy and i do not know the procedure to fix it if it is possible.

---

### Post by zvacet on 2008-12-18
@ **memullen**


> and the disk upgrade can't recognize 8.04 iso cdrom

You can upgrade only from alternate CD.If your Gutsy have ubuntu-desktop I don´t know how is it possible to upgrade to xubuntu-desktop.If desktop is only problem and all other things are upgraded right you can try this

```
sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins aumix catfish cupsys-driver-gutenprint exo-utils gnumeric gnumeric-common gnumeric-gtk gpicview gtk2-engines-xfce imagemagick latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libdiscid0 libexo-0.3-0 libfftw3-3 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libmad0 libmpcdec3 libnotify-bin libofa0 libots0 libt1-5 libtagc0 libthunar-vfs-1-2 libtunepimp5 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 link-grammar-dictionaries-en listen mousepad mozilla-thunderbird orage psutils python-ctypes python-gnome2-extras python-musicbrainz2 python-mutagen python-ogg python-pymad python-pyogg python-pysqlite2 python-pyvorbis python-tunepimp scim-modules-table scim-tables-additional slocate tango-icon-theme tango-icon-theme-common tcl8.4 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-governor-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mcs-plugins-extra xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```

---

### Post by memullen on 2008-12-18
I finally just:
sudo apt-get remove xfce*

and rebooted. Looks OK now.

Evilkastel, thanks for your help.

---

