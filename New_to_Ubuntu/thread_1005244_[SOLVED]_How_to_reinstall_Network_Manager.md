---
title: "[SOLVED] How to reinstall Network Manager"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by GrahamM on 2008-12-08
I installed Ubuntu 8.1 on my 1Gig older Asus based desktop. Everything worked fine including my wifi access - card is a D-Link, I think but comes up as Azeuris or something like that

I made teh mistake of searching for a way to avoid having to fill in the keyring password in order to access wifi. Method said to uninstall Network Manager and the install WiCD. Well, uninstalled Network manager but WiCD won't install because it says it conflicts with Network manager.

So, I would like to go back to Network manager. But when I try, it seems to want to access the net to download it. I thought it would still be available on the hard drive.

I tried to get it from my installation disk. But for some reason, I get a message saying Ubuntu cannot mount the disk. I can boot from the disk, so there is nothing wrong with the disk and I did the install from it after first loading Live CD. 

I read that I could get net access using the terminal, but  Sudo IFUP wifi0 but that does not work. Doesn't seem to recognize the wifi card.

So to sum up - How do I reinstate Network manager with no internet access from ubuntu, but with access on same machine from W2K?

---

### Post by iponeverything on 2008-12-08
cd /var/cache/apt/archives

you should be able to find the debs in there.

use "sudo dpkg -i <package>" to install them.

---

### Post by GrahamM on 2008-12-08
> **iponeverything said:**
> cd /var/cache/apt/archives

you should be able to find the debs in there.

use "sudo dpkg -i <package>" to install them.

OK, I had a look at that - But which would be the 'deb file for Network Manager?  I have posted the full list below.

WiCD won't install because it says Network Manager is already installed. Is it possible that NM is installed and just needs to be "re-activated"? For example, in Windows I would go to Install Programs, choose windows components and then click on the one I wanted to activate. It would be installed from on-disk files.

In present case when I try to reinstall NM, it wants to connect to the net, which of course it cannot do!

Here are the debs I found:

