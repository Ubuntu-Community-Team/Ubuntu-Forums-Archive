---
title: "wireless signal is weaker than it was on windows"
date: 2017-09-13
forum: Networking &amp; Wireless
---

### Post by elwakeel on 2017-09-13
I had installed ubuntu on  HP probook 4540s instead of windows, but the internet is weak on it and signal strength came from wireless is weaker that it was on windows. I searched a lot and found that is a common specially for hp users. I tried everything I founded through the search but nothing works.  so I hope anyone can help. I really don't want to go back for windows

---

### Post by wildmanne39 on 2017-09-13
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by elwakeel on 2017-09-13
WOW thanks for this fast replay 
here is the link 
[http://paste.ubuntu.com/25527269/](http://paste.ubuntu.com/25527269/)

---

### Post by wildmanne39 on 2017-09-13
Please do:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
copy and paste for accuracy!

Reboot

---

### Post by elwakeel on 2017-09-13
[COLOR=#DD4814][COLOR=#C61919]thanks [wildmanne39]("https://ubuntuforums.org/member.php?u=508533"). [/COLOR][/COLOR][COLOR=#DD4814][COLOR=#C61919][/COLOR][/COLOR]although I don't feel that it backs as it was on windows, but  I feel that it is better a little now. I can see a difference 
thanks a lot really. you increased my willing to stay on Ubuntu.

---

### Post by wildmanne39 on 2017-09-13
The question is how are you determining the signal is lower on Ubuntu then windows the icon in the top panel is not a 100 percent accurate but yes there probably was a little difference but what matters is how well it works and it should work better now and we can do a couple of things to make it better.

Please set your settings in network manager by clicking on the wifi icon in the top panel and set them to match the screenshots.

Check the settings in your router. WPA2-AES (CCMP) is best, not WPA and WPA2 mixed mode and do not use TKIP. 

Next, if your router is capable of N speeds, you will probably have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. You also should set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

We need to set your location for your router, please do:
```
sudo iw reg set US
```
then:
```
udo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
if your location is in the U.S.
Reboot

If it is working better, please use thread tools at the top of the page to mark the thread solved.

Thanks

---

### Post by elwakeel on 2017-09-27
I was wrong Wild, it was speed as it was in windows(maybe better),I realized that later. so thanks for your previous help. it was great really. 

Now I have a new problem, yesterday Wi fi was disconnected by it self and then asked me to reconnected through the pop up of the network with the password already typed so I  click "connect" and then wifi return . 
Today it is crazy. most of times, it doesn't show me any networks avilable,
sometimes when I shut wi-fi down through keyboard button that enable/ disaple wifi, and then enabled it  -> it  tells me "device not ready" . 
sometimes it show only networks that I haven't connect to before, but my network doesn't show.
sometimes when I shut down the lab top several times, it came to work

here is the output your script if you need it, I just run it so these are the new states :
[http://paste.ubuntu.com/25626458/](http://paste.ubuntu.com/25626458/)


&#1600;&#1600;&#1600;&#1600;&#1600;&#1600;&#1600;&#1600;&#1600;&#1600;&#1600;&#1600;

I applied the new edits you mentioned in last replay. 
notice : I'm not in USA, I'm from Egypt, middle east : )

---

### Post by wildmanne39 on 2017-09-27
Hi, your kernel has been upgraded since we fixed your wifi 2 weeks ago and I have seen about 4 cases where after being updated to this same kernel each user has the same exact issue, I will research this and see if I can find a fix for it, in the mean time please boot into a previous kernel and see if your wifi works in the older kernel still.

Thanks

---

### Post by elwakeel on 2017-09-27
Thanks for answer and your always help. 

booting previous kernel doesn't make it work
[http://paste.ubuntu.com/25627571/](http://paste.ubuntu.com/25627571/)

---

### Post by wildmanne39 on 2017-09-27
Let's do a little clean up I do not think it will make it work but the file is not needed for your driver, please do:
```
sudo rm /etc/modprobe.d/ath9k.conf
```
Then:
```
sudo dpkg-reconfigure resolvconf
```
then answer 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" question, then reboot.

Does it connect now?

---

### Post by elwakeel on 2017-09-27
unfortunately it doesn't. 
I think that is enough, I don't like to overload you more.

Thanks for every thing

---

### Post by wildmanne39 on 2017-09-27
It is up to you but there are a few things we can check and try that may fix the issue. It might help to reinstall the kernel.

---

### Post by elwakeel on 2017-09-27
Ok as it is ok to you, thanks .
I reinstalled it, the problem is still on.

---

### Post by wildmanne39 on 2017-09-27
Please post the output of:
```
tail -n25 /var/log/apt/history.log
```

---

### Post by elwakeel on 2017-09-27
```
End-Date: 2017-09-25  05:04:46


Start-Date: 2017-09-27  06:51:03
Commandline: apt-get install alien dpkg-dev debhelper build-essential
Requested-By: root1 (1000)
Install: autotools-dev:amd64 (20150820.1, automatic), libmail-sendmail-perl:amd64 (0.79.16-1, automatic), alien:amd64 (8.95), dh-strip-nondeterminism:amd64 (0.015-1, automatic), libfile-stripnondeterminism-perl:amd64 (0.015-1, automatic), po-debconf:amd64 (1.0.19, automatic), debhelper:amd64 (9.20160115ubuntu3), libsys-hostname-long-perl:amd64 (1.5-1, automatic)
End-Date: 2017-09-27  06:51:18


Start-Date: 2017-09-27  07:35:37
Commandline: apt dist-upgrade
Requested-By: root1 (1000)
Upgrade: libplist3:amd64 (1.12-3.1, 1.12-3.1ubuntu0.16.04.1), gnome-software:amd64 (3.20.5-0ubuntu0.16.04.5, 3.20.5-0ubuntu0.16.04.6), libpython3.5:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.2), python3.5:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.2), plymouth-label:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), python3.5-minimal:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.2), plymouth-theme-ubuntu-text:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), libplymouth4:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), atom:amd64 (1.19.6-1~webupd8~0, 1.20.1-1~webupd8~0), ubuntu-software:amd64 (3.20.5-0ubuntu0.16.04.5, 3.20.5-0ubuntu0.16.04.6), brackets:amd64 (1.10.0libgcrypt11-17483+1~webupd8~0, 1.11.0libgcrypt11-17524+1~webupd8~1), plymouth:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), libpython3.5-stdlib:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.2), plymouth-theme-ubuntu-logo:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), libpython3.5-minimal:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.2), gnome-software-common:amd64 (3.20.5-0ubuntu0.16.04.5, 3.20.5-0ubuntu0.16.04.6)
End-Date: 2017-09-27  07:39:08


