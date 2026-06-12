---
title: "Wifi connects but I cannot browse anymore on Ubuntu 14.04.3"
date: 2015-08-24
forum: Networking &amp; Wireless
---

### Post by salmanmanekia on 2015-08-24
My home wifi suddenly stopped working (i.e. it connects but I cannot browse anymore) on my linux machine Ubuntu 14.04.3 while it keeps working on Win7. Mobile internet sharing does work on the linux machine. I ran the command mentioned in the sticky post 'Before posting in networking and wireless' when I was connected to my non working wifi and below are the attached results. Any help would be appreciated

---

### Post by salmanmanekia on 2015-08-25
anyone ?

---

### Post by praseodym on 2015-08-25
Your interface names are counting up to "23", please run
```

sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
sudo service udev restart
sudo iwconfig wlan0 power off
```

---

### Post by salmanmanekia on 2015-08-25
Thanks for the reply.
I ran the sequence of commands but still the problem remains. The interface names still counts up to 23 and the last command did not work because of 'failed to find device wlan0'. Below are the executed commands

> administrator@Computer:/etc/network$ sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
administrator@Computer:/etc/network$ sudo udevadm trigger
administrator@Computer:/etc/network$ sudo service udev reload
administrator@Computer:/etc/network$ sudo service udev restart
udev stop/waiting
udev start/running, process 7544
administrator@Computer:/etc/network$ sudo iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.
administrator@Computer:/etc/network$ iwconfig
wlan23    IEEE 802.11abgn  ESSID:"wlsalmanmanekia"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: EE:43:F6:63:12:68   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:3   Missed beacon:0


eth23     no wireless extensions.


lo        no wireless extensions.


---

### Post by praseodym on 2015-08-26
Try again

sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak

and reboot

---

