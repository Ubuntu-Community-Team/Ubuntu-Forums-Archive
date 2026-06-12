---
title: "Intel NIC not detected"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by pjizz on 2008-09-09
Hello All,

I have a Dell Inspiron 530 with Vista.  I recently set it up to dual boot with Ubuntu using a Live CD for 7.04 (Feisty?).  Everything went fine, except the Network card is not detected.

My chipset is Intel g33 and my NIC is Intel(R) 82562V-2 10/100 Network Connection.  The internet works fine in Vista, just not in Ubuntu.

I also found this thread[(CLICK ME)]("http://ubuntuforums.org/archive/index.php/t-502058.html") in the archives, and followed Hiweed's instructions.  This is the output I came up with:

> 
parker@thefortress:~$ dir
 
Desktop  Examples

parker@thefortress:~$ cd Desktop

parker@thefortress:~/Desktop$ dir
 
e1000-8.0.6.tar.gz  terminal\ output

parker@thefortress:~/Desktop$ tar xfvz e1000-8.0.6.tar.gz

e1000-8.0.6/
e1000-8.0.6/src/
e1000-8.0.6/src/Makefile
e1000-8.0.6/src/e1000.h
e1000-8.0.6/src/e1000_82540.c
e1000-8.0.6/src/e1000_82541.c
e1000-8.0.6/src/e1000_82541.h
e1000-8.0.6/src/e1000_82542.c
e1000-8.0.6/src/e1000_82543.c
e1000-8.0.6/src/e1000_82543.h
e1000-8.0.6/src/e1000_api.c
e1000-8.0.6/src/e1000_api.h
e1000-8.0.6/src/e1000_defines.h
e1000-8.0.6/src/e1000_ethtool.c
e1000-8.0.6/src/e1000_hw.h
e1000-8.0.6/src/e1000_mac.c
e1000-8.0.6/src/e1000_mac.h
e1000-8.0.6/src/e1000_main.c
e1000-8.0.6/src/e1000_manage.c
e1000-8.0.6/src/e1000_manage.h
e1000-8.0.6/src/e1000_nvm.c
e1000-8.0.6/src/e1000_nvm.h
e1000-8.0.6/src/e1000_osdep.h
e1000-8.0.6/src/e1000_param.c
e1000-8.0.6/src/e1000_phy.c
e1000-8.0.6/src/e1000_phy.h
e1000-8.0.6/src/e1000_regs.h
e1000-8.0.6/src/kcompat.c
e1000-8.0.6/src/kcompat.h
e1000-8.0.6/src/kcompat_ethtool.c
e1000-8.0.6/COPYING
e1000-8.0.6/README
e1000-8.0.6/pci.updates
e1000-8.0.6/e1000.7
e1000-8.0.6/e1000.spec
e1000-8.0.6/SUMS

parker@thefortress:~/Desktop$ cd e1000-8.0.6

parker@thefortress:~/Desktop/e1000-8.0.6$ dir

COPYING  e1000.7  e1000.spec  pci.updates  README  src  SUMS

parker@thefortress:~/Desktop/e1000-8.0.6$ cd src

parker@thefortress:~/Desktop/e1000-8.0.6/src$ dir

e1000_82540.c  e1000_api.h      e1000_main.c    e1000_phy.c
e1000_82541.c  e1000_defines.h  e1000_manage.c  e1000_phy.h
e1000_82541.h  e1000_ethtool.c  e1000_manage.h  e1000_regs.h
e1000_82542.c  e1000.h          e1000_nvm.c     kcompat.c
e1000_82543.c  e1000_hw.h       e1000_nvm.h     kcompat_ethtool.c
e1000_82543.h  e1000_mac.c      e1000_osdep.h   kcompat.h
e1000_api.c    e1000_mac.h      e1000_param.c   Makefile

parker@thefortress:~/Desktop/e1000-8.0.6/src$ sudo make install