alsa-utils_1.0.17-0ubuntu3_i386.deb
apparmor_2.3+1289-0ubuntu4.1_i386.deb
apparmor-utils_2.3+1289-0ubuntu4.1_i386.deb
base-files_4.0.4ubuntu2.2_i386.deb
ca-certificates_20080514-0ubuntu1.1_all.deb
capplets-data_1%3a2.24.0.1-0ubuntu7.1_all.deb
command-not-found_0.2.26ubuntu1.1_all.deb
command-not-found-data_0.2.26ubuntu1.1_i386.deb
compiz_1%3a0.7.8-0ubuntu4.1_all.deb
compiz-core_1%3a0.7.8-0ubuntu4.1_i386.deb
compiz-gnome_1%3a0.7.8-0ubuntu4.1_i386.deb
compiz-plugins_1%3a0.7.8-0ubuntu4.1_i386.deb
compiz-wrapper_1%3a0.7.8-0ubuntu4.1_i386.deb
cups_1.3.9-2ubuntu3_i386.deb
cups-bsd_1.3.9-2ubuntu3_i386.deb
cups-client_1.3.9-2ubuntu3_i386.deb
cups-common_1.3.9-2ubuntu3_all.deb
evolution_2.24.2-0ubuntu1_i386.deb
evolution-common_2.24.2-0ubuntu1_all.deb
evolution-data-server_2.24.2-0ubuntu1_i386.deb
evolution-data-server-common_2.24.2-0ubuntu1_all.deb
evolution-exchange_2.24.2-0ubuntu1_i386.deb
evolution-plugins_2.24.2-0ubuntu1_i386.deb
firefox-3.0_3.0.4+nobinonly-0ubuntu0.8.10.1_i386.deb
firefox_3.0.4+nobinonly-0ubuntu0.8.10.1_all.deb
firefox-3.0-branding_3.0.4+nobinonly-0ubuntu0.8.10.1_i386.deb
firefox-3.0-gnome-support_3.0.4+nobinonly-0ubuntu0.8.10.1_i386.deb
firefox-gnome-support_3.0.4+nobinonly-0ubuntu0.8.10.1_all.deb
f-spot_0.5.0.3-0ubuntu4_i386.deb
gdm-guest-session_0.6.1_all.deb
gedit_2.24.2-0ubuntu1_i386.deb
gedit-common_2.24.2-0ubuntu1_all.deb
gnome-cards-data_1%3a2.24.1.1-0ubuntu1_all.deb
gnome-control-center_1%3a2.24.0.1-0ubuntu7.1_i386.deb
gnome-games_1%3a2.24.1.1-0ubuntu1_i386.deb
gnome-games-data_1%3a2.24.1.1-0ubuntu1_all.deb
gnome-panel_1%3a2.24.1-0ubuntu2.1_i386.deb
gnome-panel-data_1%3a2.24.1-0ubuntu2.1_all.deb
gnome-pilot_2.0.15-2ubuntu4_i386.deb
gnome-settings-daemon_2.24.0-0ubuntu3.3_i386.deb
gnome-terminal_2.24.1.1-0ubuntu1_i386.deb
gnome-terminal-data_2.24.1.1-0ubuntu1_all.deb
gstreamer0.10-plugins-ugly_0.10.9-1ubuntu0.1_i386.deb
hal-info_20081124-0ubuntu1~intrepid_all.deb
human-theme_0.28.6_all.deb
initramfs-tools_0.92bubuntu16_all.deb
jockey-common_0.5~beta3-0ubuntu6_all.deb
jockey-gtk_0.5~beta3-0ubuntu6_all.deb
language-pack-en_1%3a8.10+20081107_all.deb
language-pack-en-base_1%3a8.10+20081107_all.deb
language-pack-gnome-en_1%3a8.10+20081107_all.deb
language-pack-gnome-en-base_1%3a8.10+20081107_all.deb
liba52-0.7.4_0.7.4-11ubuntu1_i386.deb
libapparmor1_2.3+1289-0ubuntu4.1_i386.deb
libapparmor-perl_2.3+1289-0ubuntu4.1_i386.deb
libasound2-plugins_1.0.17-0ubuntu5_i386.deb
libcamel1.2-14_2.24.2-0ubuntu1_i386.deb
libcups2_1.3.9-2ubuntu3_i386.deb
libcupsimage2_1.3.9-2ubuntu3_i386.deb
libdecoration0_1%3a0.7.8-0ubuntu4.1_i386.deb
libdvdnav4_4.1.2-3_i386.deb
libdvdread3_0.9.7-11ubuntu2_i386.deb
libebackend1.2-0_2.24.2-0ubuntu1_i386.deb
libebook1.2-9_2.24.2-0ubuntu1_i386.deb
libecal1.2-7_2.24.2-0ubuntu1_i386.deb
libedata-book1.2-2_2.24.2-0ubuntu1_i386.deb
libedata-cal1.2-6_2.24.2-0ubuntu1_i386.deb
libedataserver1.2-11_2.24.2-0ubuntu1_i386.deb
libedataserverui1.2-8_2.24.2-0ubuntu1_i386.deb
libegroupwise1.2-13_2.24.2-0ubuntu1_i386.deb
libexchange-storage1.2-3_2.24.2-0ubuntu1_i386.deb
libgdata1.2-1_2.24.2-0ubuntu1_i386.deb
libgdata-google1.2-1_2.24.2-0ubuntu1_i386.deb
libglib2.0-0_2.18.2-0ubuntu2_i386.deb
libglib2.0-data_2.18.2-0ubuntu2_all.deb
libgnomecanvas2-0_2.20.1.1-1ubuntu3_i386.deb
libgnomecanvas2-common_2.20.1.1-1ubuntu3_all.deb
libgnome-pilot2_2.0.15-2ubuntu4_i386.deb
libgnome-window-settings1_1%3a2.24.0.1-0ubuntu7.1_i386.deb
libgnutls26_2.4.1-1ubuntu0.1_i386.deb
libgphoto2-2_2.4.2-0ubuntu3_i386.deb
libgphoto2-port0_2.4.2-0ubuntu3_i386.deb
libgtkhtml3.14-19_1%3a3.24.1.1-0ubuntu1_i386.deb
libgtkhtml-editor0_1%3a3.24.1.1-0ubuntu1_i386.deb
libgtkhtml-editor-common_1%3a3.24.1.1-0ubuntu1_all.deb
libgtksourceview2.0-0_2.4.1-0ubuntu1_i386.deb
libgtksourceview2.0-common_2.4.1-0ubuntu1_all.deb
libid3tag0_0.15.1b-10_i386.deb
libmad0_0.15.1b-3_i386.deb
libmpeg2-4_0.4.1-3_i386.deb
libpam0g_1.0.1-4ubuntu5.3_i386.deb
libpam-modules_1.0.1-4ubuntu5.3_i386.deb
libpam-runtime_1.0.1-4ubuntu5.3_all.deb
libpanel-applet2-0_1%3a2.24.1-0ubuntu2.1_i386.deb
libpango1.0-0_1.22.2-0ubuntu1_i386.deb
libpango1.0-common_1.22.2-0ubuntu1_all.deb
libsidplay1_1.36.59-5_i386.deb
libsmbclient_2%3a3.2.3-1ubuntu3.3_i386.deb
libsnmp15_5.4.1~dfsg-7.1ubuntu6.1_i386.deb
libsnmp-base_5.4.1~dfsg-7.1ubuntu6.1_all.deb
libtotem-plparser12_2.24.2-0ubuntu1_i386.deb
libvolume-id0_124-9_i386.deb
libwbclient0_2%3a3.2.3-1ubuntu3.3_i386.deb
libxml2_2.6.32.dfsg-4ubuntu1.1_i386.deb
libxml2-utils_2.6.32.dfsg-4ubuntu1.1_i386.deb
linux-generic_2.6.27.9.13_i386.deb
linux-headers-2.6.27-7_2.6.27-7.16_all.deb
linux-headers-2.6.27-7-generic_2.6.27-7.16_i386.deb
linux-headers-2.6.27-9_2.6.27-9.19_all.deb
linux-headers-2.6.27-9-generic_2.6.27-9.19_i386.deb
linux-headers-generic_2.6.27.9.13_i386.deb
linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb
linux-image-2.6.27-9-generic_2.6.27-9.19_i386.deb
linux-image-generic_2.6.27.9.13_i386.deb
linux-libc-dev_2.6.27-9.19_i386.deb
linux-restricted-modules-2.6.27-9-generic_2.6.27-9.13_i386.deb
linux-restricted-modules-common_2.6.27-9.13_all.deb
linux-restricted-modules-generic_2.6.27.9.13_i386.deb
lock
login_1%3a4.1.1-1ubuntu1.1_i386.deb
nvidia-96-modaliases_96.43.09-0ubuntu1_i386.deb
openoffice.org-base-core_1%3a2.4.1-11ubuntu2.1_i386.deb
openoffice.org-calc_1%3a2.4.1-11ubuntu2.1_i386.deb
openoffice.org-common_1%3a2.4.1-11ubuntu2.1_all.deb
openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb
openoffice.org-draw_1%3a2.4.1-11ubuntu2.1_i386.deb
openoffice.org-emailmerge_1%3a2.4.1-11ubuntu2.1_all.deb
openoffice.org-gnome_1%3a2.4.1-11ubuntu2.1_i386.deb
openoffice.org-gtk_1%3a2.4.1-11ubuntu2.1_i386.deb
openoffice.org-impress_1%3a2.4.1-11ubuntu2.1_i386.deb
openoffice.org-math_1%3a2.4.1-11ubuntu2.1_i386.deb
openoffice.org-style-human_1%3a2.4.1-11ubuntu2.1_all.deb
openoffice.org-writer_1%3a2.4.1-11ubuntu2.1_i386.deb
partial
passwd_1%3a4.1.1-1ubuntu1.1_i386.deb
pm-utils_1.1.2.4-1ubuntu8_all.deb
procps_1%3a3.2.7-9ubuntu2.1_i386.deb
python-libxml2_2.6.32.dfsg-4ubuntu1.1_i386.deb
python-software-properties_0.68.1_all.deb
python-uno_1%3a2.4.1-11ubuntu2.1_i386.deb
rhythmbox_0.11.6svn20081008-0ubuntu4.2_i386.deb
samba-common_2%3a3.2.3-1ubuntu3.3_i386.deb
smbclient_2%3a3.2.3-1ubuntu3.3_i386.deb
software-properties-gtk_0.68.1_all.deb
splix_2.0.0~rc2-0ubuntu2.3_i386.deb
system-tools-backends_2.6.0-1ubuntu1.1_i386.deb
totem_2.24.3-0ubuntu1_all.deb
totem-common_2.24.3-0ubuntu1_all.deb
totem-gstreamer_2.24.3-0ubuntu1_i386.deb
totem-mozilla_2.24.3-0ubuntu1_all.deb
totem-plugins_2.24.3-0ubuntu1_i386.deb
transmission-common_1.34-0ubuntu2.1_all.deb
transmission-gtk_1.34-0ubuntu2.1_i386.deb
ttf-opensymbol_1%3a2.4.1-11ubuntu2.1_all.deb
udev_124-9_i386.deb
update-manager_1%3a0.93.34_all.deb
update-manager-core_1%3a0.93.34_i386.deb
xkb-data_1.3-2ubuntu4.2_all.deb
xserver-xorg-input-evdev_1%3a2.0.99+git20080912-0ubuntu6_i386.deb
xserver-xorg-input-vmmouse_1%3a12.5.1-1ubuntu5.1_i386.deb
xulrunner-1.9_1.9.0.4+nobinonly-0ubuntu0.8.10.1_i386.deb
xulrunner-1.9-gnome-support_1.9.0.4+nobinonly-0ubuntu0.8.10.1_i386.deb
.10.1_i386.deb

