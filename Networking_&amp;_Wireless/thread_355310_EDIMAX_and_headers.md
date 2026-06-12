---
title: "EDIMAX and headers"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by TrueAncalagon on 2007-02-07
The first thing, I don't write in english from a lot, then, sorry!

My problem is this. I'm new in Kubuntu, I'm coming from Mandrake>Mandriva and then Suse10.1. I have a really good impression of Kubuntu but I have a problem whit it. I have a wireless network in my home, where I have my pc, my laptop, xbox and 360.  For work, I must use XP (C4D, Photoshop CS, Macromedia Studio, ...) and I haven't problem whit my WLAN. The first time that I had installed kubuntu I had tried to install the driver on the cd, but the pack that I have is pre-compiled on Debian and don't work. Whit my good friend Google I had found 2 metods to install it...

1)
-------------------------------------------------------
sudo apt-get install linux-headers-$(uname -r) build-essential g++-3.4
wget [http://www.ralinktech.com/drivers/Linux/RT73_Linux_STA_Drv1.0.3.6.tar.gz](http://www.ralinktech.com/drivers/Linux/RT73_Linux_STA_Drv1.0.3.6.tar.gz)
(of course I had downloaded in XP firt, then saved on my iPod)
tar -xvf RT73_Linux_STA_Drv1.0.3.6.tar.gz
cd RT73_Linux_STA_Drv1.0.3.6/
cd Module/
sudo cp -v Makefile.6 ./Makefile
make all
sudo cp -v rt73.ko /lib/modules/`uname -r`/kernel/drivers/usb/net/
sudo mkdir -pv /etc/Wireless/RT73STA
sudo cp -v rt73.bin /etc/Wireless/RT73STA/
dos2unix rt73sta.dat -f
(dos2unix don't exist in kubuntu then I had used "flip -u")
sudo cp -v rt73sta.dat /etc/Wireless/RT73STA/rt73sta.dat
sudo insmod /lib/modules/`uname -r`/kernel/drivers/usb/net/rt73.ko

dmesg
# now plug in your device
dmesg
#should see something like

[17385845.440000] idVendor = 0x148f, idProduct = 0x2573
[17385845.440000] **RT2573**<7>usb device name rausb0
[17385845.440000] **RT2573**<7>BulkOutMaxPacketSize 512
[17385845.624000] **RT2573**<7>rt73_get_wireless_stats --->

run the networking configuration tool from menu's System->Administration->Networking

hopefully now you see an unactivated rausb0 configure it with your ssid and encryption ect activate it and set the gateway device to rausb0
hopefully now you can connect with it. 
-----------------------------------------------------------------------

This metod had worked on Kubuntu 6.06 (dapper I think) on the first time and whitout problems. For many reasen I had formated the partition and let pass the time. After 1 week I had downloaded Kubuntu 6.10 (Edgy) and instaled. I had use the same metod BUT, and here is the problem, I got an error on "make all":

make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/otacon/Desktop/Linux/WLAN dirver/RT73_Linux_STA_Drv1.0.3.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `dirver/RT73_Linux_STA_Drv1.0.3.6/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [all] Error 2

The headers? Ok, then I must do something...

sudo apt-get install build-essential linux-headers-`uname -r`

Ok, process completed. Kubuntu get the headers and now I can try again... again error...
Ok, not bad... I had found another metod to install the driver...

2)
--------------------------------------------
sudo gedit /etc/modprobe.d/blacklist
"add to list blacklist rt73usb"
sudo apt-get install build-essential linux-headers-`uname -r` gcc
wget [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)
sudo apt-get install cvs
cvs -d:pserver:anonymous@rt2400.cvs.sourceforge.net:/cvsroot/rt2400 login
cvs -z3 -d:pserver:anonymous@rt2400.cvs.sourceforge.net:/cvsroot/rt2400 co -d rt73 -P source/rt73
tar -xvf rt73-cvs-daily.tar.gz
cd rt73-cvs-*
cd Module
make
sudo make install
sudo mkdir -p /etc/Wireless/RT73STA/
sudo cp rt73.bin /etc/Wireless/RT73STA/
sudo depmod -a
sudo modprobe rt73
------------------------------------------
....BUT.. on make.... an error

xxx@xxx:~/Desktop/Linux/WLAN dirver/rt73-cvs-2007020213/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** No rule to make target `dirver/rt73-cvs-2007020213/Module'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
rt73.ko failed to build!
make: *** [module] Error 1

Can someone help me????

---

