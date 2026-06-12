---
title: "Ubuntu 8.04 and ATi HD2600AGP graphics card problem"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Wishy2009 on 2009-11-24
This is my first ever post so please be gentle with me. 

As the thread suggests I have a problem getting my graphics card to work properly. My main issue with it is that I can't get the dual screen option. Whatever I do the best I can get is a pair of cloned screens using the none fglrx drivers.

I have tried Kubuntu 9.04, 9.10, Ubuntu 9.04 but have currently settled on Ubuntu 8.04 where I intend to stay for now. There doesn't seem to be any significant difference whichever flavour I use. 

**_Things that I have tried_**
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) results in a black screen upon boot and I can't log in. Recovery mode then xfix gets me back to where I started.

I tried [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) also but get an error on the command
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
I am typing it in letter for letter though, does uname need to be something else? I have tried substituting it for my user login name and machine name and removing the quote marks to no avail.

If I simply enable the accelerated ATI drivers in hardware drivers then I lose the ability to log in and need to run xfix again.

If I go to the resolution settings I can untick clone monitor and place my monitors side by side (exactly as I'd like them) but clicking apply does nothing and they remain cloned. They are detected properly.

lshw gives
```
nepage2                   
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2027MiB
     *-cpu
          product: AMD Athlon(tm) XP 2500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 1850MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia module=nvidia_agp
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nForce2 ISA Bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: nForce2 SMBus (MCP)
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
        *-usb:0
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: nForce2 USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a4
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: nForce2 Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: a1
             serial: 00:e0:4c:ba:01:55
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.12 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
        *-multimedia:0 UNCLAIMED
             description: Multimedia audio controller
             product: nForce Audio Processing Unit
             vendor: nVidia Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: latency=0 maxlatency=12 mingnt=1
        *-multimedia:1
             description: Multimedia audio controller
             product: nForce2 AC97 Audio Controler (MCP)
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
        *-pci:0
             description: PCI bridge
             product: nForce2 External PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-storage
                description: RAID bus controller
                product: VIA VT6420 SATA RAID Controller
                vendor: VIA Technologies, Inc.
                physical id: 8
                bus info: pci@0000:01:08.0
                version: 50
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=sata_via latency=32 module=sata_via
        *-ide
             description: IDE interface
             product: nForce2 IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: RV630 [Radeon HD 2600 AGP Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=fglrx_pci latency=32 mingnt=8 module=fglrx
  *-scsi:0
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage

```Any ideas?

---

### Post by Wishy2009 on 2009-11-26
Just to add some more information

fglrx (rather predictably) gives

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```

---

### Post by Wishy2009 on 2009-11-27
One thing that I've realised that I haven't tried yet is the manual install method from the wiki so will try that tonight.

---

### Post by mbzn on 2009-11-27
Hi welcome to the forum.

Ati and ubuntu is not good friends, their driver just suck and seldom works. Any way play around with them and hopefully you'll learn something.
The forum will be full of guru's when america wakes up. My bet is they'll get you sorted.

---

### Post by mbzn on 2009-11-27
Try searching the forums, this seems like a common issue.
[http://ubuntuforums.org/showthread.php?t=766699&highlight=ati+black+screen+startup](http://ubuntuforums.org/showthread.php?t=766699&highlight=ati+black+screen+startup)

---

### Post by Wishy2009 on 2009-11-27
Thanks for the welcome :)

Everything I've tried so far has been ideas from this forum. As much as anything this thread is a record for me of what I've tried so far that hasn't worked. 

Unfortunately I got this card a while ago (long before I ventured in any flavour of Linux), if I'd read the threads I have now beforehand I certainly would have gone for nVidia instead. But then if we all had that much foresight then life would probably be too easy and quite dull.

Some good news tonight is that the manual driver install method worked albeit with an error listed. I'm not sure if the error 

("dpkg: error processing fglrx-amdccle_8.661-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory") is significant, I've attached what I did below.

```
wishy@NePage2:~$ sudo apt-get update
[sudo] password for wishy: 
Hit http://gb.archive.ubuntu.com hardy Release.gpg
Get: 1 http://gb.archive.ubuntu.com hardy/main Translation-en_GB [19.6kB]
Hit http://security.ubuntu.com hardy-security Release.gpg    
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com hardy-security Release          
Get: 2 http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB [1956B]
Get: 3 http://gb.archive.ubuntu.com hardy/universe Translation-en_GB [4368B]
Get: 4 http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB [36.1kB]
Hit http://gb.archive.ubuntu.com hardy-updates Release.gpg
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy Release                               
Hit http://gb.archive.ubuntu.com hardy-updates Release                       
Hit http://security.ubuntu.com hardy-security/main Packages                  
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources          
Hit http://security.ubuntu.com hardy-security/restricted Sources    
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://gb.archive.ubuntu.com hardy/main Packages                           
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages            
Hit http://security.ubuntu.com hardy-security/multiverse Sources             
Hit http://gb.archive.ubuntu.com hardy/restricted Packages                   
Hit http://gb.archive.ubuntu.com hardy/main Sources        
Hit http://gb.archive.ubuntu.com hardy/restricted Sources  
Hit http://gb.archive.ubuntu.com hardy/universe Packages   
Hit http://gb.archive.ubuntu.com hardy/universe Sources    
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages 
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources  
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-updates/main Sources
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://gb.archive.ubuntu.com hardy-updates/universe Packages
Hit http://gb.archive.ubuntu.com hardy-updates/universe Sources
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Sources
Fetched 62.0kB in 0s (161kB/s)
Reading package lists... Done
wishy@NePage2:~$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
debconf is already the newest version.
linux-headers-2.6.24-25-generic is already the newest version.
The following extra packages will be installed:
  autoconf automake1.7 autotools-dev dpkg-dev fdupes g++ g++-4.2 gcc-3.3-base
  gettext html2text intltool intltool-debian libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev m4 patch po-debconf
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc devscripts
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  cvs gettext-doc glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
Recommended packages:
  automaken libmail-sendmail-perl libcompress-zlib-perl libmail-box-perl
The following NEW packages will be installed
  autoconf automake1.7 autotools-dev build-essential cdbs debhelper dh-make
  dkms dpkg-dev fakeroot fdupes g++ g++-4.2 gcc-3.3-base gettext html2text
  intltool intltool-debian libc6-dev libstdc++5 libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev m4 patch po-debconf
0 upgraded, 26 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.4MB of archives.
After this operation, 52.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com hardy/main m4 1.4.10-1 [207kB]
Get: 2 http://gb.archive.ubuntu.com hardy/main autoconf 2.61-4 [448kB]
Get: 3 http://gb.archive.ubuntu.com hardy/main autotools-dev 20070725.1 [61.9kB]
Get: 4 http://gb.archive.ubuntu.com hardy/main automake1.7 1.7.9-9 [391kB]
Get: 5 http://gb.archive.ubuntu.com hardy-updates/main linux-libc-dev 2.6.24-25.63 [707kB]
Get: 6 http://gb.archive.ubuntu.com hardy-updates/main libc6-dev 2.7-10ubuntu5 [3344kB]
Get: 7 http://gb.archive.ubuntu.com hardy-updates/main libstdc++6-4.2-dev 4.2.4-1ubuntu4 [1187kB]
Get: 8 http://gb.archive.ubuntu.com hardy-updates/main g++-4.2 4.2.4-1ubuntu4 [2784kB]
Get: 9 http://gb.archive.ubuntu.com hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1440B]
Get: 10 http://gb.archive.ubuntu.com hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get: 11 http://gb.archive.ubuntu.com hardy/main patch 2.5.9-4 [95.6kB]         
Get: 12 http://gb.archive.ubuntu.com hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get: 13 http://gb.archive.ubuntu.com hardy/main build-essential 11.3ubuntu1 [7066B]
Get: 14 http://gb.archive.ubuntu.com hardy/main html2text 1.3.2a-3build2 [87.6kB]
Get: 15 http://gb.archive.ubuntu.com hardy/main gettext 0.17-2ubuntu1 [1978kB] 
Get: 16 http://gb.archive.ubuntu.com hardy/main intltool-debian 0.35.0+20060710.1 [31.6kB]
Get: 17 http://gb.archive.ubuntu.com hardy/main po-debconf 1.0.10 [232kB]      
Get: 18 http://gb.archive.ubuntu.com hardy/main debhelper 6.0.4ubuntu1 [516kB] 
Get: 19 http://gb.archive.ubuntu.com hardy/main fdupes 1.40-4build1 [14.5kB]   
Get: 20 http://gb.archive.ubuntu.com hardy/main intltool 0.37.1-1ubuntu1 [85.8kB]
Get: 21 http://gb.archive.ubuntu.com hardy/main cdbs 0.4.51ubuntu1 [964kB]     
Get: 22 http://gb.archive.ubuntu.com hardy/main dh-make 0.44ubuntu1 [37.0kB]   
Get: 23 http://gb.archive.ubuntu.com hardy/universe dkms 2.0.19-0ubuntu2 [51.5kB]
Get: 24 http://gb.archive.ubuntu.com hardy-updates/main fakeroot 1.9ubuntu1.1 [113kB]
Get: 25 http://gb.archive.ubuntu.com hardy-updates/universe gcc-3.3-base 1:3.3.6-15ubuntu6 [151kB]
Get: 26 http://gb.archive.ubuntu.com hardy-updates/universe libstdc++5 1:3.3.6-15ubuntu6 [296kB]
Fetched 14.4MB in 12s (1173kB/s)                                               
Selecting previously deselected package m4.
(Reading database ... 113949 files and directories currently installed.)
Unpacking m4 (from .../archives/m4_1.4.10-1_i386.deb) ...
Selecting previously deselected package autoconf.
Unpacking autoconf (from .../autoconf_2.61-4_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20070725.1_all.deb) ...
Selecting previously deselected package automake1.7.
Unpacking automake1.7 (from .../automake1.7_1.7.9-9_all.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-25.63_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu5_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.4-1ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.4-1ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3build2_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.17-2ubuntu1_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.10_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_6.0.4ubuntu1_all.deb) ...
Selecting previously deselected package fdupes.
Unpacking fdupes (from .../fdupes_1.40-4build1_i386.deb) ...
Selecting previously deselected package intltool.
Unpacking intltool (from .../intltool_0.37.1-1ubuntu1_all.deb) ...
Selecting previously deselected package cdbs.
Unpacking cdbs (from .../cdbs_0.4.51ubuntu1_all.deb) ...
Selecting previously deselected package dh-make.
Unpacking dh-make (from .../dh-make_0.44ubuntu1_all.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.0.19-0ubuntu2_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.9ubuntu1.1_i386.deb) ...
Selecting previously deselected package gcc-3.3-base.
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-15ubuntu6_i386.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-15ubuntu6_i386.deb) ...Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3build2_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.17-2ubuntu1_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.10_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_6.0.4ubuntu1_all.deb) ...
Selecting previously deselected package fdupes.
Unpacking fdupes (from .../fdupes_1.40-4build1_i386.deb) ...
Selecting previously deselected package intltool.
Unpacking intltool (from .../intltool_0.37.1-1ubuntu1_all.deb) ...
Selecting previously deselected package cdbs.
Unpacking cdbs (from .../cdbs_0.4.51ubuntu1_all.deb) ...
Selecting previously deselected package dh-make.
Unpacking dh-make (from .../dh-make_0.44ubuntu1_all.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.0.19-0ubuntu2_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.9ubuntu1.1_i386.deb) ...
Selecting previously deselected package gcc-3.3-base.
Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-15ubuntu6_i386.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-15ubuntu6_i386.deb) ...