---

### Post by thadacto on 2008-12-08
Same here, Cuoldn't install cinelerra, said a problrm with dependencies with libasound2 so I decided to delete that via packet manager and low and behold, it deleted have my operating system. Eventually got a number of things back via internet, restarted and now I can't connect to the internet - seems that the Network Manager is missing or some parts of it.
If I could, and knew the package to download via my Win XP, and then located it in XP.
18 days I'm now trying to get Ubuntu/linux working.
Anyone any ideas??????????  PLEASE .........

---

### Post by gn2 on 2008-12-08
> **GrahamM said:**
> ~ So to sum up - How do I reinstate Network manager with no internet access from ubuntu, ~

Boot into Ubuntu.

Insert the Ubuntu 8.10 CD in the drive AFTER the system is running if a file browser opens, close it.

Open Synaptic Package Manager, then in Synaptic click Settings > Repositories and in the Ubuntu Software tab tick the box to use packages from the CD.

Next click Reload then you should now be able to use Synaptic to install network-manager from the CD.

---

### Post by thadacto on 2008-12-08
Cheers gn2, worked a treat,
Internet in Hardy up and running again. 
Very many thanks indeed.

---

### Post by GrahamM on 2008-12-08
> **gn2 said:**
> Boot into Ubuntu.

Insert the Ubuntu 8.10 CD in the drive AFTER the system is running if a file browser opens, close it.

