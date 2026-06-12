---
title: "Netgear WG111v2 doesn't work if plugged in before booting Ubuntu 6.10"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by mathewke on 2007-04-08
After much trouble, I finally got Ubuntu Edgy to connect to a wireless network through Netgear WG111v2. But after rebooting, I would no longer be able to connect to the network. iwconfig would say that no access points are associated. So I tried removing the adapter before rebooting and connecting it only after logging in. This somehow works. How can I get it to work without having to remove it every time I restart? 

The following is the howto guide I followed to configure ndiswrapper:

> Install ndiswrapper, specifically ndiswrapper-utils-1.8

sudo apt-get install ndiswrapper-utils-1.8

sudo gedit /etc/modprobe.d/blacklist

Copy and paste the following to the bottom of the file. Save it. Close it.

#wg111v2 conflicting drivers
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b

Download your driver at: [http://kbserver.netgear.com/release_notes/D102843.asp](http://kbserver.netgear.com/release_notes/D102843.asp)

Select version 1.3. Download wg111v2_1_3_0.zip to your desktop. Right-click on the file, and extract the compressed folder to your desktop. For ease of use, rename the extracted file “NetgearV2&#8243;.

Configure ndiswrapper. Replace with yours. Edit path as necessary. One command at a time.

sudo ndiswrapper -i /home//Desktop/NetgearV2/Driver/WIN98/net111v2.inf

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

Add the module to /etc/modules.

sudo gedit /etc/modules

Copy and paste the following to the bottom of the file. Save it. Close it.

ndiswrapper

Reboot your machine.

Insert your wg111v2.

Confirm proper ndiswrapper installation.

sudo ndiswrapper -l

The output should show

Installed drivers:
net111v2 driver installed, hardware present

Check iwconfig.

sudo iwconfig

Fire up your network by issuing the following commands.

Configure wlan0 (or appropriate interface) via iwconfig

sudo iwconfig wlan0 essid channel 10b. Obtain a valid ip

sudo dhclient wlan0



Thanks in advance.

---

### Post by rjfioravanti on 2007-04-08
post /etc/network/interfaces

---

### Post by mathewke on 2007-04-08
Here is the /etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid jawahar

auto wlan0
```

---

### Post by rjfioravanti on 2007-04-08
Try rebooting your computer with the card in the USB slot, then after the computer is finished booting, show the results to 

```

dmesg

```
and
```

cat /var/log/syslog

```

---

### Post by einar.kristian on 2007-04-08
I've also got problems with the wg111v2. However, I'm using the kernel version of the wireless driver, not Ndiswrapper.

Here's the iwconfig output:
einar@d-d-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     802.11b/g link..  ESSID:"joergensen"
          Mode:Managed  Channel=8  Access Point: 00:18:4D:AF:B6:A8
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Here's the iwlist output;
einar@d-d-desktop:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:AF:B6:A8
                    ESSID:"joergensen"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:8
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:13  Signal level:0  Noise level:28
                    Extra: Last beacon: 0ms ago

And here's the ifconfig output:
wlan0     Link encap:Ethernet  HWaddr 00:18:4D:AF:B6:A8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:590 errors:12 dropped:4 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:35382 (34.5 KiB)  TX bytes:0 (0.0 b)

To me it looks like it has contact with the access point, but it won't connect.

Any ideas? I've tried a lot of options including System settings (kubuntu) and the wireless assistant. The kernel version is Linux version 2.6.17-11-generic.

Einar

---

### Post by mathewke on 2007-04-08
I have attached below the output of dmesg when
1) I rebooted with the USB adapter plugged in (dmesg.txt)
2) I rebooted without the adapter but plugged it in after logging in (dmesg_without.txt)

I have removed some parts of the output in the beginning which I think are irrelevant. In the first case the rtl8187 driver is registered first before the ndiswrapper, even though I had added rtl8187 to /etc/modprobe.d/blacklist. But in the second case ndiswrapper is detected first. I am pretty sure this is the cause for this problem.

Should I attach the output of cat /var/log/syslog also?

---

### Post by rjfioravanti on 2007-04-09
Don't worry about the syslog, this info seems pretty good. And yes I guess the problem is that it is loading the wrong driver first if it is plugged in. Are you sure that you did all of the following steps? Maybe confirm, or redo them

Put the following lines at the end of the file, then save and close the editor

blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b

4. Configure ndiswrapper

sudo ndiswrapper -i ~/drivers/netgear/Driver/WIN98/net111v2.inf
sudo rmmod r8187   # maybe this should be spelled rmmod rtl8187, not sure
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

---

### Post by rjfioravanti on 2007-04-09
> **einar.kristian said:**
> I've also got problems with the wg111v2. However, I'm using the kernel version of the wireless driver, not Ndiswrapper.

Here's the iwconfig output:
einar@d-d-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     802.11b/g link..  ESSID:"joergensen"
          Mode:Managed  Channel=8  Access Point: 00:18:4D:AF:B6:A8
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Here's the iwlist output;
einar@d-d-desktop:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:AF:B6:A8
                    ESSID:"joergensen"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:8
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:13  Signal level:0  Noise level:28
                    Extra: Last beacon: 0ms ago

And here's the ifconfig output:
wlan0     Link encap:Ethernet  HWaddr 00:18:4D:AF:B6:A8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:590 errors:12 dropped:4 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:35382 (34.5 KiB)  TX bytes:0 (0.0 b)

To me it looks like it has contact with the access point, but it won't connect.

Any ideas? I've tried a lot of options including System settings (kubuntu) and the wireless assistant. The kernel version is Linux version 2.6.17-11-generic.

Einar



The driver that seems to be giving you limited functionality is experimental. It seemed to work for me but my computer kept freezing and it took me a while to figure out my wireless card was causing the freezes. Try ndiswrapper, it shoudl work for you no problem

---

