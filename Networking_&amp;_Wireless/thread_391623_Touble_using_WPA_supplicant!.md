---
title: "Touble using WPA_supplicant!"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by 01ago on 2007-03-23
I use a USB stick with Ralink RT73 Chip inside, by installing ndiswrapper on Ubuntu 6.10 Edgy.
I tried to use wpa_supplicant to connect the network of our school, which uses PEAP authentication. Unfortunately, I met some problems. I think there must be sth. wrong in wpa_supplicant.conf. Could anyone tell me how to modify it?

The driver has been installed correctly, I think.
I copied three driver files under WinXP, rt73.ini, rt73.sys and rt73.bin to the folder /home/pz/rt73/
and type in the terminal:
> sudo ndiswrapper -i rt73.ini
sudo ndiswrapper -m
sudo modprobe ndiswrapper

Then the wireless card works
> pz@pz-laptop:~$ iwconfig 
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"admin"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
eth0      no wireless extensions.

sit0      no wireless extensions.

> pz@pz-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:12:A9:55:BC:D5
                    ESSID:"ACCESS-ACS"
                    Mode:Master
                    Frequency:2.437 GHz
                    Encryption key:on
                    Extra:tsf=0000000089e08fb0


However there is also a small problem. After I have started Ubuntu and scanned for APs,   every time I want to scan again, there is always no results. I wonder if there is sth wrong with the driver.

I'm also not sure if I have configured wpa_supplicant correctly. Here is the content of /etc/wpa_supplicant.conf
> ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="ACCESS-ACS"
	key_mgmt=IEEE8021X
	eap=PEAP
	identity="G0452435M"
	password="athrunzala"
          phase1="peaplabel=0"
	phase2="auth=MSCHAPV2"
}

And finally the Error information
> pz@pz-laptop:~$ sudo wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf
Password:
ioctl[SIOCSIWMODE]: Device or resource busy
Could not configure driver to use managed mode
Trying to associate with 00:12:a9:55:bc:d5 (SSID='ACCESS-ACS' freq=2437 MHz)
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out.
:confused: :( :(

---

### Post by 01ago on 2007-03-26
Doesn't anyone knows?:( 
a little bit dissappointed

---