Open Synaptic Package Manager, then in Synaptic click Settings > Repositories and in the Ubuntu Software tab tick the box to use packages from the CD.

Next click Reload then you should now be able to use Synaptic to install network-manager from the CD.

Unfortunately it did not work for me. I actually had the CD checked off already. When I hit Reload, I get an error - Failed to fetch CDROM. Then its says to use apt-cdrom to make cdrom recognizable by aps. Tried that too - no dice.

If I try and access drive (it's actually a dual dvd/cd) I get a cannot mount volume Ubuntu 8.10 i386 error . It first says it is write protected, then says it is mounting read-only. Then says Can't read Superblock (whatever that is!)
Added: I tried inserting a different CD and Ubuntu mounts it just fine. Is there something about the Live CD that is stopping it from being mounted? Maybe because it was burned using Nero8? 

If I could get the Live CD access, maybe I could solve the Network problem.

I will try starting a new thread on the CD problem, because the current one is misleading.

---

### Post by GrahamM on 2008-12-09
I gave up on trying to reinstate Network Manager. 

Re-installed Ubuntu so now I have Network Manager back, but I lost all the configuratiomn work I had done on evolution and other things.

But, now I have a clean install, I find that the Live CD still cannot be mounted in Ubuntu. It is accessible from Windows and I used to re-install, so nothing wrong with CD.

I suspect it has something to do with format Nero uses, but don't know how to get Ubuntu to work with it.

Have posted a question about this in the Install forum

---

### Post by hyper_ch on 2008-12-09
if you want to run WICD then
(1) add the WICD repos
(2) install WICD - it will completly uninstall the default network manager

in order to restore the default network manager you'll have to find out what the ubuntu/kubuntu front-end version is. Install that and it will also install the actual one.

---

### Post by GrahamM on 2008-12-09
> **hyper_ch said:**
> if you want to run WICD then
(1) add the WICD repos
(2) install WICD - it will completly uninstall the default network manager

in order to restore the default network manager you'll have to find out what the ubuntu/kubuntu front-end version is. Install that and it will also install the actual one.

Now that I have re-installed Ubuntu and have Network Manager back, I will probably leave it as is.

One thing about running into problems like this, is that it accelerates the learning process.

---

