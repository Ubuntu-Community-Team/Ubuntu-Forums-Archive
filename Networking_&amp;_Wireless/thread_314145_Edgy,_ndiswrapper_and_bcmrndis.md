---
title: "Edgy, ndiswrapper and bcmrndis"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by nilsvdburg on 2006-12-07
Hi,

I've some problems getting the wireless working on Ubuntu Edgy.
I've got a Belkin F5D7051 USB device (FCC ID: K7SF5D7051) working on Ubuntu Dapper with ndiswrapper (utils version: 1.8, driver version: 1.21).

On another partition on my PC i've got Edgy installed for testing that everything works, and everything works, but the wireless.

I've been trying a lot of solution combination i found on the internet, but nothings works. Here is the last thing i tried:
> nils@nils-desktop:~/download/drivers/belkin$ sudo ndiswrapper -e bcmrndis
nils@nils-desktop:~/download/drivers/belkin$ lsusb
Bus 003 Device 004: ID 050d:7051 Belkin Components 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0409:55ab NEC Corp. Hub [iMac/iTouch kbd]
Bus 001 Device 003: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 001 Device 001: ID 0000:0000  
nils@nils-desktop:~/download/drivers/belkin$ ndiswrapper -v
utils version: 1.9
driver version:        1.31
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
nils@nils-desktop:~/download/drivers/belkin$ dir
AUTORUN.INF  BCMRNDIS.INF  DATA1.HDR  F5D7051.DLL  flashmain.swf  IKERNEL.EX_  Manual           RNDISMPK.SYS  Setup.ini  START.EXE  USB8023K.SYS
BCM43XX.CAT  DATA1.CAB     DATA2.CAB  F5D7051.exe  ICON.ICO       LAYOUT.BIN   Manual.open.exe  Setup.exe     Setup.inx  Support
nils@nils-desktop:~/download/drivers/belkin$ sudo ndiswrapper -i BCMRNDIS.INF 
installing bcmrndis ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
nils@nils-desktop:~/download/drivers/belkin$ sudo ndiswrapper -l
bcmrndis : invalid driver!
nils@nils-desktop:~/download/drivers/belkin$ 

I've also tried using the same drivers that I've on Dapper, but nothing. With utils-1.8 it says correct driver, but there is no wireless.

I don't know what to do for now on... if anyone can help... i would appreciate

Thanks
nils

---

### Post by FrodoB on 2006-12-07
Have you looked at the ndiswrapper list, post number 38:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

note the discussion of a hidden driver, bcrndis.inf

Use "ls -a" to see any files that may be hidden.

At some point you will likely need to upgrade to the latest version of ndiswrapper, which is at least 1.30, if that does not work.

---

### Post by nilsvdburg on 2006-12-07
well, i don't have the installation CD, but i've the driver installacion executable where i can extract the files, but there is no hidden bcrndis.inf file
> nils@ubuntu:/media/hda5/home/nils/download/drivers/belkin$ ls -a
.             DATA1.CAB    flashmain.swf  Manual.open.exe  START.EXE
..            DATA1.HDR    ICON.ICO       RNDISMPK.SYS     Support
AUTORUN.INF   DATA2.CAB    IKERNEL.EX_    Setup.exe        USB8023K.SYS
BCM43XX.CAT   F5D7051.DLL  LAYOUT.BIN     Setup.ini
BCMRNDIS.INF  F5D7051.exe  Manual         Setup.inx


Do you know where i cant get this file apart from the installation CD?

---

### Post by FrodoB on 2006-12-07
No, I am just reading what is on the list, unfortunately I do not have the device or the CD to look at here.

Maybe you can call Belkin and they can give you a download location for it?

[http://www.belkin.com/support/download.asp](http://www.belkin.com/support/download.asp)

---

### Post by FrodoB on 2006-12-07
I think this is it:

[http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1](http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1)

---

### Post by FrodoB on 2006-12-07
See entry number 33 on the ndiswrapper list:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

Use unzip to open up the file downloaded from Belkin and note that BCMRNDIS.INF is the .inf file that you need to install after removing the non-working one that you have.

---

### Post by nilsvdburg on 2006-12-07
Nop, the driver that is avaible from the website of belkin is the same i have and isn't working.

I think it is weird that using ndiswrapper 1.31 i get the "wrong driver" message and using ndiswrapper 1.21 i get the "valid driver, hardware present" message but can't get it working after doing sudo modprobe ndiswrapper. and on Dapper it's working fine with 1.21.

I will keep looking for solutions...

---

### Post by pepepepe1 on 2006-12-15
efty has a new feature  to  limit the power it sends to usb devices, that might be your problem, since WLAN adapters consume a lot of power.
you may try to turn this feature off.

Try the howto
[http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206) 
at the end there is a section "Getting WUSB54GS to Work in Edgy and Feisty"

replace in the Line

BUS=="usb", SYSFS{idProduct}=="0014", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

0014     and    13b1    with   your product/vender ID as seen by typing : lsusb
  in your terminal

I do not have your device so it is only a hint

good luck!
Raphael

---

### Post by pepepepe1 on 2006-12-15
Oh, I forgot, 
since your Belkin7051 has the same chipset (BCM4320) as the WUSB54GS v2 described in the above link ([http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206)) you might as well folllow all that howto.
The main difference to the method you used is that he loads the very latest ndisWrapper directly from the source (not via synaptic)
let me know if any of the suggestion worked
kndrgds
Raphael

---

