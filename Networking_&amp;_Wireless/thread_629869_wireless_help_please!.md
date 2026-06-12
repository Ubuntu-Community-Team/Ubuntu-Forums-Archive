---
title: "wireless help please!"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by yipeskop on 2007-12-02
I am using Ubuntu 7.10 and a wg311v2 internet card to connect to my wi-fi.
I left click on the internet options at the top right and it detects my connection point but cant connect to it, but on rare occasions it will successfully connect to it but my I still cant connect to the internet.
so I tried using ndiswrapper and set it up using this guide: [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)
but instead of the *****.inf file I installed the wg311v2.inf driver.

so after that Installed ndiswrapper and it installed correctly but it said:
NOTE: Windows driver configuration file format has changed since 1.5. you must re-install Windows drivers if they were installed before
(I don't know what this means and it said this for whatever different driver I installed and it said this for both 1.48 and 1.50 versions of ndiswrapper)
Then I verified the installation with the command "ndiswrapper -v" and the output was:

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:         /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version: 1.45 
vermagic: 2.6.22-14 SMP mod_unload

Which I would like to add is different readings then the guide said were supposed to have.
Then I got to the point where I had to verify installation for the driver so I used the command "ndiswrapper -l" and got these readings:

wg311v2:driver installed
            device (104C:9066) present (alternate driver: acx) 

and am I supposed to have an alternate driver if I only installed one driver?
anyways, I got to the point where I had to use the code "dmesg" and somewhere in there it said that ndiswrapper-1.45 loaded. I don't understand since I installed version 1.48 (and later tried 1.50 and said the same thing) I did the next 2 steps on the guide and rebooted. My internet still wouldn't work so I tried verifying the installation of ndiswrapper again and I got the following response:

mod info: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module '0'
module details:
mod info could not open ndiswrapper: No such device

I had to reinstall it for it to give the information I got earlier.
I then did the code "ifconfig" and did see an interface named wlan0
I then did the code "lshw -C network" and got got the following information:

*-network DISABLED
Description:wireless interface
product: ACX111 54Mbps wireless Interface
vendor: Texas Instruments
physical id: 9
bus info: pci@0000:03:09.0
logical name: wlan0
version: 00
serial: 00:09:5b:8f:e5:7e
width: 32bits
clock: 33MHz
configuration:broadcast=yes drive=acx_pci latency=32 module=acx multicast=yes wireless=IEEE 802.11b+/g+

from what I know, where it says drive it should say ndiswrapper not acx_pci.

please help me I am stuck and don't know what to do now.

---

### Post by yipeskop on 2007-12-04
bump

---

