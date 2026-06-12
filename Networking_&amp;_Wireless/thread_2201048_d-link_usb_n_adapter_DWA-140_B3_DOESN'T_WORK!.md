---
title: "d-link usb n adapter DWA-140 B3 DOESN'T WORK!"
date: 2014-01-22
forum: Networking &amp; Wireless
---

### Post by Jonatan_Barr on 2014-01-22
Hi, I'm new to linux and all this...I really need some help getting 
my "d-link usb n adapter DWA-140 B3" to work. I know this topic has been
discussed here before but I hope you can help me out anyways.  

I downloaded the drivers:
2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO
and DOP_RT5572_LinuxSTA_2.6.1.3_20121022
Neether of theese seems to work

I went in to the file:
*os/linux/config.mk*
and wrote "HAS_WPA_SUPPLICANT=y" and "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y"

Then I went in to the file:
*include/os/linux/rt_linux.h*
I renamed "usb_buffer_alloc()" to "usb_alloc_coherent()"
and renamed "usb_buffer_free()" to "usb_free_coherent()"

Then I wrote these commands in terminal:
$ sudo su
$ make
$ make install


make gave me this error:

make -C tools
make[1]: Entering directory `/root/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/root/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools'
/root/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /root/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38/build SUBDIRS=/root/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux modules
make: *** /lib/modules/2.6.38/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2


make install gave me this:
make -C /root/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/root/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /root/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.38/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.38/kernel/drivers/net/wireless/
install: cannot stat `rt5370sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/root/Desktop/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux'
make: *** [install] Error 2

Ifconfig doesn't show wlan0 or Ra0
Iwconfig doesn't show any wireless connections
lsusb shows my usb id (2001:3c15)
I'm using VMware from an asus laptop

If you need any more information, just ask! 
What have I missed? Should I buy a new wireless adapter? in that case which one?

---

### Post by chili555 on 2014-01-22
This device works with the driver rt2800usb in recent Ubuntu versions. 

You are probably not going to get this antique to compile on a recent version:> [COLOR="#FF0000"]2011[/COLOR]_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2 .5.0.3_DPOWe no longer use wooden wheels on our sleek tuxedo black BMWs! [http://www.wernerwagonworks.com/images/wagonwheel.png](http://www.wernerwagonworks.com/images/wagonwheel.png)

This error: > make: *** /lib/modules/2.6.38/build: No such file or directory. Stop....indicates that you haven't installed the necessary prerequisite linux-headers-generic. 

I see you have an ancient Ubuntu version from this:> /lib/modules/[COLOR="#FF0000"]2.6.38[/COLOR]/kernel/drivers/net/wireless/I suggest you install at least Ubuntu 12.04.3; we have made a lot of progress in drivers in the last fifty years!

---

### Post by Jonatan_Barr on 2014-01-22
thank you man, means a lot

---

### Post by praseodym on 2014-01-22
With Ubuntu 12.04 you can install the driver via dkms:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/42/20/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5370sta -v 2.5.0.3
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
sudo dkms install -m Ralink_5370sta -v 2.5.0.3 
sudo mkdir -p /etc/Wireless/RT2870STA
sudo cp /usr/src/Ralink_5370sta-2.5.0.3/src/RT2870STA.dat /etc/Wireless/RT2870STA 
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Rebiit.

This will build the driver automatically after kernel upgrades

---

### Post by Jonatan_Barr on 2014-01-29
I just updated my kernel version and everything works fine! I didn't have to upgrade to ubuntu 12.04.

---

