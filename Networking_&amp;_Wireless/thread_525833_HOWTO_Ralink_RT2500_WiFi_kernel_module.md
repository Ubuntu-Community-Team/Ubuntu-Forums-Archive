---
title: "HOWTO: Ralink RT2500 WiFi kernel module"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by bmartin on 2007-08-14
If **lspci | grep Network** returns the following line...
```
Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01) 
```
then you've got this chipset and these instructions should be appropriate for you.

Before you begin, you might want to download [wicd]("http://blakecmartin.googlepages.com/wicd.html") or [wifi-radar]("http://blakecmartin.googlepages.com/wifi-radar.html"). They're WiFi connection manager programs that are considered by many to be superior to the built-in wireless management software. wicd contains a tray icon program that many people prefer and boasts built-in WPA support.

Make sure you have a wired internet connection before beginning.

Method A: my script

Open a terminal. Paste the following commands into it:
```
wget http://blakecmartin.googlepages.com/rt2500-install.sh
chmod 755 rt2500-install.sh
./rt2500-install.sh
```

Please feel free to take a look at the script and contact me if you have any questions/comments/suggestions/problems. 

This script downloads the build-essential and Linux kernel headers necessary for compilation, then downloads the source code for the RT2500 kernel module and compiles/installs it. In addition, the rt73usb and rt2570 kernel modules are blacklisted, as they are known to interfere with the operation of many Ralink WiFi devices.
==========================
Method B: manual installation

[LIST=1]
[*]Install the software packages necessary to compile the kernel module.
```
sudo apt-get update
sudo apt-get build-essential linux-headers-`uname -r`
```
[*]Download the newest source code.
```
wget http://rt2x00.serialmonkey.com/TARFILE=rt2500-cvs-daily.tar.gz
```
[*]Extract the source code and change into the created directory.
```
tar xf rt2500-cvs-daily.tar.gz
cd rt2500-cvs-*/Module/
```
[*]Compile the source code and install the kernel module.
```
make
sudo make install
```
[*]Remove and blacklist the unneeded Ralink kernel modules.
```
sudo modprobe -r rt73usb
sudo modprobe -r rt2570
echo "blacklist rt73usb" | sudo tee -a /etc/modprobe.d/blacklist
echo "blacklist rt2570" | sudo tee -a /etc/modprobe.d/blacklist
```
[*]Insert the new kernel module.
```
sudo modprobe rt2500
```
[/LIST]

---

### Post by imdano on 2007-08-14
A much needed howto, hopefully it helps some people out.  You might want to add info about how to connect with RT2500 enhanced drivers (using iwpriv instead of wpa_supplicant, iwpriv get_site_survey, etc).

I attached an iwpriv usage file that I'm pretty sure is valid for all of serialmonkey's enhanced drivers that might be helpful as well.

---

