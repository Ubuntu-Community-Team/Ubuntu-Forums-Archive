---
title: "I lost my &quot;browse c:&quot; and &quot;uninstaller&quot; buttons in Wine after lubuntu uninstall"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by mr.xulu on 2010-09-28
Hi! I have lucid installed and have just a few minutes ago uninstalled the lubuntu desktop environment from it to revert back to a pure gnome environment.

1. I followed the instructions from this link (the full command is pasted below at the bottom of this post): 

[http://ubuntuforums.org/showthread.php?p=9843196](http://ubuntuforums.org/showthread.php?p=9843196)

2. After uninstall of lubuntu, I noticed I lost my "browse c:" and "uninstaller" buttons of Wine.

3. "Wine" is still listed in the applications menu and when I hover cursor over "wine", only the "programs" button/icon appears. "Browse C:" and "Uninstaller" should appear below that but their gone now.

4. And when I move cursor further to the right to hover cursor over "programs", the "safari" and "apple software update" buttons appear. there's supposed to be a third apple icon/button listed in this last list which I can't remember anymore and which is gone too.

How do I get the lost buttons back?

Hope someone can help.

Thanks a lot! :)



Here's the full code of the lubuntu uninstall i performed:

[code] sudo apt-get remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview aqualung arj cheese cheese-common chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg elementary-icon-theme epdfview galculator giblib1 gnome-mplayer gnumeric gnumeric-common gnumeric-doc gpicview hardinfo keyutils leafpad libabiword-2.8 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libaudio2 libavcodec52 libavformat52 libavutil49 libburn4 libcddb2 libcheese-gtk18 libcompfaceg1 libdiscid0 libdvdnav4 libdvdread4 libenca0 libexo-0.3-0 libexo-common libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-0.8-8 libgoffice-0.8-8-common libgringotts2 libgsm1 libgtkmathview0c2a libid3tag0 libifp4 libimlib2 libisofs6 libjpeg-progs liblink-grammar4 liblrdf0 liblua5.1-0 liblzo2-2 libmad0 libmcrypt4 libmenu-cache1 libmhash2 libmodplug0c2 libmp3lame0 libmpcdec3 libmusicbrainz3-6 libobparser21 libobrender21 liboggz2 libonig2 libopenal1 libots0 libpostproc51 libpsiconv6 librpm0 librpmbuild0 librpmio0 libschroedinger-1.0-0 libsexy2 libsvga1 libswscale0 libt1-5 libthunar-vfs-1-2 libuniconf4.6 libvpx0 libwv-1.2-3 libwvstreams4.6-base libwvstreams4.6-extras libx264-85 libxfce4util-bin libxfce4util-common libxfce4util4 libxfcegui4-4 libxfconf-0-2 libxvidcore4 link-grammar-dictionaries-en lubuntu-artwork lubuntu-default-settings lubuntu-desktop lubuntu-plymouth-theme lxappearance lxde-common lxde-core lxdm lxinput lxlauncher lxmenu-data lxpanel lxrandr lxsession lxsession-edit lxshortcut lxterminal mplayer mtpaint ntp obconf openbox openbox-themes osmo p7zip-full parcellite pcmanfm pidgin pidgin-data pidgin-libnotify powernowd pyneighborhood rpm rpm-common rpm2cpio scrot smbfs sylpheed sylpheed-i18n tcl thunar-data transmission transmission-cli ttf-lyx wvdial xarchiver xchat xchat-common xfburn xfce-keyboard-shortcuts xfce4-taskmanager xfconf xscreensaver xserver-xorg-input-evtouch && sudo apt-get install ubuntu-desktop[code]

---

### Post by Hippytaff on 2010-09-28
I lost loads of dependencies when reverting back to Ubuntu from Kubuntu by using a similar method to you. I decided to do a fresh install, but I'm sure theres an easier way to do it.
 
Maybe reinstall wine...or wait for some better advice from more accomplished ubuntuans :-)

---

### Post by mr.xulu on 2010-09-28
Hi Hippytaff! I did a reinstall. it worked! Thanks a lot! :)

---

### Post by Hippytaff on 2010-09-28
Glad I could help with my limited knowledge :-)

---

