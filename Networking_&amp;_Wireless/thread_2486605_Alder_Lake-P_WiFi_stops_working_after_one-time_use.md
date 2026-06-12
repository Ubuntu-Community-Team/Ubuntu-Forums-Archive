---
title: "Alder Lake-P WiFi stops working after one-time use of LAN on 22.04"
date: 2023-05-05
forum: Networking &amp; Wireless
---

### Post by xberg on 2023-05-05
Hello, 
I am stuck in a problem with my Wi-Fi network adapter on a new Dell Latitude Notebook 5531 Notebook. I installed Ubuntu Budgie 22.04.2lts and used it for three days without problems. It connected with WPA2 Wi-Fi at home and via EduRoam at the University. Yesterday, I had to connect the Notebook via LAN and a dedicated IP Address in order to get connected with a network printer at work. I deselected Wi-Fi in the control panel to check, if I also get into Internet via LAN and continued working. When I disconnected the LAN and tried to re-enable Wi-Fi I noted, that I can not change the software switch in the panel anymore. When I look into the Network-Settings panel, I get the message: "No Wi-Fi adapter found (Kein Netzwerkadapter gefunden)". 
Re-booting the computer did not help either. I looked in the BIOS settings, but there seems everything ok: WLAN is enabled and the "Wireless radio control" that switch off WLAN when LAN is connected is disabled. The only thing might be the selection for "WWAN GPS Bus mode". It is set to "Bus node PCIe". The other option is "Bus mode USB. The information text states, that PCIe is recommended for MS Windows and for other OS USB. But since I did not change the BIOS setting and WLAN worked before, I did not want to try changing this parameter without previous advice.
I tried 
```

rfkill unblock all

```
Which set the Wi-Fi control panel switch again to enabled, but without showing any Wi-Fi to connect. and in the Network settings panel there still is the message, that no wireless network adapter was found.
I looked for the network driver:
```

lspci -knn | grep Net -A3
0000:00:14.3 Network controller [0280]: Intel Corporation Alder Lake-P PCH CNVi WiFi [8086:51f0] (rev 01)
    Subsystem: Intel Corporation Device [8086:4090]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```
and then into the drivers settings:
```

nano /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```
"remove iwlwifi" does not sound got to me, but I do not know how the driver works and I do not want to change anything I do not fully understand without advice.

So I finally ask here for help. I have run the script recomended in the sticky post and put it in a paste bin: [https://pastebin.com/rRRTQuLf](https://pastebin.com/rRRTQuLf)

Thanks for any advice how to proceed and enable WLAN again.

---

### Post by xberg on 2023-05-09
I have tested to start my Dell Latitude 5130 from the Ubuntu Budgie 22.04.2 usb stick I installed my system from as live-system. It runs well and connects to WiFi without problem. I can plug in the LAN and when I unplug it, Wifi works fine.  I did run the same info-script as with the installed system. I looked at it with a diff viewer in the hope I can find some different setting that points to the problem. From what I can see, the main difference is, that the live-system runs with kernel Linux 5.19.0-32-generic and the installation on the notebook had an update to Linux 5.19.0-41-generic. I remember that I run updates shortly after the installation and as I stated in my first post Wifi worked after that fine. It stoped working imeadiatly after I first connected the notebook with LAN and a static IP. Unplugging the LAN I could not turn back to Wifi.      I post here the output of the wifi-info script from the working live-system:    [https://pastebin.com/b84CQi4u](https://pastebin.com/b84CQi4u)      Now I am realy stucked and do not know how to proceed. Maybe this is connected to the thread [https://ubuntuforums.org/showthread.php?t=2486691](https://ubuntuforums.org/showthread.php?t=2486691) since it is also a Dell Latitude? Although on my system Ubuntu Budgie 22.04.2 did work.

---

### Post by jeremy31 on 2023-05-09
On the install, in terminal do ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot and see if it works properly with wifi power management disabled

---

### Post by xberg on 2023-05-10
HI Jeremy,

thank you for the advice. It worked! On my first try it did not work after reboot, but when I tried it a second time it worked. Maybe I misspelled the first time something, the second time I used c&p :) 

If I understand this right, I have no Wi-Fi power management with that trick. What does that mean? Wi-Fi always on, consuming energy unless I deactivate it manually? I think I can live with that, although a Notebook that was sold with Ubuntu pre-installed should work properly without those tweaks.

All the best,
olaf

---

### Post by jeremy31 on 2023-05-13
If you want to enable wifi power management just do ```
sudo iwconfig wlp0s20f3 power on
```
To disable again do ```
sudo iwconfig wlp0s20f3 power off
```

---

