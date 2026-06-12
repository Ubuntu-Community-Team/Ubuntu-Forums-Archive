---
title: "Ralink RT3290 no wireless networks available on Kubuntu 16.04 (.3)"
date: 2017-12-19
forum: Networking &amp; Wireless
---

### Post by tripatos on 2017-12-19
[FONT=century gothic][SIZE=2]Hello Everyone,
[/SIZE][/FONT][FONT=century gothic]I have installed Kubuntu 16.04 on a HP Probook 455 G1 with Ralink corp. RT3290 wireless chipset. 
At the beginning (during live installation) I could connect to wireless networks and even at logging on for the first time. 
However after running a system update I can no longer see wireless network connections.
I uploaded my report here: [https://paste.ubuntu.com/26216487/](https://paste.ubuntu.com/26216487/)

Any advise would be much appreciated. :)
Thanks a lot, Balázs
[/FONT]

---

### Post by praseodym on 2017-12-19
```
wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]0 dBm[/COLOR]   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```
The card is turned off. Any button, switch, key or key combo? BIOS settings?!

---

### Post by tripatos on 2017-12-21
There is a dedicated key on the laptop to turn on wifi (though the button is always lit in kubuntu as if wifi was turned on). When I push that button I can see in the networks menu that wifi gets enabled/disabled. However I cannot see wireless networks in any case. Sometimes (not always) when I turn on computer with wired connection and remove the cable the laptop connects to wireless. As wireless works from time to time I guess it is not related to BIOS but happy to check anything if you have an idea.

---

### Post by praseodym on 2017-12-21
Wired is always preferred! Please run the script again without cable

---

### Post by tripatos on 2017-12-21
I just re-ran without cable as requested. Trying to attach it here, thanks!

---

### Post by jeremy31 on 2017-12-21
I would try disabling network manager's ability to enable wifi power management
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot and see if the wifi works correctly

---

### Post by tripatos on 2017-12-21
Thanks for the tip, I tried entering the command and restart but no joy :( (by the way, after entering the command I did not see any confirmation that anything updated/saved so I tried it 2 more times to be sure)

---

### Post by tripatos on 2017-12-22
So just to confirm, content of /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf is the following at the moment (still no wireless networks shown after reboot):
[connection]
wifi.powersave = 2

---

### Post by praseodym on 2017-12-22
Try

```
echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt29800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
dmesg | egrep 'rt2|802'
iwconfig
```

---

