---
title: "Can't update Ubuntu 10.04"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by delboy41 on 2010-08-23
I am the newest of the new to Linux but want to get Ubuntu 10.04 to work on my Windows 7 laptop.  Having installed 10.04 I saw that I needed to install over 250 updates according to update manger!  Initally none would download. but after checking that the internet connection was working and re-booting ubuntu some updates downloaded and installed.  I now have just 192 updates required according to Update Manager.  When I click the update button none will download but I just get a message that says:-
"W:Failed to fetch [http://gbarchive.ubuntu.com/ubuntu/pool/main/e/eglibc/-bin_2.11.1-Oubuntu7.2_i386.deb](http://gbarchive.ubuntu.com/ubuntu/pool/main/e/eglibc/-bin_2.11.1-Oubuntu7.2_i386.deb)
Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (113:No route to host)"
 
I am having problems getting Ubuntu to network with my Windows 7 host using a separate network adaptor with the host only card (it keeps asking me for a password to access my files but I have set no password)  so I thought the first thing to do would be to install all the updates but now I can't even do that!  Can anyone help?

---

### Post by migs73 on 2010-08-23
Is your Ubuntu on a VM inside windows7??

---

### Post by delboy41 on 2010-08-23
Yes, It's on Oracle VM Virtualbox

---

### Post by sataris on 2010-08-23
try going to software sources and ensure you are on the main repo if you are updating to 10.04
 
If it says anything other than main under the server, switch it to main.
 
It looks like its pinging a server, but unable to pull in any downloads. However, the VM may be affecting it as well. Is it a read only sandbox or did you actually install the image in your VM? If its a sandbox, it will not update as it's only readable.
 
Your VM config would be helpful to troubleshoot.

---

### Post by delboy41 on 2010-08-23
I am not updating to 10.04.  I installed 10.04 from a CD I created from the image file onto a new drive on the VM.
How do I send you the VM config?  I have taken a "snapshot" of it in the VM but don't know how to send it.

---

### Post by dfairley on 2010-08-23
This is a very good thread.. I was having a simular issue with my VM ware...

---

### Post by vijushimpi on 2010-08-24
after installing ubuntu-10.04.1 you may require few updates only, check release notes.

---

### Post by delboy41 on 2010-08-24
I have checked the release notes but I can't find any reference therein to the number of updates required after install.  Update Manager is still saying that I require 6 Important Security Updates and 192 Recommended Updates but still none will download or install.

---

### Post by yeats on 2010-08-24
Go to Applications -> Accessories -> Terminal and type:

```
sudo apt-get update
```

