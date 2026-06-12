---
title: "Bluetooth not discovering devices."
date: 2019-01-19
forum: Networking &amp; Wireless
---

### Post by jawahirjunu on 2019-01-19
I am trying to connect my Bluetooth headset with Ubuntu 18.04 LTS. Under Bluetooth, the Devices icon just rotates and no new devices are displayed. My kernel version is 4.15.0-43-generic. 
Please help me with this.

I tried the solution provided in the below link but in vain.

[https://askubuntu.com/questions/1050304/bluetooth-is-not-working-ubuntu-18-04-lts](https://askubuntu.com/questions/1050304/bluetooth-is-not-working-ubuntu-18-04-lts)

Thanks and Regards,
Jawahir Junaith A

---

### Post by jawahirjunu on 2019-01-19
I also tried the below 

[COLOR=#242729][FONT=Arial]I partially fixed the problem running the following commands:[/FONT][/COLOR]
sudo apt-get install build-essential git
git clone [https://github.com/lwfinger/rtlwifi_new/](https://github.com/lwfinger/rtlwifi_new/)
cd rtlwifi_new
make
sudo make install
echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
[COLOR=#242729][FONT=Arial]you might face a problem of a slow wifi connection after that, I fixed it with following commands:[/FONT][/COLOR]
sudo modprobe -r iwlwifi sudo modprobe iwlwifi 11n_disable=1
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf

Also Please find the output of lsusb below.



root@ubuntu:~# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b307 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0930:021d Toshiba Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 004: ID 04f3:01a4 Elan Microelectronics Corp. Wireless Keyboard
Bus 008 Device 003: ID 275d:0ba6 
Bus 008 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Installed the firmware as aper the below link. Still not working.

[https://askubuntu.com/questions/1069212/bluetooth-doesnt-work-with-ubuntu-18-04-bcm20702a1-13d3-3411](https://askubuntu.com/questions/1069212/bluetooth-doesnt-work-with-ubuntu-18-04-bcm20702a1-13d3-3411)

---

### Post by william282 on 2019-02-26
> **jawahirjunu said:**
> I also tried the below 

[COLOR=#242729][FONT=Arial]I partially fixed the problem running the following commands:[/FONT][/COLOR]
sudo apt-get install build-essential git
cd rtlwifi_new
make
sudo make install
echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
[COLOR=#242729][FONT=Arial]you might face a problem of a slow wifi connection after that, I fixed it with following commands:[/FONT][/COLOR]
sudo modprobe -r iwlwifi sudo modprobe iwlwifi 11n_disable=1
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/[[COLOR=#800000]kissanime[/COLOR]]("https://www.kissanime.vip/").d/iwlwifi.conf

Also Please find the output of lsusb below.



root@ubuntu:~# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b307 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0930:021d Toshiba Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 004: ID 04f3:01a4 Elan Microelectronics Corp. Wireless Keyboard
Bus 008 Device 003: ID 275d:0ba6 
Bus 008 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Installed the firmware as aper the below link. Still not working. 

Hi, i tried those method but didnt work for me&#8230;

---

