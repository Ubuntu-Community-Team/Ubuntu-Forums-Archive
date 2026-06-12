---
title: "wireless help atheros 5007"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by coubury on 2008-12-08
I am following this guide to get my wireless card working

> For AMD64 Users

If you are using 64 bit version following this procedure

Blacklist the default driver

echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist

Download the 64 bit driver

wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

Extract driver using the following command

tar xvf ar5007eg-*.tar.gz

tar xvf ndiswrapper-newest.tar.gz

Ensure you have your kernel headers and the build essential package.

sudo aptitude update

sudo aptitude install linux-headers-$(uname -r) build-essential

Install ndisgtk

sudo apt-get install ndisgtk

Either use ndisgtk to install the driver or

sudo ndiswrapper -i net5211.inf

Load up ndiswrapper every time Linux is loaded

sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules

Restart your system using the following command

sudo reboot

Your card should have been detected and it should show available networks but if it does not, try

sudo iwlist scan



You can see a few errors


> currys@currys-laptop:~$ echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist
“blacklist ath_pci”
currys@currys-laptop:~$ wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
--14:09:54--  [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
           => `ar5007eg-64-0.2.tar.gz.4'
Resolving blakecmartin.googlepages.com... 209.85.173.118
Connecting to blakecmartin.googlepages.com|209.85.173.118|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 369,404 (361K) [application/octet-stream]

100%[====================================>] 369,404      188.62K/s             

14:09:56 (188.28 KB/s) - `ar5007eg-64-0.2.tar.gz.4' saved [369404/369404]

currys@currys-laptop:~$ tar xvf ar5007eg-*.tar.gz
ar5007eg-64-0.2/
ar5007eg-64-0.2/ar5007eg/
ar5007eg-64-0.2/ar5007eg/net5211.inf
ar5007eg-64-0.2/ar5007eg/net5211.cat
ar5007eg-64-0.2/ar5007eg/ar5211.sys
ar5007eg-64-0.2/README
[B]currys@currys-laptop:~$ tar xvf ndiswrapper-newest.tar.gz
tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now[/B]
currys@currys-laptop:~$ sudo aptitude update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
currys@currys-laptop:~$ sudo aptitude install linux-headers-$(uname -r) build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been automatically kept back:
  linux-headers-2.6.24-19 linux-restricted-modules-common 
The following packages have been kept back:
  alacarte anacron app-install-data-commercial apt apt-utils base-files 
  bind9-host compiz-fusion-plugins-main cupsys cupsys-bsd cupsys-client 
  cupsys-common dbus dbus-x11 deskbar-applet dnsutils eject eog evince 
  evolution evolution-common evolution-data-server 
  evolution-data-server-common evolution-exchange evolution-plugins firefox 
  firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support foo2zjs 
  gcalctool gdb gdm gnome-about gnome-cards-data gnome-desktop-data 
  gnome-games gnome-games-data gnome-panel gnome-panel-data 
  gnome-system-monitor grub gstreamer0.10-tools gtk2-engines 
  gtk2-engines-murrine gtk2-engines-pixbuf gtk2-engines-ubuntulooks 
  gtkhtml3.14 gvfs gvfs-backends gvfs-fuse hal hal-info hpijs hplip 
  hplip-data initramfs-tools iproute jockey-common jockey-gtk 
  language-pack-en language-pack-gnome-en libbind9-30 libcamel1.2-11 
  libcupsimage2 libcupsys2 libdbus-1-3 libebook1.2-9 libecal1.2-7 
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 
  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 
  libexif12 libfreetype6 libgdata-google1.2-1 libgdata1.2-1 libgksu2-0 
  libglib2.0-0 libglibmm-2.4-1c2a libgnome-desktop-2 libgnutls13 
  libgphoto2-2 libgphoto2-port0 libgstreamer0.10-0 libgtk2.0-0 
  libgtk2.0-bin libgtk2.0-common libgtkhtml3.14-19 libgtksourceview2.0-0 
  libgtksourceview2.0-common libgvfscommon0 libgweather-common libgweather1 
  libhal-storage1 libhal1 libisc32 libisccc30 libisccfg30 libldap-2.4-2 
  liblwres30 libnautilus-extension1 libnspr4-0d libnss3-1d 
  libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpcre3 
  libpoppler-glib2 libpoppler2 libpurple0 libsmbclient libsmbios1 
  libsnmp-base libsnmp15 libsoup2.4-1 libtiff4 libvorbis0a libvorbisenc2 
  libvorbisfile3 libwnck-common libwnck22 libxml2 libxml2-utils libxslt1.1 
  linux-generic linux-headers-generic linux-image-2.6.24-19-generic 
  linux-image-generic linux-restricted-modules-2.6.24-19-generic 
  linux-restricted-modules-generic login logrotate module-init-tools 
  nautilus nautilus-data nautilus-sendto openoffice.org-base-core 
  openoffice.org-calc openoffice.org-common openoffice.org-core 
  openoffice.org-draw openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-style-human openoffice.org-writer 
  passwd pciutils pidgin pidgin-data poppler-utils procps python-apt 
  python-gobject python-gtkhtml2 python-libxml2 python-uno python2.5 
  python2.5-minimal rdesktop samba-common smbclient ssl-cert sudo 
  thunderbird-locale-en-gb ttf-opensymbol tzdata ufw update-manager 
  update-manager-core update-notifier update-notifier-common xkb-data 
  xserver-xorg-video-intel xsltproc xulrunner-1.9 
  xulrunner-1.9-gnome-support yelp 
0 packages upgraded, 0 newly installed, 0 to remove and 183 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
currys@currys-laptop:~$ sudo apt-get install ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndisgtk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 183 not upgraded.
[B]currys@currys-laptop:~$ sudo ndiswrapper -i net5211.inf
driver net5211 is already installed[/B]
currys@currys-laptop:~$ sudo modprobe ndiswrapper
WARNING: /etc/modprobe.d/blacklist line 40: ignoring bad line starting with '“blacklist'
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with '“blacklist'
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with '“blacklist'
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with '“blacklist'
currys@currys-laptop:~$ echo “ndiswrapper” | sudo tee -a /etc/modules
“ndiswrapper”
[B]currys@currys-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.[/B]

currys@currys-laptop:~$ 







can anyone help please?

---

### Post by 2hot6ft2 on 2008-12-08
A few basics first. What version of ubuntu? What kernel are you using?

The 5007 uses the same driver as the 5009 which I have and mines working without editing anything. But it works better with an older kernel and you can see my specs in my sig for the laptop. The 2.26.7-7 works and the 2.26.7-9 keeps dropping the connection.

---

### Post by lovelyvik293 on 2008-12-08
> 
currys@currys-laptop:~$ tar xvf ndiswrapper-newest.tar.gz
tar: ndiswrapper-newest.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

There is no ndiswrapper file at your /home/curry folder,thats why it showing this error.

---

### Post by coubury on 2008-12-08
> **2hot6ft2 said:**
> A few basics first. What version of ubuntu? What kernel are you using?

The 5007 uses the same driver as the 5009 which I have and mines working without editing anything. But it works better with an older kernel and you can see my specs in my sig for the laptop. The 2.26.7-7 works and the 2.26.7-9 keeps dropping the connection.

Using the new version of Ubuntu 8.10 is it?



how do i fins out what Kernal?


how did you install the 5009 version?


lovelyvik293 how do i put it in that folder?

---

### Post by 2hot6ft2 on 2008-12-08
Applications>System Tools>sysinfo then system and it will show you.

I didn't have to do anything.

---

### Post by lovelyvik293 on 2008-12-08
When you have to extract a file it must be there and your error says that it is not present in that folder.just copy it and that error will not come this time.

---

### Post by 2hot6ft2 on 2008-12-08
UUE 2.0 is like Ubuntu 8.10 it just has more built into it.

You may need to enable backports to get your kernel up to a more recent version which would be done in a terminal with this.
sudo apt-get install linux-backports-modules-intrepid-generic

---

### Post by 2hot6ft2 on 2008-12-08
And here's my /etc/modprobe.d/madwifi contents

> ## ath5k (mac80211)
blacklist ath5k

## madwifi (non-free)
blacklist ath_hal
#blacklist ath_pci
#blacklist ath_rate_amrr
#blacklist ath_rate_onoe
#blacklist ath_rate_sample
#blacklist wlan
#blacklist wlan_acl
#blacklist wlan_ccmp
#blacklist wlan_scan_ap
#blacklist wlan_scan_sta
#blacklist wlan_tkip
#blacklist wlan_wep
#blacklist wlan_xauth

ath5k is blacklisted since it has ath9k, the 5009 is a mini pci so ath_pci is not

and my /etc/modprobe.d/blacklist file

> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

for reference. And I am posting this on the laptop using wifi.

---

### Post by coubury on 2008-12-08
what should i do with that?

---

### Post by 2hot6ft2 on 2008-12-08
If you've made changes to them. This gives you an example of what works. It's working so yours shouldn't have anything blacklisted that mine doesn't and should have the same ones blacklisted that mine does.

Did you find out what kernel you're using?
Screenshot attached of my Sysinfo

---

### Post by acreech on 2008-12-08
This thread tells how I get my atheros 5007 wireless netwrok card working. 


[http://ubuntuforums.org/showthread.php?p=6201697#post6201697]("http://ubuntuforums.org/showthread.php?p=6201697#post6201697")

You might try this. It works for me in Hardy and Intrepid. 

I have an Acer Aspire 7520 Laptop

---

