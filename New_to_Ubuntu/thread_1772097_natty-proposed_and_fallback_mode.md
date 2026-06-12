---
title: "natty-proposed and fallback mode?"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by soylentcola on 2011-05-31
So, I think I didn't read close enough on my last 11.04 update and after updating, my graphics card is apparently not up to snuff and I was forced into fallback mode on my install, if I turned forced fallback mode off, will it cause me any detrimental problems to my system or can I do so without issues?

For that matter, how does one go about updating their graphics card through Ubuntu (or would I have to do this through Windows)? I'm running a pretty basic laptop so I doubt I'll have any updates to even get, but I just wanted to ask...

---

### Post by wildmanne39 on 2011-05-31
> **soylentcola said:**
> So, I think I didn't read close enough on my last 11.04 update and after updating, my graphics card is apparently not up to snuff and I was forced into fallback mode on my install, if I turned forced fallback mode off, will it cause me any detrimental problems to my system or can I do so without issues?

For that matter, how does one go about updating their graphics card through Ubuntu (or would I have to do this through Windows)? I'm running a pretty basic laptop so I doubt I'll have any updates to even get, but I just wanted to ask...
Hi, go into admin then additional drivers see if there is a driver for your video card if so activate it and restart.

---

### Post by soylentcola on 2011-05-31
Nope, there's no additional drivers at all, nothing shows up. =\

---

### Post by wildmanne39 on 2011-05-31
> **soylentcola said:**
> Nope, there's no additional drivers at all, nothing shows up. =\
Hi, put this command in so we can see what video card you have.
```
lspci
```

---

### Post by coffeecat on 2011-05-31
As wildmanne39 says, let us know which your graphics card is, but I want to pick up something in your thread title: "natty-proposed". Have you enabled the proposed updates repository? That could be unwise and won't necessarily help you with a graphics issue. From this community documentation page:

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu%20Updates](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu%20Updates)

> "Pre-released Updates (lucid-proposed)".  The testing area for updates.  This repository is recommended only to those interested in helping to  test updates and provide feedback.And more strongly from this page:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

> Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.

---

### Post by soylentcola on 2011-05-31
Sorry for the long wait, I went back to my Windows partition to see if my driver needed updating...I think it did, though that did nothing for me on the Ubuntu side.  Either way, I ran lspci and this is what I got:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
```

Like I said, I'm running a basic laptop here, and yeah, I had enabled the natty-proposed updates, though in hindsight, I don't think that was a particularly smart idea, though on all my previous installs (all having enabled natty-proposed) I never ran into a problem like this, but I suppose it was bound to happen eventually!

**Edit:** As an extra, I also ran "/usr/lib/nux/unity_support_test -p" to see if I was still able to run Unity (though I switched to the classic mode) and ended up with this:

```
Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
```

In case that helps at all.

---

### Post by soylentcola on 2011-05-31
Rather than making one horrendously long post, figured I'd split this up into two separate ones... I went into the synaptic package manager and pulled up the history in case something I updated could've caused this issue (because I think it's in one of those updates that I did, honestly)

Not sure where to start though, because there's a lot of stuff there. <.<

```
Commit Log for Tue May 31 02:58:08 2011


Removed the following packages:
capplets-data
libbrasero-media1
libcryptui0
libevdocument3
libevview3
nautilus-sendto-empathy

