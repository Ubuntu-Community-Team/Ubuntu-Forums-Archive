---
title: "dependency problems - leaving unconfigured"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by ejlal on 2009-06-29
newbie says: hey guys!!
newbie says: just the other day update manager showed that 272 updates are available (i wasnt getting any for quite long time)i thought it will be (a BETTER !!) idea to install those updates using synpatic ,so i went to  installed and upgradeable i marked all upgrades ,so after the installing done i got this  message:
An error occured
The following details are provided:
E: libpng12-0: subprocess post-installation script killed by signal (Interrupt)
E: libcupsimage2: dependency problems - leaving unconfigured
E: cupsys: dependency problems - leaving unconfigured
E: hplip: dependency problems - leaving unconfigured
E: libgtk2.0-0: dependency problems - leaving unconfigured
E: gtk2-engines-pixbuf: dependency problems - leaving unconfigured
E: liblaunchpad-integration1: dependency problems - leaving unconfigured
E: yelp: dependency problems - leaving unconfigured
E: ubuntu-docs: dependency problems - leaving unconfigured
E: openjdk-6-jre: dependency problems - leaving unconfigured
E: gksu: dependency problems - leaving unconfigured
E: apturl: dependency problems - leaving unconfigured
E: gstreamer0.10-plugins-good: dependency problems - leaving unconfigured
E: cheese: dependency problems - leaving unconfigured
E: cupsys-client: dependency problems - leaving unconfigured
E: cupsys-bsd: dependency problems - leaving unconfigured
E: libnautilus-extension1: dependency problems - leaving unconfigured
E: evince: dependency problems - leaving unconfigured
E: libedataserverui1.2-8: dependency problems - leaving unconfigured
E: libexchange-storage1.2-3: dependency problems - leaving unconfigured
E: liblpint-bonobo0: dependency problems - leaving unconfigured
E: evolution: dependency problems - leaving unconfigured
E: evolution-plugins: dependency problems - leaving unconfigured
E: f-spot: dependency problems - leaving unconfigured
E: gnome-power-manager: dependency problems - leaving unconfigured
E: gnome-session: dependency problems - leaving unconfigured
E: libmetacity0: dependency problems - leaving unconfigured
E: metacity: dependency problems - leaving unconfigured
E: gdm: dependency problems - leaving unconfigured
E: gedit: dependency problems - leaving unconfigured
E: libgnome-window-settings1: dependency problems - leaving unconfigured
E: gnome-control-center: dependency problems - leaving unconfigured
E: gnome-games: dependency problems - leaving unconfigured
E: mplayer: dependency problems - leaving unconfigured
E: gnome-media: dependency problems - leaving unconfigured
E: gnome-system-tools: dependency problems - leaving unconfigured
E: gnome-utils: dependency problems - leaving unconfigured
E: go-home-applet: dependency problems - leaving unconfigured
E: hpijs: dependency problems - leaving unconfigured
E: libclutter-0.8-0: dependency problems - leaving unconfigured
E: libclutter-gtk-0.8-0: dependency problems - leaving unconfigured
E: libgnome-window-settings-dev: dependency problems - leaving unconfigured
E: libgtk2.0-bin: dependency problems - leaving unconfigured
E: network-manager-gnome: dependency problems - leaving unconfigured
E: nautilus: dependency problems - leaving unconfigured
E: nautilus-sendto: dependency problems - leaving unconfigured
E: nautilus-share: dependency problems - leaving unconfigured
E: netbook-launcher: dependency problems - leaving unconfigured
E: ume-launcher: dependency problems - leaving unconfigured
E: python-gtkhtml2: dependency problems - leaving unconfigured
E: python-launchpad-integration: dependency problems - leaving unconfigured

then i noticed that my programs are no longer restore/minimize to the bottom panel, instead they disappear and i have to use alt-tab to switch between open windows, i tried to delete the panel and added newer one but noting changed i tried to change the  desktop mode but those r mess the ubuntu netbook desktop  have upper and lower panels!! beside some of my upper panel's icons are missed.
my question is: how to fix those errors ????? 
PS:at installing stage i remember there was a pop up message about upgrading/updating the kernel,i was too tired to google it(what's kernel?), so i chose to leave it as installed or some thing,i guess!!

---

### Post by Shazaam on 2009-06-29
Try these in terminal (Applications>Accessories>Terminal)...
```
sudo dpkg --configure -a
```
and...
```
sudo apt-get install -f
```
kernel...
[http://www.ibm.com/developerworks/linux/library/l-linux-kernel/](http://www.ibm.com/developerworks/linux/library/l-linux-kernel/)

---

### Post by ejlal on 2009-06-29
ejlal@TOSHIBA:~$ sudo dpkg --configure -a
[sudo] password for ejlal: 
ejlal@TOSHIBA:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclutter-0.6-0 libsnack2 dhcdbd tcltls tcl tcl8.4 tcl8.5 tk8.5 libisc32
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by theozzlives on 2009-06-30
To add stuff back to your panels, right click on the panel and select "add to panel". The one on the bottom is called "Window List". To get rid of libclutter-0.6-0 libsnack2 dhcdbd tcltls tcl tcl8.4 tcl8.5 tk8.5 libisc32, type in a terminal:```
sudo apt-get autoremove
``` Post the output of```
cat /etc/apt/sources.list
```

---

### Post by ejlal on 2009-06-30
# deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
# deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

# deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
# deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

# deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
# deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

# deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
# deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

# deb [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix main universe multiverse restricted
# deb-src [http://netbook-remix.archive.canonical.com/ubuntu/](http://netbook-remix.archive.canonical.com/ubuntu/) hardy-netbook-remix main universe multiverse restricted

deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) hardy main

---