Start-Date: 2017-09-27  10:37:06
Commandline: apt install gksu
Requested-By: root1 (1000)
Install: libgksu2-0:amd64 (2.0.13~pre1-6ubuntu8, automatic), gksu:amd64 (2.0.2-9ubuntu1)
End-Date: 2017-09-27  10:37:19


Start-Date: 2017-09-27  12:08:46
Commandline: apt-get install --reinstall linux-image-4.10.0-33-generic
Requested-By: root1 (1000)
Reinstall: linux-image-4.10.0-33-generic:amd64 (4.10.0-33.37~16.04.1)
End-Date: 2017-09-27  12:09:33
```

---

### Post by wildmanne39 on 2017-09-27
Let's run that last command again but I changed it a little to show more updates:
```
tail -n100 /var/log/apt/history.log
```

---

### Post by elwakeel on 2017-09-27
```

    Start-Date: 2017-09-15  11:11:32
Commandline: apt-get install indicator-stickynotes
Requested-By: root1 (1000)
Install: indicator-stickynotes:amd64 (0.5.8-0~ppa1)
End-Date: 2017-09-15  11:11:42

Start-Date: 2017-09-15  11:13:04
Commandline: aptdaemon role='role-commit-packages' sender=':1.142'
Install: xpad:amd64 (4.5.0-0ubuntu1)
End-Date: 2017-09-15  11:13:11

