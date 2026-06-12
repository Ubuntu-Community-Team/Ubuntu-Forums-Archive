---
title: "Changing the login manager and splash screen from xfce to gnome"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by kushlendramishra on 2010-03-22
:confused:I have installed ubuntu 9.10 karmic. Earlier, I tried xfce and liked gnome-desktop better so reverted back. Now everything is fine, but I can't get rid of the xfce login manager and the rat splash screen. I have searched all forums and tried all the solutions out there, but without any good. Any suggestions?

---

### Post by zeroseven0183 on 2010-03-22
Hi! Have you tried removing Xubuntu packages? If not, you can switch to Gnome by copy-pasting the following to a Terminal:

```

sudo apt-get remove a2ps abiword abiword-common  abiword-help abiword-plugin-grammar abiword-plugin-mathview  abiword-plugins app-install-data-commercial catfish exaile exo-utils feh  fortune-mod fortunes-min giblib1 gigolo gnome-app-install gnumeric  gnumeric-common gnumeric-doc gtk2-engines-xfce imagemagick  libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a  libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libgnomecups1.0-1  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0  libgnomeprintui2.2-common libgoffice-0-8 libgoffice-0-8-common  libgtkmathview0c2a libid3tag0 libimlib2 liblink-grammar4 libotr2 libots0  libpolkit-dbus2 libpolkit-gnome0 libpolkit-grant2 libpolkit2 librecode0  libscim8c2a libt1-5 libtagc0 libthunar-vfs-1-2 libwv-1.2-3  libxcb-keysyms1 libxfce4menu-0.1-0 libxfce4util4 libxfcegui4-4  libxfconf-0-2 libxmlrpc-core-c3 link-grammar-dictionaries-en mousepad  orage pidgin pidgin-data pidgin-libnotify pidgin-otr policykit  policykit-gnome psutils python-cddb python-mmkeys python-mutagen  ristretto scim scim-bridge-agent scim-bridge-client-gtk  scim-gtk2-immodule scim-modules-socket scim-modules-table  scim-tables-additional tango-icon-theme tango-icon-theme-common tcl  thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin  thunar-thumbnailers thunar-volman thunderbird ttf-arphic-uming  ttf-liberation usb-creator usplash-theme-xubuntu vim-runtime wdiff xchat  xchat-common xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin  xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin  xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin  xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin  xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin  xfce4-screenshooter xfce4-session xfce4-settings  xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal  xfce4-utils xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin  xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4  xfswitch-plugin xfwm4 xfwm4-themes xubuntu-artwork  xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop  xubuntu-docs xubuntu-gdm-theme xubuntu-wallpapers && sudo  apt-get install ubuntu-desktop
```

Source: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Elfy on 2010-03-22
This used to work - not sure about now though, it's a long time since I needed to do this.

```
sudo update-alternatives --config usplash-artwork.so
```

and choose the ubuntu splash

---

### Post by kushlendramishra on 2010-03-22
@zeroseven0183:It worked! Thanks:D.

@forestpiskie: I had tried that earlier but to no avail. Thanks for replying.:wink:

---

