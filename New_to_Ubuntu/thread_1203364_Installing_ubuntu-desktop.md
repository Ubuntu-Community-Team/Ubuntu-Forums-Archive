---
title: "Installing ubuntu-desktop"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by Falcon9x5 on 2009-07-03
Hi guys.

So I just got my hands on a dedicated server with Ubuntu 9.04. While I'm fairly ok with a GUI, I started off with ssh access _only_ (it's a totally fresh install).
I've managed to install a vnc server, but when I connect to it, it just has a black & white screen with some options about the clipboard in the top left. I'm fairly sure this is due to lack of a window manager.

Anyway, I've tried to install ubuntu-desktop via

```
sudo apt-get install ubuntu-desktop
```
Which then gives this:
```
root@dead:~# apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  ubuntu-desktop: Depends: alacarte but it is not going to be installed
                  Depends: cups but it is not going to be installed
                  Depends: cups-driver-gutenprint but it is not going to be installed
                  Depends: fast-user-switch-applet but it is not going to be installed
                  Depends: gdebi but it is not going to be installed
                  Depends: gedit but it is not going to be installed
                  Depends: gnome-about but it is not going to be installed
                  Depends: gnome-app-install but it is not going to be installed
                  Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-media but it is not going to be installed
                  Depends: gnome-menus but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: gstreamer0.10-pulseaudio but it is not going to be installed
                  Depends: hwtest-gtk but it is not going to be installed
                  Depends: language-selector but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: nautilus-cd-burner but it is not going to be installed
                  Depends: software-properties-gtk but it is not going to be installed
                  Depends: synaptic but it is not going to be installed
                  Depends: system-config-printer-gnome but it is not going to be installed
                  Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Depends: yelp but it is not going to be installed
                  Recommends: apport-gtk but it is not going to be installed
                  Recommends: bluez-cups but it is not going to be installed
                  Recommends: deskbar-applet but it is not going to be installed
                  Recommends: firefox
                  Recommends: firefox-gnome-support but it is not going to be installed
                  Recommends: foomatic-db-hpijs but it is not going to be installed
                  Recommends: gcc but it is not going to be installed
                  Recommends: gimp but it is not going to be installed
                  Recommends: gnome-games but it is not going to be installed
                  Recommends: gnome-orca but it is not going to be installed
                  Recommends: gnome-user-guide but it is not going to be installed
                  Recommends: hal-cups-utils but it is not going to be installed
                  Recommends: hplip but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
                  Recommends: libdeskbar-tracker but it is not going to be installed
                  Recommends: nautilus-share but it is not going to be installed
                  Recommends: onboard but it is not going to be installed
                  Recommends: pidgin but it is not going to be installed
                  Recommends: pidgin-otr but it is not going to be installed
                  Recommends: rhythmbox but it is not going to be installed
                  Recommends: totem but it is not going to be installed
                  Recommends: totem-mozilla but it is not going to be installed
                  Recommends: tracker but it is not going to be installed
                  Recommends: tracker-search-tool but it is not going to be installed
                  Recommends: ubufox but it is not going to be installed
                  Recommends: ubuntu-docs but it is not going to be installed
                  Recommends: usb-creator but it is not going to be installed
E: Broken packages
```

No idea why apt-get doesn't just install the dependancies. I've tried

```
apt-get -f install
```
and
```
apt-get clean
```
and
```
apt-get update
```
but nothing helps.

Any ideas?

---

### Post by halitech on 2009-07-03
have you considered that since its a dedicated server that the company  you got it from doesn't want a gui installed? Typically servers run without a gui as they are headless and sitting in a rack. Maybe contact them and ask if its possible or not.

---

### Post by Falcon9x5 on 2009-07-03
Hmm, fair point, didn't consider that! I'll give them a shout. Thanks! :)

---

### Post by modprobe on 2009-07-03
Wait!
 
run the following:
 
sudo tasksel
 
Then scroll down the list of options and one of them should be ubuntu-desktop or whichever other desktop environment you'd like.
 
Hope I got to you before you made that phone call.
 
:guitar:

---

### Post by liamnixon on 2009-07-03
If nothing else, you can try the [minimal image]("https://help.ubuntu.com/community/Installation/MinimalCD"), but modprobe's solution should work.

---

### Post by Falcon9x5 on 2009-07-03
Had a play around with it for a while, turns out the hosting company had edited the sources.list file, adding their own servers instead of the official ubuntu ones. Replaced the sources.list with a fresh one, did an

```
apt-get dist-upgrade
```

then ran the command again

```
apt-get install ubuntu-desktop
```

and she's installing away fine now!

Thanks for the help anyway :)

---

### Post by Falcon9x5 on 2009-07-03
Hmm, it seems to have encountered a problem with ACPI... Don't really know what's up with this:

```
root@dead:~# apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.6-9ubuntu4.9.04.3) ...
 * Starting ACPI services...
acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 acpid
 acpi-support
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I ran clean, -f install and autoremove, nothing seem to help.

Thoughts?

---

### Post by halitech on 2009-07-03
I had a feeling it was something to do with the hosting company :)

Chances are they did it for a reason and they won't give you a hard time for changing them and installing a gui on their server.

---

### Post by Falcon9x5 on 2009-07-03
Yeah, I think they were just marketing it as a barebones OS version, rather than actively trying to discourage GUI  installation.

Any thoughts on the ACPI problem above?

---

### Post by Falcon9x5 on 2009-07-03
Just a quick update on this - my /proc/acpi/ directory seems to be pretty bare for some reason

```
root@dead:/proc/acpi# ls
embedded_controller  power_resource  processor  thermal_zone
```

It seems to be happy to "stop" the ACPI service, but not restart (hence I assume it's not running the first place):

```
root@dead:/proc/acpi# /etc/init.d/acpid stop
 * Stopping ACPI services...
   ...done.
root@dead:/proc/acpi# /etc/init.d/acpid start
 * Starting ACPI services...
acpid: can't open /proc/acpi/event: No such file or directory
```

---

