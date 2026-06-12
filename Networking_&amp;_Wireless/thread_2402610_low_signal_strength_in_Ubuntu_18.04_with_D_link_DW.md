---
title: "low signal strength in Ubuntu 18.04 with D link DWA-131 Adapter"
date: 2018-10-02
forum: Networking &amp; Wireless
---

### Post by shejintr on 2018-10-02
I am facing the problem of low signal strength in Ubuntu 18.04   with D link DWA-131 Adapter. I tried  with the solution as pointed.  But when tried to "make" after downloading git, it gives error and got  stuck there. 				
Posting as new thread  because other thread was shown closed.

---

### Post by chili555 on 2018-10-02
> I tried with the solution as pointed. But when tried to "make" after downloading git, it gives error and got stuck there. Where is the post you are following; may we have the link?

What were the errors at 'make'?

What is your exact device? Please run and post:```
 lsusb
```

---

### Post by shejintr on 2018-10-03
Out put of make command is attached -  err.txt

---

### Post by shejintr on 2018-10-03
Output of lusb is attached usb.txt

---

### Post by chili555 on 2018-10-03
The driver rtl8192eu is correct for your device. I am not sure where you got the driver you now have but let's try another that 'makes' on my system with a few possibly harmless warnings but no errors:```
cd ~/Desktop
sudo rm -rf rtl8192eu-linux-driver
sudo apt update
sudo apt install git
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
cd rtl8192eu-linux-driver
sudo dkms add .
sudo dkms install rtl8192eu/1.0
sudo modprobe 8192eu
```And blacklist the current driver:

```
sudo -i
echo "blacklist rtl8xxxu"  >>  /etc/modprobe.d/blacklist.conf
exit
```
Reboot and tell us if there is any improvement.

---

