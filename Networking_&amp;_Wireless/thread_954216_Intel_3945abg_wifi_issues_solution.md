---
title: "Intel 3945abg wifi issues solution"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by bravebear on 2008-10-21
Had trouble with my Intel 3945abg wifi connection for a while, connection in and out, unable to reconnect, system freeze. This on a Toshiba Satellite R25 Tablet and a brandnew Dell Inspiron 1525n with preinstalled Ubuntu 8.04.
Spent hours going through forums, no native solution found. Finally tried this and it solved it for me:

Please visit references below for more info

1. step from [https://help.ubuntu.com/community/WifiDocs/WirelessNetworkOfUniversityOfMaastricht](https://help.ubuntu.com/community/WifiDocs/WirelessNetworkOfUniversityOfMaastricht)
install packages ndisgtk, ndiswrapper-common and ndiswrapper-utils-1.19

2. from [http://ph.ubuntuforums.com/showthread.php?t=895732](http://ph.ubuntuforums.com/showthread.php?t=895732)
get Windows drivers from:
[http://downloadcenter.intel.com/Filter_Results.aspx?strOSs=44&strTypes=all&ProductID=2259&OSFullName=Windows*%20XP%20Professional&lang=eng&sType=prev](http://downloadcenter.intel.com/Filter_Results.aspx?strOSs=44&strTypes=all&ProductID=2259&OSFullName=Windows*%20XP%20Professional&lang=eng&sType=prev)
if link does not work, go to Intel.com and look for 3945 driver for Windows 2000 (this will show the older ones, you might have to click on "archived files")
download version 11.5.1.15/9.0.4.39 dated 4/11/2008
use driver file NETw4x32.INF once unzipped in ndisgtk

3. disable networkmanager for your next sessions:
Go to System->Preferences->Sessions and disable networkmanager

4. Blacklist old driver iwl3945
Since we just setup ndiswrapper to control our wireless card, we need to disable the native linux drivers that have caused problems. This can be accomplished by editing a text file.

In a terminal window:

sudo gedit /etc/modprobe.d/blacklist 

Add the following lines to the text file:

blacklist iwl3945

Save and close

5. Setting ndiswrapper Module to Start at Boot

In a terminal window open file "modules":

sudo gedit /etc/modules

Add this to the file:

ndiswrapper

Save and close

6. Install Windows driver:
Go to System->Aministration->Windows Wireless Drivers
Install downloaded Windows driver NETw4x32.INF 

7. Reboot

--------------------------------------------------
References

[http://ph.ubuntuforums.com/showthread.php?t=895732](http://ph.ubuntuforums.com/showthread.php?t=895732)

[http://downloadcenter.intel.com/Filter_Results.aspx?strOSs=44&strTypes=all&ProductID=2259&OSFullName=Windows*%20XP%20Professional&lang=eng&sType=prev](http://downloadcenter.intel.com/Filter_Results.aspx?strOSs=44&strTypes=all&ProductID=2259&OSFullName=Windows*%20XP%20Professional&lang=eng&sType=prev)

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworkOfUniversityOfMaastricht](https://help.ubuntu.com/community/WifiDocs/WirelessNetworkOfUniversityOfMaastricht)

[https://support.uakron.edu/wiki/index.php/Wireless_Setup_on_Ubuntu_8.04_(Hardy_Heron)_with_Intel_3945/4965](https://support.uakron.edu/wiki/index.php/Wireless_Setup_on_Ubuntu_8.04_(Hardy_Heron)_with_Intel_3945/4965)

---

### Post by Bucky Ball on 2008-10-21
[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

You might find that link of interest.

---

