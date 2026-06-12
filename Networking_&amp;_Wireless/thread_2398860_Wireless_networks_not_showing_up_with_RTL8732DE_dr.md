---
title: "Wireless networks not showing up with RTL8732DE drivers"
date: 2018-08-18
forum: Networking &amp; Wireless
---

### Post by rembranded on 2018-08-18
Hi, I have a HP Laptop (Model: HP 15q-BU010TU) that I purchased recently and it came with FreeDOS. I proceeded to install the latest Ubuntu off a USB stick and the installation went just fine. I was connected via a wired ethernet connection at the time. Post installation, I was able to go about my work when I realised that the Wi-Fi wasn't working. I did some searching online and installed the latest version of the rtl8732de drivers from Larry W. Fingers github. Now my system is able to detect that I have wireless capability, but when I click on 'Search for networks' it's spinning forever and none of the network SSIDs appear. I've checked my network setup also and my SSID is hidden and another laptop is able to connect to the same SSID, so it isn't a network issue. Can anyone please help?

I've provided some details below to hopefully help with analysis:
[LIST=1]
[*]I've installed all rtlwifi_new so that should be the newest driver 
[*]I've also tried downloading the wireless script that's available in this forum's sticky, but haven't had any luck in getting this to run as it says 'Unable to resolve github.com' which is weird as I'm able to open it on my browser just fine 
[*]I've run dmesg also and below is the output 
[/LIST]

[COLOR=#8AE234]**shanker@shanks**[/COLOR]:[COLOR=#729FCF]**~**[/COLOR]$ dmesg | grep rtl
[   19.838745] [COLOR=#EF2929]**rtl**[/COLOR]wifi: loading out-of-tree module taints kernel.
[   19.838819] [COLOR=#EF2929]**rtl**[/COLOR]wifi: module verification failed: signature and/or required key missing - tainting kernel
[   19.937781] Bluetooth: hci0: [COLOR=#EF2929]**rtl**[/COLOR]: examining hci_ver=08 hci_rev=826c lmp_ver=08 lmp_subver=8873
[   19.937783] Bluetooth: hci0: [COLOR=#EF2929]**rtl**[/COLOR]: assuming no firmware upload needed
[   20.159943] [COLOR=#EF2929]**rtl**[/COLOR]8723de: Using firmware [COLOR=#EF2929]**rtl**[/COLOR]wifi/[COLOR=#EF2929]**rtl**[/COLOR]8723defw.bin
[   20.251438] ieee80211 phy0: Selected rate control algorithm '[COLOR=#EF2929]**rtl**[/COLOR]_rc'
[   20.251756] [COLOR=#EF2929]**rtl**[/COLOR]wifi: [COLOR=#EF2929]**rtl**[/COLOR]wifi: wireless switch is on
[   20.253464] [COLOR=#EF2929]**rtl**[/COLOR]8723de 0000:02:00.0 wlo1: renamed from wlan0

---

### Post by jeremy31 on 2018-08-18
Try changing antenna setting
```
sudo modprobe -r rtl8723de && sleep 10 && sudo modprobe rtl8723de ant_sel=2
```
If you can find wifi access points do
```
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```

---

### Post by rembranded on 2018-08-18
Jeremy, you are a lifesaver. I've been struggling with this for 1 month and the first command you gave me solved it. Thank you so much!

---

### Post by jeremy31 on 2018-08-18
Run the second command so you don't have to run the first command after every reboot

---

