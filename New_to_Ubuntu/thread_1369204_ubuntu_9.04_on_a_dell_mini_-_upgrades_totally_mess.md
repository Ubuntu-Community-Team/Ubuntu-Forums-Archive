---
title: "ubuntu 9.04 on a dell mini - upgrades totally messed it up"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by elvira.deeyto on 2009-12-31
Hi all, i am total beginner at this - i have a little dell mini which was working great for the last couple of momnths with 9.04. I have been ignoring all the upgrade notifications for a while, but decided to do them all in one go a couple fo days ago. Now, the touchpad isnt working, nor the wireless, and goodness knows what else 
 
So obviously i dont know where to start - shoudl i reload 9.04 and if so can i do this from an external hard drive (no cd rom) or should i try and rememdy some of the upgrades
 
Any pointers would be most welcome
 
Thanks

---

### Post by iponeverything on 2009-12-31
Choose an earlier kernel from the boot menu.

---

### Post by elvira.deeyto on 2009-12-31
thanks for the quick reply - no good though. there is only one other kernel to chose and it has exactly the same problems  :(

---

### Post by iponeverything on 2009-12-31
Was it just updates applied to 9.04 or did you go from
9.04 -> 9.10?

Can you upload or paste in the contents of latest logfile in:

/root/.synaptic/log/

---

### Post by nickpaton on 2009-12-31
> **iponeverything said:**
> Was it just updates applied to 9.04 or did you go from
9.04 -> 9.10?

Can you upload or paste in the contents of latest logfile in:

/root/.synaptic/log/

I didn't know this command and tried to run it (in 8.10) to see what I had with no results.

I then did a search through the file tree and was excluded from that directory

I then did a search via nautilus and my folder only contained a link to the Desktop.

Is there another way to look at this log?

---

### Post by iponeverything on 2010-01-01
happy new year!

to the file open a terminal and type:

```
sudo nautilus
```

What was installed with during the update is in the log, we can take a look at it and maybe see the problem package that should be reverted.

---

### Post by nickpaton on 2010-01-01
My bad - you also need to "show hidden files" and it's all there!

---

### Post by elvira.deeyto on 2010-01-01
Back again, i have just realised that i did unintentionally upgrade from 9.04 to 9.10 (but only partially- i keep getting partial upgrade notices). As i cant now get the wifi working, there is not much I can do about it. I include here the alst logfile though as iponeverything suggested (its very long though).
 
 
I dont particulalry want to run 9.10 so if there someway of just reverting to 9.04 that would be great 
 
 
Thanks a lot
 
 
 
Commit Log for Wed Dec 30 16:48:20 2009
&#12288;
Removed the following packages:
fast-user-switch-applet
startup-tasks
system-services
ubuntu-minimal
upstart-compat-sysv
upstart-logd
Upgraded the following packages:
acpi-support (0.121) to 0.129
adduser (3.110ubuntu5) to 3.110ubuntu7
alacarte (0.11.10-0ubuntu1) to 0.12.4-0ubuntu2
alsa-base (1.0.18.dfsg-1ubuntu to 1.0.20+dfsg-1ubuntu5
alsa-utils (1.0.18-1ubuntu11) to 1.0.20-2ubuntu6
apmd (3.2.2-12ubuntu3) to 3.2.2-13
app-install-data (0.7.6.1) to 0.9.10.11
app-install-data-commercial (11.9.04.4) to 12.9.10.2
apparmor (2.3+1289-0ubuntu14) to 2.3.1+1403-0ubuntu27.3
apparmor-utils (2.3+1289-0ubuntu14) to 2.3.1+1403-0ubuntu27.3
apport-gtk (1.0-0ubuntu5.4) to 1.9.3-0ubuntu4.2
aspell (0.60.6-1) to 0.60.6-2
aspell-en (6.0-0-5.1) to 6.0-0-5.1ubuntu3
at-spi (1.26.0-0ubuntu2) to 1.28.1-0ubuntu1
avahi-autoipd (0.6.23-4ubuntu4) to 0.6.25-1ubuntu5.1
avahi-utils (0.6.23-4ubuntu4) to 0.6.25-1ubuntu5.1
base-files (5ubuntu4) to 5.0.0ubuntu7
bash (3.2-5ubuntu1) to 4.0-5ubuntu2
bash-completion (20080705ubuntu3) to 1:1.0-3ubuntu2
binfmt-support (1.2.11) to 1.2.14
binutils (2.19.1-0ubuntu3) to 2.20-0ubuntu2
binutils-static (2.19.1-0ubuntu3) to 2.20-0ubuntu2
bluetooth (4.32-0ubuntu4.1) to 4.51-0ubuntu2
bluez (4.32-0ubuntu4.1) to 4.51-0ubuntu2
bluez-alsa (4.32-0ubuntu4.1) to 4.51-0ubuntu2
bluez-cups (4.32-0ubuntu4.1) to 4.51-0ubuntu2
bluez-gstreamer (4.32-0ubuntu4.1) to 4.51-0ubuntu2
bluez-utils (4.32-0ubuntu4.1) to 4.51-0ubuntu2
bogofilter (1.1.7-1ubuntu1) to 1.2.0-3ubuntu1
bogofilter-bdb (1.1.7-1ubuntu1) to 1.2.0-3ubuntu1
bogofilter-common (1.1.7-1ubuntu1) to 1.2.0-3ubuntu1
bsdmainutils (6.1.10ubuntu3) to 6.1.10ubuntu4
bsdutils (1:2.14.2-1ubuntu4) to 1:2.16-1ubuntu5
busybox-initramfs (1:1.10.2-2ubuntu7) to 1:1.13.3-1ubuntu7
bzip2 (1.0.5-1ubuntu1) to 1.0.5-3
ca-certificates (20080809) to 20090814
checkbox (0.7.2) to 0.8.6
checkbox-gtk (0.7.2) to 0.8.6
cli-common (0.6.0) to 0.7
command-not-found (0.2.34ubuntu3) to 0.2.38ubuntu4
command-not-found-data (0.2.34ubuntu3) to 0.2.38ubuntu4
compiz-wrapper (1:0.8.2-0ubuntu8.1) to 1:0.8.4-0ubuntu2
console-setup (1.28ubuntu to 1.34ubuntu4
console-terminus (4.26-2.1) to 4.28-1
consolekit (0.3.0-2ubuntu4) to 0.3.1-0ubuntu2
coreutils (6.10-6ubuntu1) to 7.4-2ubuntu1
cpio (2.9-15ubuntu1) to 2.10-1ubuntu1
cups-common (1.3.9-17ubuntu3.2) to 1.4.1-5ubuntu2.1
dash (0.5.4-12ubuntu2) to 0.5.5.1-2ubuntu3
dbus (1.2.12-0ubuntu2.1) to 1.2.16-0ubuntu9
dbus-x11 (1.2.12-0ubuntu2.1) to 1.2.16-0ubuntu9
dc (1.06.94-3ubuntu1) to 1.06.94-3.1ubuntu2
debconf (1.5.26ubuntu3) to 1.5.27ubuntu2
debconf-i18n (1.5.26ubuntu3) to 1.5.27ubuntu2
desktop-file-utils (0.15-1ubuntu7) to 0.15-2ubuntu1
dhcp3-client (3.1.1-5ubuntu8.1) to 3.1.2-1ubuntu7
dhcp3-common (3.1.1-5ubuntu8.1) to 3.1.2-1ubuntu7
dictionaries-common (1.0.0ubuntu1) to 1.2.1ubuntu1
diff (2.8.1-12ubuntu1) to 2.8.1-13
dmidecode (2.9-1ubuntu1) to 2.9-1ubuntu2
dmsetup (2:1.02.27-4ubuntu5) to 2:1.02.27-4ubuntu7
dnsmasq-base (2.47-3ubuntu0.1) to 2.50-1
doc-base (0.8.20) to 0.9.3
dosfstools (3.0.1-1) to 3.0.3-1
dpkg (1.14.24ubuntu1) to 1.15.4ubuntu2
e2fslibs (1.41.4-1ubuntu1) to 1.41.9-1ubuntu3
e2fsprogs (1.41.4-1ubuntu1) to 1.41.9-1ubuntu3
ed (0.7-3ubuntu1) to 1.4-1
eject (2.1.5+deb1+cvs20081104-5) to 2.1.5+deb1+cvs20081104-6
esound-clients (0.2.40-0ubuntu3) to 0.2.41-5
esound-common (0.2.40-0ubuntu3) to 0.2.41-5
espeak (1.40.02-0ubuntu1) to 1.41.01-0ubuntu1
espeak-data (1.40.02-0ubuntu1) to 1.41.01-0ubuntu1
ethtool (6+20080913-1) to 6+20090307-1
evolution-documentation-en (2.26.1-0ubuntu2) to 2.28.1-0ubuntu2
example-content (36) to 38
fglrx-modaliases (2:8.600-0ubuntu2) to 2:8.660-0ubuntu4
file (4.26-2ubuntu4) to 5.03-1ubuntu1
file-roller (2.26.1-0ubuntu1) to 2.28.1-0ubuntu1
findutils (4.4.0-2ubuntu4) to 4.4.2-1
finger (0.17-12) to 0.17-13
foo2zjs (20090217-0ubuntu4) to 20090623-0ubuntu5
foomatic-db-engine (4.0.0-0ubuntu6.1) to 4.0.3-0ubuntu2
foomatic-filters (4.0.0-0ubuntu9) to 4.0.3-0ubuntu2
friendly-recovery (0.2.8.1) to 0.2.8.2
fuse-utils (2.7.4-1.1ubuntu4) to 2.7.4-1.1ubuntu4.1
gamin (0.1.9-2ubuntu4) to 0.1.10-1ubuntu2
gconf2 (2.26.0-0ubuntu1) to 2.28.0-0ubuntu2
gconf2-common (2.26.0-0ubuntu1) to 2.28.0-0ubuntu2
gdebi (0.4.9) to 0.5.9
gdebi-core (0.4.9) to 0.5.9
gdm (2.20.10-0ubuntu2) to 2.28.1-0ubuntu2.1
genisoimage (9:1.1.9-1ubuntu1) to 9:1.1.9-1ubuntu2
gettext-base (0.17-6ubuntu2) to 0.17-8ubuntu2
ghostscript-x (8.64.dfsg.1-0ubuntu to 8.70.dfsg.1-0ubuntu3
gimp-help-common (2.4.1-1) to 2.4.1-2
gimp-help-en (2.4.1-1) to 2.4.1-2
gnome-about (1:2.26.1-0ubuntu2) to 1:2.28.1-0ubuntu3
gnome-accessibility-themes (2.26.0-0ubuntu1) to 2.28.1-0ubuntu1
gnome-app-install (0.5.24-0ubuntu1.1) to 0.5.60.1ubuntu2
gnome-desktop-data (1:2.26.1-0ubuntu2) to 1:2.28.1-0ubuntu3
gnome-doc-utils (0.16.0-0ubuntu1) to 0.18.0-0ubuntu1
gnome-icon-theme (2.26.0-0ubuntu1) to 2.28.0-0ubuntu1
gnome-keyring (2.26.1-0ubuntu1) to 2.28.1-0ubuntu1
gnome-menus (2.26.0-0ubuntu1) to 2.28.0.1-0ubuntu1
gnome-mount (0.8-1ubuntu5) to 0.8-2ubuntu1
gnome-nettool (2.26.1-0ubuntu1) to 2.28.0-0ubuntu1
gnome-pilot (2.0.17-0ubuntu1) to 2.0.17-0ubuntu2
gnome-session (2.26.0svn20090408-0ubuntu2) to 2.28.0-0ubuntu5
gnome-themes (2.26.0-0ubuntu1) to 2.28.1-0ubuntu1
gnome-themes-selected (2.26.0-0ubuntu1) to 2.28.1-0ubuntu1
gnome-user-guide (2.26.0+svn20090323ubuntu5) to 2.28.0+git20090921ubuntu2
gnome-user-guide-en (2.26.0+svn20090323ubuntu5) to 2.28.0+git20090921ubuntu2
grep (2.5.3~dfsg-6ubuntu1) to 2.5.4-4
groff-base (1.18.1.1-22build1) to 1.20.1-5
grub-common (1.96+20080724-12ubuntu2) to 1.97~beta4-1ubuntu4.1
gsfonts (1:8.11+urwcyr1.0.7~pre44-3) to 1:8.11+urwcyr1.0.7~pre44-4
gstreamer0.10-ffmpeg (0.10.6.2-1ubuntu2) to 0.10.9-1
gstreamer0.10-plugins-base-apps (0.10.22-5) to 0.10.25-2ubuntu1.2
gtk2-engines (1:2.18.1-0ubuntu1) to 1:2.18.4-1ubuntu2
gtk2-engines-murrine (0.90.3-1ubuntu1) to 0.90.3-1ubuntu2
gtk2-engines-pixbuf (2.16.1-0ubuntu2) to 2.18.3-1ubuntu2.1
gucharmap (1:2.26.1-0ubuntu1) to 1:2.28.0-0ubuntu1
gzip (1.3.12-6ubuntu2) to 1.3.12-8ubuntu1
hal (0.5.12~rc1+git20090403-0ubuntu4) to 0.5.13-1ubuntu8
hal-info (20090407-0ubuntu1) to 20090716-0ubuntu1
hdparm (8.9-3ubuntu3) to 9.15-1ubuntu4
hicolor-icon-theme (0.10-1ubuntu1) to 0.10-2
human-icon-theme (0.33.6ubuntu2) to 0.35
human-netbook-theme (0.15-0ubuntu1) to 0.15-0ubuntu2
hunspell-en-us (20070829-2ubuntu1) to 20070829-2ubuntu4
hwtest-gtk (0.7.2) to 0.8.6
indicator-applet (0.1.6-0ubuntu1) to 0.2.0-0ubuntu2
initramfs-tools (0.92bubuntu29) to 0.92bubuntu53
inputattach (1.23-0ubuntu2) to 1.23-0ubuntu3
iproute (20080725-2) to 20090324-1
iptables (1.4.1.1-4ubuntu3) to 1.4.4-1ubuntu1
iputils-arping (3:20071127-1) to 3:20071127-1build1
iputils-ping (3:20071127-1) to 3:20071127-1build1
iputils-tracepath (3:20071127-1) to 3:20071127-1build1
iso-codes (3.6-1) to 3.10.2-1
kbd (1.14.1-4ubuntu4) to 1.15-1ubuntu1
klibc-utils (1.5.14-1~exp1ubuntu2) to 1.5.15-1ubuntu2
klogd (1.5-5ubuntu3) to 1.5-5ubuntu4
language-pack-en (1:9.04+20090803.2) to 1:9.10+20091022
language-pack-en-base (1:9.04+20090413) to 1:9.10+20091022
language-pack-gnome-en (1:9.04+20090803.2) to 1:9.10+20091022
language-pack-gnome-en-base (1:9.04+20090413) to 1:9.10+20091022
language-selector (0.4.2.3) to 0.4.18
language-selector-common (0.4.2.3) to 0.4.18
language-support-en (1:8.10+20080703) to 1:9.10+20090909
language-support-writing-en (1:8.10+20080904) to 1:9.10+20090909
laptop-mode-tools (1.47-1ubuntu1) to 1.47-1ubuntu2
launchpad-integration (0.1.24) to 0.1.26
less (418-1) to 429-2
libaa1 (1.4p5-37build1) to 1.4p5-38
libapm1 (3.2.2-12ubuntu3) to 3.2.2-13
libapparmor-perl (2.3+1289-0ubuntu14) to 2.3.1+1403-0ubuntu27.3
libapparmor1 (2.3+1289-0ubuntu14) to 2.3.1+1403-0ubuntu27.3
libarchive1 (2.4.17-2) to 2.6.2-1
libasound2 (1.0.18-1ubuntu9) to 1.0.20-3ubuntu6
libasound2-plugins (1.0.18-1ubuntu4) to 1.0.20-1ubuntu8
libaspell15 (0.60.6-1) to 0.60.6-2
libatk1.0-0 (1.26.0-0ubuntu2) to 1.28.0-0ubuntu1
libatk1.0-data (1.26.0-0ubuntu2) to 1.28.0-0ubuntu1
libatspi1.0-0 (1.26.0-0ubuntu2) to 1.28.1-0ubuntu1
libattr1 (1:2.4.43-1) to 1:2.4.43-3
libaudio2 (1.9.1-5) to 1.9.2-1
libaudiofile0 (0.2.6-7ubuntu1) to 0.2.6-7ubuntu2
libavahi-client3 (0.6.23-4ubuntu4) to 0.6.25-1ubuntu5.1
libavahi-common-data (0.6.23-4ubuntu4) to 0.6.25-1ubuntu5.1
libavahi-common3 (0.6.23-4ubuntu4) to 0.6.25-1ubuntu5.1
libavahi-compat-libdnssd1 (0.6.23-4ubuntu4) to 0.6.25-1ubuntu5.1
libavahi-glib1 (0.6.23-4ubuntu4) to 0.6.25-1ubuntu5.1
libavcodec52 (3:0.svn20090303-1ubuntu6) to 4:0.5+svn20090706-2ubuntu2
libavformat52 (3:0.svn20090303-1ubuntu6) to 4:0.5+svn20090706-2ubuntu2
libavutil49 (3:0.svn20090303-1ubuntu6) to 4:0.5+svn20090706-2ubuntu2
libblkid1 (1.41.4-1ubuntu1) to 2.16-1ubuntu5
libbluetooth3 (4.32-0ubuntu4.1) to 4.51-0ubuntu2
libbonobo2-0 (2.24.1-1) to 2.24.2-1
libbonobo2-common (2.24.1-1) to 2.24.2-1
libbonoboui2-common (2.24.1-1ubuntu1) to 2.24.2-1ubuntu2
libbrlapi0.5 (4.0~svn4301-0ubuntu4) to 4.0-7ubuntu2
libbz2-1.0 (1.0.5-1ubuntu1) to 1.0.5-3
libc6 (2.9-4ubuntu6.1) to 2.10.1-0ubuntu15
libc6-dev (2.9-4ubuntu6.1) to 2.10.1-0ubuntu15
libc6-i686 (2.9-4ubuntu6.1) to 2.10.1-0ubuntu15
libcairo-perl (1.060-1) to 1.061-1
libcanberra-gtk-module (0.11-1ubuntu5) to 0.15-0ubuntu7
libcanberra-gtk0 (0.11-1ubuntu5) to 0.15-0ubuntu7
libcanberra0 (0.11-1ubuntu5) to 0.15-0ubuntu7
libcap2 (2.11-2) to 1:2.16-5ubuntu1
libck-connector0 (0.3.0-2ubuntu4) to 0.3.1-0ubuntu2
libcomerr2 (1.41.4-1ubuntu1) to 1.41.9-1ubuntu3
libcryptui0 (2.26.1-0ubuntu1) to 2.28.1-0ubuntu1
libcups2 (1.3.9-17ubuntu3.2) to 1.4.1-5ubuntu2.1
libcwidget3 (0.5.12-4ubuntu1) to 0.5.12-4ubuntu4
libdaemon0 (0.13-2) to 0.13-3
libdb4.6 (4.6.21-12) to 4.6.21-13ubuntu2
libdb4.7 (4.7.25-6ubuntu1) to 4.7.25-7ubuntu2
libdbus-1-3 (1.2.12-0ubuntu2.1) to 1.2.16-0ubuntu9
libdbus-glib-1-2 (0.80-3) to 0.80-4ubuntu1
libdecoration0 (1:0.8.2-0ubuntu8.1) to 1:0.8.4-0ubuntu2
libdevmapper1.02.1 (2:1.02.27-4ubuntu5) to 2:1.02.27-4ubuntu7
libdjvulibre-text (3.5.21-3ubuntu1) to 3.5.22-1ubuntu2
libdjvulibre21 (3.5.21-3ubuntu1) to 3.5.22-1ubuntu2
libdmx1 (1:1.0.2-3) to 1:1.0.2-3ubuntu1
libdrm-intel1 (2.4.5-0ubuntu4) to 2.4.14-1ubuntu1
libdrm2 (2.4.5-0ubuntu4) to 2.4.14-1ubuntu1
libdv4 (1.0.0-1ubuntu2) to 1.0.0-2ubuntu1
libelf1 (0.131-4) to 0.141-2ubuntu2
libenchant1c2a (1.4.2-3.3ubuntu1) to 1.5.0-0ubuntu3
libesd-alsa0 (0.2.40-0ubuntu3) to 0.2.41-5
libespeak1 (1.40.02-0ubuntu1) to 1.41.01-0ubuntu1
libevdocument1 (2.26.1-0ubuntu1) to 2.28.1-0ubuntu1.2
libevview1 (2.26.1-0ubuntu1) to 2.28.1-0ubuntu1.2
libexif12 (0.6.16-2.1ubuntu1) to 0.6.17-1
libexpat1 (2.0.1-4) to 2.0.1-4ubuntu1
libffi5 (3.0.7-1ubuntu1) to 3.0.7-2ubuntu1
libflac8 (1.2.1-1.2) to 1.2.1-2build1
libfreetype6 (2.3.9-4ubuntu0.1) to 2.3.9-5
libfreezethaw-perl (0.43-4) to 0.45-1
libfribidi0 (0.10.9-1) to 0.10.9-1build1
libfs6 (2:1.0.1-1) to 2:1.0.2-1
libfuse2 (2.7.4-1.1ubuntu4) to 2.7.4-1.1ubuntu4.1
libgail-common (2.16.1-0ubuntu2) to 2.18.3-1ubuntu2.1
libgail18 (2.16.1-0ubuntu2) to 2.18.3-1ubuntu2.1
libgamin0 (0.1.9-2ubuntu4) to 0.1.10-1ubuntu2
libgconf2-4 (2.26.0-0ubuntu1) to 2.28.0-0ubuntu2
libgcr0 (2.26.1-0ubuntu1) to 2.28.1-0ubuntu1
libgcrypt11 (1.4.1-2ubuntu1) to 1.4.4-2ubuntu2
libgd2-noxpm (2.0.36~rc1~dfsg-3ubuntu1) to 2.0.36~rc1~dfsg-3ubuntu1.9.10.1
libgdiplus (2.0-1) to 2.4.2-1
libglade2.0-cil (2.12.8-2) to 2.12.9-1
libglew1.5 (1.5.0dfsg1-3ubuntu1) to 1.5.1-4ubuntu1
libglib-perl (1:1.190-2) to 1:1.221-1
libglib2.0-0 (2.20.1-0ubuntu2.1) to 2.22.3-0ubuntu1
libglib2.0-cil (2.12.8-2) to 2.12.9-1
libglu1-mesa (7.4-0ubuntu3.2) to 7.6.0-1ubuntu4
libgmime-2.0-2a (2.2.22-2ubuntu1) to 2.2.22-4
libgmime2.2a-cil (2.2.22-2ubuntu1) to 2.2.22-4
libgmp3c2 (2:4.2.4+dfsg-2ubuntu1) to 2:4.3.1+dfsg-1ubuntu3
libgnome-keyring0 (2.26.1-0ubuntu1) to 2.28.1-0ubuntu1
libgnome-keyring1.0-cil (1.0.0~svn.r87622-2) to 1.0.0-1
libgnome-mag2 (1:0.15.6-0ubuntu1) to 1:0.15.9-0ubuntu1
libgnome-menu2 (2.26.0-0ubuntu1) to 2.28.0.1-0ubuntu1
libgnome-pilot2 (2.0.17-0ubuntu1) to 2.0.17-0ubuntu2
libgnome2-0 (2.26.0-0ubuntu2) to 2.28.0-0ubuntu3
libgnome2-canvas-perl (1.002-1+b1ubuntu3) to 1.002-2
libgnome2-common (2.26.0-0ubuntu2) to 2.28.0-0ubuntu3
libgnome2-perl (1.042-1build2) to 1.042-2
libgnome2-vfs-perl (1.080-1build2) to 1.081-1
libgnomecanvas2-0 (2.26.0-0ubuntu1) to 2.26.0-1
libgnomecanvas2-common (2.26.0-0ubuntu1) to 2.26.0-1
libgnomepanel2.24-cil (2.24.0-1ubuntu1) to 2.26.0-1
libgnomeui-0 (2.24.1-1) to 2.24.2-1
libgnomeui-common (2.24.1-1) to 2.24.2-1
libgnomevfs2-0 (1:2.24.1-0ubuntu1) to 1:2.24.2-1ubuntu1
libgnomevfs2-bin (1:2.24.1-0ubuntu1) to 1:2.24.2-1ubuntu1
libgnomevfs2-common (1:2.24.1-0ubuntu1) to 1:2.24.2-1ubuntu1
libgnutls26 (2.4.2-6ubuntu0.1) to 2.8.3-2
libgp11-0 (2.26.1-0ubuntu1) to 2.28.1-0ubuntu1
libgpg-error0 (1.4-2ubuntu7) to 1.6-1ubuntu1
libgphoto2-2 (2.4.2-0ubuntu4) to 2.4.6-1ubuntu6
libgphoto2-port0 (2.4.2-0ubuntu4) to 2.4.6-1ubuntu6
libgpm2 (1.20.4-3.1ubuntu1) to 1.20.4-3.2ubuntu1
libgraphviz4 (2.20.2-3ubuntu2) to 2.20.2-3ubuntu5
libgsf-1-114 (1.14.11-2ubuntu1) to 1.14.15-1ubuntu1
libgsf-1-common (1.14.11-2ubuntu1) to 1.14.15-1ubuntu1
libgsm1 (1.0.12-1) to 1.0.13-1
libgtk2.0-0 (2.16.1-0ubuntu2) to 2.18.3-1ubuntu2.1
libgtk2.0-cil (2.12.8-2) to 2.12.9-1
libgtk2.0-common (2.16.1-0ubuntu2) to 2.18.3-1ubuntu2.1
libgtkhtml-editor-common (1:3.26.0-0ubuntu2) to 1:3.28.1-0ubuntu1
libgtkhtml2-0 (2.11.1-2ubuntu1) to 2.11.1-2ubuntu2
libgtkhtml3.14-19 (1:3.26.0-0ubuntu2) to 1:3.28.1-0ubuntu1
libgtksourceview2.0-0 (2.6.1-0ubuntu1) to 2.8.1-1
libgtksourceview2.0-common (2.6.1-0ubuntu1) to 2.8.1-1
libgtop2-7 (2.26.0-0ubuntu2) to 2.26.1-0ubuntu1
libgtop2-common (2.26.0-0ubuntu2) to 2.26.1-0ubuntu1
libgucharmap7 (1:2.26.1-0ubuntu1) to 1:2.28.0-0ubuntu1
libgutenprint2 (5.2.3-0ubuntu5) to 5.2.4-0ubuntu2
libgweather-common (2.26.1-0ubuntu2) to 2.28.0-1ubuntu2
libhal-storage1 (0.5.12~rc1+git20090403-0ubuntu4) to 0.5.13-1ubuntu8
libhal1 (0.5.12~rc1+git20090403-0ubuntu4) to 0.5.13-1ubuntu8
libhtml-parser-perl (3.59-1ubuntu1) to 3.61-1ubuntu0.1
libhunspell-1.2-0 (1.2.6-1ubuntu2) to 1.2.8-4ubuntu2
libhyphen0 (2.4-2ubuntu1) to 2.4-4
libical0 (0.43-2ubuntu1) to 0.43-3
libice6 (2:1.0.4-1) to 2:1.0.5-1
libidn11 (1.10-3) to 1.15-1
libieee1284-3 (0.2.11-5ubuntu1) to 0.2.11-5ubuntu2
libijs-0.35 (0.35-6) to 0.35-7
libilmbase6 (1.0.1-2+nmu2) to 1.0.1-3build1
libiw29 (29-1.1ubuntu2) to 29-2ubuntu6
libjasper1 (1.900.1-5.1) to 1.900.1-6
libjpeg62 (6b-14) to 6b-14build1
libkeyutils1 (1.2-9) to 1.2-10
libklibc (1.5.14-1~exp1ubuntu2) to 1.5.15-1ubuntu2
libkpathsea4 (2007.dfsg.2-4ubuntu2) to 2007.dfsg.2-7ubuntu1
liblaunchpad-integration1 (0.1.24) to 0.1.26
liblcms1 (1.18.dfsg-0ubuntu1) to 1.18.dfsg-1ubuntu1
libldap-2.4-2 (2.4.15-1ubuntu3) to 2.4.18-0ubuntu1
liblircclient0 (0.8.4a-0ubuntu5) to 0.8.6-0ubuntu2
liblpint-bonobo0 (0.1.24) to 0.1.26
libltdl7 (2.2.6a-1ubuntu1) to 2.2.6a-4
libmagic1 (4.26-2ubuntu4) to 5.03-1ubuntu1
libmeanwhile1 (1.0.2-3) to 1.0.2-3build1
libmng1 (1.0.9-1) to 1.0.9-1build1
libmono-cairo2.0-cil (2.0.1-4ubuntu0.1) to 2.4.2.3+dfsg-2
libmono0 (2.0.1-4ubuntu0.1) to 2.4.2.3+dfsg-2
libmpfr1ldbl (2.4.0-1ubuntu3.1) to 2.4.1-1ubuntu1
libmtp8 (0.3.0-1ubuntu3) to 0.3.7-3ubuntu2
libmysqlclient15off (5.1.30really5.0.75-0ubuntu10.2) to 5.1.30really5.0.83-0ubuntu3
libnautilus-burn4 (2.25.3-0ubuntu1) to 2.25.3-0ubuntu3
libncurses5 (5.7+20090207-1ubuntu1) to 5.7+20090803-2ubuntu2
libncursesw5 (5.7+20090207-1ubuntu1) to 5.7+20090803-2ubuntu2
libndesk-dbus-glib1.0-cil (0.4.1-1ubuntu1) to 0.4.1-2
libnewt0.52 (0.52.2-11.3ubuntu3.1) to 0.52.10-4ubuntu1
libnl1 (1.1-3) to 1.1-5
libnm-util1 (0.7.1~rc4.1.cf199a964-0ubuntu2) to 0.8~a~git.20091013t193206.679d548-0ubuntu1
libnspr4-0d (4.7.5-0ubuntu0.9.04.1) to 4.8-0ubuntu1
libnspr4-dev (4.7.5-0ubuntu0.9.04.1) to 4.8-0ubuntu1
libnss-mdns (0.10-3ubuntu2) to 0.10-3ubuntu3
libnss3-1d (3.12.3.1-0ubuntu0.9.04.2) to 3.12.3.1-0ubuntu2
libnss3-dev (3.12.3.1-0ubuntu0.9.04.2) to 3.12.3.1-0ubuntu2
libogg0 (1.1.3-4build1) to 1.1.4~dfsg-1
liboil0.3 (0.3.15-1ubuntu3) to 0.3.16-1ubuntu1
liboobs-1-4 (2.22.0-2ubuntu1) to 2.22.2-0ubuntu1
libopenexr6 (1.6.1-3ubuntu1.9.04.1) to 1.6.1-4ubuntu3
libopenobex1 (1.5-1) to 1.5-2
libpam-ck-connector (0.3.0-2ubuntu4) to 0.3.1-0ubuntu2
libpam-gnome-keyring (2.26.1-0ubuntu1) to 2.28.1-0ubuntu1
libpam-modules (1.0.1-9ubuntu1.1) to 1.1.0-2ubuntu1
libpam-runtime (1.0.1-9ubuntu1.1) to 1.1.0-2ubuntu1
libpam0g (1.0.1-9ubuntu1.1) to 1.1.0-2ubuntu1
libpanel-applet2-0 (1:2.26.0-0ubuntu7) to 1:2.28.0-0ubuntu6
libpango1.0-common (1.24.1-0ubuntu1) to 1.26.0-1
libpcap0.8 (1.0.0-1) to 1.0.0-2ubuntu1
libpci3 (1:3.0.0-4ubuntu to 1:3.0.0-4ubuntu13
libpciaccess0 (0.10.5-1) to 0.10.6-2ubuntu1
libpcre3 (7.8-2ubuntu1) to 7.8-3
libpcsclite1 (1.4.102-1ubuntu2) to 1.5.3-1ubuntu1
libperl5.10 (5.10.0-19ubuntu1.1) to 5.10.0-24ubuntu4
libpisock9 (0.12.3-5ubuntu6) to 0.12.4-3ubuntu1
libpisync1 (0.12.3-5ubuntu6) to 0.12.4-3ubuntu1
libpixman-1-0 (0.13.2-1) to 0.14.0-1
libpng12-0 (1.2.27-2ubuntu2) to 1.2.37-1
libpolkit-dbus2 (0.9-2ubuntu1) to 0.9-4ubuntu1
libpolkit-grant2 (0.9-2ubuntu1) to 0.9-4ubuntu1
libpolkit2 (0.9-2ubuntu1) to 0.9-4ubuntu1
libportaudio2 (19+svn20071207-0ubuntu7) to 19+svn20090620-0ubuntu1
libpostproc51 (3:0.svn20090303-1ubuntu6) to 4:0.5+svn20090706-2ubuntu2
libpulse-browse0 (1:0.9.14-0ubuntu20.2) to 1:0.9.19-0ubuntu4
libpulse0 (1:0.9.14-0ubuntu20.2) to 1:0.9.19-0ubuntu4
libpurple-bin (1:2.5.5-1ubuntu8.4) to 1:2.6.2-1ubuntu7
librarian0 (0.8.1-1ubuntu2) to 0.8.1-2ubuntu3
libreadline5 (5.2-4) to 5.2-6
libsamplerate0 (0.1.4-1) to 0.1.7-2
libsane (1.0.19-23ubuntu7) to 1.0.20-4ubuntu3
libsasl2-2 (2.1.22.dfsg1-23ubuntu3.1) to 2.1.23.dfsg1-1ubuntu3
libsasl2-modules (2.1.22.dfsg1-23ubuntu3.1) to 2.1.23.dfsg1-1ubuntu3
libschroedinger-1.0-0 (1.0.5-1) to 1.0.8-2
libselinux1 (2.0.65-5build1) to 2.0.85-2ubuntu2
libsensors3 (1:2.10.7-1) to 1:2.10.8-1
libsepol1 (2.0.30-2ubuntu1) to 2.0.37-1
libsexy2 (0.1.11-2) to 0.1.11-2build1
libshout3 (2.2.2-5) to 2.2.2-5ubuntu1
libsilc-1.1-2 (1.1.7-2ubuntu1) to 1.1.10-2
libslang2 (2.1.3-3ubuntu3) to 2.1.4-3
libsm6 (2:1.1.0-1) to 2:1.1.0-2
libsndfile1 (1.0.17-4ubuntu1.1) to 1.0.20-1ubuntu1
libsnmp-base (5.4.1~dfsg-12ubuntu3) to 5.4.1~dfsg-12ubuntu7
libsnmp15 (5.4.1~dfsg-12ubuntu3) to 5.4.1~dfsg-12ubuntu7
libspectre1 (0.2.2.ds-1) to 0.2.2.ds-2
libsqlite0 (2.8.17-4build1) to 2.8.17-6build1
libsqlite3-0 (3.6.10-1ubuntu0.2) to 3.6.16-1ubuntu1
libss2 (1.41.4-1ubuntu1) to 1.41.9-1ubuntu3
libssl0.9.8 (0.9.8g-15ubuntu3.3) to 0.9.8g-16ubuntu3
libstlport4.6ldbl (4.6.2-3.2) to 4.6.2-5build1
libswscale0 (3:0.svn20090303-1ubuntu6) to 4:0.5+svn20090706-2ubuntu2
libtalloc1 (1.2.0~git20080616-1) to 1.4.0~git20090718-1
libtasn1-3 (1.5-1) to 2.2-1
libtdb1 (1.1.3~git20081222-2build1) to 1.1.5-1
libtext-wrapi18n-perl (0.06-6) to 0.06-7
libtheora0 (1.0-2) to 1.0-2.1build1
libtiff4 (3.8.2-11ubuntu0.9.04.3) to 3.8.2-13
libtrackerclient0 (0.6.93-0ubuntu3) to 0.6.95-1ubuntu3
libudev0 (141-1.2) to 147~-6.1
libusplash0 (0.5.31) to 0.5.49
libuuid1 (1.41.4-1ubuntu1) to 2.16-1ubuntu5
libv4l-0 (0.5.8-1) to 0.6.0-1
libvisual-0.4-0 (0.4.0-2.1+build1) to 0.4.0-2.1+ubuntu1
libvisual-0.4-plugins (0.4.0.dfsg.1-2ubuntu4) to 0.4.0.dfsg.1-2ubuntu5
libvorbis0a (1.2.0.dfsg-3.1ubuntu0.9.04.1) to 1.2.0.dfsg-6ubuntu0.1
libvorbisenc2 (1.2.0.dfsg-3.1ubuntu0.9.04.1) to 1.2.0.dfsg-6ubuntu0.1
libvorbisfile3 (1.2.0.dfsg-3.1ubuntu0.9.04.1) to 1.2.0.dfsg-6ubuntu0.1
libvte-common (1:0.20.0-0ubuntu2) to 1:0.22.2-0ubuntu2
libvte9 (1:0.20.0-0ubuntu2) to 1:0.22.2-0ubuntu2
libwbclient0 (2:3.3.2-1ubuntu3.2) to 2:3.4.0-3ubuntu5.1
libwmf0.2-7 (0.2.8.4-6ubuntu1.1) to 0.2.8.4-6.1ubuntu1
libwnck-common (2.26.0-0ubuntu1) to 1:2.28.0-0ubuntu1
libwww-perl (5.820-1) to 5.831-1
libx11-6 (2:1.1.99.2-1ubuntu2) to 2:1.2.2-1ubuntu1
libx11-data (2:1.1.99.2-1ubuntu2) to 2:1.2.2-1ubuntu1
libx86-1 (1.1+ds1-2) to 1.1+ds1-4
libxau6 (1:1.0.4-1) to 1:1.0.4-2
libxaw7 (2:1.0.5-1) to 2:1.0.6-1
libxcb-render-util0 (0.2.1+git1-1) to 0.3.6-1
libxcb-render0 (1.1.93-0ubuntu3.1) to 1.4-1
libxcb1 (1.1.93-0ubuntu3.1) to 1.4-1
libxcomposite1 (1:0.4.0-3) to 1:0.4.0-4
libxcursor1 (1:1.1.9-1) to 1:1.1.9-1build1
libxext6 (2:1.0.99.1-0ubuntu3) to 2:1.0.99.1-0ubuntu4
libxfixes3 (1:4.0.3-2) to 1:4.0.3-2build1
libxfont1 (1:1.3.3-1ubuntu1) to 1:1.4.0-1ubuntu1
libxi6 (2:1.2.0-1ubuntu1.1) to 2:1.2.1-2ubuntu1
libxml-twig-perl (1:3.32-2ubuntu1) to 1:3.32-3ubuntu1
libxml2 (2.6.32.dfsg-5ubuntu4.2) to 2.7.5.dfsg-1ubuntu1
libxmu6 (2:1.0.4-1) to 2:1.0.4-2
libxmuu1 (2:1.0.4-1) to 2:1.0.4-2
libxpm4 (1:3.5.7-1) to 1:3.5.7-2
libxrandr2 (2:1.3.0-1build1) to 2:1.3.0-2
libxrender1 (1:0.9.4-2) to 1:0.9.4-2ubuntu1
libxres1 (2:1.0.3-1) to 2:1.0.3-2
libxvmc1 (2:1.0.4-2ubuntu1) to 2:1.0.4-2ubuntu2
libxxf86dga1 (2:1.0.2-1) to 2:1.0.2-1build1
libxxf86vm1 (1:1.0.2-1) to 1:1.0.2-1ubuntu1
libzlcore-data (0.8.17-12ubuntu1) to 0.10.7dfsg-2ubuntu2
linux-firmware (1.11) to 1.25
linux-libc-dev (2.6.28-15.52) to 2.6.31-16.53
linux-sound-base (1.0.18.dfsg-1ubuntu to 1.0.20+dfsg-1ubuntu5
locales (2.9+cvs20090214-7) to 2.9+git20090617-3
lockfile-progs (0.1.11ubuntu2) to 0.1.13
login (1:4.1.1-6ubuntu6) to 1:4.1.4.1-1ubuntu2
logrotate (3.7.7-3ubuntu1) to 3.7.8-4ubuntu1
lsb-base (4.0-0ubuntu0.9.04.1) to 4.0-0ubuntu5
lsb-release (4.0-0ubuntu0.9.04.1) to 4.0-0ubuntu5
lsof (4.78.dfsg.1-4) to 4.81.dfsg.1-1
ltrace (0.5.1-2ubuntu1) to 0.5.3-2ubuntu2
make (3.81-5) to 3.81-6
man-db (2.5.5-1build1) to 2.5.6-2
manpages (3.15-1) to 3.21-1
mawk (1.3.3-13ubuntu1) to 1.3.3-15ubuntu1
memtest86+ (2.11-3ubuntu1) to 2.11-3ubuntu5
mesa-utils (7.4-0ubuntu3.2) to 7.6.0-1ubuntu4
mime-support (3.44-1) to 3.46-1ubuntu1
min12xxw (0.0.9-1ubuntu2) to 0.0.9-3ubuntu1
mktemp (1.5-9) to 7.4-2ubuntu1
mlocate (0.21.1-1ubuntu1) to 0.21.1-2
mount (2.14.2-1ubuntu4) to 2.16-1ubuntu5
mysql-common (5.1.30really5.0.75-0ubuntu10.2) to 5.1.37-1ubuntu5
ncurses-base (5.7+20090207-1ubuntu1) to 5.7+20090803-2ubuntu2
ncurses-bin (5.7+20090207-1ubuntu1) to 5.7+20090803-2ubuntu2
net-tools (1.60-21ubuntu1) to 1.60-23ubuntu1
ntpdate (1:4.2.4p4+dfsg-7ubuntu5.1) to 1:4.2.4p6+dfsg-1ubuntu5.1
nvidia-173-modaliases (173.14.16-0ubuntu1) to 173.14.20-0ubuntu5
nvidia-96-modaliases (96.43.10-0ubuntu1) to 96.43.13-0ubuntu6
onboard (0.91ubuntu2) to 0.92.0-0ubuntu3
openoffice.org-emailmerge (1:3.0.1-9ubuntu3.1) to 1:3.1.1-5ubuntu1
openoffice.org-hyphenation-en-us (2.4-2ubuntu1) to 2.4-4
openoffice.org-l10n-common (1:3.0.1-9ubuntu2) to 1:3.1.1-4ubuntu1
openoffice.org-style-human (1:3.0.1-9ubuntu3.1) to 1:3.1.1-5ubuntu1
openprinting-ppds (20090218-0ubuntu3) to 20090825-0ubuntu4
openssl (0.9.8g-15ubuntu3.3) to 0.9.8g-16ubuntu3
passwd (1:4.1.1-6ubuntu6) to 1:4.1.4.1-1ubuntu2
pciutils (1:3.0.0-4ubuntu to 1:3.0.0-4ubuntu13
perl (5.10.0-19ubuntu1.1) to 5.10.0-24ubuntu4
perl-base (5.10.0-19ubuntu1.1) to 5.10.0-24ubuntu4
perl-modules (5.10.0-19ubuntu1.1) to 5.10.0-24ubuntu4
pkg-config (0.22-1) to 0.22-1build1
pm-utils (1.2.2.4-0ubuntu4) to 1.2.5-2ubuntu7
pnm2ppa (1.12-16.2ubuntu1) to 1.12-16.2ubuntu2
policykit (0.9-2ubuntu1) to 0.9-4ubuntu1
poppler-utils (0.10.5-1ubuntu2.2) to 0.12.0-0ubuntu2.1
popularity-contest (1.46ubuntu1) to 1.48ubuntu1
psmisc (22.6-1) to 22.7-1
pulseaudio-utils (1:0.9.14-0ubuntu20.2) to 1:0.9.19-0ubuntu4
pxljr (1.1-0ubuntu6) to 1.1-0ubuntu7
python-brlapi (4.0~svn4301-0ubuntu4) to 4.0-7ubuntu2
python-cairo (1.4.12-1.2ubuntu1) to 1.8.6-1ubuntu1
python-central (0.6.11ubuntu7) to 0.6.11ubuntu9
python-cups (1.9.45-0ubuntu2) to 1.9.46-0ubuntu2
python-cupshelpers (1.1.3+git20090218-0ubuntu19.2) to 1.1.12+git20090826-0ubuntu8
python-dbus (0.83.0-1ubuntu1) to 0.83.0-1ubuntu2
python-debian (0.1.12ubuntu2) to 0.1.14ubuntu1
python-gconf (2.26.1-0ubuntu1) to 2.28.0-0ubuntu1
python-gdata (1.2.4-0ubuntu1) to 1.2.4-0ubuntu2
python-gdbm (2.6.2-0ubuntu1) to 2.6.3-0ubuntu1
python-gmenu (2.26.0-0ubuntu1) to 2.28.0.1-0ubuntu1
python-gnome2 (2.26.1-0ubuntu1) to 2.28.0-0ubuntu1
python-gnomecanvas (2.26.1-0ubuntu1) to 2.28.0-0ubuntu1
python-gobject (2.16.1-1ubuntu3) to 2.18.0-0ubuntu2
python-gtkhtml2 (2.19.1-0ubuntu14) to 2.25.3-3ubuntu1
python-gtksourceview2 (2.6.0-0ubuntu1) to 2.8.0-1
python-launchpad-bugs (0.3.5) to 0.3.6
python-launchpad-integration (0.1.24) to 0.1.26
python-libxml2 (2.6.32.dfsg-5ubuntu4.2) to 2.7.5.dfsg-1ubuntu1
python-newt (0.52.2-11.3ubuntu3.1) to 0.52.10-4ubuntu1
python-pkg-resources (0.6c9-0ubuntu4) to 0.6c9-0ubuntu5
python-problem-report (1.0-0ubuntu5.4) to 1.9.3-0ubuntu4.2
python-pyatspi (1.26.0-0ubuntu2) to 1.28.1-0ubuntu1
python-software-properties (0.71.5) to 0.75.4
python-support (0.8.7ubuntu4) to 1.0.3ubuntu1
python-usb (0.4.1-4ubuntu1) to 0.4.1-5
python-vte (1:0.20.0-0ubuntu2) to 1:0.22.2-0ubuntu2
readline-common (5.2-4) to 6.0-5
reiserfsprogs (1:3.6.19-6) to 1:3.6.21-1
rsync (3.0.5-1ubuntu2) to 3.0.6-1ubuntu1
sane-utils (1.0.19-23ubuntu7) to 1.0.20-4ubuntu3
screen (4.0.3-11ubuntu4) to 4.0.3-13ubuntu4
seahorse-plugins (2.26.1-0ubuntu1) to 2.28.1-0ubuntu4
sed (4.1.5-8) to 4.2.1-1
shared-mime-info (0.60-1) to 0.70-0ubuntu1
software-properties-gtk (0.71.5) to 0.75.4
ssh-askpass-gnome (1:5.1p1-5ubuntu1) to 1:5.1p1-6ubuntu2
ssl-cert (1.0.23ubuntu1) to 1.0.23ubuntu2
strace (4.5.17+cvs080723-2ubuntu1) to 4.5.18-1ubuntu2
sudo (1.6.9p17-1ubuntu3) to 1.7.0-1ubuntu2
sysklogd (1.5-5ubuntu3) to 1.5-5ubuntu4
system-config-printer-common (1.1.3+git20090218-0ubuntu19.2) to 1.1.12+git20090826-0ubuntu8
system-config-printer-gnome (1.1.3+git20090218-0ubuntu19.2) to 1.1.12+git20090826-0ubuntu8
sysvinit-utils (2.86.ds1-61ubuntu11) to 2.87dsf-4ubuntu12
tangerine-icon-theme (0.26.debian-3) to 0.27
tar (1.20-1) to 1.22-1
tasksel (2.73ubuntu18) to 2.73ubuntu23
tasksel-data (2.73ubuntu18) to 2.73ubuntu23
tcpdump (3.9.8-4ubuntu2) to 4.0.0-2ubuntu2
toshset (1.73-3) to 1.75-1
ttf-dejavu-core (2.28-1) to 2.29-2
ttf-freefont (20080323-3) to 20090104-2
ttf-opensymbol (1:3.0.1-9ubuntu3.1) to 1:3.1.1-5ubuntu1
ttf-sazanami-gothic (20040629-2ubuntu2) to 20040629-4ubuntu1
ttf-sazanami-mincho (20040629-2ubuntu2) to 20040629-4ubuntu1
ttf-thai-tlwg (1:0.4.11-2) to 1:0.4.13-1ubuntu1
tzdata (2009n-0ubuntu0.9.04.1) to 2009s-0ubuntu0.9.10
ubufox (0.7-0ubuntu1) to 0.8-0ubuntu1
ubuntu-artwork (46.3) to 51
ubuntu-docs (9.04.10) to 9.10.11
ubuntu-gdm-themes (0.32) to 0.33
ubuntu-keyring (2008.03.04) to 2009.08.28
ubuntu-netbook-remix-default-settings (0.5.1) to 0.6.7
ubuntu-sounds (0.10) to 0.12
ubuntu-standard (1.140) to 1.175
ubuntu-wallpapers (0.28.4) to 0.30
ucf (3.0014) to 3.0018ubuntu1
udev (141-1.2) to 147~-6.1
uno-libs3 (1.4.1+OOo3.0.1-9ubuntu3.1) to 1.5.1+OOo3.1.1-5ubuntu1
unzip (5.52-12ubuntu1) to 6.0-1
update-manager (1:0.111.9) to 1:0.126.9
update-manager-core (1:0.111.9) to 1:0.126.9
update-motd (1.11.1) to 3.5-0ubuntu1
update-notifier-common (0.76.7) to 0.90
upstart (0.3.9-8) to 0.6.3-11
ure (1.4.1+OOo3.0.1-9ubuntu3.1) to 1.5.1+OOo3.1.1-5ubuntu1
usbutils (0.73-8ubuntu3) to 0.82-0ubuntu1
usplash (0.5.31) to 0.5.49
usplash-theme-ubuntu (0.23) to 0.27
util-linux (2.14.2-1ubuntu4) to 2.16-1ubuntu5
uuid-runtime (1.41.4-1ubuntu1) to 2.16-1ubuntu5
vim-common (2:7.2.079-1ubuntu5) to 2:7.2.245-2ubuntu2
vim-tiny (2:7.2.079-1ubuntu5) to 2:7.2.245-2ubuntu2
w3m (0.5.2-2build1) to 0.5.2-2ubuntu1
wamerican (6-2.3) to 6-3
wbritish (6-2.3) to 6-3
webfav (1.11-0ubuntu1) to 1.16-0ubuntu1
wget (1.11.4-2ubuntu1.1) to 1.11.4-2ubuntu2
whiptail (0.52.2-11.3ubuntu3.1) to 0.52.10-4ubuntu1
whois (4.7.30) to 4.7.34ubuntu2
window-picker-applet (0.4.22-0ubuntu1) to 0.5.8-0ubuntu1
wireless-crda (1.7) to 1.10
wireless-tools (29-1.1ubuntu2) to 29-2ubuntu6
wodim (9:1.1.9-1ubuntu1) to 9:1.1.9-1ubuntu2
x11-apps (7.3+4) to 7.4+2
x11-session-utils (7.3+1) to 7.3+1build1
x11-xkb-utils (7.4+1ubuntu2) to 7.4+3
x11-xserver-utils (7.4+1) to 7.4+2ubuntu3
xautomation (1.02-1ubuntu1) to 1.03-1
xdg-user-dirs (0.10-1ubuntu2) to 0.11-0ubuntu2
xfonts-100dpi (1:1.0.0-4) to 1:1.0.0-4build1
xfonts-75dpi (1:1.0.0-4) to 1:1.0.0-4build1
xfonts-base (1:1.0.0-5) to 1:1.0.0-6
xfonts-scalable (1:1.0.0-6ubuntu0.8.04.1) to 1:1.0.0-7
xinit (1.0.9-2) to 1.1.1-1
xinput (1.4.0-1) to 1.4.2-1
xkb-data (1.5-2ubuntu11) to 1.6-1ubuntu5
xscreensaver-data (5.07-0ubuntu3) to 5.08-0ubuntu5
xscreensaver-gl (5.07-0ubuntu3) to 5.08-0ubuntu5
xserver-common (2:1.6.0-0ubuntu14) to 2:1.6.4-2ubuntu4
xserver-xorg (1:7.4~5ubuntu18) to 1:7.4+3ubuntu10
xserver-xorg-core (2:1.6.0-0ubuntu14) to 2:1.6.4-2ubuntu4
xserver-xorg-input-evdev (1:2.1.1-1ubuntu4) to 1:2.2.5-1ubuntu6
xserver-xorg-input-evtouch (0.8.8-0ubuntu3) to 0.8.8-0ubuntu6.1
xserver-xorg-input-kbd (1:1.3.1-2ubuntu1) to 1:1.3.2-3
xserver-xorg-input-mouse (1:1.4.0-1) to 1:1.4.0-2
xserver-xorg-input-synaptics (0.99.3-2ubuntu4) to 1.1.2-1ubuntu7
xserver-xorg-input-wacom (1:0.8.2.2-0ubuntu2) to 1:0.8.4.1-0ubuntu4
xserver-xorg-video-all (1:7.4~5ubuntu18) to 1:7.4+3ubuntu10
xserver-xorg-video-apm (1:1.2.1-1) to 1:1.2.1-2
xserver-xorg-video-ark (1:0.7.1-1) to 1:0.7.1-2
xserver-xorg-video-ati (1:6.12.1-0ubuntu2) to 1:6.12.99+git20090929.7968e1fb-0ubuntu1
xserver-xorg-video-chips (1:1.2.1-1) to 1:1.2.1-3
xserver-xorg-video-cirrus (1:1.2.1-3) to 1:1.3.1-1ubuntu2
xserver-xorg-video-fbdev (1:0.4.0-3) to 1:0.4.0-4
xserver-xorg-video-geode (2.11.1-1) to 2.11.6-1
xserver-xorg-video-i128 (1:1.3.1-2ubuntu1) to 1:1.3.2-1
xserver-xorg-video-i740 (1:1.2.0-2) to 1:1.3.0-1
xserver-xorg-video-intel (2:2.6.3-0ubuntu9.3) to 2:2.9.0-1ubuntu2
xserver-xorg-video-mach64 (6.8.0-3) to 6.8.2-1
xserver-xorg-video-mga (1:1.4.9.dfsg-3) to 1:1.4.11.dfsg-1
xserver-xorg-video-neomagic (1:1.2.2-1) to 1:1.2.3-1
xserver-xorg-video-nv (1:2.1.12-1ubuntu5) to 1:2.1.14-2ubuntu3
xserver-xorg-video-openchrome (1:0.2.903+svn713-1ubuntu1) to 1:0.2.903+svn758-0ubuntu1
xserver-xorg-video-r128 (6.8.0+git20090201.08d56c88-1) to 6.8.1-1
xserver-xorg-video-radeon (1:6.12.1-0ubuntu2) to 1:6.12.99+git20090929.7968e1fb-0ubuntu1
xserver-xorg-video-rendition (1:4.2.0.dfsg.1-2ubuntu1) to 1:4.2.1-1
xserver-xorg-video-s3 (1:0.6.1-1) to 1:0.6.2-1
xserver-xorg-video-s3virge (1:1.10.2-1) to 1:1.10.2-2
xserver-xorg-video-savage (1:2.2.1-4ubuntu2) to 1:2.3.0-1ubuntu1
xserver-xorg-video-siliconmotion (1:1.7.0-1) to 1:1.7.2-1
xserver-xorg-video-sis (1:0.10.1-1) to 1:0.10.1-2
xserver-xorg-video-sisusb (1:0.9.0-4) to 1:0.9.1-1
xserver-xorg-video-tdfx (1:1.4.0-2) to 1:1.4.1-1
xserver-xorg-video-trident (1:1.3.0-1ubuntu1) to 1:1.3.1-1
xserver-xorg-video-tseng (1:1.2.0-1ubuntu1) to 1:1.2.1-1
xserver-xorg-video-v4l (1:0.2.0-1ubuntu5) to 1:0.2.0-3ubuntu1
xserver-xorg-video-vesa (1:2.0.0-1ubuntu6) to 1:2.2.1-1
xserver-xorg-video-vmware (1:10.16.5-2) to 1:10.16.7-1
xserver-xorg-video-voodoo (1:1.2.0-1ubuntu1) to 1:1.2.2-1
xterm (241-1ubuntu1) to 243-1ubuntu1
zenity (2.26.0-0ubuntu2) to 2.28.0-0ubuntu2
zip (2.32-1) to 3.0-1ubuntu1
zlib1g (1:1.2.3.3.dfsg-12ubuntu2) to 1:1.2.3.3.dfsg-13ubuntu3
Installed the following packages:
gnome-session-bin (2.28.0-0ubuntu5)
libc-bin (2.10.1-0ubuntu15)
libc-dev-bin (2.10.1-0ubuntu15)
libcompress-bzip2-perl (2.09-2)
libdevkit-power-gobject1 (011-1ubuntu1)
libeggdbus-1-0 (0.5-1)
libgssapi-krb5-2 (1.7dfsg~beta3-1)
libk5crypto3 (1.7dfsg~beta3-1)
libkrb5-3 (1.7dfsg~beta3-1)
libkrb5support0 (1.7dfsg~beta3-1)
libpolkit-agent-1-0 (0.94-1ubuntu1)
libpolkit-backend-1-0 (0.94-1ubuntu1)
libpolkit-gobject-1-0 (0.94-1ubuntu1)
libpoppler5 (0.12.0-0ubuntu2.1)
libxklavier15 (4.0-0ubuntu5)
mountall (1.0)
os-prober (1.35)
policykit-1 (0.94-1ubuntu1)
policykit-1-gnome (0.94-1+1git.230873)
tcl8.4 (8.4.19-3)
tk8.4 (8.4.19-3)

---

### Post by iponeverything on 2010-01-02
> Back again, i have just realised that i did unintentionally upgrade from 9.04 to 9.10 (but only partially- i keep getting partial upgrade notices). As i cant now get the wifi working, there is not much I can do about it. I include here the alst logfile though as iponeverything suggested (its very long though).


I dont particulalry want to run 9.10 so if there someway of just reverting to 9.04 that would be great


I think you have two options:

1) complete the upgrade. You can do this via a wired connection.

2) Backup /home, reinstall 9.04 and then restore /home.

With option 2 you have to do a recursive chown on the directories in /home to match the pid's /etc/passwd.

Unfortunately there is no way that I know of to revert a dist upgrade.

---

