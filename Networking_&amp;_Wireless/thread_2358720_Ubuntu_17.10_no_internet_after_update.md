---
title: "Ubuntu 17.10 no internet after update"
date: 2017-04-16
forum: Networking &amp; Wireless
---

### Post by lemonsix on 2017-04-16
I don't have wired nor wifi internet acces, when wired there is a text of "device not managed" and with wifi i can connect to the router and install aps from terminal, but i cant use any of the browsers.
I already tried a lot of things on other users posts but nothing works. I'm posting this from my cellphone

---

### Post by wildmanne39 on 2017-04-16
Do you mean 17.04?

---

### Post by lemonsix on 2017-04-16
Yes 17.04, my bad, also slack and dropbox panels are gray rectangles without anything after update, could it be some things just didn't install propperly?

---

### Post by wildmanne39 on 2017-04-16
*Thread moved to **Networking & Wireless**.*

The slack and dropbox issues could be.

Please post the output of by putting the output on a flash drive if you need to then using a computer with an internet connection:
```
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by lemonsix on 2017-04-16
```
lemonsix@lemonsix-KJ-15-6:~$ lspci -nnk | grep -iA2 net

01:00.0 
Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    
Subsystem: AzureWave RT3290 Wireless 802.11n 1T/1R PCIe [1a3b:2e87]
    
Kernel driver in use: rt2800pci
--
02:00.0 
Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    
Subsystem: Elitegroup Computer Systems RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1019:99eb]
    
Kernel driver in use: r8169
    
Kernel modules: r8169








lemonsix@lemonsix-KJ-15-6:~$ lsusb


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate MatchingHub


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Bus 001 Device 003: ID 04f2:b3af Chicony Electronics Co., Ltd 


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub










lemonsix@lemonsix-KJ-15-6:~$ iwconfig


wlp1s0f0  IEEE 802.11  ESSID:"asdasdasdasda"  
          
Mode:Managed  Frequency:2.412 GHz  Access Point: 78:CD:8E:D6:47:D5   
          
Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          
Retry short limit:7   RTS thr:off   
Fragment thr:off
          
Power Management:on
          
Link Quality=48/70  Signal level=-62 dBm  
         
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          
Tx excessive retries:36  Invalid misc:9   Missed beacon:0


lo        
no wireless extensions.


enp2s0    no wireless extensions.






lemonsix@lemonsix-KJ-15-6:~$ rfkill list all


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```

---

### Post by wildmanne39 on 2017-04-16
Please do:
```
echo "options rt2800pci  nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci

```
Then:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Then open the file with your text editor, if you need more directions just ask:
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0

```
Save and close file then reboot.

Unplug your wired connection.

---

### Post by lemonsix on 2017-04-16
So i did eveything but still no internet connection, is weird, i mean i can install aps from terminal but no internet on any of the browsers

---

### Post by wildmanne39 on 2017-04-16
Do what is at the following link:
[https://ubuntuforums.org/showthread.php?t=2358610](https://ubuntuforums.org/showthread.php?t=2358610)
post 9.
Thanks

---

### Post by lemonsix on 2017-04-16
so i set de DNS servers with automatic (DHCP) addresses only and with 8.8.8.8,8.8.4.4 and it works!
dude i'd love to get you some beer sometime xD
you're the best, thanks

---

### Post by wildmanne39 on 2017-04-16
Your welcome, I am glad it worked!
Enjoy!:)

---

### Post by vole-boy on 2017-04-19
I want to add my thanks - the workaround in that linked post #9 worked a treat for me too. You're a star! I lost internet (lan and wifi) to my router after the upgrade and was getting seriously annoyed. I found that I could wake the internet up using netstat -r and refreshing my browser, but had to do that every single time I booted up or restarted the network connection. As a favour, could you explain (using simple language for us computing idiots :-) ) what problem the solution solved? Thank you!

---

### Post by wildmanne39 on 2017-04-19
Network manager is having an issue getting the DNS server information in some cases in 17.04, and adding the google DNS servers is a work-around that allows you to still have internet, Usually the google DNS servers are faster then most ISP providers DNS servers anyway.

Your welcome and Enjoy.:)

---

### Post by vole-boy on 2017-04-22
Ah - thank you! That makes a lot of sense (and you're right - it's a lot faster...after some investigation I'm using the Open DNS option, and it works great)! :-)

---

### Post by fijired22 on 2017-11-07
Thank You for this fix - I'd been using 4.4.4.4 and the DNS error started after upgrading to 17.10. Changing to 8.8.4.4 fixed it.

Thanks again,
Joseph

---

