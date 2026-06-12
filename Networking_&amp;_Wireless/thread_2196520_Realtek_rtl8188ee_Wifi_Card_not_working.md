---
title: "Realtek rtl8188ee Wifi Card not working"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by awhb87 on 2013-12-30
I'm new to Ubuntu, and I'm installing it on my laptop for the first time. I'm on an Hp Envy 15, and the wireless card I'm using is a RealTek RTL8188EE. I'm trying to install the drivers and I'm getting an Error 2 on the make (See attached screenshot). If you guys need anything just ask. Thanks in advance for any help.

---

### Post by varunendra on 2013-12-30
Welcome to the forums awhb87 !

You don't have "build-essential" (and probably kernel headers too) installed, hence the error. Although I doubt even with those you are going to succeed in building the driver if you are on one of the latest kernels. But anyway, while being connected to internet via cable or other means, please do -
```
sudo apt-get install build-essential linux-headers-generic
```
After the installation is finished, try -
```
make clean
make
```
From the driver source directory again.

If, as I fear, the make still fails, post back the entire output as well as the details of the problem you are having and whatever you have tried so far.

A detailed report about your wireless setup may also help. For that, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by awhb87 on 2013-12-30
This is what I get when I did the commands you asked:
```
andrew@Hennessy-Linux:~$ sudo apt-get install build-essential linux-headers-generic[sudo] password for andrew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1 thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andrew@Hennessy-Linux:~$ cd ~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/
andrew@Hennessy-Linux:~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ make clean
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Entering directory `/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192ce'
make[1]: Entering directory `/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192se'
make[1]: Entering directory `/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8192de'
make[1]: Entering directory `/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8723e'
make[1]: Entering directory `/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/rtl8188ee'
andrew@Hennessy-Linux:~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ make
make -C /lib/modules/3.10.1-031001-generic/build M=/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make: *** /lib/modules/3.10.1-031001-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2

```

In response to you asking what I have tried, well that's just about everything I could find. If you'd like I could go through my history and try to find every possible solution I've tried.

---

### Post by varunendra on 2013-12-30
Please post back the script report I asked for and it may tell us about the important aspects of your setup.

Along with that, please also post the outputs of -
```
find / -maxdepth 4 -name build 2>/dev/null
```

---

### Post by awhb87 on 2013-12-30
Wireless Report:

```


*************** info trace ***************


***** uname -a *****


Linux Hennessy-Linux 3.10.1-031001-generic #201307131550 SMP Sat Jul 13 19:51:31 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise


***** lspci *****


07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5227] (rev 01)
--
0f:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Hewlett-Packard Company Device [103c:1963]
    Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 003 Device 003: ID 0bda:571a Realtek Semiconductor Corp. 
Bus 003 Device 004: ID 138a:0050 Validity Sensors, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****




***** rfkill *****




***** lsmod *****




***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             24.217.0.5
    DNS:             24.217.201.67
    DNS:             24.247.15.53






***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


auto lo
iface lo inet loopback




***** iwlist *****




***** resolv.conf *****


nameserver 127.0.0.1


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist hp-wmi
blacklist hp-wmi


***** modinfo *****




***** udev rules *****


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.6/0000:0f:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


***** dmesg *****


[   20.561331] r8169 0000:0f:00.0 eth0: unable to load firmware patch rtl_nic/rtl8168g-2.fw (-2)


****************** done ******************

```

The other code you asked for:

```

andrew@Hennessy-Linux:~$ find / -maxdepth 4 -name build 2>/dev/null
/lib/modules/3.2.0-57-generic/build
/lib/modules/3.8.0-34-generic/build
/lib/modules/3.8.0-29-generic/build

```

---

### Post by chili555 on 2013-12-30
I believe Varun would also love to see if the correct headers are installed:```
sudo dpkg -s linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~. I suspect you do not have headers for this little beauty:> 3.10.1-031001-generic

---

### Post by awhb87 on 2013-12-30
As requested:

```
andrew@Hennessy-Linux:~$ sudo dpkg -s linux-headers-`uname -r`[sudo] password for andrew: 
Package `linux-headers-3.10.1-031001-generic' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```

---

### Post by chili555 on 2013-12-30
It is apparent that kernel headers matching your running kernel, which are needed to compile from source code, are not installed. Wherever this kernel came from:> 3.10.1-031001-generic ...is where I believe you will also find the headers. Download, install, compile and smile!

Here, perhaps? [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.1-saucy/) You will need linux-headers-xyz-all and also either i386 if you have a 32-bit system or amd64 if you have a 64-bit system.

---

