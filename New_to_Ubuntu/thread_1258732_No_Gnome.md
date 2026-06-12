---
title: "No Gnome"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-09-05
Hi

I recently removed something which took away my Ubutu desktop 
So I logged out and then when I logged back in I clicked on options and then change session followed by Gnome but when the desktop appears I've still got XFCE?

How do I get my desktop back?

---

### Post by Liolikas on 2009-09-05
Install Gnome again.

---

### Post by ibizatunes on 2009-09-05
```
sudo apt-get install ubuntu-desktop
```

should do it

---

### Post by Anybloodyid on 2009-09-05
Did that but still doesn't appear when I click on it?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.

---

### Post by ibizatunes on 2009-09-05
what did you remove?

---

### Post by Finalfantasykid on 2009-09-05
Ok I have an idea.

```
sudo apt-get remove ubuntu-desktop
```

then after that is done, type

```
sudo apt-get install ubuntu-desktop
```

I think the ubuntu-desktop package only contains a list of other packages it needs to download.  So removing it should do no harm, but when you install it again, it should check all those sources again, and download the ones that you are missing.

---

### Post by Anybloodyid on 2009-09-05
Tried uninstall and reinstall
Logged out and in
Changed session to Gnome
Nothing!!

---

### Post by snowpine on 2009-09-05
Forgive me if this is a stupid question... :)

When you choose Options->Sessions->Gnome and then log in... how exactly do you know you aren't in Gnome? What are the "symptoms"?

---

### Post by Anybloodyid on 2009-09-05
Hi
Not a stupid question at all I might be in Gnome but I can see that rat in the bottom left of my desktop which is not the desktop that I want.
I want the ubuntu desktop that I had when I first installed Ubuntu.

---

### Post by wojox on 2009-09-05
Try:

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by snowpine on 2009-09-05
Can you just right click and Change Desktop Background back to the original artwork?

---

### Post by R_W322 on 2009-09-05
Boot in to XFce then run this ```
 Sudo apt-get remove ubuntu-desktop 
```Then after its removed run this code.

```
sudo apt-get remove a2ps abiword abiword-common abiword-help abiword-plugin-grammar abiword-plugin-mathview abiword-plugins app-install-data-commercial aumix catfish cupsys-driver-gutenprint exo-utils fortune-mod fortunes-min gigolo gnumeric gnumeric-common gnumeric-doc gnumeric-gtk gpicview gtk2-engines-xfce imagemagick imagemagick-doc latex-xft-fonts libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libdiscid0 libexo-0.3-0 libfftw3-3 libgda3-3 libgda3-bin libgda3-common libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0-6 libgoffice-0-6-common libgoffice-gtk-0-6 libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libloudmouth1-0 libmad0 libmpcdec3 libnotify-bin libofa0 libots0 librecode0 libt1-5 libtagc0 libthunar-vfs-1-2 libtunepimp5 libwv-1.2-3 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4 libxfconf-0-2 link-grammar-dictionaries-en listen mousepad mozilla-thunderbird orage oss-compat psutils python-gnome2-extras python-musicbrainz2 python-mutagen python-ogg python-pymad python-pyogg python-pysqlite2 python-pyvorbis python-tunepimp scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl8.4 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime wdiff xchat xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xubuntu-artwork xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```I Don't know if you want to keep XFce or not but this will Install the Default Gnome Desktop for you.

RYAN.WDZIECZNY

---

### Post by Anybloodyid on 2009-09-06
Tried that still no luck
Now when computer starts I get Ubuntu Studio (Yes I Did install this) at least that's what it says as progress bar lights up the Ubuntu Studio wording.
But when it's loaded I still get the rat in the bottom corner.
I'm thinking maybe leave it the computer boots up I can surf the net and use Open Office so what's the point?
Used to get these quirky things in windoze so what's new?

---

### Post by Anybloodyid on 2009-09-06
Simple solution to it all really, I just removed everything that had XFCE ttached to it and back came my Ubuntu desktop.

---

