---
title: "Ralink RT5390 wifi issues on Focal 20.04"
date: 2020-08-12
forum: Networking &amp; Wireless
---

### Post by pemartins on 2020-08-12
I'm having wifi issues, often losing connection and/or the connection stops working after a while.

I've already made the procedures recommended a while ago here [https://ubuntuforums.org/showthread.php?t=2341569](https://ubuntuforums.org/showthread.php?t=2341569) for the same laptop, yet another Ubuntu version. It improved a lot but still it is not fine yet.

Here's the paste of the wireless-info report:
```
[https://pastebin.com/raw/uiK4Q9Ut](https://pastebin.com/raw/uiK4Q9Ut)
```

Is there something that can be done to improve it?

Thank you very much for any help in advance.

---

### Post by pemartins on 2020-08-23
I was able to solve my issues in the [Kubuntu forum]("https://www.kubuntuforums.net/showthread.php/77205-Ralink-RT5390-wifi-issues-on-focal-20-04?p=439947&viewfull=1#post439947"), will paste here all the tweaks in the hope that it will be useful to someone else.

1- Changed wifi router settings, moved to channel 9 and changed encryption to WPA2-AES with no WEP or TKIP.

2- Set wifi power save to off:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

3- Set my country code, which is PT:
```
sudo iw reg set PT
sudo sed -i 's/^REG.*=$/&PT/' /etc/default/crda
```

4- Set nohwcrypt to zero:
```
echo "options rt2800pci nohwcrypt=0" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```

5- Installed resolvconf, set cloudfare's dns to be used because is the  faster one for me, created a file named resolv_cloudfare.conf in etc  containing solely the cloudfare dns (this is not clever but it stops  network manager from overwriting resolv.conf) and linked the resolv.conf  file to it and (re)started the service:
```
sudo apt-get install resolvconf
echo "nameserver 1.1.1.1" | sudo tee -a /etc/resolvconf/resolv.conf.d/head > /dev/null
echo "nameserver 1.1.1.1" | sudo tee /etc/resolv_cloudfare.conf > /dev/null
sudo mv /etc/resolv.conf /etc/resolv.conf.bak
sudo ln -s /etc/resolv_cloudfare.conf /etc/resolv.conf
sudo systemctl restart resolvconf.service
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci

```

6- Stopped and disabled systemd-resolved:
```
sudo systemctl stop systemd-resolved
sudo systemctl disable systemd-resolved
```

7- Disabled ipv6:
```
sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1
```

8- Set IPv4 precedence over IPv6 by uncommenting #precedence ::ffff:0:0/96 100 in the file /etc/gai.conf

9- Since I use tlp, I made sure tlp was setting the wifi power save always to off by editing /etc/tlp.conf:
```
WIFI_PWR_ON_AC=off
WIFI_PWR_ON_BAT=off
```

10- On the wifi connection I applied these tweaks:
```
Wifi
Restricted to device (MAC address do modem)

IPv4
Method: Manual
DNS: 1.1.1.1,1.0.0.1
Address: 192.168.1.7
Netmask: 255.255.255.0
Gateway: 192.168.1.1

IPv6
Method: Ignored

```

11- I installed an application with gui for easily install/remove kernels named [Mainline]("https://code.launchpad.net/~cappelikan/+archive/ubuntu/ppa/") and installed the latest release of kernel 4.20. And applied the tweaks concerning the kernel again.

12- And, why not... I even discovered an amazing web browser called [Waterfox]("https://www.waterfox.net/")  and it is probably the fastest web browser around these days (it's  based on Firefox so all the addons are there). It is now my default  browser.

That was about it.

---

### Post by pemartins on 2020-08-26
Turns out the issue is not solved, even after all that stuff I did the  connection still loses ip randomly. It happens mostly while streaming or  downloading.

---

### Post by fggfshoko on 2021-04-09
Hello,

Did you managed to solve the issue?
In my case this seems to be happening every time i open the app Stremio...

---

