---
title: "apt-get want to remove gnome desktop..."
date: 2009-06-23
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-06-23
Hi, question:

A recent update removed the network manager in the gnome-panel.
Now I cannot connect to the wireless network anymore, which is a problem, because I don't have a wired network anymore.

I tried connecting via command line, but that just doesn't work.

Now, fortunately I still had knetworkmanager installed, so I could start knetworkmanager from console, and join my wireless network...


Now I tried to reinstall network-manager-gnome, and this is what I got:
> 
all:~# apt-get install network-manager-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libempathy23 espeak ekiga gcalctool telepathy-salut gnome-nettool
  libgtk-vnc-1.0-0 libgail-gnome-module libtelepathy-glib0 gucharmap cheese
  gnome-power-manager gnome-screensaver libgtksourceview1.0-0
  libgstfarsight0.10-0 telepathy-mission-control gtk2-engines-pixbuf
  libmissioncontrol-client0 gnome-themes seahorse empathy
  libpt2.6.1-plugins-alsa libempathy-common libempathy-gtk19 gvfs-bin vinagre
  swfdec-gnome seahorse-plugins python-gtksourceview libtelepathy-farsight0
  festlex-cmu dasher libopal3.6.1 libcryptui0 libbrlapi0.5 gnome-orca
  fast-user-switch-applet python-pyatspi gnome-volume-manager
  gnome-backgrounds dasher-data python-brlapi gok espeak-data python-metacity
  festlex-poslex at-spi libgtksourceview-common vino mousetweaks
  festvox-kallpc16k python-rsvg libswfdec-0.8-0 libespeak1 telepathy-gabble
  libmissioncontrol-server1 python-mediaprofiles libtelepathy2
  libgnome-speech7 gstreamer0.10-nice libpt2.6.1 python-totem-plparser
  dmz-cursor-theme python-evolution festival libempathy-gtk-common
  gconf-editor gnome-system-tools gnome-accessibility libpt2.6.1-plugins-v4l2
  hamster-applet python-nautilusburn libnice0 totem gnome-accessibility-themes
  python-gnome2-desktop libavahi-ui0 libestools1.2 gstreamer0.10-tools
  file-roller python-gtop sound-juicer
Use 'apt-get autoremove' to remove them.
Suggested packages:
  network-manager-openvpn-gnome network-manager-vpnc-gnome
  network-manager-pptp-gnome
[B]The following packages will be REMOVED:
  gnome-desktop-environment gnome-network-admin[/B]
The following NEW packages will be installed:
  network-manager-gnome
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 746kB of archives.
After this operation, 2101kB of additional disk space will be used.
Do you want to continue [Y/n]? n 



Is that the wrong network manager, or why is apt bitching like this? I mean once chose the Y on a prompt like this, and then gnome was gone, including most of the installed software...

---

### Post by del_diablo on 2009-06-23
> The following packages were automatically installed and are no longer required:

Which means nothing that runs needs them. Run
```
sudo apt-get autoremove
```
to clean em.

>  fortunately I still had knetworkmanager installed,

Does not Gnetwork manager and Knetwork manager conflict? And are you actually running GNOME?

---

### Post by WitchCraft on 2009-06-23
> **del_diablo said:**
> 
Does not Gnetwork manager and Knetwork manager conflict? And are you actually running GNOME?

Yes I am running gnome, no they don't conflict, I've had them both installed for more than 6 months now.

> **del_diablo said:**
> Which means nothing that runs needs them. Run
```
sudo apt-get autoremove
```
to clean em.

No, I don't think that would be good idea.
I'd rather tend to run aptitude and reinstall apt-get.

---

