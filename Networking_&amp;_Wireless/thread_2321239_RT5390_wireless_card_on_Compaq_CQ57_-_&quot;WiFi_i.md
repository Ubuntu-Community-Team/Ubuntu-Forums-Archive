---
title: "RT5390 wireless card on Compaq CQ57 - &quot;WiFi is disabled by power switch&quot;"
date: 2016-04-21
forum: Networking &amp; Wireless
---

### Post by bomberb17 on 2016-04-21
Hello,  I have a presario cq57 with a Ralink RT5390 wireless card and i cant get it to work. I'm running Lubuntu 14.04 32bit. 
When I click on the connections icon, I get a greyed out message "WiFi is disabled by power switch".
I googled around for a solution, but all of the results are working on older ubuntus, but not after ubuntu 12.
I think that I have to somehow install another driver.
Here are some information that might help:
```
root@panos-Presario-CQ57-Notebook-PC:~# rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
root@panos-Presario-CQ57-Notebook-PC:~# lspci
.....
07:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
root@panos-Presario-CQ57-Notebook-PC:~# iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
lo        no wireless extensions.

eth0      no wireless extensions.
root@panos-Presario-CQ57-Notebook-PC:~# uname -r
4.2.0-35-generic



```

---

### Post by him610 on 2016-04-21
> Hard blocked: yes really does mean it has been turned off by a switch. You need to locate the switch then set it to ON.

---

### Post by bomberb17 on 2016-04-21
> **him610 said:**
> really does mean it has been turned off by a switch. You need to locate the switch then set it to ON.

Yes I know that. The switch is actually the F12 key. Nothing happens when I press it. (stays red=off). When I boot in Windows 10, it works fine though, when I press it it becomes white=on.

---

### Post by bomberb17 on 2016-04-22
Strange, I tried resetting to BIOS defaults and the WiFi light became white after reboot and it worked... Hope it stays that way..

---

