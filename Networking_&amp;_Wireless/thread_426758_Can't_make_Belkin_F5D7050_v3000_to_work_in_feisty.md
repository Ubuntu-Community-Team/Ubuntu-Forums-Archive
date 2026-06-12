---
title: "Can't make Belkin F5D7050 v3000 to work in feisty"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by brunomiguel on 2007-04-28
Hi. I bought a Belkin F5D7050, 3000 version, but I can't make it work in feisty. I followed this how-to ([https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)), but I can't compile it because the make command gives an error. The only way to make it work (kind of...) is with ndiswrapper. :(
Anyone managed to make it work with native drivers in feisty??

---

### Post by peiserma on 2007-05-03
Had the same problem in Feisty, same usb stick. The solution was to use the serialmonkey drivers at

<http://rt2x00.serialmonkey.com/wiki/index.php/Downloads>

these compile with no errors under Feisty

---

### Post by brunomiguel on 2007-05-03
Thanks for the tip!! I'll try it as soon as I can!

---

### Post by peiserma on 2007-05-03
FWIW, you will have to adjust the instruction from that webpage slightly. The guys at serialmonkey did a terrific job and that device is already listed, so skip all the steps related to editing the rtmp_def.h file and changing permissions and running fromdos. all taken care of.

After you get all the build files for your system and untar,  just follow the readme file. basically make, then make install, then modprobe. it compiled w/o errors or warnings for me. try without any encryption first to get the configuration right.  I installed it on a co-workers´s laptop in an evening and handed it off. Again, it went off without a hitch.

that webpage really ought to be updated, since it was one of the first I found. And it seems I not the only one to have found it.

---

### Post by voice on 2007-05-10
i donwload the last driver in  [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads")
When i tried make i got this error:
------------------------------------------------------------------------
lars@doslinux:~/Desktop/rt73-cvs-2007051016/Module$ make
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/rtmp_main.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/mlme.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/connect.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/rtusb_bulk.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/rtusb_io.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/sync.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/assoc.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/auth.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/auth_rsp.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/rtusb_data.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/rtmp_init.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/sanity.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/rtmp_wep.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/rtmp_info.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/rtmp_tkip.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/wpa.o
  CC [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/md5.o
  LD [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/rt73.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/lars/Desktop/rt73-cvs-2007051016/Module/rt73.mod.o
  LD [M]  /home/lars/Desktop/rt73-cvs-2007051016/Module/rt73.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.20-15-generic'

-----------------------------------------------------------------------
Any idea?
Thank you.
Sorry for my english.

---

### Post by brunomiguel on 2007-05-10
make install?!
I don't see any error.

---

### Post by boetie2 on 2007-05-16
Works for me

to summarise - adapted from <https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29>

Step 1 - Disable Competing Driver

You need to blacklist the existing rt73 module which is not working:

user@ubuntu:~$ gksudo gedit /etc/modprobe.d/blacklist 

add the following three lines to the end of the file:

# Added when rt73 module was installed
blacklist rt73usb
blacklist rt2570

Save the file. The blacklisted module will not be loaded from now on. 
Step 2 - Prepare the Linux build environment

You will need to install the essential build files to compile the driver:

user@ubuntu:~$ sudo apt-get update  
user@ubuntu:~$ sudo apt-get install build-essential

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`  
user@ubuntu:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build

Step 3 -  get the driver from <http://rt2x00.serialmonkey.com/wiki/index.php/Downloads>

Step 4 - 

	a. $tar -xvzf rt73-x.x.x.tar.gz
	go to "./rt73-x.x.x/Module" directory.

	b. $make # compile driver source code

	c. $make install # installs kernel module driver

	d. $modprobe rt73

Step 5 -
user@ubuntu:$ gksudo gedit /etc/network/interfaces

Dynamic Address Assignment using DHCP: Add this data at the end of the file for a DHCP setup: (Choose one key type, either hex or ASCII, but not both, uncomment one, and fill in your key.)

#  wireless network device using DHCP
iface wlan1 inet dhcp
pre-up ifconfig wlan1 up
wireless-essid MY_ESSID
# wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                  # This line for ASCII (string) keys
auto wlan1

Static IP Address Example: Add this data at the end of the file for a static IP address setup: (Choose one key type, either hex or ASCII, but not both, uncomment one, and fill in your key.) You may have better luck by setting up the device using the Networking applet and the modifying the record and adding the necessary "pre-up ifconfig wlan1 up" line. If you do so make sure that you do not end up with more than one line that says "auto rausb0".

# wireless network device using static IP address
iface wlan1 inet static
pre-up ifconfig wlan1 up
wireless-essid MY_ESSID
# wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                  # This line for ASCII (string) keys
address XXX.XXX.XXX.XXX
netmask XXX.XXX.XXX.XXX
network XXX.XXX.XXX.XXX
broadcast XXX.XXX.XXX.XXX
gateway XXX.XXX.XXX.XXX
auto wlan1


Then
iwconfig

hope this helps

---

