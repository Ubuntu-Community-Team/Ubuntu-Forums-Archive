---
title: "partial upgrade?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by libihero on 2009-10-31
I know that in the beta form, u werent supposed to do a partial upgrade.
what about now with a clean install of the official release?

---

### Post by kansasnoob on 2009-10-31
Whenever I'm offered a partial upgrade I say no and close the update manager, then open synaptic and click on reload. 

When it's done click on mark all upgrades and then click apply. You'll be presented with a window listing everything that's going to be upgraded, installed, and/or removed.

Then I can parse the list and figure out if it's safe or not. If you'd c&p the list here we could probably help you figure it out.

---

### Post by lavinog on 2009-10-31
you shouldn't do a partial upgrade for the same reasons as in beta.

---

### Post by trulan on 2009-10-31
Partial upgrade means this:
A package/packages must be removed to install upgrades.  Sometimes this is necessary, sometimes it is dangerous.  Always, always, always, check what is going to be removed before proceeding.

The release version shouldn't offer partial upgrades, at least not very often at all.  If it offers one, don't turn away and do nothing.  Always, always, always, check what it wants to remove.  Investigate carefully before proceeding.

---

### Post by lavinog on 2009-10-31
> **trulan said:**
> 
The release version shouldn't offer partial upgrades, at least not very often at all.  If it offers one, don't turn away and do nothing.  Always, always, always, check what it wants to remove.  Investigate carefully before proceeding.

Partial upgrades can happen with the release.  It depends on the timing.  Sometimes there is a delay in adding a dependency to the repos.

---

### Post by slakkie on 2009-10-31
Hi,

to determine wheter or not you want to do the partial upgrade you need to know what Ubuntu will remove and add.

```
aptitude -s full-upgrade
```

This will simulate the action and it will tell which packages will be removed and which will be added. If you post the output of this command we can help you to determine what you need to do.

