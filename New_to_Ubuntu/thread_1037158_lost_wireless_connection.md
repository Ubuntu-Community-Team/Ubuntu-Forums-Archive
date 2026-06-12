---
title: "lost wireless connection"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by newbie_sarah_xx on 2009-01-11
hiya, 

i have a dell mini 9 netbook which runs on ubuntu 8.04. i had a connection to my router since i got it and now its gone, i've been on system>administration>network and cant seem to get it back, the wireless connection doesn't even appear in the box. 

any help would be much appreciated

ta

:confused:

---

### Post by jimmy the saint on 2009-01-11
please open a terminal and type in
```
lspci
```
and post the results.

---

### Post by newbie_sarah_xx on 2009-01-11
hiya this is the outcome of that command:

daz@daz:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

---

### Post by jimmy the saint on 2009-01-11
Hmm.  there is a community page for the mini 9.  It has a section for solving common issues with wireless.  I would try those solutions, then post back here if none of them work.  Below is a link and the section is titled "Connecting to a wireless router"
[https://help.ubuntu.com/community/DellMini9#Bluetooth%20/%20WiFi%20switch](https://help.ubuntu.com/community/DellMini9#Bluetooth%20/%20WiFi%20switch)

Let us know if there is a good solution for you there.  I would start with the disable/enable restricted driver method and see if that works.

---

### Post by newbie_sarah_xx on 2009-01-11
i have already tried that an it doesn't work for me as my netbook wont even recognise on the network manager that there is a wireless connection avaliable :confused:

---

### Post by jimmy the saint on 2009-01-11
You went to the restricted drivers app and completely disabled the restricted driver, restarted, then re-enabled (installed) the driver again? 
None of this takes place in the network manager app.  You have to go to 
system>administration>Hardware Drivers in order to do this.

---

### Post by ugm6hr on 2009-01-11
```
lsmod|grep wl
```
Does this return anything?

---

### Post by newbie_sarah_xx on 2009-01-11
yes i have tried this before, i lfound that page before i come here asking for help because nothing seems to be working for me :confused:

---

### Post by newbie_sarah_xx on 2009-01-11
hi, lsmod|grep wl returns nothing

---

### Post by ugm6hr on 2009-01-11
> **newbie_sarah_xx said:**
> hi, lsmod|grep wl returns nothing

Thats the problem then.

The driver is not loaded.

1 second while I double-check how to sort this out.

EDIT:
Does this return "wl" anywhere?
```
cat /etc/modules
```

If no - try this:
```
echo wl | sudo tee -a /etc/modules
```

Then reboot.  Hopefully you haven't messed around with too many of the default settings trying to get this to work.

---

### Post by newbie_sarah_xx on 2009-01-11
ok i'll try now, how do i reboot is it the same as restarting it? i am completly numb to things like this

---

### Post by ugm6hr on 2009-01-11
> **newbie_sarah_xx said:**
> ok i'll try now, how do i reboot is it the same as restarting it? i am completly numb to things like this

Yes. Restart / Turn off etc.

---

### Post by newbie_sarah_xx on 2009-01-11
it doesn't seem to have worked, is there any way i can just like reset everything back to default?

---

### Post by newbie_sarah_xx on 2009-01-11
i forgot to mention i lost my connection whilst it was installing updates and now since it wont recognise the router

---

### Post by ugm6hr on 2009-01-11
> **newbie_sarah_xx said:**
> i forgot to mention i lost my connection whilst it was installing updates and now since it wont recognise the router

Can you plug in with ethernet cable?

Then just complete the updates:
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

Then reboot again.

---

### Post by newbie_sarah_xx on 2009-01-11
hi, just tried connecting the netbook with erthernet cable and still cant access internet it comes up address not found

---

### Post by ugm6hr on 2009-01-11
> **newbie_sarah_xx said:**
> hi, just tried connecting the netbook with erthernet cable and still cant access internet it comes up address not found

Did you try any of the commands above?  dpkg does not require internet.

If that doesn't do anything, give the output from:
```
ifconfig
lshw -class network
```

---

### Post by newbie_sarah_xx on 2009-01-11
i still have nothing

---

### Post by ugm6hr on 2009-01-11
> **newbie_sarah_xx said:**
> i still have nothing

I'm afraid you will have to give the output from those commands.  Without it, I have no way of knowing whats going on.

---

### Post by newbie_sarah_xx on 2009-01-11
this is the outcome i got of them 2:

Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main libgweather1 2.22.3-0ubuntu2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main gnome-panel 1:2.22.2-0ubuntu1.1netbook2belmont1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main libglibmm-2.4-1c2a 2.16.4-0ubuntu1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main gnome-system-monitor 2.22.3-0ubuntu2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main gnome-system-tools 2.22.0-0ubuntu9usg3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main grub 0.97-29ubuntu21netbook2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main gstreamer0.10-alsa 0.10.18-3netbook2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main gstreamer0.10-gnomevfs 0.10.18-3netbook2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main gstreamer0.10-tools 0.10.18-4ubuntu1netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main gstreamer0.10-plugins-base-apps 0.10.18-3netbook2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main gtk2-engines 1:2.14.3-0ubuntu2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main libgvfscommon0 0.2.5-0ubuntu2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main gvfs-backends 0.2.5-0ubuntu2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main gvfs 0.2.5-0ubuntu2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main gvfs-fuse 0.2.5-0ubuntu2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main libck-connector0 0.2.3-3ubuntu5belmont1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe libclutter-0.6-0 0.6.0-2netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main libdrm2 2.3.0.16-0ubuntu2~804um3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main libgksu2-0 2.0.5-1ubuntu5.2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main libgtksourceview2.0-common 2.2.2-0ubuntu1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main libgtksourceview2.0-0 2.2.2-0ubuntu1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main pidgin-data 1:2.4.3-0ubuntu1~hardy1netbook3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main libpurple0 1:2.4.3-0ubuntu1~hardy1netbook3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main libusplash0 0.5.19netbook3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted linux-restricted-modules-common 2.6.24.13-19.45netbook5
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted linux-restricted-modules-2.6.24-19-lpia 2.6.24.13-19.45netbook5
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main nautilus-sendto 0.13.2-0ubuntu2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main network-manager-gnome 0.6.6-0ubuntu3usg6
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main pidgin 1:2.4.3-0ubuntu1~hardy1netbook3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main python-gobject 2.14.2-0ubuntu1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main rhythmbox 0.11.5-0ubuntu8netbook1belmont3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main system-config-printer-common 0.7.81+svn1976-0ubuntu9netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main system-config-printer-gnome 0.7.81+svn1976-0ubuntu9netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main totem-plugins 2.22.1-0ubuntu2netbook0belmont3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main totem-common 2.22.1-0ubuntu2netbook0belmont3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main totem-gstreamer 2.22.1-0ubuntu2netbook0belmont3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main totem 2.22.1-0ubuntu2netbook0belmont3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main totem-mozilla 2.22.1-0ubuntu2netbook0belmont3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main ubuntu-gdm-themes 0.29usg6
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main lsb-release 3.2-4ubuntu1netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main update-manager 1:0.87.30netbook0belmont2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main update-manager-core 1:0.87.30netbook0belmont2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main update-notifier-common 0.70.9netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main update-notifier 0.70.9netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main usplash 0.5.19netbook3
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main usplash-theme-ubuntu 0.18ubuntu0netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe webfav 1.0ubuntu5
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main xdg-user-dirs 0.10-1ubuntu1netbook0belmont2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main xscreensaver-data 5.04-4ubuntu1netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main xscreensaver-gl 5.04-4ubuntu1netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main xserver-xorg-video-intel 2:2.2.1-1ubuntu13.6
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main xserver-xorg-video-psb 0.16.0+repack-0ubuntu1~804um5netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main yelp 2.22.1-0ubuntu2.8.04.3.1netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe belmont-config-travel 0.42
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main belocs-locales-bin 2.4-2.2ubuntu7netbook1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe desktop-switcher 0.3.0
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe language-installer 0.1-0netbook17
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe maximus 0.4.2netbook0belmont1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main oem-config 1.37.2netbook9belmont2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main oem-config-gtk 1.37.2netbook9belmont2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe ume-config-belmont 0.101.4
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main libpoppler2 0.6.4-1ubuntu3.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main libpoppler-glib2 0.6.4-1ubuntu3.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main libavutil1d 3:0.cvs20070307-5ubuntu7.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main libavcodec1d 3:0.cvs20070307-5ubuntu7.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main libpostproc1d 3:0.cvs20070307-5ubuntu7.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe libxine1-ffmpeg 1.1.11.1-1ubuntu3.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main libxine1 1.1.11.1-1ubuntu3.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main libxine1-x 1.1.11.1-1ubuntu3.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main libxine1-misc-plugins 1.1.11.1-1ubuntu3.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main libxine1-console 1.1.11.1-1ubuntu3.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main libxine1-bin 1.1.11.1-1ubuntu3.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe libxine1-plugins 1.1.11.1-1ubuntu3.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main libxslt1.1 1.1.22-1ubuntu1.2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main poppler-utils 0.6.4-1ubuntu3.1
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Err [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main xsltproc 1.1.22-1ubuntu1.2
  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-plugins-base_0.10.18-3netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-plugins-base_0.10.18-3netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-x_0.10.18-3netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-x_0.10.18-3netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.5_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.5_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-9_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-9_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.0.3-0ubuntu0.8.04.4_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.0.3-0ubuntu0.8.04.4_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-11_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-11_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/esound-common_0.2.40-0ubuntu1~netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/esound-common_0.2.40-0ubuntu1~netbook1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libgnome2-0_2.22.0-0ubuntu1netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libgnome2-0_2.22.0-0ubuntu1netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libesd-alsa0_0.2.40-0ubuntu1~netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libesd-alsa0_0.2.40-0ubuntu1~netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libgnome2-common_2.22.0-0ubuntu1netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libgnome2-common_2.22.0-0ubuntu1netbook1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/cheese_2.22.3-0ubuntu1usg7_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/cheese_2.22.3-0ubuntu1usg7_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/dbus-x11_1.1.20-1ubuntu3.1netbook0belmont1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/dbus-x11_1.1.20-1ubuntu3.1netbook0belmont1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2_2.22.3-0ubuntu1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2_2.22.3-0ubuntu1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.22.3-0ubuntu1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.22.3-0ubuntu1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/desktop-file-utils_0.15-1ubuntu4netbook0belmont1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/desktop-file-utils_0.15-1ubuntu4netbook0belmont1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/eog/eog_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/eog/eog_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_2.22.3-0ubuntu2_all.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_2.22.3-0ubuntu2_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/libs/libsoup2.4/libsoup2.4-1_2.4.1-1ubuntu1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/libs/libsoup2.4/libsoup2.4-1_2.4.1-1ubuntu1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/evolution_2.22.3.1-0ubuntu1netbook8_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/evolution_2.22.3.1-0ubuntu1netbook8_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/evolution-common_2.22.3.1-0ubuntu1netbook8_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/evolution-common_2.22.3.1-0ubuntu1netbook8_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gtkhtml3.14/libgtkhtml3.14-19_3.18.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gtkhtml3.14/libgtkhtml3.14-19_3.18.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gtkhtml3.14/gtkhtml3.14_3.18.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gtkhtml3.14/gtkhtml3.14_3.18.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-exchange/evolution-exchange_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/e/evolution-exchange/evolution-exchange_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/evolution-plugins_2.22.3.1-0ubuntu1netbook8_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/evolution-plugins_2.22.3.1-0ubuntu1netbook8_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/f-spot_0.4.3.1-0ubuntu1netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/f-spot_0.4.3.1-0ubuntu1netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xulrunner-1.9-gnome-support_1.9.0.5+nobinonly-0ubuntu0.8.04.1netbook0build1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xulrunner-1.9-gnome-support_1.9.0.5+nobinonly-0ubuntu0.8.04.1netbook0build1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xulrunner-1.9_1.9.0.5+nobinonly-0ubuntu0.8.04.1netbook0build1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xulrunner-1.9_1.9.0.5+nobinonly-0ubuntu0.8.04.1netbook0build1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/firefox-3.0-gnome-support_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/firefox-3.0-gnome-support_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/firefox-3.0_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/firefox-3.0_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/firefox_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/firefox_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/firefox-gnome-support_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/firefox-gnome-support_3.0.5+nobinonly+nb1-0ubuntu0.8.04.1netbook1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/multiverse/binary-lpia/flashplugin-nonfree_9.0.152.0ubuntu0netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/multiverse/binary-lpia/flashplugin-nonfree_9.0.152.0ubuntu0netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gcalctool_5.22.3-0ubuntu0.1netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gcalctool_5.22.3-0ubuntu0.1netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gdebi_0.3.8netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gdebi_0.3.8netbook1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gdebi-core_0.3.8netbook1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/hal-info_20080508+git20080601-0ubuntu0.8.04netbook1belmont1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/hal-info_20080508+git20080601-0ubuntu0.8.04netbook1belmont1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libhal-storage1_0.5.11~rc2-1ubuntu8.2netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libhal-storage1_0.5.11~rc2-1ubuntu8.2netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libsmbios1_0.13.10-1ubuntu1.1netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libsmbios1_0.13.10-1ubuntu1.1netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/pm-utils_0.99.2-3ubuntu10belmont2_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/pm-utils_0.99.2-3ubuntu10belmont2_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/hal_0.5.11~rc2-1ubuntu8.2netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/hal_0.5.11~rc2-1ubuntu8.2netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libpanel-applet2-0_2.22.2-0ubuntu1.1netbook2belmont1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libpanel-applet2-0_2.22.2-0ubuntu1.1netbook2belmont1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/libw/libwnck/libwnck-common_2.22.3-0ubuntu1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/libw/libwnck/libwnck-common_2.22.3-0ubuntu1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/libw/libwnck/libwnck22_2.22.3-0ubuntu1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/libw/libwnck/libwnck22_2.22.3-0ubuntu1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-power-manager_2.22.1-1ubuntu4usg2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-power-manager_2.22.1-1ubuntu4usg2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gdm_2.20.7-0ubuntu1.1netbook3belmont2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gdm_2.20.7-0ubuntu1.1netbook3belmont2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-session_2.22.1.1-0ubuntu2netbook1belmont2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-session_2.22.1.1-0ubuntu2netbook1belmont2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/metacity-common_2.22.0-0ubuntu4.netbook2_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/metacity-common_2.22.0-0ubuntu4.netbook2_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libmetacity0_2.22.0-0ubuntu4.netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libmetacity0_2.22.0-0ubuntu4.netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/metacity_2.22.0-0ubuntu4.netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/metacity_2.22.0-0ubuntu4.netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/k/kdebase/konsole_3.5.9-0ubuntu7.3_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/k/kdebase/konsole_3.5.9-0ubuntu7.3_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libgimp2.0_2.4.5-1ubuntu2netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libgimp2.0_2.4.5-1ubuntu2netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gimp-python_2.4.5-1ubuntu2netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gimp-python_2.4.5-1ubuntu2netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gimp-gnomevfs_2.4.5-1ubuntu2netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gimp-gnomevfs_2.4.5-1ubuntu2netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gimp-data_2.4.5-1ubuntu2netbook2_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gimp-data_2.4.5-1ubuntu2netbook2_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6.4-1ubuntu3.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6.4-1ubuntu3.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6.4-1ubuntu3.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6.4-1ubuntu3.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gimp_2.4.5-1ubuntu2netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gimp_2.4.5-1ubuntu2netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.22.3-0ubuntu1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.22.3-0ubuntu1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.22.3-0ubuntu1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.22.3-0ubuntu1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-app-install_0.5.2.8-0ubuntu1netbook0belmont1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-app-install_0.5.2.8-0ubuntu1netbook0belmont1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-cards-data_2.22.3-0ubuntu2netbook3_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-cards-data_2.22.3-0ubuntu2netbook3_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-control-center_2.22.1-0ubuntu4.1usg4_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-control-center_2.22.1-0ubuntu4.1usg4_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libgnome-window-settings1_2.22.1-0ubuntu4.1usg4_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libgnome-window-settings1_2.22.1-0ubuntu4.1usg4_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-games-data_2.22.3-0ubuntu2netbook3_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-games-data_2.22.3-0ubuntu2netbook3_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-games_2.22.3-0ubuntu2netbook3_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-games_2.22.3-0ubuntu2netbook3_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-panel-data_2.22.2-0ubuntu1.1netbook2belmont1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-panel-data_2.22.2-0ubuntu1.1netbook2belmont1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/libg/libgweather/libgweather-common_2.22.3-0ubuntu2_all.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/libg/libgweather/libgweather-common_2.22.3-0ubuntu2_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/libg/libgweather/libgweather1_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/libg/libgweather/libgweather1_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-panel_2.22.2-0ubuntu1.1netbook2belmont1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-panel_2.22.2-0ubuntu1.1netbook2belmont1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1c2a_2.16.4-0ubuntu1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1c2a_2.16.4-0ubuntu1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gnome-system-monitor/gnome-system-monitor_2.22.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gnome-system-monitor/gnome-system-monitor_2.22.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-system-tools_2.22.0-0ubuntu9usg3_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gnome-system-tools_2.22.0-0ubuntu9usg3_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/grub_0.97-29ubuntu21netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/grub_0.97-29ubuntu21netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-alsa_0.10.18-3netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-alsa_0.10.18-3netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-gnomevfs_0.10.18-3netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-gnomevfs_0.10.18-3netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-tools_0.10.18-4ubuntu1netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-tools_0.10.18-4ubuntu1netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-plugins-base-apps_0.10.18-3netbook2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/gstreamer0.10-plugins-base-apps_0.10.18-3netbook2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines_2.14.3-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines_2.14.3-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gvfs/libgvfscommon0_0.2.5-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gvfs/libgvfscommon0_0.2.5-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gvfs/gvfs-backends_0.2.5-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gvfs/gvfs-backends_0.2.5-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gvfs/gvfs_0.2.5-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gvfs/gvfs_0.2.5-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gvfs/gvfs-fuse_0.2.5-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gvfs/gvfs-fuse_0.2.5-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/f/ffmpeg/libavutil1d_0.cvs20070307-5ubuntu7.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/f/ffmpeg/libavcodec1d_0.cvs20070307-5ubuntu7.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libck-connector0_0.2.3-3ubuntu5belmont1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libck-connector0_0.2.3-3ubuntu5belmont1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/libclutter-0.6-0_0.6.0-2netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/libclutter-0.6-0_0.6.0-2netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libdrm2_2.3.0.16-0ubuntu2~804um3_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libdrm2_2.3.0.16-0ubuntu2~804um3_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/libg/libgksu/libgksu2-0_2.0.5-1ubuntu5.2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/libg/libgksu/libgksu2-0_2.0.5-1ubuntu5.2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gtksourceview2/libgtksourceview2.0-common_2.2.2-0ubuntu1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gtksourceview2/libgtksourceview2.0-common_2.2.2-0ubuntu1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gtksourceview2/libgtksourceview2.0-0_2.2.2-0ubuntu1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/g/gtksourceview2/libgtksourceview2.0-0_2.2.2-0ubuntu1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/f/ffmpeg/libpostproc1d_0.cvs20070307-5ubuntu7.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/pidgin-data_2.4.3-0ubuntu1~hardy1netbook3_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/pidgin-data_2.4.3-0ubuntu1~hardy1netbook3_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libpurple0_2.4.3-0ubuntu1~hardy1netbook3_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libpurple0_2.4.3-0ubuntu1~hardy1netbook3_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libusplash0_0.5.19netbook3_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/libusplash0_0.5.19netbook3_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/universe/x/xine-lib/libxine1-ffmpeg_1.1.11.1-1ubuntu3.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/universe/x/xine-lib/libxine1-ffmpeg_1.1.11.1-1ubuntu3.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.11.1-1ubuntu3.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xine-lib/libxine1_1.1.11.1-1ubuntu3.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.11.1-1ubuntu3.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xine-lib/libxine1-x_1.1.11.1-1ubuntu3.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xine-lib/libxine1-misc-plugins_1.1.11.1-1ubuntu3.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xine-lib/libxine1-misc-plugins_1.1.11.1-1ubuntu3.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.11.1-1ubuntu3.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xine-lib/libxine1-console_1.1.11.1-1ubuntu3.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.11.1-1ubuntu3.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xine-lib/libxine1-bin_1.1.11.1-1ubuntu3.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/universe/x/xine-lib/libxine1-plugins_1.1.11.1-1ubuntu3.1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/universe/x/xine-lib/libxine1-plugins_1.1.11.1-1ubuntu3.1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.22-1ubuntu1.2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/libx/libxslt/libxslt1.1_1.1.22-1ubuntu1.2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/binary-lpia/linux-restricted-modules-common_2.6.24.13-19.45netbook5_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/binary-lpia/linux-restricted-modules-common_2.6.24.13-19.45netbook5_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/binary-lpia/linux-restricted-modules-2.6.24-19-lpia_2.6.24.13-19.45netbook5_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/restricted/binary-lpia/linux-restricted-modules-2.6.24-19-lpia_2.6.24.13-19.45netbook5_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/n/nautilus-sendto/nautilus-sendto_0.13.2-0ubuntu2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/n/nautilus-sendto/nautilus-sendto_0.13.2-0ubuntu2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/network-manager-gnome_0.6.6-0ubuntu3usg6_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/network-manager-gnome_0.6.6-0ubuntu3usg6_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/pidgin_2.4.3-0ubuntu1~hardy1netbook3_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/pidgin_2.4.3-0ubuntu1~hardy1netbook3_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6.4-1ubuntu3.1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6.4-1ubuntu3.1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/p/pygobject/python-gobject_2.14.2-0ubuntu1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/p/pygobject/python-gobject_2.14.2-0ubuntu1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/rhythmbox_0.11.5-0ubuntu8netbook1belmont3_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/rhythmbox_0.11.5-0ubuntu8netbook1belmont3_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/system-config-printer-common_0.7.81+svn1976-0ubuntu9netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/system-config-printer-common_0.7.81+svn1976-0ubuntu9netbook1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/system-config-printer-gnome_0.7.81+svn1976-0ubuntu9netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/system-config-printer-gnome_0.7.81+svn1976-0ubuntu9netbook1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/totem-plugins_2.22.1-0ubuntu2netbook0belmont3_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/totem-plugins_2.22.1-0ubuntu2netbook0belmont3_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/totem-common_2.22.1-0ubuntu2netbook0belmont3_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/totem-common_2.22.1-0ubuntu2netbook0belmont3_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/totem-gstreamer_2.22.1-0ubuntu2netbook0belmont3_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/totem-gstreamer_2.22.1-0ubuntu2netbook0belmont3_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/totem_2.22.1-0ubuntu2netbook0belmont3_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/totem_2.22.1-0ubuntu2netbook0belmont3_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/totem-mozilla_2.22.1-0ubuntu2netbook0belmont3_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/totem-mozilla_2.22.1-0ubuntu2netbook0belmont3_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/ubuntu-gdm-themes_0.29usg6_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/ubuntu-gdm-themes_0.29usg6_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/lsb-release_3.2-4ubuntu1netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/lsb-release_3.2-4ubuntu1netbook1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/update-manager_0.87.30netbook0belmont2_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/update-manager_0.87.30netbook0belmont2_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/update-manager-core_0.87.30netbook0belmont2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/update-manager-core_0.87.30netbook0belmont2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/update-notifier-common_0.70.9netbook1_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/update-notifier-common_0.70.9netbook1_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/update-notifier_0.70.9netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/update-notifier_0.70.9netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/usplash_0.5.19netbook3_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/usplash_0.5.19netbook3_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/usplash-theme-ubuntu_0.18ubuntu0netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/usplash-theme-ubuntu_0.18ubuntu0netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/webfav_1.0ubuntu5_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/webfav_1.0ubuntu5_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xdg-user-dirs_0.10-1ubuntu1netbook0belmont2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xdg-user-dirs_0.10-1ubuntu1netbook0belmont2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xscreensaver-data_5.04-4ubuntu1netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xscreensaver-data_5.04-4ubuntu1netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xscreensaver-gl_5.04-4ubuntu1netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xscreensaver-gl_5.04-4ubuntu1netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.2.1-1ubuntu13.6_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.2.1-1ubuntu13.6_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xserver-xorg-video-psb_0.16.0+repack-0ubuntu1~804um5netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/xserver-xorg-video-psb_0.16.0+repack-0ubuntu1~804um5netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/pool/main/libx/libxslt/xsltproc_1.1.22-1ubuntu1.2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/pool/main/libx/libxslt/xsltproc_1.1.22-1ubuntu1.2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/yelp_2.22.1-0ubuntu2.8.04.3.1netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/yelp_2.22.1-0ubuntu2.8.04.3.1netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/belmont-config-travel_0.42_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/belmont-config-travel_0.42_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/belocs-locales-bin_2.4-2.2ubuntu7netbook1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/belocs-locales-bin_2.4-2.2ubuntu7netbook1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/desktop-switcher_0.3.0_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/desktop-switcher_0.3.0_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/language-installer_0.1-0netbook17_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/language-installer_0.1-0netbook17_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/maximus_0.4.2netbook0belmont1_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/maximus_0.4.2netbook0belmont1_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/oem-config_1.37.2netbook9belmont2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/oem-config_1.37.2netbook9belmont2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/oem-config-gtk_1.37.2netbook9belmont2_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/main/binary-lpia/oem-config-gtk_1.37.2netbook9belmont2_lpia.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
Failed to fetch [http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/ume-config-belmont_0.101.4_all.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-dell-mini/universe/binary-lpia/ume-config-belmont_0.101.4_all.deb)  Could not resolve â€˜dell-mini.archive.canonical.comâ€™
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
daz@daz:~$ --fix-missing
bash: --fix-missing: command not found
daz@daz:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
daz@daz:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:c7:f2:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3383906856 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62700 (61.2 KB)  TX bytes:62700 (61.2 KB)

daz@daz:~$ lshw -class network
bash: lshw: command not found
daz@daz:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:c7:f2:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2114540064 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62700 (61.2 KB)  TX bytes:62700 (61.2 KB)

daz@daz:~$ lshw -class network

---

### Post by ugm6hr on 2009-01-11
Does this return anything?
```
lsmod | grep r8169
```

If nothing - try this:
```
sudo modprobe r8169
```

And presumably that ifconfig was done with the ethernet plugged in?

---

### Post by ugm6hr on 2009-01-11
Looking through your apt-get update response, it appears that some of the updates have downloaded, although I'm unclear on whether they installed or not.

Try the following, and post the results:
```
sudo dpkg --configure -a
sudo apt-get install -f
ls /var/cache/apt/archives/
```

---

### Post by newbie_sarah_xx on 2009-01-11
i got 

daz@daz:~$ lsmod | grep r8169
r8169                  33156  0 
daz@daz:~$ 
 
and yes i used erthernet cable for iconfig command

---

### Post by ugm6hr on 2009-01-11
> **newbie_sarah_xx said:**
> daz@daz:~$ lsmod | grep r8169
r8169                  33156  0 

At least the ethernet driver is installed.

Not sure why it hasn't automatically picked up the network.  Try (0=zero):
```
sudo ifdown eth0
sudo ifup eth0
```

With ethernet plugged in

---

### Post by newbie_sarah_xx on 2009-01-11
this is what i got off them other commands

daz@daz:~$ lsmod | grep r8169
r8169                  33156  0 
daz@daz:~$ sudo dpkg --configure -a
[sudo] password for daz: 
daz@daz:~$ sudo dpkg --configure -a
daz@daz:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 151 not upgraded.
daz@daz:~$ ls /var/cache/apt/archives
acpid_1.0.4-5ubuntu9netbook1_lpia.deb
adblock-plus_0.7.5.4-0ubuntu1_all.deb
adept-common_2.1.3ubuntu25_all.deb
adept-manager_2.1.3ubuntu25_lpia.deb
all-in-one-sidebar_0.7.4-0ubuntu1_all.deb
anacron_2.3-13ubuntu2.1_lpia.deb
app-install-data-commercial_9.2_all.deb
bluez-audio_3.26-0ubuntu6netbook1_lpia.deb
bluez-cups_3.26-0ubuntu6netbook1_lpia.deb
bluez-gnome_0.25-0ubuntu2~804um1msg10_lpia.deb
bluez-utils_3.26-0ubuntu6netbook1_lpia.deb
capplets-data_1%3a2.22.1-0ubuntu4.1usg4_all.deb
dbus_1.1.20-1ubuntu3.1netbook0belmont1_lpia.deb
debtags_1.7.3ubuntu4_lpia.deb
eject_2.1.5-6ubuntu1_lpia.deb
firefox-3.0_3.0.3+build1+nobinonly-0ubuntu0.8.04.1netbook2build1_lpia.deb
firefox_3.0.3+build1+nobinonly-0ubuntu0.8.04.1netbook2build1_all.deb
firefox-3.0-gnome-support_3.0.3+build1+nobinonly-0ubuntu0.8.04.1netbook2build1_lpia.deb
firefox-gnome-support_3.0.3+build1+nobinonly-0ubuntu0.8.04.1netbook2build1_all.deb
initramfs-tools_0.85eubuntu39.2netbook1_all.deb
iproute_20071016-2ubuntu2_lpia.deb
konsole_4%3a3.5.9-0ubuntu7.2_lpia.deb
libdbus-1-3_1.1.20-1ubuntu3.1netbook0belmont1_lpia.deb
libept0_0.5.15_lpia.deb
libglib2.0-0_2.16.4-0ubuntu3_lpia.deb
libgstreamer0.10-0_0.10.18-4ubuntu1netbook1_lpia.deb
libgstreamer-plugins-base0.10-0_0.10.18-3netbook2_lpia.deb
libhal1_0.5.11~rc2-1ubuntu8.2netbook2_lpia.deb
libldap-2.4-2_2.4.9-0ubuntu0.8.04.1_lpia.deb
libxapian15_1.0.5-1_lpia.deb
linux-image-2.6.24-19-lpia_2.6.24-19.41netbook11_lpia.deb
linux-ubuntu-modules-2.6.24-19-lpia_2.6.24-19.29netbook16_lpia.deb
lock
lsb-base_3.2-4ubuntu1netbook1_all.deb
module-init-tools_3.3-pre11-4ubuntu5.8.04.1_lpia.deb
partial
pciutils_1%3a2.2.4-1.1ubuntu5_lpia.deb
procps_1%3a3.2.7-5ubuntu3_lpia.deb
python2.5_2.5.2-2ubuntu4.1_lpia.deb
python2.5-minimal_2.5.2-2ubuntu4.1_lpia.deb
tzdata_2008e-1ubuntu0.8.04_all.deb
ume-config-belmont_0.77.3_all.deb
unrar-free_1%3a0.0.1+cvs20070515-1_lpia.deb
xulrunner-1.9_1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1_lpia.deb
xulrunner-1.9-gnome-support_1.9.0.3+build1+nobinonly-0ubuntu0.8.04.1_lpia.deb
daz@daz:~$

---

### Post by newbie_sarah_xx on 2009-01-11
> **ugm6hr said:**
> At least the ethernet driver is installed.

Not sure why it hasn't automatically picked up the network.  Try (0=zero):
```
sudo ifdown eth0
sudo ifup eth0
```

With ethernet plugged in

daz@daz:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
daz@daz:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
daz@daz:~$

---

### Post by newbie_sarah_xx on 2009-01-11
daz@daz:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
daz@daz:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
daz@daz:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
daz@daz:~$ sudo ifup eth0

---

### Post by ugm6hr on 2009-01-11
OK. Looks like only about 40 of the 180-odd updates downloaded.
Doesn't look like any of them installed partially.

I am afraid I'm uncertain how eth0 is an "unknown interface".  It is clearly recognised by ifconfig as eth0.

The other thing to check is to ensure you have HD space (make sure free = more than 100,000):
```
df /dev/sda2
```

I'm going to have to go to bed, but will give this some thought.

---

### Post by newbie_sarah_xx on 2009-01-11
ok thanx, i'll leave it for tonight too x

---

### Post by ugm6hr on 2009-01-11
One last suggestion before I forget it (check the df command earlier too).

Try turning off the "Automatic mode" for the Wired connection in:
System -> Administration -> Network
Unlock
Select Wired Connection
Click Properties
Untick "Enable Automatic Mode"
Select "DHCP" in Configuration.
Then OK
Close

Then try again
```
sudo ifdown eth0
sudo ifup eth0
```

We just need to get online to finish all the updates.  Hopefully once they're done, we should be able to get everything sorted.

If this proves impossible, you could manually download the updates (specifically the linux-restricted-modules) and try installing just them.

I wonder what happened to lose your connection mid-download.

---

