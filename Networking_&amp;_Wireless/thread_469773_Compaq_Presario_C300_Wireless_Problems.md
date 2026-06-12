---
title: "Compaq Presario C300: Wireless Problems"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by timbenton on 2007-06-10
I have a C304NR with a BCM4326 802.11b/g adapter. I managed to get internet access with it for a few seconds using instructions from other topics, but I couldn't choose what access point to connect to. It just automatically connected to an unknown network and wouldn't let me connect to my own because of something to do with IPs. Does anyone know what I should do? I have all the ndiswrapper, bcm43xx-fwcutter and bcm-firmware packages. When I go to install the driver from dell.com or hp.com it says it's already installed, but then it doesn't work.

---

### Post by spd106 on 2007-06-12
First thing you need to do is clarify which driver you are using, sorry but you can't have both as they conflict. By default the bcm43xx driver will take control, unless you blacklist it in the /etc/modprobe.d/blacklist file. It is likely that this issue is preventing ndiswrapper from working even when it says it's installed.

If you run this command you will be able to see the driver in use. Might be useful to post the output here.
```
sudo lshw -class network
```

Also try this command to check that ndiswrapper-utils are installed properly.
```
ndiswrapper -v
```

If the driver is working then you should be able to see a wireless interface with this command.
```
iwconfig
```

and this command will show you a list of local networks to join.
```
sudo iwlist wlan0 scan
```

Good luck

---

### Post by timbenton on 2007-06-14
Step 01: Go to System -> Administration -> Synaptic Package Manager
Step 02: Search for and install cabextract and ndiswrapper-utils1
Step 03: Go to hp.com and find the driver secion for your model
Step 04: Save the Broadcom driver (sp34152.exe) to your desktop
Step 05: In Terminal type "cd /home/yourname/Desktop"
Step 06: Type "cabextract sp34152.exe"
Step 07: Type "sudo ndiswrapper -r bcmwl5"
Step 08: Type "sudo ndiswrapper -r bcm43xx"
Step 09: Type "sudo modprobe -r bcm43xx"
Step 10: Type "sudo ndiswrapper -i /home/yourname/Desktop/bcmwl5.inf"
Step 11: Type "sudo gedit /etc/modprobe.d/blacklist" and add the line "blacklist bcm43xx"
Step 12: Type "sudo ndiswrapper -m" into Terminal
Step 13: Type "sudo modprobe ndiswrapper"
Step 14: Type "sudo gedit /etc/modules" and add the line "ndiswrapper"
Step 15: Type "sudo dmesg" into Terminal
Step 15: Type "sudo gedit /var/run/wpa_supplicant.conf"
Step 16: Write this:

ctrl_interface=/var/run/wpa_supplicant

network={
    ssid="your SSID"
    psk="your password"
}

Step 17: Type "sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf -dd" into Terminal
Step 18: Type "sudo gedit /etc/network/interfaces"
Step 19: Delete everything in the file and write:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -ieth1 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

---