Start-Date: 2017-09-16  10:41:47
Commandline: apt install gnome-control-center gnome-online-accounts
Requested-By: root1 (1000)
Install: libgoa-backend-1.0-1:amd64 (3.18.3-1ubuntu2, automatic), gnome-control-center-data:amd64 (1:3.18.2-1ubuntu6, automatic), gnome-control-center:amd64 (1:3.18.2-1ubuntu6), realmd:amd64 (0.16.2-2, automatic), gnome-icon-theme:amd64 (3.12.0-1ubuntu3, automatic), libdleyna-connector-dbus-1.0-1:amd64 (0.2.0-1, automatic), libgupnp-1.0-4:amd64 (0.20.16-1, automatic), gnome-settings-daemon:amd64 (3.18.2-0ubuntu3.1, automatic), iio-sensor-proxy:amd64 (1.1-1ubuntu1, automatic), gnome-icon-theme-symbolic:amd64 (3.12.0-1, automatic), dleyna-server:amd64 (0.4.0-1, automatic), gnome-online-accounts:amd64 (3.18.3-1ubuntu2), libgssdp-1.0-3:amd64 (0.14.14-1ubuntu1, automatic), libdleyna-core-1.0-3:amd64 (0.4.0-1, automatic), libcolord-gtk1:amd64 (0.1.26-1, automatic), libgupnp-dlna-2.0-3:amd64 (0.10.4-1, automatic), libgupnp-av-1.0-2:amd64 (0.12.8-1, automatic)
End-Date: 2017-09-16  10:42:31

Start-Date: 2017-09-16  13:47:00
Commandline: apt-get install python-pip
Requested-By: root1 (1000)
Install: python2.7-dev:amd64 (2.7.12-1ubuntu0~16.04.1, automatic), libexpat1-dev:amd64 (2.1.0-7ubuntu0.16.04.3, automatic), libpython-all-dev:amd64 (2.7.11-1, automatic), libpython2.7-dev:amd64 (2.7.12-1ubuntu0~16.04.1, automatic), libpython-dev:amd64 (2.7.11-1, automatic), python-pkg-resources:amd64 (20.7.0-1, automatic), python-all:amd64 (2.7.11-1, automatic), python-dev:amd64 (2.7.11-1, automatic), python-setuptools:amd64 (20.7.0-1, automatic), python-wheel:amd64 (0.29.0-1, automatic), python-pip-whl:amd64 (8.1.1-2ubuntu0.4, automatic), python-pip:amd64 (8.1.1-2ubuntu0.4), python-all-dev:amd64 (2.7.11-1, automatic)
End-Date: 2017-09-16  13:47:25

Start-Date: 2017-09-16  13:54:43
Commandline: apt-get install -f
Requested-By: root1 (1000)
Install: libindicator7:amd64 (12.10.2+16.04.20151208-0ubuntu1, automatic), python-gi:amd64 (3.20.0-0ubuntu1, automatic), python-pyinotify:amd64 (0.9.6-0fakesync1, automatic), libappindicator1:amd64 (12.10.1+16.04.20170215-0ubuntu1, automatic)
End-Date: 2017-09-16  13:55:18

Start-Date: 2017-09-16  14:03:30
Commandline: apt-get remove overgrive
Requested-By: root1 (1000)
Remove: overgrive:amd64 (3.2.3)
End-Date: 2017-09-16  14:03:35

Start-Date: 2017-09-16  14:40:37
Commandline: apt-get -f install
Requested-By: root1 (1000)
Install: libc-ares2:amd64 (1.10.0-3ubuntu0.2, automatic), libcrypto++9v5:amd64 (5.6.1-9, automatic)
End-Date: 2017-09-16  14:40:42

