---
title: "kismet problems with bcm43xx driver"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by blatch on 2006-08-18
I have a broadcom 4306 mPCI wireless card. 
> jtth@twotone:~$ uname -a
Linux twotone 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux


I have kismet-devel installed. Latest. I've had the same error with the one the apt repository. 

> jtth@twotone:~$ sudo kismet
Password:
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to jtth (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (bcm43xxsource): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
FATAL: SetIFFlags: Unknown interface eth1: No such file or directory

Here's my kismet source line:
> source=bcm43xx,eth1,bcm43xxsource

Anyone got any ideas?

---

### Post by ubuntuuser on 2006-08-19
From the Kismet Readme:```
bcm43xx         Broadcom            Linux       Berlios-BCM43XX
                    http://bcm43xx.berlios.de
                    Capture interface:  'ethX'
                    *Very experimental* drivers with *experimental* Kismet
                     support.  These reverse-engineered drivers support a
                     range of Broadcom based wireless cards.  At the time
                     of this writing, they support ONLY monitor mode, normal
                     mode is not functional.
                    These drivers are in a state of high development, and 
                     support is only added because of demand.  If it doesn't
                     work, I wouldn't be too surprised.
```Are you able to enter monitor mode manually?```
sudo iwconfig eth1 mode monitor
```If not, then your driver doesn't support monitor mode. Also, I don't think you need the devel-files, although it shouldn't cause any harm to have them installed. The only options I see are: compile the latest broadcom driver or get yourself a card with a supported chipset. I strongly recommend an Atheros chip. Good luck.

---

### Post by blatch on 2006-08-19
Yeah, it goes into monitor mode fine. I switched it for an mPCI Intel 2100, works fine in kismet.

---

### Post by Esoterick on 2007-09-03
Ive got the same problem

> esoterick@esoterick-desktop:/etc/kismet$ sudo kismet 
Server options:  none
Client options:  none
Starting server...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (MadWifi): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
Waiting for server to start before starting UI...
FATAL: SetIFFlags: Unknown interface eth1: No such file or directory
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

[9]+  Stopped                 sudo kismet
esoterick@esoterick-desktop:/etc/kismet$ 

kismet.conf:
> source=bcm43xx,eth1,MadWifi

---

### Post by Esoterick on 2007-09-03
I installed Kismet from the sources online now i get this error when i tried to run it...

> esoterick@esoterick-desktop:~/kismet-2007-01-R1b$ sudo kismetServer options:  none
Client options:  none
Starting server...
Will drop privs to esoterick (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'bcm43xx' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.


what should i do? should i remove all the instances of kismet and reinstall them if so how do i get rid of them?

---

