---
title: "Removing files in a glorious cleansing fire"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by new__buntu on 2010-07-19
I typed the following command into terminal:"$sudo apt-get install xubuntu-desktop"
so that I could try out xubuntu. Turns out I like gnome, so I typed in:"$sudo apt-get purge xubuntu-desktop" to clear that junk out. My computer still insists that it's a xubuntu machine when booting up and down and I still have a bunch of redundant applications that came along with xubuntu, plus I can still select a xubuntu session when logging in. It's not really a serious problem, but it's annoying me to no end (I *hate* feeling powerless over my computer). So what's an effective means of clearing that stuff off of my computer?

---

### Post by bigsmitty64 on 2010-07-19
[THIS]("http://www.psychocats.net/ubuntu/puregnome") may help?

---

### Post by Legendary_Bibo on 2010-07-19
> **bigsmitty64 said:**
> [THIS]("http://www.psychocats.net/ubuntu/puregnome") may help?

for the lazy.

```

sudo apt-get remove a2ps abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview app-install-data-commercial aumix aumix-common catfish exaile exo-utils fortune-mod fortunes-min gigolo gimp gimp-data gnumeric gnumeric-common gnumeric-doc gtk2-engines-xfce libabiword-2.8 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libbabl-0.0-0 libexo-0.3-0 libexo-common libgdome2-0 libgdome2-cpp-smart0c2a libgegl-0.0-0 libgimp2.0 libgoffice-0.8-8 libgoffice-0.8-8-common libgtkmathview0c2a libjpeg-progs  liblink-grammar4 libmng1 libotr2 libots0 libpsiconv6 librecode0 libscim8c2a libsdl1.2debian-alsa libsexy2 libt1-5 libtagc0 libthunar-vfs-1-2 libwv-1.2-3 libxcb-keysyms1 libxfce4menu-0.1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfcegui4-4 libxfconf-0-2 libxmlrpc-core-c3 link-grammar-dictionaries-en mousepad murrine-themes orage oss-compat pidgin pidgin-data pidgin-libnotify pidgin-otr psutils python-cddb python-mmkeys python-mutagen python-sexy ristretto scim scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional tango-icon-theme tango-icon-theme-common tcl thunar  thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird ttf-lyx usb-creator vim-runtime wdiff xchat xchat-common xfce-keyboard-shortcuts xfce4-appfinder xfce4-clipman  xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin  xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfswitch-plugin xfwm4 xfwm4-themes xscreensaver xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-gdm-theme xubuntu-icon-theme xubuntu-plymouth-theme xubuntu-wallpapers &&  sudo apt-get install ubuntu-desktop 

```

---

### Post by Legendary_Bibo on 2010-07-19
And for the really lazy, just enable permissions if you have to and then run it in terminal.

---

### Post by Kay The Bantu on 2010-07-19
I'm not quite sure if this will help but i always use

```
sudo apt-get autoremove
```

cleans out everything including dependancies.

---

### Post by Legendary_Bibo on 2010-07-19
> **Kay The Bantu said:**
> I'm not quite sure if this will help but i always use

```
sudo apt-get autoremove
```cleans out everything including dependancies.

The problem I have with this is that if you're using applications from two DE's then it will remove the dependencies of one. I have some KDE applications and I keep getting a message to remove the KDE dependencies and I know that's not a great idea.

---

### Post by new__buntu on 2010-07-19
SUCCESS! Many thanks to everybody, this forum has once more saved me from my own stupid self, and in a timely manner to boot. :D

---

### Post by Legendary_Bibo on 2010-07-19
> **new__buntu said:**
> SUCCESS! Many thanks to everybody, this forum has once more saved me from my own stupid self, and in a timely manner to boot. :D
what did you use?

---

### Post by new__buntu on 2010-07-19
I used the terrifyingly long terminal command, followed by an apt-get autoremove for good measure.

---

### Post by Kay The Bantu on 2010-07-19
> **Legendary_Bibo said:**
> The problem I have with this is that if you're using applications from two DE's then it will remove the dependencies of one. I have some KDE applications and I keep getting a message to remove the KDE dependencies and I know that's not a great idea.

Thanx for the heads-up, i'll tread carefully.

---

### Post by Legendary_Bibo on 2010-07-19
> **new__buntu said:**
> I used the terrifyingly long terminal command, followed by an apt-get autoremove for good measure.

Well all is good then! :)

Shell scripts are for people who fear the terminal. ;)

Don't fear it, it's the most powerful tool in Linux.

---