You will see many lines of output.  Copy and paste them here surrounded by "CODE" tags (you can click the # symbol when composing your post).  While you're at it, after the above command, do:

```
sudo apt-get upgrade
```

and post that output too.  That will help others troubleshoot this for you.

---

### Post by julio_cortez on 2010-08-24
Just one stupid thing: have you checked that the internet connection on the host OS is alright?

Yesterday I was trying to run updates of the XP virtual machine I have in Windows 7, and they kept failing.. *Then I realized I didn't trigger the connection in Windows 7* :)

---

### Post by delboy41 on 2010-08-24
> **julio_cortez said:**
> Just one stupid thing: have you checked that the internet connection on the host OS is alright?

Yesterday I was trying to run updates of the XP virtual machine I have in Windows 7, and they kept failing.. *Then I realized I didn't trigger the connection in Windows 7* :)
Yes the internet connection is fine.  As I have said it has already downloaded and installed several updates and I have no trouble using Firefox.

---

### Post by delboy41 on 2010-08-24
Chris,

Here is what I get:

```
sudo apt-get update
Err http://gb.archive.ubuntu.com lucid Release.gpg                             
  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (113: No route to host)
Err http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB          
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates Release.gpg
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com:http:
Ign http://gb.archive.ubuntu.com lucid Release        
Ign http://gb.archive.ubuntu.com lucid-updates Release
Ign http://gb.archive.ubuntu.com lucid/main Packages  
Ign http://gb.archive.ubuntu.com lucid/restricted Packages
Ign http://gb.archive.ubuntu.com lucid/main Sources   
Ign http://gb.archive.ubuntu.com lucid/restricted Sources
Ign http://gb.archive.ubuntu.com lucid/universe Packages
Ign http://gb.archive.ubuntu.com lucid/universe Sources
Ign http://gb.archive.ubuntu.com lucid/multiverse Packages
Ign http://gb.archive.ubuntu.com lucid/multiverse Sources
Ign http://gb.archive.ubuntu.com lucid-updates/main Packages
Ign http://gb.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://gb.archive.ubuntu.com lucid-updates/main Sources
Ign http://gb.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://gb.archive.ubuntu.com lucid-updates/universe Packages
Ign http://gb.archive.ubuntu.com lucid-updates/universe Sources
Ign http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://gb.archive.ubuntu.com lucid/main Packages   
Ign http://gb.archive.ubuntu.com lucid/restricted Packages
Ign http://gb.archive.ubuntu.com lucid/main Sources    
Ign http://gb.archive.ubuntu.com lucid/restricted Sources
Ign http://gb.archive.ubuntu.com lucid/universe Packages
Ign http://gb.archive.ubuntu.com lucid/universe Sources
Ign http://gb.archive.ubuntu.com lucid/multiverse Packages
Ign http://gb.archive.ubuntu.com lucid/multiverse Sources
Ign http://gb.archive.ubuntu.com lucid-updates/main Packages
Ign http://gb.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://gb.archive.ubuntu.com lucid-updates/main Sources
Ign http://gb.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://gb.archive.ubuntu.com lucid-updates/universe Packages
Ign http://gb.archive.ubuntu.com lucid-updates/universe Sources
Ign http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
Ign http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
Err http://gb.archive.ubuntu.com lucid/main Packages   
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/restricted Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/main Sources    
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/restricted Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/universe Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/universe Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/multiverse Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid/multiverse Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/main Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/restricted Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/main Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/restricted Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/universe Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/universe Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
  Unable to connect to gb.archive.ubuntu.com:http:
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com lucid-security Release
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (113: No route to host)

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  Unable to connect to gb.archive.ubuntu.com:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
derek@Sony-Ubuntu:~$ 

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  acpi-support acpid app-install-data-partner apt apt-transport-https
  apt-utils at-spi binutils brasero brasero-common byobu capplets-data dpkg
  empathy empathy-common evince evolution evolution-common
  evolution-data-server evolution-data-server-common evolution-plugins f-spot
  fglrx-modaliases file-roller gdm gedit gedit-common gnome-about
  gnome-control-center gnome-desktop-data gnome-keyring gnome-orca gnome-panel
  gnome-panel-data gnome-screensaver gnome-settings-daemon grub-common grub-pc
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gtk2-engines-pixbuf gvfs
  gvfs-backends gvfs-bin gvfs-fuse gwibber gwibber-service hal
  humanity-icon-theme hunspell-en-ca indicator-applet indicator-applet-session
  indicator-sound jockey-common jockey-gtk language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector language-selector-common libatk1.0-0 libatk1.0-data
  libatspi1.0-0 libbrasero-media0 libc-bin libc-dev-bin libc6 libc6-dev
  libc6-i686 libcairomm-1.0-1 libcamel1.2-14 libdbusmenu-glib1
  libdbusmenu-gtk1 libebackend1.2-0 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11
  libedataserverui1.2-8 libegroupwise1.2-13 libevdocument2 libevview2
  libexchange-storage1.2-3 libgail-common libgail18 libgcr0 libgdata-common
  libgdata-google1.2-1 libgdata1.2-1 libgdata6 libgl1-mesa-dri libgl1-mesa-glx
  libglib2.0-0 libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa
  libgnome-desktop-2-17 libgnome-keyring0 libgnome-window-settings1
  libgnomekbd-common libgnomekbd4 libgp11-0 libgstfarsight0.10-0 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libgtkmm-2.4-1c2a libgtksourceview2.0-0
  libgtksourceview2.0-common libgvfscommon0 libhal-storage1 libhal1
  libido-0.1-0 libldap-2.4-2 liblircclient0 libnautilus-extension1 libnotify1
  libpam-gnome-keyring libpanel-applet2-0 libpangomm-1.4-1 libparted0debian1
  libpoppler-glib4 libpoppler5 librsvg2-2 librsvg2-common libsdl1.2debian
  libsdl1.2debian-pulseaudio libsmbclient libsoup-gnome2.4-1 libsoup2.4-1
  libtag1-vanilla libtag1c2a libusb-0.1-4 libwbclient0 light-themes
  linux-firmware mountall myspell-en-gb myspell-en-za nautilus nautilus-data
  nautilus-sendto-empathy nvidia-current-modaliases obexd-client
  openssh-client parted pm-utils pm-utils-powersave-policy poppler-utils
  python-apt python-cupshelpers python-farsight python-gtksourceview2
  python-papyon python-pyatspi python-ubuntuone-client rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins samba-common samba-common-bin
  simple-scan smbclient software-center ssh-askpass-gnome synaptic
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev telepathy-butterfly tomboy totem totem-common
  totem-mozilla totem-plugins transmission-common transmission-gtk tzdata
  ubuntu-system-service ubuntuone-client ubuntuone-client-gnome udisks
  unattended-upgrades update-manager update-manager-core upstart ureadahead
  vinagre xserver-common xserver-xorg-core
192 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 111MB of archives.
After this operation, 5,394kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libc-bin libc6 libc6-i686 libc-dev-bin libc6-dev tzdata grub-pc grub-common
  dpkg language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base apt apt-utils libldap-2.4-2 mountall upstart
  ureadahead libglib2.0-0 libusb-0.1-4 apt-transport-https python-apt
  libatk1.0-0 libgail-common libgail18 libgtk2.0-common gtk2-engines-pixbuf
  libgtk2.0-0 synaptic language-selector language-selector-common
  openssh-client libparted0debian1 parted update-manager update-manager-core
  acpid pm-utils acpi-support app-install-data-partner python-pyatspi
  libatspi1.0-0 at-spi binutils libdbusmenu-glib1 brasero-common
  libbrasero-media0 libnautilus-extension1 libgvfscommon0 gvfs-fuse gvfs-bin
  libgp11-0 libgcr0 libgnome-keyring0 gnome-keyring libwbclient0 libsmbclient
  libsoup2.4-1 libsoup-gnome2.4-1 gvfs-backends gvfs brasero byobu
  libgnome-desktop-2-17 libedataserver1.2-11 libcamel1.2-14 libebook1.2-9
  gnome-control-center capplets-data libgnome-window-settings1
  libgnomekbd-common libgnomekbd4 librsvg2-common librsvg2-2 libnotify1
  gnome-settings-daemon gnome-about gnome-desktop-data ubuntu-system-service
  libtag1c2a libtag1-vanilla gstreamer0.10-plugins-good libgstfarsight0.10-0
  nautilus-sendto-empathy empathy empathy-common libevdocument2 libevview2
  libpoppler5 libpoppler-glib4 evince libebackend1.2-0 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libegroupwise1.2-13 libgdata1.2-1
  libgdata-google1.2-1 evolution-data-server evolution-data-server-common
  libedataserverui1.2-8 libexchange-storage1.2-3 evolution evolution-common
  evolution-plugins libgl1-mesa-dri libgl1-mesa-glx f-spot file-roller
  libpanel-applet2-0 gdm libgtksourceview2.0-common libgtksourceview2.0-0
  gedit-common python-gtksourceview2 gedit gnome-orca gnome-panel-data
  gnome-panel gnome-screensaver gstreamer0.10-pulseaudio gwibber
  gwibber-service libhal1 libhal-storage1 hal humanity-icon-theme
  hunspell-en-ca indicator-applet-session indicator-applet jockey-gtk
  jockey-common libatk1.0-data libcairomm-1.0-1 libdbusmenu-gtk1
  libgdata-common libgdata6 libglib2.0-data libglibmm-2.4-1c2a libgtk2.0-bin
  libpangomm-1.4-1 libgtkmm-2.4-1c2a libido-0.1-0 libpam-gnome-keyring
  libsdl1.2debian libsdl1.2debian-pulseaudio light-themes linux-firmware
  myspell-en-gb myspell-en-za nautilus-data nautilus nvidia-current-modaliases
  obexd-client pm-utils-powersave-policy poppler-utils python-cupshelpers
  python-farsight python-papyon ubuntuone-client-gnome ubuntuone-client
  python-ubuntuone-client liblircclient0 rhythmbox-plugins
  rhythmbox-plugin-cdrecorder rhythmbox smbclient samba-common
  samba-common-bin simple-scan software-center ssh-askpass-gnome
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev telepathy-butterfly tomboy totem-plugins
  totem-mozilla totem-common totem transmission-gtk transmission-common udisks
  unattended-upgrades vinagre xserver-common xserver-xorg-core
  fglrx-modaliases indicator-sound libglu1-mesa
Install these packages without verification [y/N]? Y
 Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main fglrx-modaliases 2:8.723.1-0ubuntu4
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main indicator-sound 0.2.3-0ubuntu1
  Unable to connect to gb.archive.ubuntu.com:http:
Err http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main libglu1-mesa 7.7.1-1ubuntu3
  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.11.1-0ubuntu7.2_i386.deb  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (113: No route to host)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.11.1-0ubuntu7.2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i686_2.11.1-0ubuntu7.2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-dev-bin_2.11.1-0ubuntu7.2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.11.1-0ubuntu7.2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010k-0ubuntu0.10.04_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.98-1ubuntu7_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.98-1ubuntu7_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_10.04+20100714_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_10.04+20100714_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_10.04+20100714_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_10.04+20100714_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.25.3ubuntu9.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.21-0ubuntu5.3_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.15_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_0.6.5-7_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/ureadahead_0.100.0-4.1.2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.24.1-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libu/libusb/libusb-0.1-4_0.1.12-14ubuntu0.2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.25.3ubuntu9.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.7.94.2ubuntu6.2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/atk1.0/libatk1.0-0_1.30.0-0ubuntu2.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail-common_2.20.1-0ubuntu2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail18_2.20.1-0ubuntu2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.20.1-0ubuntu2_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.20.1-0ubuntu2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.20.1-0ubuntu2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.63.1ubuntu7_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector_0.5.8_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-common_0.5.8_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_5.3p1-3ubuntu4_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/parted/libparted0debian1_2.2-5ubuntu5.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/parted/parted_2.2-5ubuntu5.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.134.10_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.134.10_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/acpid/acpid_1.0.10-5ubuntu2.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pm-utils/pm-utils_1.3.0-1ubuntu2_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/acpi-support/acpi-support_0.136.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-partner/app-install-data-partner_12.10.04.3_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/at-spi/python-pyatspi_1.30.1-0ubuntu1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/at-spi/libatspi1.0-0_1.30.1-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/at-spi/at-spi_1.30.1-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.20.1-3ubuntu6_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libd/libdbusmenu/libdbusmenu-glib1_0.2.9-0ubuntu3.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/brasero/brasero-common_2.30.2-0ubuntu1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/brasero/libbrasero-media0_2.30.2-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.30.1-0ubuntu1.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/libgvfscommon0_1.6.1-0ubuntu1build1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-fuse_1.6.1-0ubuntu1build1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-bin_1.6.1-0ubuntu1build1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libgp11-0_2.92.92.is.2.30.3-0ubuntu1.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libgcr0_2.92.92.is.2.30.3-0ubuntu1.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgnome-keyring/libgnome-keyring0_2.30.1-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_2.92.92.is.2.30.3-0ubuntu1.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.4.7~dfsg-1ubuntu3.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.7~dfsg-1ubuntu3.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup2.4-1_2.30.2-0ubuntu0.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup-gnome2.4-1_2.30.2-0ubuntu0.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-backends_1.6.1-0ubuntu1build1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs_1.6.1-0ubuntu1build1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/brasero/brasero_2.30.2-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/byobu/byobu_2.68-0ubuntu1.1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2-17_2.30.2-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-11_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-14_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_2.30.1-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/capplets-data_2.30.1-0ubuntu1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/libgnome-window-settings1_2.30.1-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomekbd/libgnomekbd-common_2.30.2-0ubuntu0.1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomekbd/libgnomekbd4_2.30.2-0ubuntu0.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libr/librsvg/librsvg2-common_2.26.3-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libr/librsvg/librsvg2-2_2.26.3-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libn/libnotify/libnotify1_0.4.5-1ubuntu4_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_2.30.1-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.30.2-0ubuntu1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.30.2-0ubuntu1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-system-service/ubuntu-system-service_0.1.20.1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtag1c2a_1.6.3-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtag1-vanilla_1.6.3-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-plugins-good_0.10.21-1ubuntu3_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/farsight2/libgstfarsight0.10-0_0.0.17-2ubuntu2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.30.2-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.30.2-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.30.2-0ubuntu1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevdocument2_2.30.3-0ubuntu1.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevview2_2.30.3-0ubuntu1.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler5_0.12.4-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib4_0.12.4-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.30.3-0ubuntu1.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebackend1.2-0_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_2.28.3.1-0ubuntu5_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_2.28.3.1-0ubuntu5_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.28.3-0ubuntu10_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.28.3-0ubuntu10_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.28.3-0ubuntu10_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_7.7.1-1ubuntu3_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_7.7.1-1ubuntu3_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/f-spot/f-spot_0.6.1.5-2ubuntu7_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/file-roller/file-roller_2.30.1.1-0ubuntu2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.30.2-0ubuntu0.2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.30.2.is.2.30.0-0ubuntu3_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gtksourceview2/libgtksourceview2.0-common_2.10.4-0ubuntu1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gtksourceview2/libgtksourceview2.0-0_2.10.4-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit-common_2.30.3-0ubuntu0.1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/pygtksourceview/python-gtksourceview2_2.10.1-0ubuntu1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit_2.30.3-0ubuntu0.1_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-orca/gnome-orca_2.30.2-0ubuntu1_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.30.2-0ubuntu0.2_all.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.30.2-0ubuntu0.2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_2.30.0-0ubuntu2_i386.deb  Unable to connect to gb.archive.ubuntu.com:http:
```

---

### Post by sataris on 2010-08-24
I know that in a lot of cases VM os's will not utilize wireless adapters. This could be an issue, after having thought it over. 
 
For the OP and second poster saying they're having problems are you using Ethernet or Wifi?
 
If you are using wifi, and have a router you can hardline into, plug it in, and ensure the VM software is configured to allow ubuntu to utilize the ethernet port.
 
If you are using Wifi, and can connect to network/etc (within the Ubuntu VM), check to make sure the virtual machine is not read only. Both should be options you can configure.

---

### Post by yeats on 2010-08-24
> Yes the internet connection is fine. As I have said it has already downloaded and installed several updates and I have no trouble using Firefox.

So what happens in the VM when you go to [http://gb.archive.ubuntu.com/](http://gb.archive.ubuntu.com/) from the web browser?

---

### Post by delboy41 on 2010-08-25
> **sataris said:**
> I know that in a lot of cases VM os's will not utilize wireless adapters. This could be an issue, after having thought it over. 
 
For the OP and second poster saying they're having problems are you using Ethernet or Wifi?
 
If you are using wifi, and have a router you can hardline into, plug it in, and ensure the VM software is configured to allow ubuntu to utilize the ethernet port.
 
If you are using Wifi, and can connect to network/etc (within the Ubuntu VM), check to make sure the virtual machine is not read only. Both should be options you can configure.
My internet connection is via wi-fi but since, as I said. I have already downloaded and installed several updates and Firefox works well, all from the same Ubuntu OS on the same PC can it really be the internet connection?

---

### Post by delboy41 on 2010-08-27
> **chrissharp123 said:**
> So what happens in the VM when you go to [http://gb.archive.ubuntu.com/](http://gb.archive.ubuntu.com/) from the web browser?
Chris,
In Firefox I can connect to http:[www.ubuntu.com](www.ubuntu.com) and happily browse the site but it fails to connect (time-out waiting for reply from the server) if I try to connect to [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com).

---

### Post by delboy41 on 2010-08-27
> **chrissharp123 said:**
> So what happens in the VM when you go to [http://gb.archive.ubuntu.com/](http://gb.archive.ubuntu.com/) from the web browser?
Chris,

If I leave out the gb and type in [http://archive.ubuntu.com](http://archive.ubuntu.com) I connect and can browse the folders.

---

### Post by delboy41 on 2010-08-27
Well!  I changed the software source for updates from GB to Main and the updates worked fine.  I am not sure if I can call this thread now solved because surely if you are in GB you should be able to update from the GB server.  Anyway since I now have a fully up to date version of Ubuntu 10.04 it is solves as far as I am concerned.

Thanks to everyone who has contributed and especially to Chris who made me think of changing the update server setting.

---

