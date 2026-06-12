---
title: "How to install Tar file"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by geoher on 2008-10-10
HI all. I downloaded a tar file from ralink for my usb wifi adapter and extracted folder "Module" which has a lot of files, can anyone tell me in "dummies steps" what to do next. I have spent hours trying to install it.
thanks in advance

---

### Post by StOoZ on 2008-10-10
usually it comes with instructions , in case its a driver , is there a README file or any documentation?

---

### Post by geoher on 2008-10-10
ok read the readme and started this is what I got
bash: /home/george/Documents/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/Makefile.6: Permission denied

---

### Post by mespinos on 2008-10-10
run "sudo" before the command

---

### Post by tuxxy on 2008-10-10
Use a sudo at the start of the command to enable admin privs, which should then allow it to run.

---

### Post by geoher on 2008-10-10
ok thanks to all here is what i get

$ sudo cp Documents/2008_0506_RT73_Linux_STA_Drv1.1.0.1/Module/Makefile.6  ./Makefile
george@linux:~$ sudo make all
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/george modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: *** No rule to make target `/home/george/rtmp_main.o', needed by `/home/george/rt73.o'.  Stop.
make[1]: *** [_module_/home/george] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2
george@linux:~$

ican't get past make all

this is the read me

README
Ralink Tech Inc.
[http://www.ralinktech.com](http://www.ralinktech.com)
ModelName:
RT73(RT2571W) Wireless Lan Linux Driver
Driver lName:
rt73
Supporting Kernel:
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.
Description:
This is a linux device driver for Ralink RT73 a/b/g WLAN Card.
Contents:
Makefile.4		    : Makefile for kernel 2.4 series
Makefile.6		    : Makefile for kernel 2.6 series
*.c					: c files
*.h					: header files
Features:
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode 
   with open or shared or WPA-PSK or WPA2-PSK authentication method. 
   NONE, WEP, TKIP and AES encryption. 
Build Instructions:  
1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.
2> $cp Makefile.4  ./Makefile       # [kernel 2.4]
    or
   $cp Makefile.6  ./Makefile       # [kernel 2.6]
3> [kernel 2.4]
    $chmod 755 Configure
    $make config         # config build linux os version
4> $make all            # compile driver source code
4.1> $make install
5> $cp rt73.bin /etc/Wireless/RT73STA/	    # copy firmware
6>  $dos2unix rt73sta.dat
    $cp rt73sta.dat  /etc/Wireless/RT73STA/rt73sta.dat       
    # !!!check if it is a binary file before loading !!!  
7> $load                
    #[kernel 2.4]
    #    $/sbin/insmod rt73.o
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt73.ko
    #    $/sbin/ifconfig rausb0 inet YOUR_IP up

---

### Post by StOoZ on 2008-10-10
try :
> sudo apt-get install build-essential

and then try again...

---

### Post by geoher on 2008-10-11
Thanks StOoZ that worked

---