Upgraded the following packages:
aisleriot (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
avahi-autoipd (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
avahi-daemon (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
avahi-utils (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
baobab (2.32.0-0ubuntu5) to 3.0.1-0ubuntu3~natty1
brasero-cdrkit (2.32.1-0ubuntu2) to 3.0.0-1ubuntu2~natty1
brasero-common (2.32.1-0ubuntu2) to 3.0.0-1ubuntu2~natty1
cdbs (0.4.90ubuntu14) to 0.4.93ubuntu3~natty1
cheese (2.32.0-0ubuntu2) to 3.0.0-0ubuntu1~build2
cheese-common (2.32.0-0ubuntu2) to 3.0.0-0ubuntu1~build2
empathy-common (2.34.0-0ubuntu3) to 3.0.2-0ubuntu1~build2
eog (2.32.1-0ubuntu2) to 3.0.2-0ubuntu1~natty1
evince (2.32.0-0ubuntu12.1) to 3.0.2-0ubuntu2~natty2
evince-common (2.32.0-0ubuntu12.1) to 3.0.2-0ubuntu2~natty2
evolution-common (2.32.2-0ubuntu7) to 3.0.0-2ubuntu1~natty1
evolution-data-server (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
evolution-data-server-common (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
evolution-plugins (2.32.2-0ubuntu7) to 3.0.0-2ubuntu1~natty1
file-roller (2.32.2-0ubuntu0.1) to 3.0.1-0ubuntu2~natty1
gcalctool (6.0.1~git20110421-0ubuntu1) to 6.0.2-0ubuntu1~natty1
gconf-editor (2.32.0-0ubuntu2) to 3.0.0-1ubuntu1~natty1
gdm (2.32.1-0ubuntu3.1) to 3.0.2-0ubuntu1~build1
gedit (2.30.4-2ubuntu1) to 3.0.3-0ubuntu1~natty1
gedit-common (2.30.4-2ubuntu1) to 3.0.3-0ubuntu1~natty1
gedit-plugins (2.30.0-1ubuntu1) to 3.0.2-0
gir1.2-freedesktop (0.10.7-0ubuntu1) to 0.10.8-1ubuntu1~natty1
gir1.2-glib-2.0 (0.10.7-0ubuntu1) to 0.10.8-1ubuntu1~natty1
gir1.2-notify-0.7 (0.7.2-0ubuntu2) to 0.7.3-1~natty1
gir1.2-soup-2.4 (2.34.0-0ubuntu1) to 2.34.2-1~natty1
glchess (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
glines (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnect (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnibbles (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnobots2 (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnome-accessibility-themes (2.32.1-0ubuntu1) to 3.0.0-0ubuntu1~build2
gnome-bluetooth (2.91.2.is.2.32.0-0ubuntu3) to 3.0.0-1ubuntu1~natty1
gnome-control-center (1:2.32.1-0ubuntu15) to 1:3.0.2-1ubuntu3~natty1
gnome-disk-utility (2.32.1-0ubuntu4) to 3.0.0-1ubuntu1~natty1
gnome-doc-utils (0.20.5-0ubuntu1) to 0.20.6-0ubuntu1~natty1
gnome-games-common (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnome-icon-theme (2.31.0-0ubuntu2) to 3.0.0-1ubuntu1~natty1
gnome-keyring (2.92.92.is.2.32.1-0ubuntu2) to 3.0.2-1~natty2
gnome-mahjongg (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnome-media (2.32.0-0ubuntu7) to 2.91.2-2ubuntu1~natty1
gnome-menus (2.30.5-0ubuntu3) to 3.0.0-0ubuntu1
gnome-nettool (2.32.0-0ubuntu1.1) to 3.0.0-0ubuntu2~natty1
gnome-orca (3.0.0-0ubuntu2) to 3.0.2-0ubuntu1~natty~build1
gnome-power-manager (2.32.0-2ubuntu2) to 3.0.0-1ubuntu4~natty1
gnome-screensaver (2.30.2-0ubuntu2) to 3.0.0-2ubuntu1~natty1
gnome-screenshot (2.32.0-0ubuntu5) to 3.0.1-0ubuntu3~natty1
gnome-search-tool (2.32.0-0ubuntu5) to 3.0.1-0ubuntu3~natty1
gnome-session (2.32.1-0ubuntu20) to 3.0.2-0ubuntu3~natty1
gnome-session-bin (2.32.1-0ubuntu20) to 3.0.2-0ubuntu3~natty1
gnome-session-common (2.32.1-0ubuntu20) to 3.0.2-0ubuntu3~natty1
gnome-settings-daemon (2.32.1-0ubuntu13.1) to 3.0.2-1ubuntu1~natty1
gnome-system-log (2.32.0-0ubuntu5) to 3.0.1-0ubuntu3~natty1
gnome-system-monitor (2.28.2-0ubuntu1) to 3.0.0-0ubuntu1~build1
gnome-terminal (2.32.1-0ubuntu3) to 3.0.1-0ubuntu1~natty1
gnome-terminal-data (2.32.1-0ubuntu3) to 3.0.1-0ubuntu1~natty1
gnome-themes-selected (2.32.1-0ubuntu1) to 3.0.0-0ubuntu1~build2
gnome-user-share (2.30.2-0ubuntu2) to 3.0.0-0ubuntu1~build1
gnome-utils-common (2.32.0-0ubuntu5) to 3.0.1-0ubuntu3~natty1
gnomine (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnotravex (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnotski (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gsettings-desktop-schemas (3.0.0-0ubuntu1) to 3.0.1-1~natty1
gtali (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gucharmap (1:2.32.1-0ubuntu2) to 1:3.0.0-1ubuntu1~natty1
iagno (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
ibus (1.3.9-0ubuntu3) to 1.3.9-0ubuntu4~gtk3
ibus-gtk (1.3.9-0ubuntu3) to 1.3.9-0ubuntu4~gtk3
libavahi-client3 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-common-data (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-common3 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-core7 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-glib1 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-gobject0 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-ui0 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libebook1.2-10 (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
libecal1.2-8 (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
libedataserver1.2-14 (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
libegroupwise1.2-13 (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
libevolution (2.32.2-0ubuntu7) to 3.0.0-2ubuntu1~natty1
libgdata-common (0.8.0-0ubuntu1) to 0.8.1-1~natty1
libgdata11 (0.8.0-0ubuntu1) to 0.8.1-1~natty1
libgdu-gtk0 (2.32.1-0ubuntu4) to 3.0.0-1ubuntu1~natty1
libgdu0 (2.32.1-0ubuntu4) to 3.0.0-1ubuntu1~natty1
libgirepository-1.0-1 (0.10.7-0ubuntu1) to 0.10.8-1ubuntu1~natty1
libgnome-bluetooth8 (2.91.2.is.2.32.0-0ubuntu3) to 3.0.0-1ubuntu1~natty1
libgnome-keyring0 (2.32.0-1ubuntu2) to 3.0.2-2~natty1
libgnome-menu2 (2.30.5-0ubuntu3) to 3.0.0-0ubuntu1
libgnomekbd-common (2.32.0-0ubuntu1) to 3.0.0.1-1~natty1
libgtk-vnc-1.0-0 (0.4.3-0ubuntu3) to 0.4.3-2ubuntu2~natty1
libgucharmap7 (1:2.32.1-0ubuntu2) to 1:3.0.0-1ubuntu1~natty1
libgweather-common (2.30.3-1ubuntu1) to 3.0.2-0ubuntu1~natty1
libibus2 (1.3.9-0ubuntu3) to 1.3.9-0ubuntu4~gtk3
libmission-control-plugins0 (1:5.7.7-1) to 1:5.7.11-1~natty1
libnautilus-extension1 (1:2.32.2.2-0ubuntu3~ppa170) to 1:3.0.2-0ubuntu1~natty1
libnotify4 (0.7.2-0ubuntu2) to 0.7.3-1~natty1
libpam-gnome-keyring (2.92.92.is.2.32.1-0ubuntu2) to 3.0.2-1~natty2
libpolkit-agent-1-0 (0.101-1ubuntu1) to 0.101-4~natty1
libpolkit-backend-1-0 (0.101-1ubuntu1) to 0.101-4~natty1
libpolkit-gobject-1-0 (0.101-1ubuntu1) to 0.101-4~natty1
libpolkit-gtk-1-0 (0.99-1ubuntu4) to 0.101-2ubuntu3~natty1
librsvg2-2 (2.32.1-0ubuntu3) to 2.34.0-0ubuntu2~natty2
librsvg2-common (2.32.1-0ubuntu3) to 2.34.0-0ubuntu2~natty2
libsoup-gnome2.4-1 (2.34.0-0ubuntu1) to 2.34.2-1~natty1
libsoup2.4-1 (2.34.0-0ubuntu1) to 2.34.2-1~natty1
libstartup-notification0 (0.10-1build1) to 0.12-1~natty1
libtelepathy-glib0 (0.14.3-1ubuntu1) to 0.14.6-0ubuntu1~natty~build1
libtelepathy-logger2 (0.2.6-1ubuntu1.2) to 0.2.9-1~natty1
libtotem-plparser17 (2.32.4-0ubuntu1) to 2.32.4-3~natty1
libxklavier16 (5.0-2ubuntu1) to 5.1-1ubuntu1~natty1
mousetweaks (3.0.0-0ubuntu2) to 3.0.2-0ubuntu1~natty~build2
nautilus (1:2.32.2.2-0ubuntu3~ppa170) to 1:3.0.2-0ubuntu1~natty1
nautilus-data (1:2.32.2.2-0ubuntu3~ppa170) to 1:3.0.2-0ubuntu1~natty1
nautilus-sendto (2.32.0-0ubuntu1) to 3.0.0-1ubuntu1~natty1
network-manager-gnome (0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1) to 0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1+noindicator1~build1
policykit-1 (0.101-1ubuntu1) to 0.101-4~natty1
policykit-1-gnome (0.99-1ubuntu4) to 0.101-2ubuntu3~natty1
python-gmenu (2.30.5-0ubuntu3) to 3.0.0-0ubuntu1
python-ibus (1.3.9-0ubuntu3) to 1.3.9-0ubuntu4~gtk3
quadrapassel (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
seahorse (2.32.0-0ubuntu3) to 3.0.2-0ubuntu1~natty1
seed (2.31.91-0ubuntu4) to 3.0.0-1~natty1
telepathy-butterfly (0.5.15-1) to 0.5.15-2.1~natty1
telepathy-gabble (0.11.10-1ubuntu1) to 0.12.0-1~natty1
telepathy-idle (0.1.8-1ubuntu1) to 0.1.10-1~natty1
telepathy-mission-control-5 (1:5.7.7-1) to 1:5.7.11-1~natty1
telepathy-salut (0.4.0-1) to 0.5.0-1~natty1
totem (2.32.0-0ubuntu10) to 3.0.1-0ubuntu2~natty1
totem-common (2.32.0-0ubuntu10) to 3.0.1-0ubuntu2~natty1
totem-mozilla (2.32.0-0ubuntu10) to 3.0.1-0ubuntu2~natty1
totem-plugins (2.32.0-0ubuntu10) to 3.0.1-0ubuntu2~natty1
vinagre (2.30.3-1ubuntu2) to 3.0.1-0ubuntu1~natty1
vino (2.32.1-0ubuntu2.1) to 3.0.2-0ubuntu4~natty1
yelp-xsl (3.0.0-0ubuntu1) to 3.0.2-1~natty1
zenity (2.32.1-0ubuntu1) to 3.0.0-1~natty1

Installed the following packages:
accountsservice (0.6.12-1ubuntu2~natty1)
apg (2.2.3.dfsg.1-2)
dh-translations (95)
evolution (3.0.0-2ubuntu1~natty1)
gir1.2-gnomebluetooth-1.0 (3.0.0-1ubuntu1~natty1)
gir1.2-gtk-3.0 (3.0.9-0ubuntu2~natty1)
gir1.2-gucharmap-2.90 (1:3.0.0-1ubuntu1~natty1)
gir1.2-peas-1.0 (1.0.0-1~natty1)
gir1.2-totem-1.0 (3.0.1-0ubuntu2~natty1)
gir1.2-totem-plparser-1.0 (2.32.4-3~natty1)
gir1.2-vte-2.90 (1:0.27.90-0ubuntu1)
gnome-control-center-data (1:3.0.2-1ubuntu3~natty1)
gnome-desktop3-data (3.0.2-1~natty1)
gnome-icon-theme-symbolic (3.0.0-1~build1)
gnome-session-fallback (3.0.2-0ubuntu3~natty1)
gnome-video-effects (0.3.0-1~natty1)
gtk3-engines (2.91.1-0ubuntu1~build2)
libaccountsservice0 (0.6.12-1ubuntu2~natty1)
libappindicator3-1 (0.3.0-0ubuntu1)
libavahi-ui-gtk3-0 (0.6.30-3ubuntu1~natty1)
libbrasero-media3-1 (3.0.0-1ubuntu2~natty1)
libcamel-1.2-23 (3.0.0-1ubuntu1~natty1)
libcanberra-gtk3-0 (0.28-0ubuntu3)
libcanberra-gtk3-module (0.28-0ubuntu3)
libcap2-bin (1:2.20-1)
libcheese-gtk19 (3.0.0-0ubuntu1~build2)
libclutter-gst-1.0-0 (1.3.6-1)
libclutter-gtk-1.0-0 (1.0.0-0ubuntu1)
libclutter-imcontext-0.1-0 (0.1.4-1ubuntu1)
libcluttergesture-0.0.2-0 (0.0.2.1-2ubuntu1)
libcryptui0a (3.0.2-0ubuntu1~natty1)
libdbusmenu-gtk3-3 (0.4.3-0ubuntu3)
libebackend-1.2-1 (3.0.0-1ubuntu1~natty1)
libedata-book-1.2-9 (3.0.0-1ubuntu1~natty1)
libedata-cal-1.2-11 (3.0.0-1ubuntu1~natty1)
libedataserverui-3.0-0 (3.0.0-1ubuntu1~natty1)
libevince3-3 (3.0.2-0ubuntu2~natty2)
libgail-3-0 (3.0.9-0ubuntu2~natty1)
libgck0 (3.0.2-1~natty2)
libgcr-3-0 (3.0.2-1~natty2)
libgnome-control-center1 (1:3.0.2-1ubuntu3~natty1)
libgnome-desktop-3-0 (3.0.2-1~natty1)
libgnome-media-profiles-3.0-0 (3.0.0-0ubuntu1~build1)
libgnomekbd7 (3.0.0.1-1~natty1)
libgtk-3-0 (3.0.9-0ubuntu2~natty1)
libgtk-3-bin (3.0.9-0ubuntu2~natty1)
libgtk-3-common (3.0.9-0ubuntu2~natty1)
libgtk-vnc-2.0-0 (0.4.3-2ubuntu2~natty1)
libgtkhtml-4.0-0 (4.0.0-1~build1)
libgtkhtml-4.0-common (4.0.0-1~build1)
libgtkhtml-editor-4.0-0 (4.0.0-1~build1)
libgtkmm-3.0-1 (3.0.1-0ubuntu1~natty~build1)
libgtksourceview-3.0-0 (3.0.2-1~natty1)
libgtksourceview-3.0-common (3.0.2-1~natty1)
libgucharmap-2-90-7 (1:3.0.0-1ubuntu1~natty1)
libgvnc-1.0-0 (0.4.3-2ubuntu2~natty1)
libgweather-3-0 (3.0.2-0ubuntu1~natty1)
libindicator3-3 (0.3.22-0ubuntu1)
liblaunchpad-integration-3.0-1 (0.1.51)
libmx-1.0-2 (1.1.3-0ubuntu4)
libpeas-1.0-0 (1.0.0-1~natty1)
libpeas-common (1.0.0-1~natty1)
libseed-gtk3-0 (3.0.0-1~natty1)
libtotem0 (3.0.1-0ubuntu2~natty1)
libunique-3.0-0 (3.0.0-1~natty1)
libvte-2.90-9 (1:0.27.90-0ubuntu1)
libwebkitgtk-3.0-0 (1.3.13-0ubuntu2)
libwebkitgtk-3.0-common (1.3.13-0ubuntu2)
libwnck-3-0 (3.0.2-1~natty1)
libwnck-3-common (3.0.2-1~natty1)
zenity-common (3.0.0-1~natty1)
```

---

### Post by coffeecat on 2011-05-31
Hi

> **soylentcola said:**
> 
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)[/code]

I have (nearly) the same graphics in one of my laptops, except that it is rev 07, not rev 09. Unity works just fine in Natty including with a recent update to the Intel xserver driver. Although not listed in your Synaptic history (it could have come in through apt-get update or Upadte Manager) I wonder if there has been a recent broken Intel driver from the proposed repository. 

The Intel video driver I have is: xserver-xorg-video-intel 2:2.14.0-4ubuntu7.1

Have a look in Synaptic and see if you have the same or later. If later it could be a proposed one and you could try rolling back to the earlier one.

**EDIT**: no, scratch that. I've just tried enabling the proposed repository to see what it would bring in and xserver-xorg-video-intel was not among them. However, it did want to update with some proposed xorg packages and also kernel version 2.6.38-9. Any of those could have broken the Intel display. I suggest you disable the proposed repository anyway and see if you can downgrade the packages that were brought in by proposed.

---

### Post by wildmanne39 on 2011-05-31
> **soylentcola said:**
> Rather than making one horrendously long post, figured I'd split this up into two separate ones... I went into the synaptic package manager and pulled up the history in case something I updated could've caused this issue (because I think it's in one of those updates that I did, honestly)

Not sure where to start though, because there's a lot of stuff there. <.<

```
Commit Log for Tue May 31 02:58:08 2011


Removed the following packages:
capplets-data
libbrasero-media1
libcryptui0
libevdocument3
libevview3
nautilus-sendto-empathy

Upgraded the following packages:
aisleriot (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
avahi-autoipd (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
avahi-daemon (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
avahi-utils (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
baobab (2.32.0-0ubuntu5) to 3.0.1-0ubuntu3~natty1
brasero-cdrkit (2.32.1-0ubuntu2) to 3.0.0-1ubuntu2~natty1
brasero-common (2.32.1-0ubuntu2) to 3.0.0-1ubuntu2~natty1
cdbs (0.4.90ubuntu14) to 0.4.93ubuntu3~natty1
cheese (2.32.0-0ubuntu2) to 3.0.0-0ubuntu1~build2
cheese-common (2.32.0-0ubuntu2) to 3.0.0-0ubuntu1~build2
empathy-common (2.34.0-0ubuntu3) to 3.0.2-0ubuntu1~build2
eog (2.32.1-0ubuntu2) to 3.0.2-0ubuntu1~natty1
evince (2.32.0-0ubuntu12.1) to 3.0.2-0ubuntu2~natty2
evince-common (2.32.0-0ubuntu12.1) to 3.0.2-0ubuntu2~natty2
evolution-common (2.32.2-0ubuntu7) to 3.0.0-2ubuntu1~natty1
evolution-data-server (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
evolution-data-server-common (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
evolution-plugins (2.32.2-0ubuntu7) to 3.0.0-2ubuntu1~natty1
file-roller (2.32.2-0ubuntu0.1) to 3.0.1-0ubuntu2~natty1
gcalctool (6.0.1~git20110421-0ubuntu1) to 6.0.2-0ubuntu1~natty1
gconf-editor (2.32.0-0ubuntu2) to 3.0.0-1ubuntu1~natty1
gdm (2.32.1-0ubuntu3.1) to 3.0.2-0ubuntu1~build1
gedit (2.30.4-2ubuntu1) to 3.0.3-0ubuntu1~natty1
gedit-common (2.30.4-2ubuntu1) to 3.0.3-0ubuntu1~natty1
gedit-plugins (2.30.0-1ubuntu1) to 3.0.2-0
gir1.2-freedesktop (0.10.7-0ubuntu1) to 0.10.8-1ubuntu1~natty1
gir1.2-glib-2.0 (0.10.7-0ubuntu1) to 0.10.8-1ubuntu1~natty1
gir1.2-notify-0.7 (0.7.2-0ubuntu2) to 0.7.3-1~natty1
gir1.2-soup-2.4 (2.34.0-0ubuntu1) to 2.34.2-1~natty1
glchess (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
glines (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnect (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnibbles (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnobots2 (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnome-accessibility-themes (2.32.1-0ubuntu1) to 3.0.0-0ubuntu1~build2
gnome-bluetooth (2.91.2.is.2.32.0-0ubuntu3) to 3.0.0-1ubuntu1~natty1
gnome-control-center (1:2.32.1-0ubuntu15) to 1:3.0.2-1ubuntu3~natty1
gnome-disk-utility (2.32.1-0ubuntu4) to 3.0.0-1ubuntu1~natty1
gnome-doc-utils (0.20.5-0ubuntu1) to 0.20.6-0ubuntu1~natty1
gnome-games-common (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnome-icon-theme (2.31.0-0ubuntu2) to 3.0.0-1ubuntu1~natty1
gnome-keyring (2.92.92.is.2.32.1-0ubuntu2) to 3.0.2-1~natty2
gnome-mahjongg (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnome-media (2.32.0-0ubuntu7) to 2.91.2-2ubuntu1~natty1
gnome-menus (2.30.5-0ubuntu3) to 3.0.0-0ubuntu1
gnome-nettool (2.32.0-0ubuntu1.1) to 3.0.0-0ubuntu2~natty1
gnome-orca (3.0.0-0ubuntu2) to 3.0.2-0ubuntu1~natty~build1
gnome-power-manager (2.32.0-2ubuntu2) to 3.0.0-1ubuntu4~natty1
gnome-screensaver (2.30.2-0ubuntu2) to 3.0.0-2ubuntu1~natty1
gnome-screenshot (2.32.0-0ubuntu5) to 3.0.1-0ubuntu3~natty1
gnome-search-tool (2.32.0-0ubuntu5) to 3.0.1-0ubuntu3~natty1
gnome-session (2.32.1-0ubuntu20) to 3.0.2-0ubuntu3~natty1
gnome-session-bin (2.32.1-0ubuntu20) to 3.0.2-0ubuntu3~natty1
gnome-session-common (2.32.1-0ubuntu20) to 3.0.2-0ubuntu3~natty1
gnome-settings-daemon (2.32.1-0ubuntu13.1) to 3.0.2-1ubuntu1~natty1
gnome-system-log (2.32.0-0ubuntu5) to 3.0.1-0ubuntu3~natty1
gnome-system-monitor (2.28.2-0ubuntu1) to 3.0.0-0ubuntu1~build1
gnome-terminal (2.32.1-0ubuntu3) to 3.0.1-0ubuntu1~natty1
gnome-terminal-data (2.32.1-0ubuntu3) to 3.0.1-0ubuntu1~natty1
gnome-themes-selected (2.32.1-0ubuntu1) to 3.0.0-0ubuntu1~build2
gnome-user-share (2.30.2-0ubuntu2) to 3.0.0-0ubuntu1~build1
gnome-utils-common (2.32.0-0ubuntu5) to 3.0.1-0ubuntu3~natty1
gnomine (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnotravex (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gnotski (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gsettings-desktop-schemas (3.0.0-0ubuntu1) to 3.0.1-1~natty1
gtali (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
gucharmap (1:2.32.1-0ubuntu2) to 1:3.0.0-1ubuntu1~natty1
iagno (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
ibus (1.3.9-0ubuntu3) to 1.3.9-0ubuntu4~gtk3
ibus-gtk (1.3.9-0ubuntu3) to 1.3.9-0ubuntu4~gtk3
libavahi-client3 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-common-data (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-common3 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-core7 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-glib1 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-gobject0 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libavahi-ui0 (0.6.30-0ubuntu2) to 0.6.30-3ubuntu1~natty1
libebook1.2-10 (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
libecal1.2-8 (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
libedataserver1.2-14 (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
libegroupwise1.2-13 (2.32.2-0ubuntu2) to 3.0.0-1ubuntu1~natty1
libevolution (2.32.2-0ubuntu7) to 3.0.0-2ubuntu1~natty1
libgdata-common (0.8.0-0ubuntu1) to 0.8.1-1~natty1
libgdata11 (0.8.0-0ubuntu1) to 0.8.1-1~natty1
libgdu-gtk0 (2.32.1-0ubuntu4) to 3.0.0-1ubuntu1~natty1
libgdu0 (2.32.1-0ubuntu4) to 3.0.0-1ubuntu1~natty1
libgirepository-1.0-1 (0.10.7-0ubuntu1) to 0.10.8-1ubuntu1~natty1
libgnome-bluetooth8 (2.91.2.is.2.32.0-0ubuntu3) to 3.0.0-1ubuntu1~natty1
libgnome-keyring0 (2.32.0-1ubuntu2) to 3.0.2-2~natty1
libgnome-menu2 (2.30.5-0ubuntu3) to 3.0.0-0ubuntu1
libgnomekbd-common (2.32.0-0ubuntu1) to 3.0.0.1-1~natty1
libgtk-vnc-1.0-0 (0.4.3-0ubuntu3) to 0.4.3-2ubuntu2~natty1
libgucharmap7 (1:2.32.1-0ubuntu2) to 1:3.0.0-1ubuntu1~natty1
libgweather-common (2.30.3-1ubuntu1) to 3.0.2-0ubuntu1~natty1
libibus2 (1.3.9-0ubuntu3) to 1.3.9-0ubuntu4~gtk3
libmission-control-plugins0 (1:5.7.7-1) to 1:5.7.11-1~natty1
libnautilus-extension1 (1:2.32.2.2-0ubuntu3~ppa170) to 1:3.0.2-0ubuntu1~natty1
libnotify4 (0.7.2-0ubuntu2) to 0.7.3-1~natty1
libpam-gnome-keyring (2.92.92.is.2.32.1-0ubuntu2) to 3.0.2-1~natty2
libpolkit-agent-1-0 (0.101-1ubuntu1) to 0.101-4~natty1
libpolkit-backend-1-0 (0.101-1ubuntu1) to 0.101-4~natty1
libpolkit-gobject-1-0 (0.101-1ubuntu1) to 0.101-4~natty1
libpolkit-gtk-1-0 (0.99-1ubuntu4) to 0.101-2ubuntu3~natty1
librsvg2-2 (2.32.1-0ubuntu3) to 2.34.0-0ubuntu2~natty2
librsvg2-common (2.32.1-0ubuntu3) to 2.34.0-0ubuntu2~natty2
libsoup-gnome2.4-1 (2.34.0-0ubuntu1) to 2.34.2-1~natty1
libsoup2.4-1 (2.34.0-0ubuntu1) to 2.34.2-1~natty1
libstartup-notification0 (0.10-1build1) to 0.12-1~natty1
libtelepathy-glib0 (0.14.3-1ubuntu1) to 0.14.6-0ubuntu1~natty~build1
libtelepathy-logger2 (0.2.6-1ubuntu1.2) to 0.2.9-1~natty1
libtotem-plparser17 (2.32.4-0ubuntu1) to 2.32.4-3~natty1
libxklavier16 (5.0-2ubuntu1) to 5.1-1ubuntu1~natty1
mousetweaks (3.0.0-0ubuntu2) to 3.0.2-0ubuntu1~natty~build2
nautilus (1:2.32.2.2-0ubuntu3~ppa170) to 1:3.0.2-0ubuntu1~natty1
nautilus-data (1:2.32.2.2-0ubuntu3~ppa170) to 1:3.0.2-0ubuntu1~natty1
nautilus-sendto (2.32.0-0ubuntu1) to 3.0.0-1ubuntu1~natty1
network-manager-gnome (0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1) to 0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1+noindicator1~build1
policykit-1 (0.101-1ubuntu1) to 0.101-4~natty1
policykit-1-gnome (0.99-1ubuntu4) to 0.101-2ubuntu3~natty1
python-gmenu (2.30.5-0ubuntu3) to 3.0.0-0ubuntu1
python-ibus (1.3.9-0ubuntu3) to 1.3.9-0ubuntu4~gtk3
quadrapassel (1:2.32.1-0ubuntu5) to 1:3.0.0-0ubuntu1~build1
seahorse (2.32.0-0ubuntu3) to 3.0.2-0ubuntu1~natty1
seed (2.31.91-0ubuntu4) to 3.0.0-1~natty1
telepathy-butterfly (0.5.15-1) to 0.5.15-2.1~natty1
telepathy-gabble (0.11.10-1ubuntu1) to 0.12.0-1~natty1
telepathy-idle (0.1.8-1ubuntu1) to 0.1.10-1~natty1
telepathy-mission-control-5 (1:5.7.7-1) to 1:5.7.11-1~natty1
telepathy-salut (0.4.0-1) to 0.5.0-1~natty1
totem (2.32.0-0ubuntu10) to 3.0.1-0ubuntu2~natty1
totem-common (2.32.0-0ubuntu10) to 3.0.1-0ubuntu2~natty1
totem-mozilla (2.32.0-0ubuntu10) to 3.0.1-0ubuntu2~natty1
totem-plugins (2.32.0-0ubuntu10) to 3.0.1-0ubuntu2~natty1
vinagre (2.30.3-1ubuntu2) to 3.0.1-0ubuntu1~natty1
vino (2.32.1-0ubuntu2.1) to 3.0.2-0ubuntu4~natty1
yelp-xsl (3.0.0-0ubuntu1) to 3.0.2-1~natty1
zenity (2.32.1-0ubuntu1) to 3.0.0-1~natty1

Installed the following packages:
accountsservice (0.6.12-1ubuntu2~natty1)
apg (2.2.3.dfsg.1-2)
dh-translations (95)
evolution (3.0.0-2ubuntu1~natty1)
gir1.2-gnomebluetooth-1.0 (3.0.0-1ubuntu1~natty1)
gir1.2-gtk-3.0 (3.0.9-0ubuntu2~natty1)
gir1.2-gucharmap-2.90 (1:3.0.0-1ubuntu1~natty1)
gir1.2-peas-1.0 (1.0.0-1~natty1)
gir1.2-totem-1.0 (3.0.1-0ubuntu2~natty1)
gir1.2-totem-plparser-1.0 (2.32.4-3~natty1)
gir1.2-vte-2.90 (1:0.27.90-0ubuntu1)
gnome-control-center-data (1:3.0.2-1ubuntu3~natty1)
gnome-desktop3-data (3.0.2-1~natty1)
gnome-icon-theme-symbolic (3.0.0-1~build1)
gnome-session-fallback (3.0.2-0ubuntu3~natty1)
gnome-video-effects (0.3.0-1~natty1)
gtk3-engines (2.91.1-0ubuntu1~build2)
libaccountsservice0 (0.6.12-1ubuntu2~natty1)
libappindicator3-1 (0.3.0-0ubuntu1)
libavahi-ui-gtk3-0 (0.6.30-3ubuntu1~natty1)
libbrasero-media3-1 (3.0.0-1ubuntu2~natty1)
libcamel-1.2-23 (3.0.0-1ubuntu1~natty1)
libcanberra-gtk3-0 (0.28-0ubuntu3)
libcanberra-gtk3-module (0.28-0ubuntu3)
libcap2-bin (1:2.20-1)
libcheese-gtk19 (3.0.0-0ubuntu1~build2)
libclutter-gst-1.0-0 (1.3.6-1)
libclutter-gtk-1.0-0 (1.0.0-0ubuntu1)
libclutter-imcontext-0.1-0 (0.1.4-1ubuntu1)
libcluttergesture-0.0.2-0 (0.0.2.1-2ubuntu1)
libcryptui0a (3.0.2-0ubuntu1~natty1)
libdbusmenu-gtk3-3 (0.4.3-0ubuntu3)
libebackend-1.2-1 (3.0.0-1ubuntu1~natty1)
libedata-book-1.2-9 (3.0.0-1ubuntu1~natty1)
libedata-cal-1.2-11 (3.0.0-1ubuntu1~natty1)
libedataserverui-3.0-0 (3.0.0-1ubuntu1~natty1)
libevince3-3 (3.0.2-0ubuntu2~natty2)
libgail-3-0 (3.0.9-0ubuntu2~natty1)
libgck0 (3.0.2-1~natty2)
libgcr-3-0 (3.0.2-1~natty2)
libgnome-control-center1 (1:3.0.2-1ubuntu3~natty1)
libgnome-desktop-3-0 (3.0.2-1~natty1)
libgnome-media-profiles-3.0-0 (3.0.0-0ubuntu1~build1)
libgnomekbd7 (3.0.0.1-1~natty1)
libgtk-3-0 (3.0.9-0ubuntu2~natty1)
libgtk-3-bin (3.0.9-0ubuntu2~natty1)
libgtk-3-common (3.0.9-0ubuntu2~natty1)
libgtk-vnc-2.0-0 (0.4.3-2ubuntu2~natty1)
libgtkhtml-4.0-0 (4.0.0-1~build1)
libgtkhtml-4.0-common (4.0.0-1~build1)
libgtkhtml-editor-4.0-0 (4.0.0-1~build1)
libgtkmm-3.0-1 (3.0.1-0ubuntu1~natty~build1)
libgtksourceview-3.0-0 (3.0.2-1~natty1)
libgtksourceview-3.0-common (3.0.2-1~natty1)
libgucharmap-2-90-7 (1:3.0.0-1ubuntu1~natty1)
libgvnc-1.0-0 (0.4.3-2ubuntu2~natty1)
libgweather-3-0 (3.0.2-0ubuntu1~natty1)
libindicator3-3 (0.3.22-0ubuntu1)
liblaunchpad-integration-3.0-1 (0.1.51)
libmx-1.0-2 (1.1.3-0ubuntu4)
libpeas-1.0-0 (1.0.0-1~natty1)
libpeas-common (1.0.0-1~natty1)
libseed-gtk3-0 (3.0.0-1~natty1)
libtotem0 (3.0.1-0ubuntu2~natty1)
libunique-3.0-0 (3.0.0-1~natty1)
libvte-2.90-9 (1:0.27.90-0ubuntu1)
libwebkitgtk-3.0-0 (1.3.13-0ubuntu2)
libwebkitgtk-3.0-common (1.3.13-0ubuntu2)
libwnck-3-0 (3.0.2-1~natty1)
libwnck-3-common (3.0.2-1~natty1)
zenity-common (3.0.0-1~natty1)
```
Hi, it looks like you installed gnome three if so that is probably the problem you can not have gnome 3 and unity, not yet it is one or the other is the gnome you looking into look like a new gnome, can you give a screen shot?

---

### Post by soylentcola on 2011-05-31
A screenshot of what exactly? The ubuntu that's running currently (i.e. fallback mode) or what I had previously?

---

### Post by wildmanne39 on 2011-05-31
> **soylentcola said:**
> A screenshot of what exactly? The ubuntu that's running currently (i.e. fallback mode) or what I had previously?
Hi, yes I was talking about the fall back. On the log in screen do you see an option to log in to ubuntu or gnome shell? Log out and see what is there and let me know.

---

### Post by soylentcola on 2011-05-31
I saw the option to log into the "ubuntu" shell, I also checked the software manager and found no mention of Gnome3.

---

### Post by soylentcola on 2011-05-31
I'm also having a bit of trouble with downgrading that kernel package...there doesn't seem to even be an option TO downgrade it, it's all grayed out, and I'm hesitant to remove it because I have a feeling it could damage the system...

---

### Post by soylentcola on 2011-05-31
m'kay, I *think* I found a solution to my problem, I managed to find the linux 2.6.38-8-generic kernel, which I'm assuming was the original one packaged with my install. I'm downloading it now to see if that'll fix things up, and if so, I'm going to remove the old kernel when I reboot.

I'll let you know how it goes.

---

### Post by coffeecat on 2011-05-31
> **soylentcola said:**
> I'm also having a bit of trouble with downgrading that kernel package...there doesn't seem to even be an option TO downgrade it, it's all grayed out, and I'm hesitant to remove it because I have a feeling it could damage the system...

You should still have the 2.6.38-8 kernel installed. Try booting into that - you'll find it under "Previous Linux Version" in the grub menu - to see if that helps. We can look into uninstalling the 2.6.38-9 kernel later.

However, wildmanne39 picked up an important point that I missed. You have a lot of gnome3 packages installed, and there are references to ppa and git repositories. So there are several possible causes for breakage. I haven't tried gnome3 in Natty since just before Natty was released and then (at least with the ppa I tried) it was not possible to log into a working Unity desktop with gnome3/gnome-shell installed. I don't know if things have changed since, or what you might expect with other PPAs. Which PPAs have you enabled? In fact it might be a good idea if you list all the repositories you have enabled apart from main, restricted, universe and multiverse.

**EDIT**: Just noticed this:

> **soylentcola said:**
> m'kay, I *think* I found a solution to  my problem, I managed to find the linux 2.6.38-8-generic kernel, which  I'm assuming was the original one packaged with my install. I'm  downloading it now to see if that'll fix things up, and if so, I'm going  to remove the old kernel when I reboot.

I'll let you know how it goes.

Unless you installed it, you will still have the 2.6.38-8 kernel - it doesn't get uninstalled automatically. You should be able to boot into it already.

---

### Post by soylentcola on 2011-05-31
> **coffeecat said:**
> **EDIT**: Just noticed this:



Unless you installed it, you will still have the 2.6.38-8 kernel - it doesn't get uninstalled automatically. You should be able to boot into it already.
I did manage to find it in synaptic, I had to do a search for it and pick through a few before I noticed it. Going to reboot now and see if I can't boot into it before I try to list out all my PPAs.

---

### Post by soylentcola on 2011-05-31
All right, I'm back and did manage to boot into 2.6.38-8, though it didn't help with fallback mode.  I'm also not entirely sure which PPAs you wanted exactly (I searched and got a bunch of "restricted, main, universe and multiverse") so I hope it's all right that I just copy-paste the sources.list file anyway.

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://archive.canonical.com/ natty partner
deb-src http://archive.canonical.com/ natty partner
deb http://dl.google.com/linux/deb/ testing non-free
```

As far as I know, all of these are active, but I think I'll double check to see if any of them aren't.

**Edit:** Yep, everything in here is active!

---

### Post by coffeecat on 2011-05-31
PPA repositories usually do not put entries in /etc/apt/sources.list. They create their own lists in /etc/apt/sources.list.d/. So to see what other repos you have enabled, post the output of:

```
ls /etc/apt/sources.list.d/
```We don't need to see the contents of each *list file. Just which ones you have.

---

### Post by soylentcola on 2011-05-31
Ah, gotcha! Here it is:

```
-me-davidsansome-natty.list
-me-davidsansome-natty.list.save
am-monkeyd-nautilus-elementary-ppa-natty.list
am-monkeyd-nautilus-elementary-ppa-natty.list.save
chromium-daily-stable-natty.list
chromium-daily-stable-natty.list.save
do-core-ppa-natty.list
do-core-ppa-natty.list.save
extras.list
extras.list.save
gnome3-team-gnome3-natty.list
gnome3-team-gnome3-natty.list.save
google-chrome.list
google-chrome.list.save
google-earth.list
google-earth.list.save
google.list
google.list.save
me-davidsansome-clementine-natty.list
me-davidsansome-clementine-natty.list.save
medibuntu.list
medibuntu.list.save
opera.list
opera.list.save
tiheum-equinox-natty.list
tiheum-equinox-natty.list.save
tualatrix-ppa-natty.list
tualatrix-ppa-natty.list.save
ubuntu-wine-ppa-natty.list
ubuntu-wine-ppa-natty.list.save
virtualbox.list
virtualbox.list.save
```

---

### Post by coffeecat on 2011-05-31
Hmmm. :-k A lot of 3rd party repos! :wink:

The potential problem with 3rd party repos is that they may introduce package conflicts and inconsistencies. Be that as it may, I've re-read your original post and I have a question. You say you were forced into "fallback" mode after some updates. Was that after enabling the gnome3-team ppa? I'll say again that I believe wildmanne39's mention of gnome3 may be the thing we need to focus on.

---

### Post by soylentcola on 2011-05-31
Now that you mention it, even looking through the list myself, I have no idea what the gnome3 repos are, I can identify most of the others pretty easily, but I can't for the life of me figure out where those gnome3 repos came from...outside of disabling them, what else do you think I should in order to fix up this problem?

---

### Post by coffeecat on 2011-05-31
> **soylentcola said:**
> Now that you mention it, even looking through the list myself, I have no idea what the gnome3 repos are, I can identify most of the others pretty easily, but I can't for the life of me figure out where those gnome3 repos came from...outside of disabling them, what else do you think I should in order to fix up this problem?

The gnome3-team repo was the one I used when I wanted to try gnome-shell (which is the shell that comes with gnome3) when Natty was still in testing. As I mentioned before, this prevented me from logging into the Unity desktop - I could only log into the gnome3 shell desktop, which looks something like this:

[http://www.gnome.org/gnome-3/](http://www.gnome.org/gnome-3/)

The ghastly blue-stripey default wallpaper is one distinctive feature. :(

Is your desktop like that? When you get to the login screen, are you being offered "Ubuntu Gnome Shell Desktop"? If so, that desktop is not a fallback mode, it's gnome-shell. If that's what you're seeing and you want Unity back, this is not a video driver problem but a conflict between all the gnome 3 stuff that came from the PPA and the fact that Unity is built on gnome2.

How to fix the problem? You could try ppa-purge to try to remove all the gnome3-team stuff, but rolling back to gnome2 has the potential for all sorts of breakage. I would seriously think of backing up your personal data and re-installing, but wait to see what others say.

**EDIT** Sorry, I was being a bit negative there. I think I did come across a thread where someone successfully uninstalled gnome3 and reverted to Unity - I'll see if I can find it. Perhaps not for a little while. I need to log off soon.

---

### Post by soylentcola on 2011-05-31
Oh no, I actually got an error when I logged in about some sort of hardware and having to be put into fallback mode, the screen when I login IS blue, but it's not striped, my desktop is just a plain purple.

---

### Post by coffeecat on 2011-05-31
OK, I follow you. Yes, "Fallback" mode is a gnome3 feature for when you have unsupported graphics hardware, so we're back to the video issue. However, your video chip is perfectly adequate for both Unity and gnome3-shell.

Since you didn't intend to install gnome3 but have it anyway, I think that's where the problem lies. I'll pm someone who has used gnome3 more than myself and ask him to have a look at this thread. I'm sure he'll have something constructive to add. He's offline at the moment, so you may have to wait a bit. And/or perhaps wildmanne39 will suggest something.

---

### Post by Quackers on 2011-05-31
I believe some have purged the gnome3 team ppa with the commands below. I would also make you aware that if it doesn't work properly you may be left with a broken system and need to re-install. But you're already at that point, it seems, so may be worth a try.
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
```
You may then need to manually downgrade gnome-settings-daemon in aptitude or synaptic 
and you may then need to run ```
sudo apt-get install -f
``` to downgrade other packages.

This was discussed in the Natty Testing thread (pages 7 & 8, amongst others)
[http://ubuntuforums.org/showthread.php?t=1722627&highlight=gnome-shell](http://ubuntuforums.org/showthread.php?t=1722627&highlight=gnome-shell)

If you then reboot you should hopefully be able to log in to "Ubuntu" which should be the unity desktop, or the Ubuntu Classic desktop.

---

### Post by wildmanne39 on 2011-05-31
> **soylentcola said:**
> Oh no, I actually got an error when I logged in about some sort of hardware and having to be put into fallback mode, the screen when I login IS blue, but it's not striped, my desktop is just a plain purple.
Hi, sorry I have been gone I tried to get a little sleep. Let us know if the commands quakers gave you get rid of gnome 3,and return your system to unity. The reason you did not see a gnome 3 option to log in they call it gnome shell or something close to that.

---

