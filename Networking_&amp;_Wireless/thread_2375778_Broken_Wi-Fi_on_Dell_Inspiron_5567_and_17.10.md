---
title: "Broken Wi-Fi on Dell Inspiron 5567 and 17.10"
date: 2017-10-27
forum: Networking &amp; Wireless
---

### Post by Pitel on 2017-10-27
I've brand new latop and freshly installed Ubuntu. But I can't change wifi networks. Whenver I try to "touch" (change network, disable) the wifi after boot, it gets stuck.

It also happened in installer. I wanted to connect to my 2 home networks, but after successfully connecting to the first one, attempt to connect to second resulted in frozen and unresponsive installer.

After I try to do something with wifi, even ip addr gets stuck.

I also can't get into gnome settings, probably because wifi is the first section.

Also, shutdown gets stuck on Network Manager, WPA supplicant and Raise network interfaces tasks.

The adapter is Atheros QCA9377 (rev 31)

(Copied from [https://askubuntu.com/q/969461](https://askubuntu.com/q/969461))

---

### Post by praseodym on 2017-10-27
Please run the wireles script from the sticky thread and show the outputs here

---

### Post by Pitel on 2017-10-27
[https://paste.ubuntu.com/25832501/](https://paste.ubuntu.com/25832501/)

Also, the wifi internet connection dies after a while. apt update passed, apt upgrade not, everything times out.

---

### Post by praseodym on 2017-10-27
Try disabling the power management:
```

sudo iwconfig wlp2s0 power off
```
Maybe the network manager bug from 17.04 is still present?

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```
Firmware update?

```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Reboot

---

### Post by Pitel on 2017-10-28
None of it helped. :(

---

### Post by jeremy31 on 2017-10-28
Post results for
```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf; iwconfig
```

---

### Post by Pitel on 2017-10-28
```

wlp2s0    IEEE 802.11  ESSID:"R5D5"  
          Mode:Managed  Frequency:5.3 GHz  Access Point: <MAC 'R5D5' [AN1]>   
          Bit Rate=6 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:69  Invalid misc:58   Missed beacon:0

```

```

[connection]
wifi.powersave = 2 //was 3, before changing it in previous post

```

I also reverted to original firmware directory, because I was now in airplane mode after each boot.

EDIT: Sorry, the iuwconfig's power management now says off. But the problem are still not fixed anyway.

---

### Post by jeremy31 on 2017-10-28
And you did reboot since making the changes as power management is still on?

---

### Post by Pitel on 2017-10-28
Yes, sorry, I pasted wrong text. The power management is now ooff in iwconfig's output. But the problems still persist: can't change network, can't reboot cleanly.

---

### Post by boski-cinek on 2017-10-28
Try remco wouts solution shown in post #6 of bug report [URL="https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/1725690"]https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/1725690
[/URL]

---

### Post by Pitel on 2017-10-29
Installing kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13.10/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.13.10/) fixed the issue for me!

---

