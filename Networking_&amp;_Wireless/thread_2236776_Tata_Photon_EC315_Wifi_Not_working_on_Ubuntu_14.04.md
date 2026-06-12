---
title: "Tata Photon EC315 Wifi Not working on Ubuntu 14.04"
date: 2014-07-28
forum: Networking &amp; Wireless
---

### Post by Puneet_Agarwal on 2014-07-28
Hi,


I bought a new laptop - HP Zbook 14 and installed Ubuntu 14.04 no it.


I also have a Tata Photon EC315 data card. This card does not work on Ubuntu 14.04.
However, it works on Ubuntu 12.04 (old laptop).


Details of the data card can be observed from the following links:


a. [http://www.youtube.com/watch?v=PVfF0rPQYqg](http://www.youtube.com/watch?v=PVfF0rPQYqg)
b. [http://www.gpcircles.com/huawei-ec315-data-card-specifications-and-price-in-india.html](http://www.gpcircles.com/huawei-ec315-data-card-specifications-and-price-in-india.html)
c. [http://www.4gltemall.com/huawei-ec315-3g-mobile-cdma-evdo-modem.html](http://www.4gltemall.com/huawei-ec315-3g-mobile-cdma-evdo-modem.html)
 
Usually, this device does not need to be installed on the OS; if plugged in power point through a USB charger, it works.
But does not workon Ubuntu 14.04.

I also tried the USB Charging port in the laptop - it did not work.

output of "lsusb" command is shown below

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0424:5534 Standard Microsystems Corp. 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 05c8:0369 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 003: ID 03f0:521d Hewlett-Packard 
Bus 002 Device 023: ID 12d1:1f01 Huawei Technologies Co., Ltd. 
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 002: ID 0424:2134 Standard Microsystems Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Please guide on what I can do to get it working.


Thanks in advance
Puneet

---

### Post by Puneet_Agarwal on 2014-07-29
One of my friend has the same data card and uses Ubuntu 14.04. It works for him.
It seems to be USB 2.0 vs USB 3.0 issue. Not sure yet. 

I will keep you all posted on what I choose to do finally.

If someone can help I will appreciate.

---

### Post by asadajk on 2014-08-09
Hi @Puneet_Agarwal, I too am in the same boat. not yet used my new MTS Ultra connection with this wingle- Huawei EC315 which is awaiting activation. However, I've tried their(also provided by Tata docomo max wifi) ZTE AC3633 wingle which is totally supported in Ubuntu and Fedora. you can even install the MTS gui which has to be compiled and it is 32-bit. ztemtapp is the command to launch the Graphical interface which shows signal strength etc. Network manager supports this datacard/wingle. you can install [modem-manager-gui]("http://screenshots.debian.net/screenshots/m/modem-manager-gui/10269_large.png") from ubuntu repo to know informations on the datacard. 
Coming to the Linux support issue, did you made sure you have usb_modeswitch package installed. otherwise, the confusion whether to mount as a usb drive or as a modem by the OS will prevent configuring the device. I will reply back after activation of my connection(MTS).
**EDIT: This is the specifications for this modem Huawei EC315:**
[http://consumer.huawei.com/en/mobile-broadband/wingles/features/ec315-en.htm](http://consumer.huawei.com/en/mobile-broadband/wingles/features/ec315-en.htm)

---

### Post by asadajk on 2014-08-11
@Puneet_Agarwal: I got my MTS Ultra connection activated. now, I am  using this Huawei EC315 Highspeed CDMA modem. Huawei's "Mobile Partner"  software is not provided along with this Modem(when mounted as storage).  Instead, It has a web interface to deal with settings and configuration  and even has a Signal strength indicator on the web-ui. However, you  can install Mobile partner dashboard(latest version for Linux which has  to be compiled AFAIK!) so that to get more configuration options. Huawei EC315 is not supplied by MTS from past 2 months or so. instead, Lava DF800 modem is given. EC315 is considered good option as per online reviews.

Now,  coming to the problem: Ubuntu does not see it as a modem.  usb_modeswitch latest version is needed to be installed. else, you have  to manually add the [device details]("http://www.draisberghof.de/usb_modeswitch/device_reference.txt")  . the Kernel module that supports the LAN connection(NIC) to the PC  where the device is plugged in is : "cdc_ether". it shows cdc_ether,  mii, usbnet as the modules used by EC315 to work in Linux. try upgrading  usb_modswitch as 2.2.x version seems to support many new devices? There is a ppa for usb-modeswitch maintained by Debian maintainer himself:
[https://launchpad.net/~odyx/+archive/ubuntu/usb-modeswitch](https://launchpad.net/~odyx/+archive/ubuntu/usb-modeswitch)

This  will give insight about usb_modeswitch which makes Linux "see" Usb  modems and other usb devices so as to work instead of detecting as mass  storage device:
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

Wifi works perfectly with my laptops having Ubuntu installed. but, then Wifi support in laptops/desktop is owing to the different drivers needed to configure it. e.g., broadcom etc. has nothing to do with the EC315 modem. What I've observed is, it takes slightly long to detect this modem by the wifi card. otherwise, everything works fine.

---

### Post by asadajk on 2014-08-12
Firstly, with a Ubuntu 12.04 64-bit installed Laptop, I downloaded usb_modeswitch_2.2.0 which is the latest version.
1. Usb_modeswitch: [https://packages.debian.org/sid/amd64/usb-modeswitch/download](https://packages.debian.org/sid/amd64/usb-modeswitch/download)
2. Usb_modeswitch_data: [https://packages.debian.org/sid/all/usb-modeswitch-data/download](https://packages.debian.org/sid/all/usb-modeswitch-data/download)
3. libjim0.75: [http://packages.ubuntu.com/utopic/amd64/libjim0.75/download](http://packages.ubuntu.com/utopic/amd64/libjim0.75/download)
Downloaded .deb files are manually installed :
```
sudo dpkg -i ~/Downloads/PACKAGE_NAME 
```
First to install is libjim0.75 followed by usb-modeswitch-data and lastly usb-modeswitch
Since, @Puneet_Agarwal also have the same hardware(Huawei EC315), below lines can be added/appended to /etc/usb_modeswitch.conf and save:
```
#Huawei EC315
DefaultVendor=0x12d1
DefaultProduct=0x1f01

TargetVendor=0x12d1
TargetProductList="14db,14dc"
MessageContent="55534243123456780000000000000011062000000100000000000000000000"
```

If in doubt, open a terminal(gnome-terminal) and run:
```
sudo nano -w /etc/usb_modeswitch.conf
```
when asked give the login password. copy the above content to the file and after that press "CTRL+O and Enter" to save and "CTRL+X" to exit.
then, run:
```
sudo usb_modeswitch -c /etc/usb_modeswitch.conf
```
now, after this, Linux detects the device as a cdma modem: 
```
# lsusb 
Bus 002 Device 005: ID 12d1:**14db** Huawei Technologies Co., Ltd. 

```

Now it is configured as a LAN interface(eth3) and modem is working fine. 
```
# ifconfig 
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1454  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

**eth3**      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5978186 (5.9 MB)  TX bytes:2862924 (2.8 MB)

eth0:avahi Link encap:Ethernet  HWaddr 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0


```
Hope this helps those Huawei modem users in Gnu/Linux.

---

### Post by Kanfused on 2014-10-29
You need to make sure usbnet and cdc_ether kernel modules are loaded.

---

### Post by Akul_Narang on 2015-02-26
Hey [[COLOR=#000000]asadajk[/COLOR]]("http://ubuntuforums.org/member.php?u=1938904"),
I've followed these steps ones and it even started working. But now again I'm facing the same problem that the device is not working.
I've followed the steps again but no success.

I've have also installed a netgear driver wnda3100v2. Is it due to that?

---

### Post by amar8 on 2015-08-08
I have GSM  post pay plan. I am using huwai dongle. I able to conect using mobile broadband connection using network manager. However I am not getting speed more than 0.1 MB
In connection information , I see  Interface:GSM (cdc-wdm0), Speed is unknodwn adn driver is unknown.  I am using UBANTU 14.04.  I am not getting 3G speed.  Is there any other setting I have to do to get 3G speed.  The range bar is showing three lines and dongle light is blinking with light blue color. Can anybody shade little light on it?

---

### Post by Vladlenin5000 on 2015-08-08
> **amar8 said:**
> i have gsm  post pay plan.

gsm = 2g

---

### Post by amar8 on 2015-08-09
Is there any setting? I don't see that.  Can I use wvdial command to connect?

---