Start-Date: 2017-09-19  06:45:55
Commandline: /usr/bin/unattended-upgrade
Install: linux-image-extra-4.10.0-35-generic:amd64 (4.10.0-35.39~16.04.1, automatic), linux-headers-4.10.0-35-generic:amd64 (4.10.0-35.39~16.04.1, automatic), linux-headers-4.4.0-96:amd64 (4.4.0-96.119, automatic), linux-headers-4.4.0-96-generic:amd64 (4.4.0-96.119, automatic), linux-headers-4.10.0-35:amd64 (4.10.0-35.39~16.04.1, automatic), linux-image-4.10.0-35-generic:amd64 (4.10.0-35.39~16.04.1, automatic)
Upgrade: libdns-export162:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.7, 1:9.10.3.dfsg.P4-8ubuntu1.8), libisccfg140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.7, 1:9.10.3.dfsg.P4-8ubuntu1.8), linux-headers-generic:amd64 (4.4.0.93.98, 4.4.0.96.101), linux-libc-dev:amd64 (4.4.0-93.116, 4.4.0-96.119), gir1.2-gdkpixbuf-2.0:amd64 (2.32.2-1ubuntu1.2, 2.32.2-1ubuntu1.3), libgdk-pixbuf2.0-0:amd64 (2.32.2-1ubuntu1.2, 2.32.2-1ubuntu1.3), linux-image-generic-hwe-16.04:amd64 (4.10.0.33.35, 4.10.0.35.37), bind9-host:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.7, 1:9.10.3.dfsg.P4-8ubuntu1.8), linux-generic-hwe-16.04:amd64 (4.10.0.33.35, 4.10.0.35.37), dnsutils:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.7, 1:9.10.3.dfsg.P4-8ubuntu1.8), libisc160:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.7, 1:9.10.3.dfsg.P4-8ubuntu1.8), libisc-export160:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.7, 1:9.10.3.dfsg.P4-8ubuntu1.8), liblwres141:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.7, 1:9.10.3.dfsg.P4-8ubuntu1.8), libgdk-pixbuf2.0-common:amd64 (2.32.2-1ubuntu1.2, 2.32.2-1ubuntu1.3), libdns162:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.7, 1:9.10.3.dfsg.P4-8ubuntu1.8), libxml2:amd64 (2.9.3+dfsg1-1ubuntu0.2, 2.9.3+dfsg1-1ubuntu0.3), libisccc140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.7, 1:9.10.3.dfsg.P4-8ubuntu1.8), linux-headers-generic-hwe-16.04:amd64 (4.10.0.33.35, 4.10.0.35.37), libbind9-140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.7, 1:9.10.3.dfsg.P4-8ubuntu1.8)
End-Date: 2017-09-19  06:48:19

Start-Date: 2017-09-19  11:58:08
Commandline: apt-get install flashplugin-installer
Requested-By: root1 (1000)
Install: flashplugin-installer:amd64 (27.0.0.130ubuntu0.16.04.1)
End-Date: 2017-09-19  12:19:21

