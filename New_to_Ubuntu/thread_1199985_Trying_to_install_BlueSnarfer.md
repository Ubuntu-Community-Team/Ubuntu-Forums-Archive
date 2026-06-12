---
title: "Trying to install BlueSnarfer"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by callumacrae on 2009-06-29
Hello,

I'm trying to install BlueSnarfer on my newly installed version of Ubuntu on my ASUS Eee 1000. I've tried several methods, neither of which have worked.

I have downloaded the package bluesnarfer.tar.gz.

I'm intending on using this program totally legally, seeing if I can secure my own phone against such software.

Thanks for your help,
~Callum

---

### Post by ramazani on 2009-09-29
hi after thee house searching on line this how i installed bluesnarfer on ubuntu 9.04



install bluesnarfer in ubuntu 9.04
first download this two file below
bluesnarfer.tar.gz (program), available at [www.alighieri.org/project.html](www.alighieri.org/project.html)
bluez-4.54.tar.gz 9programe). available at [http://www.bluez.org/download/](http://www.bluez.org/download/)
open a sell type
sudo mkdir /opt/bluesnarfer
then copy this two download to it 
sudo cp -r bluesnarfer.tar.gz /opt/bluesnarfer
sudo cp -r bluez-4.54.tar.gz /opt/bluesnarfer

now cd /opt/bluesnarfer then type ls -l
first extract bluez-4.54.tar.gz
sudo tar xvzf bluez-4.54.tar.gz and make sure you have installed libdus
if not install it first before extract you file download
sudo apt-get install libdbus-1-dev libdbus-glib-1-dev

after extract tar bluez-4.54.tar.gz 
make sure you in in directory
cd /opt/bluesnarfer/
ls -l
cd bluez-4.54  then type in
sudo ./configure –prefix=/usr
when it doen type
sudo make && sudo make install

not untar bluesnarfer
cd /opt/bluesnarfer/
ls -l
sudo tar xvzf bluesnarfer.tar.gz
make

---

### Post by callumacrae on 2009-10-06
Doesn't work:

> root@callum-laptop:/opt/bluesnarfer/bluesnarfer# make
gcc -Iinclude -W -g3 -lbluetooth src/bluesnarfer.c -o bluesnarfer
src/bluesnarfer.c:29:33: error: bluetooth/bluetooth.h: No such file or directory
src/bluesnarfer.c:30:27: error: bluetooth/hci.h: No such file or directory
src/bluesnarfer.c:31:31: error: bluetooth/hci_lib.h: No such file or directory
src/bluesnarfer.c:32:30: error: bluetooth/rfcomm.h: No such file or directory
src/bluesnarfer.c: In function ‘parse_rw’:
src/bluesnarfer.c:39: warning: incompatible implicit declaration of built-in function ‘strchr’
src/bluesnarfer.c: In function ‘bluesnarfer’:
src/bluesnarfer.c:146: error: ‘HCI_UP’ undeclared (first use in this function)
src/bluesnarfer.c:146: error: (Each undeclared identifier is reported only once
src/bluesnarfer.c:146: error: for each function it appears in.)
src/bluesnarfer.c:147: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
src/bluesnarfer.c:152: error: ‘BTPROTO_RFCOMM’ undeclared (first use in this function)
src/bluesnarfer.c: In function ‘bt_get_remote_name’:
src/bluesnarfer.c:190: error: storage size of ‘cr’ isn’t known
src/bluesnarfer.c:193: error: ‘bdaddr_t’ undeclared (first use in this function)
src/bluesnarfer.c:193: error: expected ‘;’ before ‘bdaddr’
src/bluesnarfer.c:197: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
src/bluesnarfer.c:201: error: ‘bdaddr’ undeclared (first use in this function)
src/bluesnarfer.c:203: warning: incompatible implicit declaration of built-in function ‘memcpy’
src/bluesnarfer.c:204: error: ‘ACL_LINK’ undeclared (first use in this function)
src/bluesnarfer.c:206: error: ‘HCIGETCONNINFO’ undeclared (first use in this function)
src/bluesnarfer.c:208: error: ‘HCI_DM1’ undeclared (first use in this function)
src/bluesnarfer.c:208: error: ‘HCI_DH1’ undeclared (first use in this function)
src/bluesnarfer.c:223: error: ‘HCI_OE_USER_ENDED_CONNECTION’ undeclared (first use in this function)
src/bluesnarfer.c: In function ‘rfcomm_read’:
src/bluesnarfer.c:251: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c: In function ‘bt_rfcomm’:
src/bluesnarfer.c:265: error: storage size of ‘req’ isn’t known
src/bluesnarfer.c:267: error: ‘bdaddr_t’ undeclared (first use in this function)
src/bluesnarfer.c:267: error: expected ‘;’ before ‘bdaddr’
src/bluesnarfer.c:276: error: ‘bdaddr’ undeclared (first use in this function)
src/bluesnarfer.c:278: warning: incompatible implicit declaration of built-in function ‘memset’
src/bluesnarfer.c:284: warning: incompatible implicit declaration of built-in function ‘memcpy’
src/bluesnarfer.c:284: error: ‘BDADDR_ANY’ undeclared (first use in this function)
src/bluesnarfer.c:287: error: ‘RFCOMMCREATEDEV’ undeclared (first use in this function)
src/bluesnarfer.c:289: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
src/bluesnarfer.c: In function ‘bt_rfcomm_config’:
src/bluesnarfer.c:313: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
src/bluesnarfer.c:321: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
src/bluesnarfer.c:334: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
src/bluesnarfer.c: In function ‘custom_cmd’:
src/bluesnarfer.c:382: warning: incompatible implicit declaration of built-in function ‘strstr’
src/bluesnarfer.c:390: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c:392: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
src/bluesnarfer.c: In function ‘bt_rfcomm_rel’:
src/bluesnarfer.c:411: error: storage size of ‘req’ isn’t known
src/bluesnarfer.c:413: warning: incompatible implicit declaration of built-in function ‘memset’
src/bluesnarfer.c:416: error: ‘RFCOMMRELEASEDEV’ undeclared (first use in this function)
src/bluesnarfer.c: In function ‘rw_cmd’:
src/bluesnarfer.c:434: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c:442: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c:455: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c:457: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’
src/bluesnarfer.c: In function ‘parse’:
src/bluesnarfer.c:500: warning: incompatible implicit declaration of built-in function ‘memset’
src/bluesnarfer.c:503: warning: incompatible implicit declaration of built-in function ‘strchr’
src/bluesnarfer.c:506: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c: In function ‘search_cmd’:
src/bluesnarfer.c:550: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c: In function ‘list_cmd’:
src/bluesnarfer.c:600: warning: incompatible implicit declaration of built-in function ‘strlen’
src/bluesnarfer.c:614: warning: incompatible implicit declaration of built-in function ‘strchr’
src/bluesnarfer.c:622: warning: incompatible implicit declaration of built-in function ‘strstr’
src/bluesnarfer.c: In function ‘info_cmd’:
src/bluesnarfer.c:643: warning: incompatible implicit declaration of built-in function ‘strlen’
make: *** [bluesnarfer] Error 1


---

