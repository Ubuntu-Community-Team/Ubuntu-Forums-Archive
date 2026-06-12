---
title: "TP-Link WIreless Modem TL-WN725N"
date: 2016-05-10
forum: Networking &amp; Wireless
---

### Post by afz12 on 2016-05-10
I am using an old HP Pavilion dv6 that lost its internal wireless card  some time ago. I plugged a TP-Link TL-WN725N USB WiFi modem in and  booted into Ubuntu 16.04. Interestingly the modem worked but was very  "deaf". Unfortunately TP-Link doesn't have a Linux driver for this model  so I tried the Windows set-up using Wine and this partially installed. I  then ran XP as a VM using Virtualbox and installed it and now the modem  works fine - using it now

However this is temporary. Getting this Windows USB to work on Linux when it probably shouldn't is tantalizingly close to working fine. Surely there must be an excellent Linux way to do this, even if such a solution has evaded TP-Link so far.

I am curious I guess and this would be an opportunity to learn a bit more about Linux I guess:)

I think the chipset is Realtek rtl8188eus

---

### Post by afz12 on 2016-05-12
I hope not to be correctly accused of replying to myself as I am, but I went out and spent $NZ 36 on a TP-Link WN-821 USB WiFi dongley and installed Linux drivers as per some other post who I forget - but appreciate though. Anyway this text might help others - the code steps work on a HP Pavilion dv6 notebook in OS dual boot Mint Cinnamon 1.3 and Ubuntu 16.04 - also seems to install in a HP Envy in Mint 17.3 Cinnamon and Ubuntu 16.04 also. Also I like LinSSID - code steps for a terminal follow. Anyway, all is curious stuff to me - I really like Linux but I certainly don't dis Windows, I suspect we owe a lot in CPU technology-progress to Bill Gate's claim to "put a computer in every home". Well now we have them crawling out our ears everywhere don't we? It's a better fun to have as many OS as we can poke sticks at :D


  	 	 	 	   "Ensure you have the necessary prerequisites installed:

 sudo apt-get update
sudo apt-get install git linux-headers-generic build-essential dkms Clone this repository:
 git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git) Set it up as a DKMS module:

 sudo dkms add ./rtl8192cu-fixes Build and install it:
 sudo dkms install 8192cu/1.10 Refresh the module list:
 sudo depmod -a Ensure the native (and broken) kernel driver is blacklisted:
 sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/ And reboot. You're done."

I'll retrace this author - a bright spark luminary as ever there was

 
some more...
 
 "There is a known issue with power management on some hardware. If your WiFi connection drops after a few minutes, install the following module setting file to disable power management in your WiFi interface:

 sudo cp ./rtl8192cu-fixes/8192cu-disable-power-management.conf /etc/modprobe.d/ And then reboot."


As promised here is a nice WiFi monitor. Interestingly my other notebooks report -50 dBm (I assume semi-calibrated reference to 1 mW as dBm but perhaps dB is just a scale anyway - all dB are relative to something of course :)) The code steps seem to work on any machine I toss them to. However isn’t as yet the universe of things... The TP-Link WN821 reports -10 dB so I guess it isn't quite so deaf?


 [SIZE=3]**Install LinSSID Wireless Monitor**[/SIZE]
sudo add-apt-repository ppa:wseverin/ppa
sudo apt-get update; sudo apt-get install linssid

I suspect therefore that this 725 is just a lost cause.

---

### Post by carlo-anselmi2105 on 2017-02-22
Hello! I have a problem similar to the one of afz12. I'm happily using a very old ASUS EEPC  1001 HA with LUBUNTU 16.04. Now, after several years of honorable service, the Atheros Wireless on board of the ASUS, died. I tried using a Tplink wn725n because I know that it works properly on my desktop pc. But something weird happen: the first time I used it, it worked perfectly. Since that first and unique time, I wasn't able to use it anymore. The system doesn't recognize it anymore....
Can anyone help? Thanks and forgive my bad English
Carlo

---

### Post by jeremy31 on 2017-02-22
Hi carlo-anselmi2105
Please provide results for the following from terminal
```
lsusb; rfkill list all; dkms status
```

---

### Post by carlo-anselmi2105 on 2017-02-24
Hello Jeremy. Thank you for your help!

the output of the commands is the following:
```
---------------------------------------------------------------------------------------
lsusb
Bus 001 Device 004: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 002: ID 13d3:5108 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: 
	


dkms status
virtualbox, 5.0.24, 4.4.0-47-generic, i686: installed 
virtualbox, 5.0.24, 4.4.0-53-generic, i686: installed
virtualbox, 5.0.24, 4.4.0-57-generic, i686: installed

--------------------------------------------
```

---

### Post by wildmanne39 on 2017-02-24
Please do:
```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```
Reboot and wifi should work, but the Fn+F2 still won't work.

---

### Post by wildmanne39 on 2017-02-24
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by carlo-anselmi2105 on 2017-02-25
Hello Mildmanne39
I thank you for your help. Actually I tried the above command and rebooted, but apparently nothing has changed. Moreover I entered the previous commands:
```

lsusb; rfkill list all; dkms status

```
and I obtained the same result

---

### Post by jeremy31 on 2017-02-25
Go into the BIOS settings and see if wireless or WLAN is disabled there

---

### Post by carlo-anselmi2105 on 2017-02-26
jeremy31: YOU'R RIGHT!!!! the wireless was disabled in the BIOS and now it works again!! my old, beloved ASUS EEE PC 1001 HA is on duty again!! Thank you so much!!! 
BDW I suspect that the wireless went turned off when I tried plying around with Wireshark...

---

