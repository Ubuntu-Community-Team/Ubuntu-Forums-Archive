---
title: "Unable to get Broadcom 4306 wireless card working"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by zulasmum on 2010-08-03
Hi
I have recently installed Ubuntu 10.04 and am up and running with my wired connection but my Buffalo PCI card with Broadcom BCM4306 chipset is not working and shows up as disabled. I have looked at various tutorials and howtos to get it going using ndiswrapper etc but have not got there yet.

iwconfig is:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Not sure what other info you need me to give right now but any pointers would be appreciated.

Thanks

---

### Post by Paul820 on 2010-08-03
Is this any good to you: [http://andriesurya.wordpress.com/2010/05/02/enabling-broadcom-4306-rev-3-on-ubuntu-10-04-internetless/]("http://andriesurya.wordpress.com/2010/05/02/enabling-broadcom-4306-rev-3-on-ubuntu-10-04-internetless/")

---

### Post by zulasmum on 2010-08-03
Thanks
I'll check it out, although the link seems to be for those with no wired connection either - which I do have.

---

### Post by beew on 2010-08-03
The broadcom 4306 uses legacy drivers which apparently are not in the bcm43 kernel sources from the repository, those work for newer cards. You have to download and install them manually with b43-fwcutter.

I managed to get the wifi working beautifully  for an old laptop with the bcm4306 card following the instructions here [http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy](http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy)

The relevant part is here
 
 
 > If you are using the **b43legacy** driver, follow these instructions. 
Install b43-fwcutter, then use version 3.130.20.0 of Broadcom's proprietary driver.
Download and extract the firmware from this driver: 

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
sudo ./b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta-3.130.20.0.oNote  that you must adjust the FIRMWARE_INSTALL_DIR path to your  distribution. The standard place where firmware is installed to is  /lib/firmware. However some distributions put firmware in a different  place. 

Good luck. :)

Oh, instead of "sudo ./b43-fwcutter-013/b43-fwcutter -w.." I  just  did "sudo ./b43-fwcutter -w...". Also, check if the directory /lib/firmware already exists. If it does, then you don't need the first line and simply type /lib/firmware instead of "$FIRMWARE_INSTALL_DIR" in the third.

---

### Post by zulasmum on 2010-08-03
Thanks for your help, I've got it going now at last!

---

### Post by bkratz on 2010-08-03
> **beew said:**
> The broadcom 4306 uses legacy drivers which apparently are not in the bcm43 kernel sources from the repository, those work for newer cards. You have to download and install them manually with b43-fwcutter.

I managed to get the wifi working beautifully  for an old laptop with the bcm4306 card following the instructions here [http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy](http://linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy)

The relevant part is here
 
 
 Good luck. :)

Oh, instead of "sudo ./b43-fwcutter-013/b43-fwcutter -w.." I  just  did "sudo ./b43-fwcutter -w...". Also, check if the directory /lib/firmware already exists. If it does, then you don't need the first line and simply type /lib/firmware instead of "$FIRMWARE_INSTALL_DIR" in the third.

Rev 3 of the BCM4306 uses the b43 drivers not the legacy. You can tell which one you have by going to the terminal and doing

```
lspci -vnn | grep 14e4
```


and checking against the codes shown here

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)


Too little too late--congratulations!

---

### Post by beew on 2010-08-03
you're right. Mine was rev2.

---

