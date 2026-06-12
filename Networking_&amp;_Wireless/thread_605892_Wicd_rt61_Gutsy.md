---
title: "Wicd rt61 Gutsy"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by yousaf on 2007-11-07
Hi

Here is the problem:

I just installed Gutsy on a dualboot with Win2K. I have Edimax EW7128g RT61 pci wireless card. The built-in rt61pci driver was working with wired network but not with the wireless. It is wireless that I want to enable.

My wireless network is WPA2 AES enabled. I have disabled mac address filtering as suggested in other posts. I have also installed serialmonkey rt61 driver and removed the old one following the instructions on this link:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

I also installed Wicd. 

Despite this, I still can't connect to my wireless network. Wicd does give me the option to set WPA 1 or 2, but whenever I try to connect to it Wicd shows that it is connected to the wireless network at 0% signal.

Following the serialmonkey instructions, I also amended my /etc/network/interface file and the wireless entry looks like this:

auto wlan0
iface wlan0 inet static
address 10.0.0.2
netmask 255.255.255.0
network 10.0.0.138
gateway 10.0.0.138
pre-up ifconfig wlan0 up
pre-up iwpriv wlan0 set AuthMode=WPA2-PSK
pre-up iwpriv wlan0 set EncrypType=AES
pre-up iwpriv wlan0 set WPA2-PSK=passphrasehere
pre-up iwpriv wlan0 set SSID=networkname
pre-up iwpriv wlan0 set NetworkType=Infra

I am not sure if I needed the above entry or not as Wicd lets me enter all this information through GUI anyway.

Could someone who managed to set his/her connection with RT61 and Wicd on Gutsy please help me with this?

Thanks
Yousaf

---

### Post by yousaf on 2007-11-07
Hi

It seems I can access my wireless network through Wicd but without any encryption. I tried both WEP and WPA2 but didn't work.

Does anyone know how to tweak Wicd to enable WEP or WPA?

Thanks
Yousaf

---

### Post by Cybergod on 2007-11-07
Try adding quotation marks around the key in the text box.

---

### Post by yousaf on 2007-11-08
Just tried that, didn't work.

I am thinking of clean installing gutsy again and work with wicd and the original driver.

---

### Post by yousaf on 2007-11-08
Update:

Just did a clean install. Everything is working out of the box. Didn't even have to install Wicd!

The only different thing I did this time was to select AES and CCMP [?] from the drop down on the system tray. Then I manually configured my wireless connection with static IP and WPA Personal encryption. 

I am now afraid to download Wicd, even though I prefer the GUI.

---

### Post by yousaf on 2007-11-08
Update2:

Just so that other people can benefit, here is the entry in my /etc/network/interfaces file:

iface wlan0 inet static
address <IPADDR>
netmask <NETMASK>
gateway <ROUTERADDR>
wpa-psk <HEXVALUE> #I entered this in network manager as an alpha-numeric value
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid <SSID>

auto wlan0

Please note that I used network manager's GUI to enter all the above.

---

### Post by yousaf on 2007-11-08
Update3:

My joy was short-lived. I rebooted the machine and the wireless was gone. In /etc/network/interfaces, the following entry magically appeared:

iface wlan0 inet static
address <IPADDR>
netmask <NETMASK>
gateway <MYROUTER>
wireless-essid <MYESSID>

auto wlan0

Don't know why the previous entry got deleted after the reboot!

:-k

---

### Post by yousaf on 2007-11-08
Update4:

Installed Wicd using the instructions on Wicd site and so far it is working without any problems.

---

