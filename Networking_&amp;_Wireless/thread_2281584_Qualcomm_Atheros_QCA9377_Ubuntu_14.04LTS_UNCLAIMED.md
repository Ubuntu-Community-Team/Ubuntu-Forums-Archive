---
title: "Qualcomm Atheros QCA9377 Ubuntu 14.04LTS UNCLAIMED"
date: 2015-06-08
forum: Networking &amp; Wireless
---

### Post by seeyouu on 2015-06-08
Dear all, 
I've just bought an ACER aspire E15 and and tried to run ubuntu 14.04 LTS with Windows8.1 dual booting. 

I'd face the problem which I can't detect wireless network, while wired and Bluetooth are working fine. 
I tried to look for many solutions online and the closest solution maybe under this post [http://ubuntuforums.org/showthread.php?t=2172044](http://ubuntuforums.org/showthread.php?t=2172044), but unfortunately none of them is working. 

while I run sudo lshw -C network, this is what I get: 

> *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 2c:60:0c:68:dd:06
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=13.199.113.165 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:63 ioport:4000(size=256) memory:c4404000-c4404fff memory:c4400000-c4403fff
  *-network UNCLAIMED
       description: Network controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:c4200000-c43fffff


I'm not sure what's the root cause, or perhaps QCA9377 still not yet supported by ubuntu? 

I'd uploaded my wifi info here: 
[http://paste.ubuntu.com/11643858/](http://paste.ubuntu.com/11643858/)

Appreciate if anyone can help me on this. Thanks!

---

### Post by Bucky Ball on 2015-06-08
Plug in with a cable> update your install> open Additional Drivers. Anything there for your wireless card? 

For starters, you have Network Manager AND Wicd installed. Remove one as trying to run them both together will cause major issues. After that, plug in a cable and reboot. If the one you didn't remove doesn't work, try the other by itself, if you follow me. Either use Wicd or Network Manager to test. Not both. That is creating more issues.

---

### Post by seeyouu on 2015-06-08
Thanks Bucky Ball.

I can't find any additional drivers there. and removing either wicd or network manager doesn't solve the problem.

---

### Post by chili555 on 2015-06-08
Here is your device: > Qualcomm Atheros Device [[COLOR="#FF0000"]168c:0042[/COLOR]] (rev 30)A Google search for this device yields nothing whatever that's useful. Yours may be the first in the universe. I suggest you register and file a bug report. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) I suggest something along the lines of 'Atheros QCA9377 device 168c:0042 not supported.'

Next, I notice there is a Broadcom driver installed and loaded:> wl                   6367833  0 
cfg80211              521225  1 wlIt is not helpful and will probably conflict with other appropriate drivers. I suggest you remove it:```
sudo apt-get purge bcmwl-kernel-source
```You could try ndiswrapper to try to get your device working. Frankly, it is a weak crutch. It depends on Windows XP driver files. I doubt they exist for this shiny new device.

Finally, until support comes along, I'd suggest an inexpensive USB wireless device. There are often threads here about working devices. I have and use a TP-Link TL-WN722N that cost all of US$12.

---

### Post by seeyouu on 2015-06-08
Thank you very much, Chili555 :p

---

### Post by Bucky Ball on 2015-06-08
> **chili555 said:**
> A Google search for this device yields nothing whatever that's useful. Yours may be the first in the universe.

Thanks for confirming. Exactly what I was finding and thinking. Not being able to find much info on device usually means one of two things: it works out of the box or it has only just arrived on shelves. :)

I'd go with what chili has suggested and grab a cheap wireless dongle for now. Support will arrive for that device eventually, hopefully, and the ndiswrapper option can be fraught with issues. I wouldn't go there, either. Good luck.

---

### Post by seeyouu on 2015-06-09
Is there anyone able to find a fix for this??

---

### Post by Bucky Ball on 2015-06-10
If chili555 couldn't it is doubtful anyone here can, but you never know. He is one of the resident networking gurus. 

The main reason wireless devices don't work on Ubuntu is that they are very new and/or the manufacturer isn't Linux friendly, and the community and developers haven't had any time to create a driver. Your card appears to be very new (as there is scant reference to it online) ...

Generally, if it doesn't work now it will in the future. Many Qualcomm devices work out of the box. Yours will probably join their number in the future. The question is when ...

---

### Post by QIII on 2015-06-10
It's not a matter of whether Ubuntu supports your hardware.  It's a matter of whether your hardware OEM supports its hardware with a Linux driver.  I found no Linux driver on qca.qualcomm.com.

It may be that someone in the community will come up with an open source driver, but they will have to do so designing in to a black box.  I'm sure Qualcomm doesn't publish its trade secrets.

So, unfortunately, there is no "fix".  There is only hoping that Qualcomm comes out with a driver that supports Linux.

---

### Post by seeyouu on 2015-06-10
:cry::cry::cry::cry::cry::cry::cry:

---

### Post by Bucky Ball on 2015-06-10
And another from me. :(

If you get into Linux/Ubuntu you'll get into the habit of checking for compatibility prior to buying hardware. Some new users have the issue of their hardware not working because, obviously, they bought it before they had any need for it to 'just work' in Ubuntu. It can put them off and I hope this doesn't have the same effect on your good self.

The majority of hardware does 'just work', but as QIII outlines, the Ubuntu community and devs can only 'do what they can' when a manufacturer doesn't provide Linux drivers. It is down to the manufacturer to provide drivers and compatibilty, not Ubuntu or Canonical. They have no control over such things. All they can do is cobble something together at their own expense and in their own time, if one of their number has both to spare and the inclination.

There are many friendly manufacturers out there, though, thankfully. Most thing Broadcom or Realtek will work 'out of the box'. If you go ahead and buy a cheap dongle (the last I bought was about $8 and worked when I plugged it in) have a check here and elsewhere to confirm it will work 'out of the box'. ;)

---

### Post by QIII on 2015-06-10
Sigh.  This is our lot...

---

### Post by chili555 on 2015-06-10
> **seeyouu said:**
> :cry::cry::cry::cry::cry::cry::cry:As I said:> Finally, until support comes along, I'd suggest an inexpensive USB wireless device. There are often threads here about working devices.

---

### Post by Aneesh_Vivekananda on 2015-07-31
Hi I am Also facing the same issue.Anybody pls help...

---

### Post by Bucky Ball on 2015-07-31
> **Aneesh_Vivekananda said:**
> Hi I am Also facing the same issue.Anybody pls help...

Welcome. Please post a new thread rather than waking this one up. If you want help, please include as much information as possible about your problem. Expect little to no chance of support on the strength of the information you've provided. 

You're problem is the same? Are you using the same hardware? Same Ubuntu release and flavour? There is generally a 99% chance the problems aren't the same. Too many variables.

Jumping in fourteen posts deep on someone else's thread that has been asleep for six weeks doesn't help your chances of support, either. ;)