Start-Date: 2017-09-22  11:22:41
Commandline: apt-get install kazam python3-cairo python3-xlib
Requested-By: root1 (1000)
Install: gstreamer1.0-plugins-ugly-amr:amd64 (1.8.3-1ubuntu0.1, automatic), libsnappy1v5:amd64 (1.1.3-2, automatic), libavutil-ffmpeg54:amd64 (7:2.8.11-0ubuntu0.16.04.1, automatic), libcrystalhd3:amd64 (1:0.0~git20110715.fdd2f19-11build1, automatic), libopencore-amrnb0:amd64 (0.1.3-2.1, automatic), vdpau-va-driver:amd64 (0.7.4-5, automatic), va-driver-all:amd64 (1.7.0-1, automatic), libopencv-imgproc2.4v5:amd64 (2.4.9.1+dfsg-1.5ubuntu1, automatic), python3-xlib:amd64 (0.14+20091101-5), libavfilter-ffmpeg5:amd64 (7:2.8.11-0ubuntu0.16.04.1, automatic), libopenjpeg5:amd64 (1:1.5.2-3.1, automatic), libzmq5:amd64 (4.1.4-7, automatic), gir1.2-keybinder-3.0:amd64 (0.3.1-1, automatic), libdvdread4:amd64 (5.0.3-1, automatic), libswresample-ffmpeg1:amd64 (7:2.8.11-0ubuntu0.16.04.1, automatic), libvdpau1:amd64 (1.1.1-3ubuntu1, automatic), libmp3lame0:amd64 (3.99.5+repack1-9build1, automatic), liba52-0.7.4:amd64 (0.7.4-18, automatic), libopencore-amrwb0:amd64 (0.1.3-2.1, automatic), libbdplus0:amd64 (0.1.2-1, automatic), vdpau-driver-all:amd64 (1.1.1-3ubuntu1, automatic), libdvdnav4:amd64 (5.0.3-1, automatic), libva1:amd64 (1.7.0-1, automatic), libx264-148:amd64 (2:0.148.2643+git5c65704-1, automatic), libass5:amd64 (0.13.1-1, automatic), libx265-79:amd64 (1.9-3, automatic), libpostproc-ffmpeg53:amd64 (7:2.8.11-0ubuntu0.16.04.1, automatic), libmpg123-0:amd64 (1.22.4-1, automatic), libxvidcore4:amd64 (2:1.3.4-1, automatic), libzvbi0:amd64 (0.2.35-10, automatic), libaacs0:amd64 (0.8.1-1, automatic), kazam:amd64 (1.4.5-2), libgme0:amd64 (0.6.0-3ubuntu0.16.04.1, automatic), libssh-gcrypt-4:amd64 (0.6.3-4.3, automatic), libmad0:amd64 (0.15.1b-8ubuntu1, automatic), libtbb2:amd64 (4.4~20151115-0ubuntu3, automatic), libsoxr0:amd64 (0.1.2-1, automatic), libmpeg2-4:amd64 (0.5.1-7, automatic), libsodium18:amd64 (1.0.8-5, automatic), libswscale-ffmpeg3:amd64 (7:2.8.11-0ubuntu0.16.04.1, automatic), libavresample-ffmpeg2:amd64 (7:2.8.11-0ubuntu0.16.04.1, automatic), libshine3:amd64 (3.1.0-4, automatic), libopencv-core2.4v5:amd64 (2.4.9.1+dfsg-1.5ubuntu1, automatic), gstreamer1.0-libav:amd64 (1.8.3-1ubuntu0.2, automatic), libsidplay1v5:amd64 (1.36.59-8, automatic), libavcodec-ffmpeg56:amd64 (7:2.8.11-0ubuntu0.16.04.1, automatic), libtwolame0:amd64 (0.3.13-1.2, automatic), libgsm1:amd64 (1.0.13-4, automatic), libmodplug1:amd64 (1:0.8.8.5-2, automatic), libbs2b0:amd64 (3.1.0+dfsg-2.2, automatic), libavformat-ffmpeg56:amd64 (7:2.8.11-0ubuntu0.16.04.1, automatic), mesa-vdpau-drivers:amd64 (17.0.7-0ubuntu0.16.04.1, automatic), libkeybinder-3.0-0:amd64 (0.3.1-1, automatic), i965-va-driver:amd64 (1.7.0-1, automatic), libzvbi-common:amd64 (0.2.35-10, automatic), libbluray1:amd64 (1:0.9.2-2, automatic), libflite1:amd64 (2.0.0-release-1, automatic), libschroedinger-1.0-0:amd64 (1.0.11-2.1build1, automatic), gstreamer1.0-plugins-ugly:amd64 (1.8.3-1ubuntu0.1, automatic)
End-Date: 2017-09-22  11:24:46

Start-Date: 2017-09-23  06:26:28
Commandline: /usr/bin/unattended-upgrade
Upgrade: libwbclient0:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.10, 2:4.3.11+dfsg-0ubuntu0.16.04.11), samba-libs:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.10, 2:4.3.11+dfsg-0ubuntu0.16.04.11), chromium-browser:amd64 (60.0.3112.113-0ubuntu0.16.04.1298, 61.0.3163.79-0ubuntu0.16.04.1300), chromium-codecs-ffmpeg-extra:amd64 (60.0.3112.113-0ubuntu0.16.04.1298, 61.0.3163.79-0ubuntu0.16.04.1300), libsmbclient:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.10, 2:4.3.11+dfsg-0ubuntu0.16.04.11), chromium-browser-l10n:amd64 (60.0.3112.113-0ubuntu0.16.04.1298, 61.0.3163.79-0ubuntu0.16.04.1300)
End-Date: 2017-09-23  06:27:25

Start-Date: 2017-09-25  05:03:17
Commandline: apt-get install sublime-text
Requested-By: root1 (1000)
Install: sublime-text:amd64 (3144)
End-Date: 2017-09-25  05:03:37

Start-Date: 2017-09-25  05:04:35
Commandline: apt-get --purge remove indicator-stickynotes
Requested-By: root1 (1000)
Purge: indicator-stickynotes:amd64 (0.5.8-0~ppa1)
End-Date: 2017-09-25  05:04:46

