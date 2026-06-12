---
title: "I don't succeed in installing the modem usb!!! Help!!!"
date: 2005-09-29
forum: Networking &amp; Wireless
---

### Post by Cocomi on 2005-09-29
I have a modem USB Digicom Michelangelo usb cx
I have connected the modem to the computer through the  usb  port
On the computer I have installed the OS Ubuntu 5.10 Breezy Badger
(AMD64)
Going to see in the installed devices the modem regularly appears
Then I have installed the modem in the following way after having
verified that the drivers (eciadsl-usermode-0.10.tar.gz ) support this
modem:

I have unloaded the file (driver)  eciadsl-usermode-0.10.tar.gz . I
have download the  file  eciadsl_0.10-1_amd64.deb  on the sites of
Ubuntu because the correspondent file in
eciadsl-usermode-0.10.tar.gz  (eciadsl_0.10--1.i386.deb ) doesn't
recognize the kernel for amd

I have opened the terminal

su 
(password) 

I have decompressed in a directory(here I will denominate the
directory : 'eciadsl-usermode-0.10' )   the file 

tar zxvf eciadsl-usermode-0.10.tar.gz 


cd 'eciadsl-usermode-0.10' 

./configure 
make 
make install 

dpkg -i  eciadsl_0.10-1_amd64.deb

To this point I have decompressed the following file that is contained
in the file of the drivers(eciadsl-usermode-0.10.tar.gz) and that it
contains what it serves for syncronizing the modem during the
configuration

tar zxvf eciadsl-synch_bin.tar.gz 

I enter the directory created above decompressing

cd 'eciadsl-synch_bin' 

 Now we copy the whole files in the directory where Linux has
installed the drivers. 

cp *.*    ' /etc/eciadsl' 


 I now close the terminal, and I restart it 
 
su 
(password mia)

 To this point throwing the program to configure  the modem:
 
cd '/usr/local/bin' 
eciadsl-config

 I configure the modem with all the his proper parameters and with
those related to my provider (precise that have installed already in
the same way the same modem but on another Linux distribution and I
have not had problems)

To this point throwing the command to open the connection
(eciadsl-start) and I get to video the following message:  "I cannot
find your ADSL modem: Fatal"

and if I go to see better as the things they are here is thing I get:

root@systemrob:~# ./eciadsl-doctor 

You are using linux kernel version 2.6.12-8-amd64-generic
Support for USB is OK
Preliminary USB device filesystem is OK
dabusb module is not loaded: OK
UHCI support is OK
OHCI support is not needed
/dev/ppp is OK
HDLC support is OK
HDLC support is OK (no bug)
I cannot find your ADSL modem: Fatal
root@systemrob:~#


Hertfull Thanks

CR

---