You also might want to have a look here:
[http://ubuntuforums.org/showthread.php?t=1286309](http://ubuntuforums.org/showthread.php?t=1286309)

---

### Post by libihero on 2009-10-31
how do i copy n paste the list?

---

### Post by NCLI on 2009-10-31
Mark it with the mouse, right-click, choose "Copy"?

---

### Post by kansasnoob on 2009-10-31
> **libihero said:**
> how do i copy n paste the list?

Oh, from synaptic you have to click on "show details" before you can copy.

---

### Post by libihero on 2009-10-31
i can't find the "show details"

---

### Post by kansasnoob on 2009-10-31
Look where my pointer is in the screenshot:

[ATTACH]133999[/ATTACH]

The text inside the window can be copied after you click on that, it just toggles from View details to Hide details.

---

### Post by zaivala on 2009-10-31
I attempted to do a full upgrade.  What I got was a partial upgrade.  xulrunner never installed, leaving me with a partial upgrade, and told me that I was not getting an official version of Ubuntu -- which is odd, as I was using Ubuntu's Update Manager to upgrade...

when I did a second update, it fixed the xulrunner  mis-installation... however, I now have no sound, and have a red-circle-with-slash icon instead of Firefox... but other than sound, it's working.

---

### Post by libihero on 2009-11-01
here's what its asking for me:

```
acpi-support will be removed

acpid will be removed

alsa-base will be removed

alsa-utils will be removed

apparmor will be removed

apparmor-utils will be removed

apport will be removed

apport-gtk will be removed

at will be removed

avahi-daemon will be removed

bluetooth will be removed

bluez will be removed

bluez-cups will be removed

bluez-utils will be removed

brltty will be removed

brltty-x11 will be removed

checkbox will be removed

checkbox-gtk will be removed

console-setup will be removed

couchdb-bin will be removed

cron will be removed

cups will be removed

cups-driver-gutenprint will be removed

desktopcouch will be removed

dmraid will be removed

dmsetup will be removed

erlang-base will be removed

erlang-crypto will be removed

erlang-inets will be removed

erlang-mnesia will be removed
erlang-public-key will be removed

erlang-runtime-tools will be removed

erlang-ssl will be removed

erlang-syntax-tools will be removed

erlang-xmerl will be removed

evolution-couchdb will be removed

foo2zjs will be removed

foomatic-db will be removed

foomatic-db-engine will be removed

friendly-recovery will be removed

ftp will be removed

fuse-utils will be removed

gdm will be removed

gdm-guest-session will be removed

ghostscript-cups will be removed

gnome-bluetooth will be removed

gnome-do will be removed

gnome-do-docklets will be removed

gnome-do-plugins will be removed

gnome-system-tools will be removed

gparted will be removed

gvfs-fuse will be removed

hal will be removed

hpijs will be removed

hplip will be removed

ifupdown will be removed

indicator-applet-session will be removed

indicator-session will be removed

initramfs-tools will be removed

kbd will be removed

kpartx will be removed

lftp will be removed

libcanberra-pulse will be removed

libnet-dbus-perl will be removed

libnss-mdns will be removed
liboobs-1-4 will be removed

librpc-xml-perl will be removed

libwww-perl will be removed

libxml-parser-perl will be removed

libxml-twig-perl will be removed

libxml-xpath-perl will be removed

linux-generic will be removed

linux-image-2.6.31-14-generic will be removed

linux-image-generic will be removed

linux-sound-base will be removed

media-player-info will be removed

module-init-tools will be removed

moovida will be removed

moovida-plugins-bad will be removed

moovida-plugins-good will be removed

moovida-plugins-ugly will be removed

netbase will be removed

network-manager will be removed

network-manager-gnome will be removed

ntfs-3g will be removed

ntpdate will be removed

openoffice.org-emailmerge will be removed

openprinting-ppds will be removed

pcmciautils will be removed

pm-utils will be removed

powermgmt-base will be removed

ppp will be removed

pppconfig will be removed

pppoeconf will be removed

procps will be removed

pulseaudio will be removed

pulseaudio-esound-compat will be removed

pulseaudio-module-bluetooth will be removed

pulseaudio-module-gconf will be removed

pulseaudio-module-udev will be removed

pulseaudio-module-x11 will be removed

pxljr will be removed
python-desktopcouch will be removed

python-desktopcouch-records will be removed

rhythmbox will be removed

rsyslog will be removed

splix will be removed

sreadahead will be removed

system-tools-backends will be removed

telepathy-salut will be removed

telnet will be removed

ubuntu-desktop will be removed

ubuntu-minimal will be removed

ubuntu-standard will be removed

udev will be removed

ufw will be removed

usplash will be removed

usplash-theme-sabily will be removed

usplash-theme-taibah will be removed

usplash-theme-ubuntu will be removed

usplash-theme-ubuntume will be removed

wine will be removed

wireless-crda will be removed

xorg will be removed

xserver-xorg will be removed

xserver-xorg-core will be removed

xserver-xorg-input-all will be removed

xserver-xorg-input-evdev will be removed

xserver-xorg-input-mouse will be removed

xserver-xorg-input-synaptics will be removed

xserver-xorg-input-vmmouse will be removed

xserver-xorg-input-wacom will be removed

xserver-xorg-video-all will be removed

xserver-xorg-video-apm will be removed

xserver-xorg-video-ark will be removed

xserver-xorg-video-ati will be removed

xserver-xorg-video-chips will be removed

xserver-xorg-video-cirrus will be removed

xserver-xorg-video-fbdev will be removed

xserver-xorg-video-geode will be removed

xserver-xorg-video-i128 will be removed

xserver-xorg-video-i740 will be removed

xserver-xorg-video-intel will be removed

xserver-xorg-video-mach64 will be removed

xserver-xorg-video-mga will be removed

xserver-xorg-video-neomagic will be removed

xserver-xorg-video-nv will be removed

xserver-xorg-video-openchrome will be removed

xserver-xorg-video-r128 will be removed

xserver-xorg-video-radeon will be removed

xserver-xorg-video-rendition will be removed

xserver-xorg-video-s3 will be removed

xserver-xorg-video-s3virge will be removed

xserver-xorg-video-savage will be removed

xserver-xorg-video-siliconmotion will be removed

xserver-xorg-video-sis will be removed

xserver-xorg-video-sisusb will be removed

xserver-xorg-video-tdfx will be removed

xserver-xorg-video-trident will be removed

xserver-xorg-video-tseng will be removed

xserver-xorg-video-v4l will be removed

xserver-xorg-video-vesa will be removed

xserver-xorg-video-vmware will be removed

xserver-xorg-video-voodoo will be removed

```

---

### Post by zaivala on 2009-11-01
I think I panicked about the sound, as I have had that problem in prior upgrades... but in this case, the problem was caused by a short circuit between the chair and the keyboard (i.e., I hadn't turned my speakers on).

The Firefox Icon Issue was solved by removing the icon from the launcher and then re-adding it from the menu.

So I'm good.  Just wasn't a seamless upgrade, with the mess of not getting xulrunner to load the first time.

---

### Post by libihero on 2009-11-03
bump...

---

### Post by lavinog on 2009-11-03
update the repository
filter the list by status (lower left part of synaptic)
then click on upgradable.
for each item listed, mark install.  You should get a dialog for some of them that a dependancy requires installing/upgrading another package. Continue to upgrade those packages.
Some packages will give you a message that they will remove a bunch of packages...don't install/upgrade those...instead post what package is causing this.

---

### Post by libihero on 2009-11-03
i dont see where it says "upgradable"

---

### Post by pistos on 2009-11-03
I hope this is not considered hijacking the thread, but I have the same problem, where it is offering me a partial upgrade. I have followed the instructions given by lavinog above, and these are the packages that want to remove other packages in order to proceed:

libmlt1

To be removed:
  libsox1
To be installed:
  libsox1a
To be upgraded:
  libsox-fmt-alsa
  libsoxpfmt-base

---

### Post by lavinog on 2009-11-03
> **pistos said:**
> I hope this is not considered hijacking the thread, but I have the same problem, where it is offering me a partial upgrade. I have followed the instructions given by lavinog above, and these are the packages that want to remove other packages in order to proceed:

libmlt1

To be removed:
  libsox1
To be installed:
  libsox1a
To be upgraded:
  libsox-fmt-alsa
  libsoxpfmt-base
it looks like libsox1a is replacing libsox1.  I would go ahead and do it.

---

### Post by lavinog on 2009-11-03
> **libihero said:**
> i dont see where it says "upgradable"

[img]http://ubuntuforums.org/attachment.php?attachmentid=134623&stc=1&d=1257311399[/img]

---

### Post by libihero on 2009-11-04
ya it doesnt show.  i chose mark all upgrades and clicked on status and this is what i have.

---

### Post by lavinog on 2009-11-04
That might be because you already marked all upgrades.
exit and restart synaptic, click reload, then status and see if it is there.

you could also try the custom filter button and see if there is an upgradable section listed there too.

---

