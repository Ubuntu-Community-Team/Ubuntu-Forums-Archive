---
title: "My live cd customization script from 8.04.02 does not work for 10.04"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-06-09
here is what I am getting, I made sure the names are all updated, sources.list, live cd name, all that stuff, I get this rsync error/mapping thing, anyone help?```
Extracting CD contents... rsync: read errors mapping "/home/eric/live/mnt/.disk/casper-uuid-generic": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/.disk/cd_type": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/.disk/info": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/.disk/release_notes_url": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/casper/initrd.lz": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/casper/vmlinuz": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/Release": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/Release.gpg": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/main/binary-i386/Packages.gz": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/main/binary-i386/Release": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/restricted/binary-i386/Packages.gz": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/restricted/binary-i386/Release": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/install/README.sbm": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/install/mt86plus": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/install/sbm.bin": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/blue-lowerleft.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/blue-lowerright.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/blue-upperleft.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/blue-upperright.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/debian.jpg": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/logo-50.jpg": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/red-lowerleft.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/red-lowerright.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/red-upperleft.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/red-upperright.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/b/build-essential/build-essential_11.4build1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/d/dpkg/dpkg-dev_1.15.5.6ubuntu4_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/g/gcc-4.4/g++-4.4_4.4.3-4ubuntu5_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/l/linux-wlan-ng/linux-wlan-ng-doc_0.2.9+dfsg-4_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.9+dfsg-4_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/l/lupin/lupin-support_0.29_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/m/mouseemu/mouseemu_0.16-0ubuntu6_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/s/setserial/setserial_2.17-45.2_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/u/ubiquity/oem-config-gtk_2.2.24_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/u/ubiquity/oem-config_2.2.24_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/w/wvdial/wvdial_1.60.3_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/w/wvstreams/libuniconf4.6_4.6.1-1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/w/wvstreams/libwvstreams4.6-base_4.6.1-1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/x/xz-utils/xz-utils_4.999.9beta+20091116-1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/restricted/s/sl-modem/sl-modem-daemon_2.9.11~20100303-2_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/preseed/cli.seed": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/preseed/ltsp.seed": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/preseed/ubuntu.seed": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/.disk/casper-uuid-generic": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/.disk/cd_type": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/.disk/info": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/.disk/release_notes_url": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/casper/initrd.lz": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/casper/vmlinuz": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/Release": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/Release.gpg": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/main/binary-i386/Packages.gz": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/main/binary-i386/Release": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/restricted/binary-i386/Packages.gz": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/dists/lucid/restricted/binary-i386/Release": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/install/README.sbm": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/install/mt86plus": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/install/sbm.bin": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/blue-lowerleft.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/blue-lowerright.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/blue-upperleft.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/blue-upperright.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/debian.jpg": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/logo-50.jpg": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/red-lowerleft.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/red-lowerright.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/red-upperleft.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pics/red-upperright.png": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/b/build-essential/build-essential_11.4build1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/d/dpkg/dpkg-dev_1.15.5.6ubuntu4_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/g/gcc-4.4/g++-4.4_4.4.3-4ubuntu5_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/l/linux-wlan-ng/linux-wlan-ng-doc_0.2.9+dfsg-4_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.9+dfsg-4_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/l/lupin/lupin-support_0.29_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/m/mouseemu/mouseemu_0.16-0ubuntu6_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/s/setserial/setserial_2.17-45.2_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/u/ubiquity/oem-config-gtk_2.2.24_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/u/ubiquity/oem-config_2.2.24_all.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/w/wvdial/wvdial_1.60.3_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/w/wvstreams/libuniconf4.6_4.6.1-1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/w/wvstreams/libwvstreams4.6-base_4.6.1-1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/main/x/xz-utils/xz-utils_4.999.9beta+20091116-1_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/pool/restricted/s/sl-modem/sl-modem-daemon_2.9.11~20100303-2_i386.deb": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/preseed/cli.seed": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/preseed/ltsp.seed": Input/output error (5)
rsync: read errors mapping "/home/eric/live/mnt/preseed/ubuntu.seed": Input/output error (5)
ERROR: .disk/casper-uuid-generic failed verification -- update discarded.
ERROR: .disk/cd_type failed verification -- update discarded.
ERROR: .disk/info failed verification -- update discarded.
ERROR: .disk/release_notes_url failed verification -- update discarded.
ERROR: casper/initrd.lz failed verification -- update discarded.
ERROR: casper/vmlinuz failed verification -- update discarded.
ERROR: dists/lucid/Release failed verification -- update discarded.
ERROR: dists/lucid/Release.gpg failed verification -- update discarded.
ERROR: dists/lucid/main/binary-i386/Packages.gz failed verification -- update discarded.
ERROR: dists/lucid/main/binary-i386/Release failed verification -- update discarded.
ERROR: dists/lucid/restricted/binary-i386/Packages.gz failed verification -- update discarded.
ERROR: dists/lucid/restricted/binary-i386/Release failed verification -- update discarded.
ERROR: install/README.sbm failed verification -- update discarded.
ERROR: install/mt86plus failed verification -- update discarded.
ERROR: install/sbm.bin failed verification -- update discarded.
ERROR: pics/blue-lowerleft.png failed verification -- update discarded.
ERROR: pics/blue-lowerright.png failed verification -- update discarded.
ERROR: pics/blue-upperleft.png failed verification -- update discarded.
ERROR: pics/blue-upperright.png failed verification -- update discarded.
ERROR: pics/debian.jpg failed verification -- update discarded.
ERROR: pics/logo-50.jpg failed verification -- update discarded.
ERROR: pics/red-lowerleft.png failed verification -- update discarded.
ERROR: pics/red-lowerright.png failed verification -- update discarded.
ERROR: pics/red-upperleft.png failed verification -- update discarded.
ERROR: pics/red-upperright.png failed verification -- update discarded.
ERROR: pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb failed verification -- update discarded.
ERROR: pool/main/b/build-essential/build-essential_11.4build1_i386.deb failed verification -- update discarded.
ERROR: pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb failed verification -- update discarded.
ERROR: pool/main/d/dpkg/dpkg-dev_1.15.5.6ubuntu4_all.deb failed verification -- update discarded.
ERROR: pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb failed verification -- update discarded.
ERROR: pool/main/g/gcc-4.4/g++-4.4_4.4.3-4ubuntu5_i386.deb failed verification -- update discarded.
ERROR: pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb failed verification -- update discarded.
ERROR: pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_i386.deb failed verification -- update discarded.
ERROR: pool/main/l/linux-wlan-ng/linux-wlan-ng-doc_0.2.9+dfsg-4_all.deb failed verification -- update discarded.
ERROR: pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.9+dfsg-4_i386.deb failed verification -- update discarded.
ERROR: pool/main/l/lupin/lupin-support_0.29_all.deb failed verification -- update discarded.
ERROR: pool/main/m/mouseemu/mouseemu_0.16-0ubuntu6_i386.deb failed verification -- update discarded.
ERROR: pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb failed verification -- update discarded.
ERROR: pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb failed verification -- update discarded.
ERROR: pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb failed verification -- update discarded.
ERROR: pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb failed verification -- update discarded.
ERROR: pool/main/s/setserial/setserial_2.17-45.2_i386.deb failed verification -- update discarded.
ERROR: pool/main/u/ubiquity/oem-config-gtk_2.2.24_all.deb failed verification -- update discarded.
ERROR: pool/main/u/ubiquity/oem-config_2.2.24_all.deb failed verification -- update discarded.
ERROR: pool/main/w/wvdial/wvdial_1.60.3_i386.deb failed verification -- update discarded.
ERROR: pool/main/w/wvstreams/libuniconf4.6_4.6.1-1_i386.deb failed verification -- update discarded.
ERROR: pool/main/w/wvstreams/libwvstreams4.6-base_4.6.1-1_i386.deb failed verification -- update discarded.
ERROR: pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-1_i386.deb failed verification -- update discarded.
ERROR: pool/main/x/xz-utils/xz-utils_4.999.9beta+20091116-1_i386.deb failed verification -- update discarded.
ERROR: pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb failed verification -- update discarded.
ERROR: pool/restricted/s/sl-modem/sl-modem-daemon_2.9.11~20100303-2_i386.deb failed verification -- update discarded.
ERROR: preseed/cli.seed failed verification -- update discarded.
ERROR: preseed/ltsp.seed failed verification -- update discarded.
ERROR: preseed/ubuntu.seed failed verification -- update discarded.
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1058) [sender=3.0.4]
Done
Extracting Desktop System... mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

cp: cannot stat `squashfs/*': No such file or directory
umount: squashfs: not mounted
Done

cp: accessing `edit/etc/apt/sources.list': Not a directory
Start package removal? y/[n] y

chroot: cannot run command `apt-get': No such file or directory
chroot: cannot run command `apt-get': No such file or directory

Start package installation? y/[n]
```


Thanks in advance, PLZ HELP :).

---

### Post by SRST Technologies on 2010-06-09
If you're going to customize Ubuntu 10.04, it's best to use the 10.04 ISO to do it with and not an extremely old ISO and hope it works.

---

### Post by ericeclifford on 2010-06-09
> **SRST Technologies said:**
> If you're going to customize Ubuntu 10.04, it's best to use the 10.04 ISO to do it with and not an extremely old ISO and hope it works.

I did, do you see somewhere in the code that I do not use the 10.04?, because my script points to ubuntu-10.04-i386.iso, same name that is on the website, same name that is on the iso image i call to customize, unless I am wrong, if you see anything let me know?

---

### Post by ericeclifford on 2010-06-09
```
echo -n "Loading squashfs module... "
modprobe squashfs
echo Done
echo

echo -n "Extract iso contents? y/[n] "
read ua

if [ "$ua" = "y" ]; then
if [ -e "edit" ]; then
echo -n "Removing existing Desktop System... "
rm -r edit
echo Done
fi
mkdir edit
if [ -e "extract-cd" ]; then
echo -n "Removing existing CD contents... "
rm -r extract-cd
echo Done
fi
mkdir extract-cd
if ! [ -e "mnt" ]; then
mkdir mnt
fi
if ! [ -e "squashfs" ]; then
mkdir squashfs
fi
echo -n "Extracting CD contents... "
mount -o loop ubuntu-10.04-desktop-i386.iso mnt
rsync --exclude=/casper/filesystem.squashfs -a mnt/ extract-cd
echo Done
echo -n "Extracting Desktop System... "
mount -t squashfs -o loop mnt/casper/filesystem.squashfs squashfs
cp -a squashfs/* edit/
umount squashfs
umount mnt
echo Done
fi
echo
```

Ok so here is the first part of my code of my script(in terminal of course), I am in the live directory, with this in it(below is the iso image of 10.04.)

file:///home/eric/live/ubuntu-10.04-desktop-i386.iso

Thanks for helping!

EDIT: did you mean I should install 10.04 onto my desktop I am doing it with and then use the script I created it in that environment? Maybe an update or upgrade I might need? I use apt-mirror, and I am using 8.04.2 install version for the customization computer, but I am using the 10.04 ISO image for the actual customization.

---

### Post by ericeclifford on 2010-06-14
Bump

---

### Post by ericeclifford on 2010-06-14
Oh, I think I found the problem, I looked on the docs of ubuntu.com and it said I needed grub2 and a plymouth-x11.

I have grub2 installed, by plymouth wont install on my 8.04.2 hard drive disk, so I downloaded it, and tried to install it using the "configure"script and it saids I am missing a lib file , that I can not apt-get,

Is this a lost cause with a 8.04.2 install? Should I just use 10.04 install computer for the live cd customizations?

---

