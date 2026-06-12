---
title: "Pawerware 5110 UPS"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by tchoklat on 2009-08-22
When I used PCLinuxOS I was able to install the UPS management software from the site <http://powerquality.eaton.com/Support/Software-Drivers/Downloads/lansafe6.asp> after registration. I chose the 32 bit tar file for linux.

It does not install on UBUNTU and gives a persistent fault as follows -

tony@tony-desktop:~/Desktop$ sudo ./install.sh



-----------------------------------------------------------------

                      EATON | Powerware

                   Welcome to LanSafe!
                       Version 6.0.0

To install LanSafe for LINUX/UNIX, press y and then press <ENTER>
and fill in the configuration items as they are presented to you.

-----------------------------------------------------------------


		Continue installation? (y/n) [y] y


                    Installing from CD-ROM


   The default install path name for this software is:
   /usr/Powerware/LanSafe

   Do you want to continue with this install path? (y/n) [y] y


---------------------------------------------------------------
                   LanSafe Installation Parameters:

   File to install from                 :  CD_ROM
   Directory to install to              :  /usr/Powerware/LanSafe
---------------------------------------------------------------


  Are these installation parameters acceptable? (y/n) y
 
License Agreement:

 

                      Eaton Corporation
                              
                 END-USER LICENSE AGREEMENT


Revised: May, 2008


IMPORTANT, READ CAREFULLY.  THIS EATON CORPORATION END  USER
LICENSE  AGREEMENT (THE "AGREEMENT") IS A  BINDING  CONTRACT
BETWEEN  YOU,  THE  END-USER  (THE  "LICENSEE")  AND   EATON
CORPORATION ("EATON" OR "LICENSOR").  EXCEPT TO  THE  EXTENT
YOU  ARE BOUND BY A WRITTEN AGREEMENT SIGNED BY BOTH YOU AND
EATON  REGARDING  THE  USE  AND  LICENSE  OF  THIS  SOFTWARE
PRODUCT, BY INSTALLING OR USING THIS SOFTWARE PRODUCT,  YOU,
THE  LICENSEE,  ARE  AGREEING TO  BE  BOUND  BY  THE  TERMS,
CONDITIONS   AND   LIMITATIONS  OF  THIS  AGREEMENT,   WHICH
INCLUDES, BUT IS NOT LIMITED TO, THE SOFTWARE USAGE LICENSE,
THE   DISCLAIMER  OF  WARRANTY  AND  LIMITED  WARRANTY,  AND
 
Press <ENTER> to continue, (1) to skip to the end, or (0) to cancel: 1
 
Do you accept all terms of the preceding license Agreement?
If you do not accept the terms, then the Setup will close.
To install LanSafe, you must accept this agreement.
 
1. I accept.
0. I do not accept.
 
Enter selection: 1

Installing PowerMonitor.email to /usr/Powerware/LanSafe/Bin ...done
Installing PowerMonitor.broadcast to /usr/Powerware/LanSafe/Bin ...done
Installing PowerMonitor.shutdown to /usr/Powerware/LanSafe/Bin ...done
Installing PowerMonitor.unload to /usr/Powerware/LanSafe/Bin ...done
Installing PowerMonitor.sh to /usr/Powerware/LanSafe/Bin ...done
Installing upslist.ups to /usr/Powerware/LanSafe/Config ...done
Installing PowerMonitorEvents.def to /usr/Powerware/LanSafe/Config ...done
Installing install.ls to /usr/Powerware/LanSafe/Bin ...done
Installing install.txt to /usr/Powerware/LanSafe/Bin ...done
Installing PowerMonitorC to /usr/Powerware/LanSafe/Bin ...done
Installing PowerMonitorM to /usr/Powerware/LanSafe/Bin ...done
Installing PowerMonitorX to /usr/Powerware/LanSafe/Bin ...done
Installing PowerMonitorIcon to /usr/Powerware/LanSafe/Bin ...done
Installing uninstall.sh to /usr/Powerware/LanSafe/Bin ...done
Installing OEMModel.ini to /usr/Powerware/LanSafe/Bin ...done
Installing license.txt to /usr/Powerware/LanSafe ...done
Adding PowerMonitor services in  /etc/services.
sysv_startatboot
Ready to copy ls.init to install path
Installing ls.init to init.d ...done
Deleting /etc/init.d/rc5.d/S89ls.init
Linking /etc/init.d/rc5.d/S89ls.init to /etc/init.d/ls.init ... Linking /etc/init.d/rc0.d/K89ls.init to /etc/init.d/ls.init ... ln: creating symbolic link `/etc/init.d/rc0.d/K89ls.init': No such file or directory
Install failed. Exiting

I cannot see what is happening or what I should do. Can anyone help. I would prefer to use this as it was easy to setup and does not use NUT.


Tony

---

### Post by Liolikas on 2009-08-22
Ask in support.

---

### Post by sandyd on 2009-08-22
pclinux is based on mandriva which is a fedora based distro.
stuff meant for fedora based distros are unfortunately sometimes incompatible with ubuntu.

perhaps
```

sudo mkdir /etc/init.d/rc0.d/

```

---

### Post by tchoklat on 2009-08-22
You little ripper Carlee, that mkdir command did the trick. It is intalled, now I will turn off the powere and see if it works BRB ....

---

### Post by tchoklat on 2009-08-22
Arrgghh! It installs fine, though does not detect the UPS on USB nor does it shut the system down despite it being there;

"tony@tony-desktop:~$ lsusb
Bus 002 Device 004: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 003: ID 03f0:0324 Hewlett-Packard 
Bus 002 Device 002: ID 0592:0002 Powerware Corp. UPS (X-Slot)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tony@tony-desktop:~$'

I guess I will have to go back to the manufacturers!

Tony

---

