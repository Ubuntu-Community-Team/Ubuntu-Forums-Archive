---
title: "Making my Gigafast Wireless adapter WF748-CUI work without internet access"
date: 2014-06-20
forum: Networking &amp; Wireless
---

### Post by fdd2 on 2014-06-20
Hi, I need help now. I'm trying to make it work since yesterday without any success. 

I have a **Gigafast Wireless adapter USB WF748-CUI** that I'm trying to install on my new **Ubuntu 12.04**. I know that the linux driver *zd1211*  is suppose to work with the device, but the installation requires *built-essential* that requires *dpkg-dev *that requires* libc6-dev *that I can't install for some reason...(ubuntu tells me it's already there but refuses to install* dpkg-dev* because it says that we miss *libc6-dev.*

I also tried earlier to install the windows driver with ndiswrapper, but I'm stuck at the installation of ndiswrapper. I got ndiswrapper 1.59 installed from sources earlier and I think the driver worked because the computer recognized the wireless adapter (but still I couldn't see the networks around, but I think that's another problem), but it broke something inside ubuntu because I couldn't use sudo and some command like iwconfig anymore...I had to start again with a fresh install of ubuntu!

I tried with ndiswrapper 1.58, but I'm stuck at the make command (something about linux-headers). I also tried to install ndiswrapper with the .dev files, but still got no luck : I was able to install the driver, but modprobe didn't work and I got the module not found error (and yes I installed ndiswrapper-dkms also).

I'm running out of ideas. It's also important to mention that I don't have any internet access from that computer, so every time I need to install something it has to be downloaded on windows and transfered to the other computer.

Thanks in advance for your help!

---

### Post by chili555 on 2014-06-20
Isn't the driver zd1211rw present on your 12.04 install?```
modinfo zd1211rw
```You needn't post the whole thing, just tell us if you get a result. Also, may we see details about the device?```
lsusb
```I hate ndiswrapper.

---

### Post by fdd2 on 2014-07-01
Sorry for the delay, I'm back to my wireless problem now. I have internet on this computer now, so it's an improvement !

I get results, it seems that this driver is installed. I also get 

Bus 001 Device 004: ID 0457:0163 Silicon Integrated Systems Corp. 802.11 Wireless LAN Adapter

with lsusb, so the computer recognises the usb adapter. 

I think the connection between the driver and the adapter is not working.

Thanks for helping

---

### Post by chili555 on 2014-07-01
Sadly, the native driver zd1211rw doesn't apply to your device. It has been reported to work with ndiswrapper. Here is a good tutorial; notice the usb.id of 0457:0163 is specifically mentioned: [http://wirelessmania.blogspot.com/2013/11/installing-trendnet-tew-424ub-version-2.html](http://wirelessmania.blogspot.com/2013/11/installing-trendnet-tew-424ub-version-2.html)

Notice it asks you to use the AMD64 files. That applies if yours is a 64-bit system; check:```
arch
```If not, download the 32-bit drivers.

Did you get ndiswrapper installed correctly?```
sudo dpkg -s ndiswrapper-utils-1.9
```Ideally, we see:> Package: ndiswrapper-utils-1.9
Status: install ok installed


---

### Post by fdd2 on 2014-07-01
My system is a 32-bits. I got all of the steps ok untill modprobe ndiswrapper where I got an internal error. 

I'm not using a driver downloaded on the internet, I'm using one of the driver I found on the installation cd that came with the device. I'm using the one for windows XP, but they don't do any distinction between 32 and 64 bits on the folders of the cds. (but I have other OS's drivers) 

Right now, I'm trying to uninstall and reinstall correctly ndiswrapper.

---

### Post by fdd2 on 2014-07-01
Ok as I said, I tried deleting and installing ndiswrapper, but no luck.

I also freshly reinstalled ubuntu with all the updates and installed ndiswrapper again. I'm still getting the same error. I suppose it might be a 64/32 bits problem.

Anyway, I get nothing with ndiswrapper -l (the cursor is blinking and I have to stop it manually)
When I try to remove the driver, I get : 

couldn't delete /etc/ndiswrapper/sis163u: Inappropriate ioctl for device

---

### Post by chili555 on 2014-07-02
> **fdd2 said:**
> Ok as I said, I tried deleting and installing ndiswrapper, but no luck.

I also freshly reinstalled ubuntu with all the updates and installed ndiswrapper again. I'm still getting the same error. I suppose it might be a 64/32 bits problem.

Anyway, I get nothing with ndiswrapper -l (the cursor is blinking and I have to stop it manually)
When I try to remove the driver, I get : 

couldn't delete /etc/ndiswrapper/sis163u: Inappropriate ioctl for deviceAny clues here:```
cat /var/log/syslog | grep ndis
```

---