Setting up m4 (1.4.10-1) ...
Setting up autoconf (2.61-4) ...
Setting up autotools-dev (20070725.1) ...
Setting up automake1.7 (1.7.9-9) ...
Setting up linux-libc-dev (2.6.24-25.63) ...
Setting up libc6-dev (2.7-10ubuntu5) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up html2text (1.3.2a-3build2) ...
Setting up gettext (0.17-2ubuntu1) ...
Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.10) ...
Setting up debhelper (6.0.4ubuntu1) ...
Setting up fdupes (1.40-4build1) ...
Setting up intltool (0.37.1-1ubuntu1) ...
Setting up cdbs (0.4.51ubuntu1) ...
Setting up dh-make (0.44ubuntu1) ...
Setting up dkms (2.0.19-0ubuntu2) ...
Setting up fakeroot (1.9ubuntu1.1) ...
Setting up gcc-3.3-base (1:3.3.6-15ubuntu6) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu6) ...
Setting up libstdc++6-4.2-dev (4.2.4-1ubuntu4) ...
Setting up g++-4.2 (4.2.4-1ubuntu4) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...
Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
wishy@NePage2:~$ cd Desktop
wishy@NePage2:~/Desktop$ ls
120.pdf
ati-driver-installer-9-10-x86.x86_64(2).run
ati-driver-installer-9-10-x86.x86_64(2).run.part
ati-driver-installer-9-10-x86.x86_64.run
linux_cat910-inst.pdf
ubuntupocketguide-v1-1.pdf
wishy@NePage2:~/Desktop$ sh ati-driver-installer-9-10-x86.x86_64.run --buildpkg Ubuntu/hardy
Created directory fglrx-install.d22114
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.661........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/hardy