Password:
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/parker/Desktop/e1000-8.0.6/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_main.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_82540.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_82542.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_82541.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_82543.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_mac.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_nvm.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_phy.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_manage.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_param.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_ethtool.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/kcompat.o
  CC [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000_api.o
  LD [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/parker/Desktop/e1000-8.0.6/src/e1000.mod.o
  LD [M]  /home/parker/Desktop/e1000-8.0.6/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
gzip -c ../e1000.7 > e1000.7.gz

# remove all old versions of the driver

find /lib/modules/2.6.20-15-generic -name e1000.ko -exec rm -f {} \; || true
find /lib/modules/2.6.20-15-generic -name e1000.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000.ko /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man: 
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.

parker@thefortress:~/Desktop/e1000-8.0.6/src$ sudo modprobe e1000

parker@thefortress:~/Desktop/e1000-8.0.6/src$ 



you can see that it said "cannot write to /var/cahce/man/cat7/e1000.7.gz in catman mode"

it also did nothing with i entered the command "sudo modprobe e1000", but I thought this could be because of the error from the "make install" command.

I hope there is something simple I can do to fix this.  I'd really like to get rolling with Ubuntu.  I'll check this thread frequently, so any information you need just let me know.

---

### Post by pjizz on 2008-09-09
One more note: I took some steps at another forum, just some information-gathering commands.  Here is the link to that information:

[http://www.linuxquestions.org/questions/ubuntu-63/no-network-connection-in-ubuntu-after-setting-up-dual-boot-668483/](http://www.linuxquestions.org/questions/ubuntu-63/no-network-connection-in-ubuntu-after-setting-up-dual-boot-668483/)

---

### Post by pjizz on 2008-09-09
One more note: I took some steps at another forum, just some information-gathering commands.  Here is the link to that information:

[http://www.linuxquestions.org/questions/ubuntu-63/no-network-connection-in-ubuntu-after-setting-up-dual-boot-668483/](http://www.linuxquestions.org/questions/ubuntu-63/no-network-connection-in-ubuntu-after-setting-up-dual-boot-668483/)

---

### Post by lilmale1 on 2008-09-09
do u still need help. i can help

---

### Post by pjizz on 2008-09-09
yessssss please thank you

---

### Post by lilmale1 on 2008-09-09
type under application>terminal

type su
type your user password

type lspci

and check which one is you wifi or ethernet card your using

after that come back and let me know

---

### Post by lilmale1 on 2008-09-09
ok you will need ndiswrapper and your inf file from vista
check if you got the inf with the driver part

---

### Post by lilmale1 on 2008-09-09
[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148)


ndiswrapper there


download it to the computer in the directory where ur user name is

for example mine is xbatis so put the forder tar gz there

---

### Post by lilmale1 on 2008-09-09
while you download and put it there i forget get your ubuntu cd
and put that in your computer

and install build essentials that works with ndiswrapper.1.5.3.tar.gz
  
but that is next so put the cd

type in terminal 

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential


type that right one after another and then y to any yes

---

### Post by lilmale1 on 2008-09-09
are u with me

---

### Post by pjizz on 2008-09-09
yea sorry i was going the dishes

i'll have to reboot to do all this but then i'll get right back with the info.  thanks for checkin the foum.

---

### Post by pjizz on 2008-09-09
okay i got ndiswrapper and put it in the username folder in ubuntu.

i ran the commands that you said, and here was my output.  the update command seemed not to work, which is expected since i have no internet connection in ubuntu

> 
parker@thefortress:~$ su
Password: 
su: Authentication failure
Sorry.
parker@thefortress:~$ su
Password: 
su: Authentication failure
Sorry.
parker@thefortress:~$ sudo lspci
Password:
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Unknown device 29c2 (rev 02)
00:19.0 Ethernet controller: Intel Corporation Unknown device 10c0 (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
parker@thefortress:~$

and here are the others

> parker@thefortress:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [b0eec9ebb2f73cb755ea5ff17b89a5e4-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
This disc is called: 
'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
Copying package lists...gpgv: Signature made Sun 15 Apr 2007 06:52:01 AM PDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
parker@thefortress:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg                          
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US               
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US         
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US           
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US         
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg                  
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US       
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US 
  Could not resolve 'us.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                   
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US        
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US  
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US    
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US  
  Could not resolve 'security.ubuntu.com'
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
  Could not resolve 'us.archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
  Could not resolve 'us.archive.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
parker@thefortress:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8050kB of archives.
After unpacking 33.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package linux-libc-dev.
(Reading database ... 88002 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.20-15.27_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up linux-libc-dev (2.6.20-15.27) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
parker@thefortress:~$ 



alright, take a look, let me know what ya think.

---

### Post by lilmale1 on 2008-09-09
ndiswrapper didn't isntall because you need extrack it first

to do it you will need this command

[COLOR="darkred"]tar -zxvf ndiswrapper-1.53.tar.gz[/COLOR]

after that type this in red too, it look like this 

type command 

[COLOR="darkred"]make[/COLOR]                          

and then command:

[COLOR="darkred"]make install[/COLOR]

xbatis@xbatis-desktop:~$ [COLOR="darkred"]cd /home/xbatis/ndiswrapper-1.53[/COLOR]

                            xbatis is a example of my name
                            put your name of your computer there


and then type

[COLOR="darkred"]ndisgtk[/COLOR]

it will tell you to type apt-get intall ndisgtk

type it again and pow. you have your installer.

command: [COLOR="darkred"]ndisgtk[/COLOR]

---

### Post by lilmale1 on 2008-09-09
oh yeah, i forgot after installer shows

install the inf file that you have with the drivers folders
i think it would be easey if you also put that into ur name directory

and then let me know if you need more help

cuz wifi radar works great radar that using network manager
imbeded in ubuntu 8

---

### Post by pjizz on 2008-09-09
okay i didn't exactly understand your instructions but here's what i did...

> 

parker@thefortress:~$ tar -zxvf ndiswrapper-1.53.tar.gz
ndiswrapper-1.53/
ndiswrapper-1.53/README
ndiswrapper-1.53/loadndisdriver.8
ndiswrapper-1.53/ndiswrapper.spec
ndiswrapper-1.53/INSTALL
ndiswrapper-1.53/ChangeLog
ndiswrapper-1.53/ndiswrapper.8
ndiswrapper-1.53/utils/
ndiswrapper-1.53/utils/ndiswrapper
ndiswrapper-1.53/utils/loadndisdriver.c
ndiswrapper-1.53/utils/ndiswrapper-buginfo
ndiswrapper-1.53/utils/Makefile
ndiswrapper-1.53/driver/
ndiswrapper-1.53/driver/mkexport.sh
ndiswrapper-1.53/driver/wrapmem.c
ndiswrapper-1.53/driver/pnp.h
ndiswrapper-1.53/driver/longlong.h
ndiswrapper-1.53/driver/rtl.c
ndiswrapper-1.53/driver/ntoskernel.c
ndiswrapper-1.53/driver/loader.h
ndiswrapper-1.53/driver/iw_ndis.c
ndiswrapper-1.53/driver/win2lin_stubs.S
ndiswrapper-1.53/driver/wrapper.c
ndiswrapper-1.53/driver/winnt_types.h
ndiswrapper-1.53/driver/wrapndis.h
ndiswrapper-1.53/driver/usb.h
ndiswrapper-1.53/driver/pe_linker.h
ndiswrapper-1.53/driver/ndis.h
ndiswrapper-1.53/driver/divdi3.c
ndiswrapper-1.53/driver/ndiswrapper.h
ndiswrapper-1.53/driver/hal.c
ndiswrapper-1.53/driver/wrapndis.c
ndiswrapper-1.53/driver/ntoskernel.h
ndiswrapper-1.53/driver/crt.c
ndiswrapper-1.53/driver/workqueue.c
ndiswrapper-1.53/driver/ntoskernel_io.c
ndiswrapper-1.53/driver/lin2win.h
ndiswrapper-1.53/driver/pnp.c
ndiswrapper-1.53/driver/loader.c
ndiswrapper-1.53/driver/ndis.c
ndiswrapper-1.53/driver/iw_ndis.h
ndiswrapper-1.53/driver/pe_linker.c
ndiswrapper-1.53/driver/wrapmem.h
ndiswrapper-1.53/driver/mkstubs.sh
ndiswrapper-1.53/driver/usb.c
ndiswrapper-1.53/driver/wrapper.h
ndiswrapper-1.53/driver/Makefile
ndiswrapper-1.53/driver/proc.c
ndiswrapper-1.53/AUTHORS
ndiswrapper-1.53/Makefile
parker@thefortress:~$ type command
command is a shell builtin
parker@thefortress:~$ make
make: *** No targets specified and no makefile found.  Stop.
parker@thefortress:~$ command make
make: *** No targets specified and no makefile found.  Stop.
parker@thefortress:~$ make install
make: *** No rule to make target `install'.  Stop.
parker@thefortress:~$ make ndiswrapper-1.53
make: Nothing to be done for `ndiswrapper-1.53'.
parker@thefortress:~$ make install ndiswrapper-1.53
make: *** No rule to make target `install'.  Stop.
parker@thefortress:~$ cd /home/parker/ndiswrapper-1.53
parker@thefortress:~/ndiswrapper-1.53$ ndisgtk
The program 'ndisgtk' is currently not installed.  You can install it by typing:
sudo apt-get install ndisgtk
Make sure you have the 'universe' component enabled
bash: ndisgtk: command not found
parker@thefortress:~/ndiswrapper-1.53$ ndisgtk
The program 'ndisgtk' is currently not installed.  You can install it by typing:
sudo apt-get install ndisgtk
Make sure you have the 'universe' component enabled
bash: ndisgtk: command not found
parker@thefortress:~/ndiswrapper-1.53$ sudo apt-get install ndisgtk
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndisgtk
parker@thefortress:~/ndiswrapper-1.53$ ndisgtk
The program 'ndisgtk' is currently not installed.  You can install it by typing:
sudo apt-get install ndisgtk
Make sure you have the 'universe' component enabled
bash: ndisgtk: command not found
parker@thefortress:~/ndiswrapper-1.53$ cd /
parker@thefortress:/$ ndisgtk
The program 'ndisgtk' is currently not installed.  You can install it by typing:
sudo apt-get install ndisgtk
Make sure you have the 'universe' component enabled
bash: ndisgtk: command not found
parker@thefortress:/$ make install
make: *** No rule to make target `install'.  Stop.



---

### Post by lilmale1 on 2008-09-09
u extracted it correctly just when u put type command isn't right

i meant to type command bold in red
so u would type 

[COLOR="Red"]tar -zxvf ndiswrapper-1.53.tar.gz[/COLOR]

then

[COLOR="Red"]cd /home/xbatis/ndiswrapper-1.53[/COLOR]

where xbatis is your computer name

then

[COLOR="red"]make[/COLOR]


then

[COLOR="red"]make install[/COLOR]


type

[COLOR="red"]ndisgtk[/COLOR]

then, im not sure but it tell you that you need to install
apt-get install ndisgtk

when u press y for yes.. and when that does it job 

type

[COLOR="red"]ndisgtk[/COLOR]               once more time.

---

### Post by lilmale1 on 2008-09-09
ok so now that i got it right this time.
you can use any driver that has an inf. file
you will notice that because it will ask you for one

this is the package site for wifi radar.
you just run it and i'll work just like that

[http://packages.debian.org/etch/wifi-radar](http://packages.debian.org/etch/wifi-radar)

click on the last thing that is bold in "all"\
download it and put it in you ubuntu comp and open it
instal package and your done with that

try this video when you reboot after intalling wifi radar
it will show u how to configure password by selecting you network


[http://www.youtube.com/watch?v=465rGa_uXfY](http://www.youtube.com/watch?v=465rGa_uXfY)

after your done with that close wifi radar 
go to the top of your screen where the little internet icon screnn is and click once on it it will show you your networks
or network and  select it and you should be done.

---

### Post by pjizz on 2008-09-09
okay i'm getting a little confused.  i'm trying to configure a wired NIC, not a wireless card.  is this still what i'm supposed to do?

---

### Post by lilmale1 on 2008-09-09
ok here. put the inf and .sys file that have the same name but diffenrent extension on you directory of computer name
REMEMBER JUST THE TWO FILE NOT THE WHOLE FOLDER.



type


[COLOR="red"]ndiswrapper -i /home/xbatis/NET8180.INF[/COLOR]

NOTE: MY NAME IS XBATIS AND THE MY INF IS CALL NET8180.INF

SO PUT YOURS.

AND THEN SHOW ME THE LOG
BECAUSE THAT SHOULD AUTOMATICALLY INSTALL THE FILES
AND CONFIGURE THE MODPROBE
THAT MEANS TO INSTALL IT
AFTER THAT I'LL GET U ANOTHER OPEN SOURCE ALIKE WIFI RADAR BUT
IN WIRED

---

### Post by pjizz on 2008-09-09
i don't know what you mean by the .inf and .sys files.  which ones?

---

### Post by lilmale1 on 2008-09-10
hold up im going to get the drivers for you because it looks like the only got .exe file

im going to search in driveguide and if they have them i will need to upload them somewhere so u can get them


t

---

### Post by lilmale1 on 2008-09-10
I should email you the files there not to big
i got them already and they are for linux

---

### Post by lilmale1 on 2008-09-10
ndiswrapper -i 

it does really work

so i came up with this great idea for you

start up your computer on vista,,, i say because you will get the files needed from there....if you want to know what im talking about vista files and xp files are all the same as sys and inf.

so in order to get them and put them the new ubuntu way
is to copy and paste them to a flash drive. and then put them yes on your name directory. and go from there.

heres how you do it. trust you canot mess up you computer because they are the right files just the ubuntu way to install them

go to vista. go to my computer, right click, open manage
click on device manager that is on the left side of them computer management screen.

so go to network adapter
look for your netword card that is ethernet

double click on your card or right click and 
select properties>>>> click on the tab driver

go to driver detail

see which is your driver. to get it from its location 

write down the location like mine is

C:\Windows\system32\DRIVERS\b57nd60x.sys

thats an example

if you really want to fix i suggest going there

by 

your c drive
windows folder
system32 folder
DRIVERS folder
and pow your driver b57nd60x.sys

most important are inf and sys files
but i think sys is ok

let me try it tonight with my own card
and then i'll tell you the results

so just wait get the drivers copy them in the mean while
and will see tomorrow how it goes

thanks, bye

---

### Post by pjizz on 2008-09-10
okay i found mine.  it's c:\windows\system32\drivers\e1e6032.sys

i don't understand what you mean by "and pow your driver b57nd60x.sys"

i also don't see any .inf files in the driver details for the network adapter.  

so, you're going to have me install the .sys file with ndiswrapper?

---

### Post by lilmale1 on 2008-09-10
go to that location c drive, windows, system32, drivers and copy ur sys file


then go to you ubuntu computer paste it to name of computer directory


and type like this examples except fill in your data

ndiswrapper -i /home/xbatis/e1e6032.sys       where xbatis is ur comp name

---

### Post by lilmale1 on 2008-09-10
if that dont work we will install wine that is a program that will let u install windows vista stuff. like if it where to be windows since they only have a .exe file we can just run it if it where to be vista then install it like that


but first try that and then tell me when ur done

---

### Post by pjizz on 2008-09-10
so i don't need the .inf file?

---

### Post by lilmale1 on 2008-09-10
no just try  that

and paste the log here.

on my comp it only read a sys file when i tried to use ethernet

---

### Post by lilmale1 on 2008-09-10
sorry but now i know where your inf is at

you will have to go get it, and we wont try wine anymore as that takes up more details.

go to c drive. windows. system32. driverstore. and get e1e6032.inf

---

### Post by pjizz on 2008-09-10
okay, i got the .sys file

but i don't see an .inf file (or any files for that matter) in the driverstore folder.  i do see en-US, FileRepository, and Temp folders.  

EDIT: okay i found the .inf file, in the FileRepository folder and then in an e1e6032.inf_344290b6

sorry i took a minute...accident down the street knocked the power out.  i'm going to copy those over and try it out...i'll get back to you with the output

---

### Post by lilmale1 on 2008-09-10
sorry its cuz our menus are different

try file repsitory

---

### Post by pjizz on 2008-09-10
okay strangest thing....i have the .inf and .sys file on my jumpdrive ready to follow your instructions and i notice that my internet is up and working (im running ubuntu now)

any idea what's going on?  if i deleted the files on the jumpdrive would it not work anymore.

*royally confused*

---

### Post by lilmale1 on 2008-09-10
ndiswrapper -i /home/xbatis/e1e6032.inf

---

### Post by pjizz on 2008-09-10
parker@thefortress:~$ ndiswrapper -i /home/parker/e1e6032.sys
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
parker@thefortress:~$ sudo apt-get install ndiswrapper-common
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
parker@thefortress:~$ 
parker@thefortress:~$ ndiswrapper -i /home/parker/e1e6032.inf
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
parker@thefortress:~$

---

### Post by lilmale1 on 2008-09-10
first

[COLOR="Red"]sudo apt-get install ndiswrapper-common[/COLOR]

then first

[COLOR="Red"]ndiswrapper -i /home/xbatis/e1e6032.inf[/COLOR]

---

### Post by pjizz on 2008-09-10
> parker@thefortress:~$ sudo apt-get install ndiswrapper-common
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
parker@thefortress:~$ ndiswrapper -i /home/parker/e1e6032.inf
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
parker@thefortress:~$ 


f

---

### Post by lilmale1 on 2008-09-10
i get the same thing over here

but try typing su the your password 

check is ndis wrapper is installed by typing

cd /home/xbatis/ndiswrapper-1.53



it should go to the next line and look like this

root@xbatis-desktop:/home/xbatis/ndiswrapper-1.53#

---

### Post by pjizz on 2008-09-10
okay i updated and restarted and saw taht two new options were added to GRUB...its the new shell 2.6.20-17 generic and 2.6.20-17 safemode...when i booted to the new kernel, networking was gone, so i'm back to 15 generic

---

### Post by lilmale1 on 2008-09-10
[http://packages.ubuntu.com/feisty/all/ndiswrapper-common/download](http://packages.ubuntu.com/feisty/all/ndiswrapper-common/download)

you need the north america one
just install it since its for all systems

double click and install package

---

### Post by pjizz on 2008-09-10
this seems to make a little bit of sense...since with noob12's instructions ([http://ubuntuforums.org/showthread.php?p=3370406](http://ubuntuforums.org/showthread.php?p=3370406)) you had to do it again once you had the new kernel

---

### Post by pjizz on 2008-09-10
okay...i used the auto thing to install ndiswrapper and now i have it, including a gtk frontend...i'm attaching an image of what i got

---

### Post by pjizz on 2008-09-10
i was able to use the ndiswrapper frontend to install the .inf file...i'm going to boot in the new kernel and try that there

---

### Post by lilmale1 on 2008-09-10
hey u lost me

can u explain everything in simple mode

---

### Post by pjizz on 2008-09-10
okay...when i boot into 2.6.20-15 kernel i have network...when i boot into the 2.6.20-17 kernel i don't have any.

i just tried to use ndiswrapper to install the same .inf file i got from vista...but it said the driver was already installed...here is an image

---

### Post by lilmale1 on 2008-09-10
im not sure what your telling me


what is kernel 

and how does it work and how did you switch to one to another


plus i'll be back i got to go pick up my sis at school
let me know bye

---

### Post by pjizz on 2008-09-10
well, i really don't know what happened...but i've upgraded all the way to Hardy and still have network connex, so i'm going to give up on trying to figure out why and just accept that it works.  thanks for all your help with this!

---

