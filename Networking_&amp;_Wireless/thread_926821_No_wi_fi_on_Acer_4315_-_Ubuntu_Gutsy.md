---
title: "No wi fi on Acer 4315 - Ubuntu Gutsy"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by thewebpromoter on 2008-09-22
guys,
I need your help, I have been roaming around the internet and a lot of forums, but I have not found anything that can help me get my wi fi UP on my Ubuntu Gutsy, I am using an Acer 4315 Aspire laptop, and I cannot make it with the wireless LAN, I tried to issue a command such as ifconfig -a and it shows the following:


eth0      Link encap:Ethernet  HWaddr 00:1D:72:32:40:C1  
          inet addr:192.168.122.229  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe32:40c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19554349 (18.6 MB)  TX bytes:1007868 (984.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I have also tried madwifi, but it does not help.

Thanks for your advise and more power to Linux users

---

### Post by thewebpromoter on 2008-10-05
> **thewebpromoter said:**
> guys,
I need your help, I have been roaming around the internet and a lot of forums, but I have not found anything that can help me get my wi fi UP on my Ubuntu Gutsy, I am using an Acer 4315 Aspire laptop, and I cannot make it with the wireless LAN, I tried to issue a command such as ifconfig -a and it shows the following:


eth0      Link encap:Ethernet  HWaddr 00:1D:72:32:40:C1  
          inet addr:192.168.122.229  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe32:40c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19554349 (18.6 MB)  TX bytes:1007868 (984.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I have also tried madwifi, but it does not help.

Thanks for your advise and more power to Linux users


SOLVED:

sudo aptitude update && sudo aptitude -y install build-essential linux-headers-$(uname -r)
cd ~
wget -O driver.tar.gz [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz)
tar xf driver.tar.gz
cd madwifi-*
make
sudo make install
echo ath_pci | sudo tee -a /etc/modules
sudo modprobe ath_pci

Thanks, bmartin:

[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

---

