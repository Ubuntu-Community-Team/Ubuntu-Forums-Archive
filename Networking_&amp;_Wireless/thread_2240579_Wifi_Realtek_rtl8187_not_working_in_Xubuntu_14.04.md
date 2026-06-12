---
title: "Wifi Realtek rtl8187 not working in Xubuntu 14.04"
date: 2014-08-20
forum: Networking &amp; Wireless
---

### Post by jacortijo on 2014-08-20
Hi,
I just install xubuntu 14.04 and the wifi seems not to be detected.
When I click in the network indicator icon on the upper right side, "Enable Wifi" appears grey out, I cannot enable it.

From a terminal, I run the following commands 
```
olga@OlgaX:~$ sudo modprobe rtl8187
olga@OlgaX:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
olga@OlgaX:~$ sudo nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             unavailable
  Default:           no
  HW Address:        00:1B:9E:FF:BE:D8

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```

I dont know what else to do, it seems like detected but doesnt work...

I am quite newbie... sorry for the simple question. I search in google and no luck so far.

thanks a lot in advance.
Jose

---

### Post by varunendra on 2014-08-25
Hi Jose,

Some system BIOS are programmed to automatically disable the wirless interface if a wired connection is detected (to save battery power). So make sure the ethernet cable is disconnected, then try enabling the wireless (using your wifi on/off toggle switch or key combo, even a reboot if required). If it remains disabled, please try -
```
sudo iwconfig wlan0 power off
sudo rfkill unblock all
sudo ifconfig wlan0 up
```
Can you use the wireless now? If not, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by jacortijo on 2014-08-26
Thanks a lot for the reply.
indeed, it was a matter of switch a toogle in order to enable the wifi. only that, the drivers were already installed and it worked inmediately.

thanks a lot once more.

Jose

---

### Post by varunendra on 2014-08-26
Happy to help. :)
> **jacortijo said:**
> indeed, it was a matter of switch a toogle in order to enable the wifi.

I remember that day when I opened my computer's case, pulled out the RAM, cleaned it, disconnected/reconnected drives, even pulled out all but essential internal cables to pin-point the problem.... only to realize later that the only thing I needed to check was the mains power cable plug, that was somehow pulled out of its socket :lolflag:

---