---

### Post by rinfinity on 2015-11-07
[http://ubuntuforums.org/showthread.php?t=2300861&page=3](http://ubuntuforums.org/showthread.php?t=2300861&page=3)

Here's all you'll need to make your QCA9377 work: at post #25
Kindly post your results in the said thread.

---

### Post by tintumon2 on 2015-12-29
Hi, 

*****THIS WORKED FOR ME******* (My Laptop: ACER ASPIRE E5-573G-376F)

[https://codeload.github.com/ajaybhatia/Qualcomm-Atheros-QCA9377-Wifi-Linux/zip/master](https://codeload.github.com/ajaybhatia/Qualcomm-Atheros-QCA9377-Wifi-Linux/zip/master)

Just download & install it.

Thanks.;)

---

### Post by joucoski on 2016-01-02
I tried using the procedures in this discussion, but I could not run my  wifi card. Part of the file "wireless-info.txt" is here (the complete  file is attached):

```
##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Samsung Electronics Co Ltd Device [144d:412b]

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 0c)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c757]
    Kernel driver in use: r8169
```

Could someone show me how I can fix the device to work?

wireless-info.txt: [ATTACH]266505[/ATTACH]

---

### Post by satish-babariya on 2016-06-30
[h=3]This is how I fixed the WiFi issue in my Laptop[/h] 
 
 [h=5]Identify your WiFi device. Open a terminal and issue[/h] 
 
 lspci  | grep Network
# It should display the name of your WiFi card
# If the output is similar to the one below, you are in luck, we can fix this easily
mansoor ~ $ lspci  | grep Network
03:00.0 Network controller: Qualcomm Atheros Device 0042 (rev 30) 
 
 Once you have made sure that the Network device is the one above, follow the below steps to install the driver for WiFi ##### Install git and tools to compile the driver
 
 
 sudo apt-get install build-essential linux-headers-$(uname -r) git[h=5]Issue the following commands one by one. Anything written after “#” is a comment and you don’t have to execute it.[/h] 
 
 # Modify the config files
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf

# Download the backport
wget [https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz)

# Extract it
tar zxvf backports-20151120.tar.gz

# cd to the directory, compile and install it. The commands 'make' and 'make install' will take some time to finish
cd backports-20151120
make defconfig-wifi
make
sudo make install

# Download the firmware for the WiFi card
git clone [https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)

# Copy the firmware to appropriate locations. 
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
sudo cp /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin 
 
 [h=5]Reboot your machine. That’s it. Your wifi should work now until you do a kernel update.[/h]

---

### Post by jeremy31 on 2016-06-30
> **satish-babariya said:**
> [h=3]This is how I fixed the WiFi issue in my Laptop[/h] 
 
 [h=5]Identify your WiFi device. Open a terminal and issue[/h] 
 
 lspci  | grep Network
# It should display the name of your WiFi card
# If the output is similar to the one below, you are in luck, we can fix this easily
```
mansoor ~ $ lspci  | grep Network
03:00.0 Network controller: Qualcomm Atheros Device 0042 (rev 30) 
```
 
 Once you have made sure that the Network device is the one above, follow the below steps to install the driver for WiFi ##### Install git and tools to compile the driver
 
 
 ```
sudo apt-get install build-essential linux-headers-$(uname -r) git
```[h=5]Issue the following commands one by one. Anything written after “#” is a comment and you don’t have to execute it.[/h] 
 
 # Modify the config files
```
echo "options ath10k_core skip_otp=y" | sudo tee /etc/modprobe.d/ath10k_core.conf
```

# Download the backport
```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2015/11/20/backports-20151120.tar.gz
```

# Extract it
```
tar zxvf backports-20151120.tar.gz
```

# cd to the directory, compile and install it. The commands 'make' and 'make install' will take some time to finish
```
cd backports-20151120
make defconfig-wifi
make
sudo make install
```

# Download the firmware for the WiFi card
```
git clone https://github.com/kvalo/ath10k-firmware.git
```

# Copy the firmware to appropriate locations. 
```
sudo cp -r ath10k-firmware/QCA9377 /lib/firmware/ath10k/
sudo cp /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware-5.bin
``` 
 
 [h=5]Reboot your machine. That’s it. Your wifi should work now until you do a kernel update.[/h]

Please use code tags, I changed it in the quoted part of this post.  There is a much newer version of backports available and an easier way to get the firmware
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb
```

The backports are not needed in Ubuntu 16.04

```
sudo apt-get install build-essential linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz
tar -zxvf backports-4.4.2-1.tar.gz
cd backports-4.4.2-1
make defconfig-wifi
make
sudo make install
```

---

