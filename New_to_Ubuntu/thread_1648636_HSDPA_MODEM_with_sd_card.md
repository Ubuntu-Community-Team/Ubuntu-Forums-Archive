---
title: "HSDPA MODEM with sd card"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by lakmalsuranga on 2010-12-19
I'm using Huwaei E153 hsdpa modem on Ubuntu 10.10. 
Modem is working and its auto detected buy system and I'm accessing Internet trough it. 
BUT, inbuilt sd card (2GB card installed) not identified by Ubuntu 10.10.
I have update the system through Update Manager and it's up-to date.

HELP ME....................

This is the result of lsusb and df


lakmal@lakmal:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lakmal@lakmal:~$ df
Filesystem                                                    1K-blocks                            Used                                        Available                                       Use%                               Mounted on
/dev/sda1                                                            150814948                       3216756                        139937240                               3%                                                 /
none                                                                    502600                                    292                                 502308                                   1%                                /dev
none                                                                   508196                                    184                 508012                                   1%                                /dev/shm
none                       508196                92                                     508104                                   1%                                /var/run  
none                                                                    508196                                      4                     508192                                   1%                                /var/lock
lakmal@lakmal:~$

---

### Post by Aero_Zeppelin on 2010-12-19
Is it a tata photon plus connection?Have you done the setup properly?(Username=internet,password=internet)

---

### Post by Aero_Zeppelin on 2010-12-19
Sorry.Didnt read your Query properly..Im using an olive dialer.It has an inbuilt transflash reader..n its workin fine..Dunno bout sd cards..Have you formatted the card?Does the card get recognized in the Disk Utility?

---

### Post by lakmalsuranga on 2010-12-19
> **Arindam Momin said:**
> Is it a tata photon plus connection?Have you done the setup properly?(Username=internet,password=internet)


It is Huwaei E153 hsdpa modem. Connection is Mobitel (Sri Lanka)
I dont have any problem with internet connection. Modem and Internet working properly.

The problem is "inbuilt micro SD slot / reader" of the USB hsdpa modem. card slot / reader did not identified by system,
 
micro SD card is formatted and it is identified by windows and earlier versions of ubuntu.

---

### Post by lakmalsuranga on 2010-12-19
> **Arindam Momin said:**
> Sorry.Didnt read your Query properly..Im using an olive dialer.It has an inbuilt transflash reader..n its workin fine..Dunno bout sd cards..Have you formatted the card?Does the card get recognized in the Disk Utility?



"Card recognized in the disk utility" but is did not display in My computer or file system.

---

### Post by Aero_Zeppelin on 2010-12-21
format the card to ext2 n see if it works.

---

### Post by gandaran on 2010-12-21
> **lakmalsuranga said:**
> It is Huwaei E153 hsdpa modem. Connection is Mobitel (Sri Lanka)
I dont have any problem with internet connection. Modem and Internet working properly.

The problem is "inbuilt micro SD slot / reader" of the USB hsdpa modem. card slot / reader did not identified by system,
 
micro SD card is formatted and it is identified by windows and earlier versions of ubuntu.
the problem is due to the version of 'usb-modeswitch' installed in ubuntu 10.10 which doesn't mount the drive like it did in ubuntu 10.04, I don't know of any fix but I suggest you look in launchpad bugs for a fix or file a bug report yourself if you don't find any.

---

### Post by avanga on 2011-01-07
[COLOR=Red]**I do have a tata photon plus (olive v-me101) it works fine in all the windows and doors. But i'm unable to install or get it worked in ubuntu 10.10 please some 1 help me out.**[/COLOR]

---

### Post by pragya on 2011-01-09
Hey,

even I am trying to connect to internet using tata photon plus.I have filled up the username and password field correctly. But, it does not connect to the internet. On typing wvdial on the terminal i get:


--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.

Also, though I have installed usb-modeswitch and usb-modeswitch-data..the computer still detects my modem as an HUAWEI SD Storage instead of detecting it as a modem.

Can anyone help me out?

---