Start-Date: 2017-09-27  06:51:03
Commandline: apt-get install alien dpkg-dev debhelper build-essential
Requested-By: root1 (1000)
Install: autotools-dev:amd64 (20150820.1, automatic), libmail-sendmail-perl:amd64 (0.79.16-1, automatic), alien:amd64 (8.95), dh-strip-nondeterminism:amd64 (0.015-1, automatic), libfile-stripnondeterminism-perl:amd64 (0.015-1, automatic), po-debconf:amd64 (1.0.19, automatic), debhelper:amd64 (9.20160115ubuntu3), libsys-hostname-long-perl:amd64 (1.5-1, automatic)
End-Date: 2017-09-27  06:51:18

Start-Date: 2017-09-27  07:35:37
Commandline: apt dist-upgrade
Requested-By: root1 (1000)
Upgrade: libplist3:amd64 (1.12-3.1, 1.12-3.1ubuntu0.16.04.1), gnome-software:amd64 (3.20.5-0ubuntu0.16.04.5, 3.20.5-0ubuntu0.16.04.6), libpython3.5:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.2), python3.5:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.2), plymouth-label:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), python3.5-minimal:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.2), plymouth-theme-ubuntu-text:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), libplymouth4:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), atom:amd64 (1.19.6-1~webupd8~0, 1.20.1-1~webupd8~0), ubuntu-software:amd64 (3.20.5-0ubuntu0.16.04.5, 3.20.5-0ubuntu0.16.04.6), brackets:amd64 (1.10.0libgcrypt11-17483+1~webupd8~0, 1.11.0libgcrypt11-17524+1~webupd8~1), plymouth:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), libpython3.5-stdlib:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.2), plymouth-theme-ubuntu-logo:amd64 (0.9.2-3ubuntu13.1, 0.9.2-3ubuntu13.2), libpython3.5-minimal:amd64 (3.5.2-2ubuntu0~16.04.1, 3.5.2-2ubuntu0~16.04.2), gnome-software-common:amd64 (3.20.5-0ubuntu0.16.04.5, 3.20.5-0ubuntu0.16.04.6)
End-Date: 2017-09-27  07:39:08

Start-Date: 2017-09-27  10:37:06
Commandline: apt install gksu
Requested-By: root1 (1000)
Install: libgksu2-0:amd64 (2.0.13~pre1-6ubuntu8, automatic), gksu:amd64 (2.0.2-9ubuntu1)
End-Date: 2017-09-27  10:37:19

Start-Date: 2017-09-27  12:08:46
Commandline: apt-get install --reinstall linux-image-4.10.0-33-generic
Requested-By: root1 (1000)
Reinstall: linux-image-4.10.0-33-generic:amd64 (4.10.0-33.37~16.04.1)
End-Date: 2017-09-27  12:09:33


```

---

### Post by wildmanne39 on 2017-09-27
Do you still have network manager icon in the top right corner or the screen? if so is networking and wireless enabled?

---

### Post by elwakeel on 2017-09-27
yes both are enabled, network manager icon sometimes show some networks, but mine not included .. and sometimes mine show too, and when I try to connect to it.. it keeps trying  but no connection happens

---

### Post by wildmanne39 on 2017-09-27
Reboot your router and after it is completely back up remove your network from network manger and reboot and let it find your connection itself and enter your information and see if that fixes it.

---

### Post by elwakeel on 2017-09-27
I already tried that before. I even open a hot spot from my mobile phone but network manager didn't find it . 
"network manager" is now saying "device not ready". it is going crazy like that all the day. sometimes show some networks sometimes not showing any. sometimes show mine but refuse to connect. 

anyway I really can't thank you enough for your time and your kindness. 

Thanks from the heart

---

### Post by wildmanne39 on 2017-09-27
Try:
```
sudo systemctl restart network-manager
```

---

### Post by jeremy31 on 2017-09-27
Have you tried removing the bottom cover and swap the antenna wires on the wifi card?
If possible change your wifi router encryption settings to WPA2 only, without TKIP and see if you can change channel width to 20 MHz instead of auto or 40MHz
Most of the HP users with signal strength issues have newer laptops with RTL8723BE wifi cards that HP only used one antenna for.

---

