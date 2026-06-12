---
title: "Heeelp. Nvidia trouble in Lynx"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by tweety_r78 on 2010-05-04
I just upgraded to Lucid Lynx, and as so many others I habe trouble with the Nvidia graphic card. It runs now on low graphic, I have no sound and the XBMC doesn't work anymore.
Can someone please help med with a guide on how to fix this?

---

### Post by xumuk37 on 2010-05-04
which way did you install the drivers?

---

### Post by tweety_r78 on 2010-05-04
I haven't installed any new Nvidia drivers since upgrading. 
I have gathered as much by googling the problem that I am supposed to downoad a new nvidia driver manually, but I could use some help on how to do that.
Also which driver is best suited for this version of Ubuntu.

---

### Post by xumuk37 on 2010-05-04
ctrl+alt+f1
```
sudo -i
service gdm stop
apt-get remove --purge nvidia*
apt-get install nvidia* or sh NVIDIA-Linux-x86_64-195.36.15-pkg2.run
reboot
```

---

### Post by tweety_r78 on 2010-05-04
Great, thank you!!
Is this all there is to it? will the sound and XBMC work again after downoading this?

---

### Post by xumuk37 on 2010-05-04
you're welcome) no, you have to provide me a little more info about what's wrong...

---

### Post by furoido on 2010-05-04
Can I but in here, sorry.

This is what I got when I ran your recommended commands...

andrew@andrew-desktop:~$ sudo -i
[sudo] password for andrew: 
root@andrew-desktop:~# apt-get remove --purge nvidia*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-kernel-100.14.19 for regex ‘nvidia*’
Note, selecting nvidia-libvdpau-ia32 for regex ‘nvidia*’
Note, selecting nvidia-libvdpau1 for regex ‘nvidia*’
Note, selecting nvidia-glx-dev for regex ‘nvidia*’
Note, selecting nvidia-settings for regex ‘nvidia*’
Note, selecting nvidia-vdpau-driver for regex ‘nvidia*’
Note, selecting nvidia-cg-toolkit for regex ‘nvidia*’
Note, selecting nvidia-glx-new for regex ‘nvidia*’
Note, selecting nvidia-kernel-71.86.04 for regex ‘nvidia*’
Note, selecting nvidia-180-modaliases for regex ‘nvidia*’
Note, selecting nvidia-kernel-common for regex ‘nvidia*’
Note, selecting nvidia-kernel-1.0.7185 for regex ‘nvidia*’
Note, selecting nvidia-libvdpau for regex ‘nvidia*’
Note, selecting nvidia-kernel-1.0.9639 for regex ‘nvidia*’
Note, selecting nvidia-current-modaliases for regex ‘nvidia*’
Note, selecting nvidia-173-modaliases for regex ‘nvidia*’
Note, selecting nvidia-185-modaliases for regex ‘nvidia*’
Note, selecting nvidia-glx-legacy for regex ‘nvidia*’
Note, selecting nvidia-common for regex ‘nvidia*’
Note, selecting nvidia-kernel-96.43.05 for regex ‘nvidia*’
Note, selecting nvidia-kernel-169.12 for regex ‘nvidia*’
Note, selecting nvidia-libvdpau-dev for regex ‘nvidia*’
Note, selecting nvidia-96-modaliases for regex ‘nvidia*’
Note, selecting nvidia-glx for regex ‘nvidia*’
The following packages were automatically installed and are no longer required:
  policykit libgda3-sqlite libpolkit-gnome0 libpolkit-dbus2 mplayer-nogui
  libpolkit-grant2 libpolkit2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  nvidia-173-modaliases* nvidia-96-modaliases* nvidia-common*
  nvidia-current-modaliases* nvidia-kernel-common*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 557kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 190205 files and directories currently installed.)
