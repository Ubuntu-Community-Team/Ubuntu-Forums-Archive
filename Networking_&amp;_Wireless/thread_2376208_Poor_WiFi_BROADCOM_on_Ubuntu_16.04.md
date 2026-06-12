---
title: "Poor WiFi: BROADCOM on Ubuntu 16.04"
date: 2017-10-31
forum: Networking &amp; Wireless
---

### Post by cyberfox97 on 2017-10-31
Hello, 

I am using Ubuntu 16.04 LTS 64-bit and I am experiencing some network issues such as low Wi-Fi signal, low speed, no connection. Initially, my wireless device (BROADCOM BCM43142 rev 01) didn't have a driver installed so(no wireless connection) I installed bcmwl-kernel-source ( labeled as Broadcom 802.11 Linux STA driver ) from the control panel. I have done some research and found out that this driver happens to have some bugs/issues that cause me problems. 

I have run few commands and got the following output:

1. lspci:

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:04.0 Signal processing controller: Intel Corporation Haswell-ULT Thermal Subsystem (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.5 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 6 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 8 Series Thermal (rev 04)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
0d:00.0 Network controller: Broadcom Limited BCM43142 802.11b/g/n (rev 01)


2. iwconfig : 

wlp13s0 IEEE 802.11 ESSID:"AirLink14169C" 
Mode:Managed Frequency:2.437 GHz Access Point: 34:21:09:14:16:9C 
Retry short limit:7 RTS thr:off Fragment thr:off
Power Management:on
          
enp7s0 no wireless extensions.


lo no wireless extensions.



3. inxi -nz:

Network: Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
driver: r8169
IF: enp7s0 state: down mac: <filter>
Card-2: Broadcom Limited BCM43142 802.11b/g/n driver: wl
IF: wlp13s0 state: up mac: <filter>


Thanks!

PS: Something went really wrong when I named this thread. My apologizes....

---

### Post by vasa1 on 2017-10-31
I tried to improve the title.

Please read [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) carefully and provide the information requested in there.

---

### Post by cyberfox97 on 2017-10-31
> **vasa1 said:**
> I tried to improve the title.

Please read [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) carefull and provide the information requested in there.

Thank you. I have executed the script. 
[http://paste.ubuntu.com/25859081/](http://paste.ubuntu.com/25859081/)

Edit: I have a 300Mbps optic-fiber connection on the modem. I am using a Jensen AC5000AC v1 (300Mbps). I am only using the 2.4Ghz band on my laptop. I can confirm that the network works properly as my other devices work well.

---

### Post by Hadaka on 2017-10-31
Hi, from a working wired connection please Copy and Paste
one line at a time.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo iw reg set RO
sudo sed -i 's/=.*/=RO/' /etc/default/crda
```
*Remove wired connection and ANY usb unit..boot
and test wireless.
Thanks.

---

### Post by cyberfox97 on 2017-10-31
> **Hadaka said:**
> Hi, from a working wired connection please Copy and Paste
one line at a time.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo iw reg set RO
sudo sed -i 's/=.*/=RO/' /etc/default/crda
```
*Remove wired connection and ANY usb unit..boot
and test wireless.
Thanks.

I have executed all the commands. I can't tell if there is a difference..... I mean previously it behaved the same: wifi worked fine a while then it started to get worse. Only a reboot fixes it in my case. By the way, what's the meaning of the last 3 lines? 

Pastebin link to a newly generated report: [http://paste.ubuntu.com/25859746/](http://paste.ubuntu.com/25859746/)


EDIT: it failed again. I have checked the network in "Network details" and it displayed 5 MBps ... plus that the internet was not available..... so it is a failure...

---

### Post by praseodym on 2017-10-31
Deactivate SecureBoot in your UEFI/BIOS

---

### Post by Hadaka on 2017-10-31
The 3 commands used sed..sed is a commandline stream editor.
' man sed ' for full explanaton of sed.
Command Explanation.
*#iwconfig # Power Management was set to [COLOR=#ff0000]on[/COLOR]..This can create slow connect and disconnects.
*The following command turnes it off by chaning the wifi.powersave value from 3-[COLOR=#ff0000]on[/COLOR] to 2-[COLOR=#ff0000]off[/COLOR]
#Both commands do EXACTLY the same thing...the shorter command was posted.
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

*BEFORE..
##### iwconfig ##########################

wlp13s0   IEEE 802.11  ESSID:"AirLink14169C"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'AirLink14169C' [AC1]>   
          Retry short limit:7   RTS thr-off   Fragment thr-off
          Power Management:[COLOR=#ff0000]on[/COLOR]
*AFTER..
##### iwconfig ##########################

wlp13s0   IEEE 802.11  ESSID:"AirLink14169C"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'AirLink14169C' [AC1]>   
          Retry short limit:7   RTS thr off   Fragment thr off
          Power Management:[COLOR=#ff0000]off[/COLOR]

*# iw reg get # The Region Country code was unset -> [COLOR=#ff0000]00[/COLOR] , the correct country code
* per [https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) for Region: Europe/Bucharest is [COLOR=#ff0000]RO[/COLOR]
*These 2 commands correctly set the country code
```
sudo iw reg set RO
sudo sed -i 's/=.*/=RO/' /etc/default/crda
```

*BEFORE..
##### iw reg get ########################

 (based on set time zone)

country [COLOR=#ff0000]00[/COLOR]: DFS-UNSET


*AFTER..
##### iw reg get ########################

Region: Europe/Bucharest (based on set time zone)

country [COLOR=#ff0000]RO[/COLOR]: DFS-ETSI

---

### Post by cyberfox97 on 2017-11-01
> **Hadaka said:**
> The 3 commands used sed..sed is a commandline stream editor.
' man sed ' for full explanaton of sed.
Command Explanation.
*#iwconfig # Power Management was set to [COLOR=#ff0000]on[/COLOR]..This can create slow connect and disconnects.
*The following command turnes it off by chaning the wifi.powersave value from 3-[COLOR=#ff0000]on[/COLOR] to 2-[COLOR=#ff0000]off[/COLOR]
#Both commands do EXACTLY the same thing...the shorter command was posted.
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

*BEFORE..
##### iwconfig ##########################

wlp13s0 IEEE 802.11 ESSID:"AirLink14169C" 
Mode:Managed Frequency:2.437 GHz Access Point: <MAC 'AirLink14169C' [AC1]> 
Retry short limit:7 RTS thr-off Fragment thr-off
Power Management:[COLOR=#ff0000]on[/COLOR]
*AFTER..
##### iwconfig ##########################

wlp13s0 IEEE 802.11 ESSID:"AirLink14169C" 
Mode:Managed Frequency:2.437 GHz Access Point: <MAC 'AirLink14169C' [AC1]> 
Retry short limit:7 RTS thr off Fragment thr off
Power Management:[COLOR=#ff0000]off[/COLOR]

*# iw reg get # The Region Country code was unset -> [COLOR=#ff0000]00[/COLOR] , the correct country code
* per [https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) for Region: Europe/Bucharest is [COLOR=#ff0000]RO[/COLOR]
*These 2 commands correctly set the country code
```
sudo iw reg set RO
sudo sed -i 's/=.*/=RO/' /etc/default/crda
```

*BEFORE..
##### iw reg get ########################

(based on set time zone)

country [COLOR=#ff0000]00[/COLOR]: DFS-UNSET


*AFTER..
##### iw reg get ########################

Region: Europe/Bucharest (based on set time zone)

country [COLOR=#ff0000]RO[/COLOR]: DFS-ETSI



Thanks for the explanations. I still don't understand why the time-zone was not correctly set and the region code. Shouldn't those things be set by linux during installation phase?


[[COLOR=#000000]praseodym[/COLOR]]("https://ubuntuforums.org/member.php?u=1411497")[COLOR=#000000] :[/COLOR]Secure Boot has been disabled long before I have installed Ubuntu. Still getting drops in speeds from 72 to 5 or even lower. I should mention that there are a bunch of wifi networks in my neighborhood. I notice a wifi speed/signal strength drop on my other devices, but only for few seconds. (just like lag) Everything goes back to normal afterward. 

Thanks!

---

### Post by Hadaka on 2017-11-01
Hi, the last wireless diagnostic report on the pastebin had an error message in the dmesg section.

```
# wl: module verification failed: signature and/or required key missing - tainting kernel
```

This error message is a very strong indication that secure boot is enabled or that you need to set it to legacy
mode. Please verify the secure boot is disabled as praseodym suggests.
Thanks.

---

### Post by cyberfox97 on 2017-11-01
> **Hadaka said:**
> Hi, the last wireless diagnostic report on the pastebin had an error message in the dmesg section.

```
# wl: module verification failed: signature and/or required key missing - tainting kernel
```

This error message is a very strong indication that secure boot is enabled or that you need to set it to legacy
mode. Please verify the secure boot is disabled as praseodym suggests.
Thanks.

[ATTACH=CONFIG]277371[/ATTACH]

Secure boot is disabled. Does it have anything to do with linux being installed in UEFI mode?

---

### Post by Hadaka on 2017-11-01
I am not 100% sure but would suspect yes the UEFI mode is very iikely
the cause of the error message. Perhaps someone with more UEFI knowldge
than i, can verify. Try turning it off and see what happens.
Thanks.

---

### Post by cyberfox97 on 2017-11-01
> **Hadaka said:**
> I am not 100% sure but would suspect yes the UEFI mode is very iikely
the cause of the error message. Perhaps someone with more UEFI knowldge
than i, can verify. Try turning it off and see what happens.
Thanks.

Can you be more specific, please? When I have installed Ubuntu, the setup warned me that I am installing in the UEFI mode and that other OSes may fail to boot if I proceed. ( I didn't care because Ubuntu is my only OS on my laptop) How can I run it  "outside" UEFI ? If that might work, it's worth a shot. My greatest fear is that I would have to reinstall everything, and that wouldn't be nice.

---

### Post by Hadaka on 2017-11-01
Hi, since it is not working correctly anyway..would it really matter ?
From the 'warning' statement you described and the error message
the odds are that it is the UEFI creating your problem. To verify..boot
up to the media you used to install and instead of..install...go with the
"Try Me" mode and see if you can correctly connect. You should also know that
the Broadcom wl driver will likely NOT work in the 5Ghz. mode..only 2.4 with the
later loads of Ubuntu. Try the "Try Ubuntu" mode and report back please.
Thanks.

---

### Post by cyberfox97 on 2017-11-01
> **Hadaka said:**
> Hi, since it is not working correctly anyway..would it really matter ?
From the 'warning' statement you described and the error message
the odds are that it is the UEFI creating your problem. To verify..boot
up to the media you used to install and instead of..install...go with the
"Try Me" mode and see if you can correctly connect. You should also know that
the Broadcom wl driver will likely NOT work in the 5Ghz. mode..only 2.4 with the
later loads of Ubuntu. Try the "Try Ubuntu" mode and report back please.
Thanks.

I have tried that before installing. It connected, then crashed with some error. I had to reboot, then installed without the network. So no, It didn't work....

---

### Post by Hadaka on 2017-11-01
Hi, ok...i dont know when "before" was or if you had the 2 other errors 
that were corrected..pwr/mgmt. off...country code set RO.  I am out of
ideas and have nothing else to suggest. 
Good luck to you

---

### Post by cyberfox97 on 2017-11-01
> **Hadaka said:**
> Hi, ok...i dont know when "before" was or if you had the 2 other errors 
that were corrected..pwr/mgmt. off...country code set RO. I am out of
ideas and have nothing else to suggest. 
Good luck to you

Thank you very much for your time and your support. Would it help if I would reinstall Ubuntu in legacy (BIOS) mode? Would it be better switching to 17.10 ?

---

### Post by cyberfox97 on 2017-11-02
Hello, 

I have just installed a fresh copy of Ubuntu 17.10, in BIOS mode. (no more UEFI) The problem persists. The pastebin link from wireless script is : [http://paste.ubuntu.com/25875688/](http://paste.ubuntu.com/25875688/)

EDIT: I am getting a question mark instead of the wireless signal indicator. (same driver as on 16.04)

---