Package /home/wishy/Desktop/xorg-driver-fglrx_8.661-0ubuntu1_i386.deb has been successfully generated
Package /home/wishy/Desktop/xorg-driver-fglrx-dev_8.661-0ubuntu1_i386.deb has been successfully generated
Package /home/wishy/Desktop/fglrx-kernel-source_8.661-0ubuntu1_i386.deb has been successfully generated
Package /home/wishy/Desktop/fglrx-amdcccle_8.661-0ubuntu1_i386.deb has been successfully generated
Package /home/wishy/Desktop/fglrx-modaliases_8.661-0ubuntu1_i386.deb has been successfully generated
Package /home/wishy/Desktop/libamdxvba1_8.661-0ubuntu1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install.d22114
wishy@NePage2:~/Desktop$ 
wishy@NePage2:~/Desktop$ sudo gedit /etc/default/linux-restricted-modules-common
 
wishy@NePage2:~/Desktop$ 
wishy@NePage2:~/Desktop$ sudo gedit /etc/modprobe.d/blacklist-restricted
wishy@NePage2:~/Desktop$ sudo gedit /etc/modprobe.d/blacklist-local
wishy@NePage2:~/Desktop$ sudo dpkg -i xorg-driver-fglrx_8.661-0ubuntu1_i386.deb fglrx-kernel-source_8.661-0ubuntu1_i386.deb fglrx-amdccle_8.661-0ubuntu1_i386.deb
(Reading database ... 116888 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 1:7.1.0-8-3+2.6.24.18-25.2 (using xorg-driver-fglrx_8.661-0ubuntu1_i386.deb) ...
 * Stopping atieventsd                                                                                    [ OK ] 
Unpacking replacement xorg-driver-fglrx ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.661-0ubuntu1_i386.deb) ...
dpkg: error processing fglrx-amdccle_8.661-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Setting up fglrx-kernel-source (2:8.661-0ubuntu1) ...
Loading new fglrx-8.661 DKMS files...
First Installation: checking all kernels...
Building initial module for 2.6.24-25-generic, architecture -a i686
Done.
Running module version sanity check.