### Post by awhb87 on 2013-12-30
I downloaded and installed:
[linux-headers-3.10.1-031001_3.10.1-031001.201307131550_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.1-saucy/linux-headers-3.10.1-031001_3.10.1-031001.201307131550_all.deb")
[linux-headers-3.10.1-031001-generic_3.10.1-031001.201307131550_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.1-saucy/linux-headers-3.10.1-031001-generic_3.10.1-031001.201307131550_amd64.deb")

They installed successfully

Then a make clean followed by:

```
andrew@Hennessy-Linux:~/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ make
make -C /lib/modules/3.10.1-031001-generic/build M=/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.10.1-031001-generic'
  CC [M]  /home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function &#8216;rtl_action_proc&#8217;:
/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:885:32: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:886:32: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function &#8216;rtl_send_smps_action&#8217;:
/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:1451:24: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
make[2]: *** [/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/andrew/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.10.1-031001-generic'
make: *** [all] Error 2

```

---

### Post by chili555 on 2013-12-30
We have hopped over one hurdle, now the next. Please download this file to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.12/backports-3.12-1.tar.bz2) Right-click it and select 'Extract Here.' Now to the terminal:```
cd ~/Desktop/backports-3.12-1
make defconfig-rtlwifi
make
suco make install
sudo modprobe rtl8188ee
```Working?

---

### Post by awhb87 on 2013-12-30
Good news: The make and install all took. However running the modprobe did not reset the WiFi, so I decided, why not try a reboot. What could possibly go wrong? Well Murphy struck again. I get all the way to the Ubuntu splash screen for booting, the orange dots fill completely, but it just idles there. I left it for around 10 minutes but no luck. Unfortunately, I had to boot to my Windows 8.1 partition.

---

### Post by chili555 on 2013-12-30
Can you try to boot to Ubuntu again, please?

---

### Post by awhb87 on 2013-12-30
I tried twice. But I'll go ahead and humor you.

---

### Post by chili555 on 2013-12-30
> **awhb87 said:**
> I tried twice. But I'll go ahead and humor you.When it boots, we want to see:```
dmesg | grep rtl
```Firmware, methinks.

---

### Post by awhb87 on 2013-12-30
That's a no-go on the booting. I can't get through to Ubuntu. If I need to leave it for a long while I can do that. 

A little tidbit of information that I'm unsure if it's relevant or not, but to much information can't be bad. I do have nomodeset in my grub so that I get a display. Without it, when it boots, my display turns off completely.

We could go try a clean install if you'd think that would help.

---

### Post by chili555 on 2013-12-30
> **awhb87 said:**
> That's a no-go on the booting. I can't get through to Ubuntu. If I need to leave it for a long while I can do that. 

A little tidbit of information that I'm unsure if it's relevant or not, but to much information can't be bad. I do have nomodeset in my grub so that I get a display. Without it, when it boots, my display turns off completely.

We could go try a clean install if you'd think that would help.As much as I hate to concede (temporary) defeat, a reinstall is quick, about 20 minutes, and pretty easy. That's what I'd do.

---

### Post by awhb87 on 2013-12-30
Alright I'm back up and live again. Only things I've done so far is:

```

sudo apt-get update

sudo apt-get upgrade
```

Also, I have updated my Grub to have nomodeset a default for easier booting. Now what exactly would you like me to do?

---

### Post by chili555 on 2013-12-30
Please do:```
sudo apt-get install linux-headers-generic build-essential
```Then the steps in post #10.

---

### Post by awhb87 on 2013-12-30
Ran the commands as asked. All of the commands took, however it still appears that my WiFi is still broken. Guessing you want me to run the command from earlier: [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep rtl
[/FONT][/COLOR]
```
andrew@Hennessy-Linux:~/Desktop/backports-3.12-1$ dmesg | grep rtl
[ 6084.194598] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[ 6084.226965] rtlwifi: Firmware rtlwifi/rtl8188efw.bin not available

```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by chili555 on 2013-12-30
> rtlwifi: Firmware rtlwifi/rtl8188efw.bin not availableEasily fixable. We are getting close to the finish line here.

Some pretty smart guy posted how to get the firmware right here: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281)> If the message logs say you need firmware....et seq

---

### Post by awhb87 on 2013-12-30
Thanks for all the help man. It's up and working now.

---

### Post by chili555 on 2013-12-30
Awesome! Glad it's working. You will have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after reboot, re-compile:

```
cd ~/Desktop/backports-3.12-1/
make clean
make defconfig-rtlwifi
make
sudo make install
sudo modprobe rtl8188ee

```Please retain the file and these instructions for that time.

---