Removing nvidia-kernel-common ...
/var/lib/dpkg/info/nvidia-kernel-common.prerm: 7: update-modules: not found
dpkg: error processing nvidia-kernel-common (--purge):
 subprocess installed pre-removal script returned error exit status 127
update-rc.d: warning: /etc/init.d/nvidia-kernel missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
		-n: not really
		-f: force

The disable|enable API is not stable and might change in the future.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Removing nvidia-common ...
Purging configuration files for nvidia-common ...
Removing nvidia-173-modaliases ...
Removing nvidia-96-modaliases ...
Removing nvidia-current-modaliases ...
Errors were encountered while processing:
 nvidia-kernel-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@andrew-desktop:~# apt-get install nvidia* or sh NVIDIA-Linux-x86_64-195.36.15-pkg2.run
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-kernel-100.14.19 for regex ‘nvidia*’
Note, selecting nvidia-libvdpau-ia32 for regex ‘nvidia*’
Note, selecting nvidia-libvdpau1 for regex ‘nvidia*’
Note, selecting nvidia-glx-dev for regex ‘nvidia*’
Note, selecting nvidia-settings for regex ‘nvidia*’
Note, selecting nvidia-vdpau-driver for regex ‘nvidia*’
Note, selecting nvidia-cg-toolkit for regex ‘nvidia*’
Note, selecting nvidia-glx-new for regex ‘nvidia*’
Note, selecting nvidia-kernel-71.86.04 for regex ‘nvidia*’
Note, selecting nvidia-180-modaliases for regex ‘nvidia*’
Note, selecting nvidia-kernel-common for regex ‘nvidia*’
Note, selecting nvidia-kernel-1.0.7185 for regex ‘nvidia*’
Note, selecting nvidia-libvdpau for regex ‘nvidia*’
Note, selecting nvidia-kernel-1.0.9639 for regex ‘nvidia*’
Note, selecting nvidia-current-modaliases for regex ‘nvidia*’
Note, selecting nvidia-173-modaliases for regex ‘nvidia*’
Note, selecting nvidia-185-modaliases for regex ‘nvidia*’
Note, selecting nvidia-glx-legacy for regex ‘nvidia*’
Note, selecting nvidia-common for regex ‘nvidia*’
Note, selecting nvidia-kernel-96.43.05 for regex ‘nvidia*’
Note, selecting nvidia-kernel-169.12 for regex ‘nvidia*’
Note, selecting nvidia-libvdpau-dev for regex ‘nvidia*’
Note, selecting nvidia-96-modaliases for regex ‘nvidia*’
Note, selecting nvidia-glx for regex ‘nvidia*’
E: Couldn't find package or
root@andrew-desktop:~#

---

### Post by xumuk37 on 2010-05-04
```
sudo -i
service gdm stop
apt-get remove --purge nvidia*
sh /path/to/NVIDIA-Linux-x86_64-195.36.15-pkg2.run
reboot
```

but you have to download NVIDIA-Linux-x86_64-195.36.15-pkg2.run first

---

### Post by furoido on 2010-05-04
Hi xumuk,
when i run service gdm stop, I get a black screen with a couple of command lines and nothing happens...is that normal?
also, where/how do i downlaod NVIDIA-Linux-x86_64-195.36.15-pkg2.run first

---

### Post by xumuk37 on 2010-05-04
hi,
1. yes. should appear something like 'gdm stop/waiting'
2. from nvidia web, use google for find it)

---

### Post by Linuxforall on 2010-05-04
The method listed here doesnt work on Lucid, also Lucid repos carry a fairly new nvidia drivers, also for convenience, the xswat ppa carries the latest nvidia driver as well, if you wish to install it manually, follow Andy_Boy's excellent post here at [http://ubuntuforums.org/printthread.php?t=1467074](http://ubuntuforums.org/printthread.php?t=1467074)

---

### Post by xumuk37 on 2010-05-04
how can I emprove you that it worked for me? xD

---

### Post by afrodeity on 2010-07-12
bump

---

