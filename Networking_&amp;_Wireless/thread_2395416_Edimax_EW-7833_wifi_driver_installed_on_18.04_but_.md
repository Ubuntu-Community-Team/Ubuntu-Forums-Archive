---
title: "Edimax EW-7833 wifi driver installed on 18.04 but connects only once"
date: 2018-07-02
forum: Networking &amp; Wireless
---

### Post by tony-whelan2 on 2018-07-02
Clean install of Ubuntu 18.04 (64 bit).  I have an Edimax EW-7833 USB dual-band wireless dongle (model "AC1750"). 

It uses an rtl8814 driver.

Installing a driver into the kernel on a previous build with kernel 4.13.0 was successful. The driver installation process I used was as follows:

cd /home/$MYUSER
git clone [https://github.com/tpircher/rtl8814AU.git/](https://github.com/tpircher/rtl8814AU.git/)
cd rtl8814AU/
cp -R . /usr/src/rtl8814au-4.3.21
dkms build -m rtl8814au -v 4.3.21
dkms install -m rtl8814au -v 4.3.21
reboot

However the same driver installed on 18.04 (kernel 4.15.0) does not give good results. The wifi appears in Network Manager, and I can connect to an access point ONCE.
If I disconnect wifi or log out or reboot, wifi fails to connect next time. It displays "Connecting" for maybe 30 seconds then gives up with a "connection failed" message.

There are three wifi access points I can normally connect to, and this odd behaviour occurs with all three of them. 

Output of wireless-info script is here: [http://paste.ubuntu.com/p/HFKP5pBt54/](http://paste.ubuntu.com/p/HFKP5pBt54/)

As I said, this driver worked on the earlier (4.13.0) kernel.

Any insights would be appreciated.

---

### Post by jeremy31 on 2018-07-02
I have been using [https://github.com/jeremyb31/rtl8814AU](https://github.com/jeremyb31/rtl8814AU) with my Edimax 7833 on 18.04, it is just a fork of [https://github.com/lkw16/rtl8814AU](https://github.com/lkw16/rtl8814AU) with a fixed dkms.conf file
You might have some problems because all 3 AP's are on channel 6 and 2 of them have TKIP encryption enabled

EDIT: actually in 4.15 I used [https://github.com/zebulon2/rtl8814au](https://github.com/zebulon2/rtl8814au) and fixed the dkms

---

### Post by tony-whelan2 on 2018-07-02
Thanks jeremy31

I had previously used the zebulon2 driver without success.

When I started up the machine a short while ago it auto-upgraded the kernel from 4.15.0-23 to 4.15.0-24.

I then uninstalled the previous rtl8814 driver from dkms, and ran a new script to  patch the dkms.conf file and install the zebulon2 driver and

It built and installed and after reboot the symptoms are just the same. I can't connect to any of the access points.

I deleted the TETHYS connection and selected it anew, but it won't connect - reports "connection failed"

latest wireless-info report is at [http://paste.ubuntu.com/p/QhsWDGyqK2/](http://paste.ubuntu.com/p/QhsWDGyqK2/)

The script I used is:
```
clear
[ "$(id -u)" -ne "0" ] && echo "FAILED- This script must be run as root" && exit 1
MYUSER=$SUDO_USER # assign username to MYUSER variable
echo "About to compile and install Edimax 7833 driver for kernels > 4.4"
cd /home/$MYUSER
rm -r -f rtl8814au
git clone https://github.com/zebulon2/rtl8814au.git
cd rtl8814au/
echo 'PACKAGE_NAME="rtl8814AU"
PACKAGE_VERSION="1.0"
BUILT_MODULE_NAME[0]="8814au"
MAKE[0]="make all KVER=${kernelver}"
CLEAN="make clean"
DEST_MODULE_LOCATION[0]="/updates/dkms"
AUTOINSTALL="YES"' > dkms.conf
# need to wrap make in single quotes or will fail
sed -i "s/make/'make'/g" dkms.conf
echo "Copy files to /usr/src"
cp -R . /usr/src/rtl8814au-4.3.21
echo "Build ..."
dkms build -m rtl8814au -v 4.3.21
echo "Install ..."
dkms install -m rtl8814au -v 4.3.21
```

---

### Post by tony-whelan on 2018-07-02
Re TKIP, my APs are set to "auto" but I switched one to AES only and re-tried, same problem as before.

---

### Post by jeremy31 on 2018-07-03
Ok do ```
echo "options 8814au rtw_power_mgnt=0 rtw_enusbss=0" | sudo tee /etc/modprobe.d/8814au.ko
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot and see if it works better

---

### Post by tony-whelan2 on 2018-07-04
Thanks Jeremy, I just tried those commands and rebooted but alas no change to the situation.

Its not a big deal if I can't get this working, as I have another adaptor EW-7611 which works on kernel 4.15, although its only designed for the 2.4GHz band.

I appreciate your assistance thus far. Please don't feel you need spend more time on it unless it suits you.

Either way I am grateful for your expertise on this forum.

Tony
Canberra, AUS

---

### Post by tony-whelan2 on 2018-07-06
Just an update on this issue. I have used several different driver packages from github and all produce the same result. Once installed and I reboot, the SSIDs appear, and I can connect to an SSID. 
When I log off or reboot, Network Manager simply won't reconnect - the connection fails. 

I have wiped and rebuilt the (test) machine and the driver setup multiple times and this "connect-only-once" scenario happens every time.

I'm baffled by it, and mention it because its possible others may have the same issue.

---