fglrx.ko:
 - Original module
   - Found /lib/modules/2.6.24-25-generic/volatile/fglrx.ko
   - Storing in /var/lib/dkms/fglrx/original_module/2.6.24-25-generic/i686/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/2.6.24-25-generic/updates/dkms/

depmod......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)

Setting up xorg-driver-fglrx (2:8.661-0ubuntu1) ...
Installing new version of config file /etc/init.d/atieventsd ...
Installing new version of config file /etc/ati/signature ...
Installing new version of config file /etc/ati/atiogl.xml ...
Installing new version of config file /etc/ati/amdpcsdb.default ...
Installing new version of config file /etc/ati/control ...
Installing new version of config file /etc/ati/authatieventsd.sh ...
 Removing any system startup links for /etc/init.d/atieventsd ...
   /etc/rc0.d/K20atieventsd
   /etc/rc1.d/K20atieventsd
   /etc/rc2.d/S20atieventsd
   /etc/rc3.d/S20atieventsd
   /etc/rc4.d/S20atieventsd
   /etc/rc5.d/S20atieventsd
   /etc/rc6.d/K20atieventsd
 Adding system startup for /etc/init.d/atieventsd ...
   /etc/rc0.d/K31atieventsd -> ../init.d/atieventsd
   /etc/rc1.d/K31atieventsd -> ../init.d/atieventsd
   /etc/rc6.d/K31atieventsd -> ../init.d/atieventsd
   /etc/rc2.d/S31atieventsd -> ../init.d/atieventsd
   /etc/rc3.d/S31atieventsd -> ../init.d/atieventsd
   /etc/rc4.d/S31atieventsd -> ../init.d/atieventsd
   /etc/rc5.d/S31atieventsd -> ../init.d/atieventsd

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-25-generic
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 fglrx-amdccle_8.661-0ubuntu1_i386.deb
wishy@NePage2:~/Desktop$ sudo dpkg -i fglrx-modaliases_8.661-0ubuntu1_i386.deb
Selecting previously deselected package fglrx-modaliases.
(Reading database ... 116995 files and directories currently installed.)
Unpacking fglrx-modaliases (from fglrx-modaliases_8.661-0ubuntu1_i386.deb) ...
Setting up fglrx-modaliases (2:8.661-0ubuntu1) ...
wishy@NePage2:~/Desktop$ 
```and fglrxinfo now says

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 Pro AGP
OpenGL version string: 2.1.9026

```Unfortunately I still can't get away from cloned screens so I guess it's more reading tonight. I do however have windows that wobble when dragged so I guess that makes up for it.:-k

---

### Post by Wishy2009 on 2009-11-27
xorg.cong FWIW

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```One thing that I have noticed is that despite having the catalyst drivers installed now I don't see the control appear in applications.

---

