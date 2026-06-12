---
title: "Managing Wireless without Network Manager"
date: 2016-09-05
forum: Networking &amp; Wireless
---

### Post by vman76nj on 2016-09-05
Verison: Ubuntu version 16.04

I have a Rosewill RNX-N600ube usb wireless card that I would like to manage without Network Manager. It works fine with Network Manager but I would like to manage this card through the command line directly through Ubuntu. The device is recognized by the OS but for some reason it doesn't show up in /etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

But does show up in ifconfig and iwconfig  (see below). I can "ifconfig up/down" the device. However when I add it to the interfaces files, i can't restart the networking service and get errors that it can't be found



```
wlx681ca2027102 Link encap:Ethernet  HWaddr 68:1c:a2:02:71:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlx681ca2027102  IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:offSep 05 13:22:25 basebuntu ifup[10801]: Unknown interface wlx681ca2027102
Sep 05 13:22:25 basebuntu systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Sep 05 13:22:25 basebuntu systemd[1]: Failed to start Raise network interfaces.
Sep 05 13:22:25 basebuntu systemd[1]: networking.service: Unit entered failed state.
Sep 05 13:22:25 basebuntu systemd[1]: networking.service: Failed with result 'exit-code'.

          Power Management:on
          

/etc/network/interfaces after I manually add the devices:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# Wifi Interface
auto wlx681ca2027102 

The error is:
sudo service networking start
Job for networking.service failed because the control process exited with error code. See "systemctl status networking.service" and "journalctl -xe" for details.

Sep 05 13:22:25 basebuntu ifup[10801]: Unknown interface wlx681ca2027102
Sep 05 13:22:25 basebuntu systemd[1]: networking.service: Main process exited, code=exited, status=1/FAILURE
Sep 05 13:22:25 basebuntu systemd[1]: Failed to start Raise network interfaces.
Sep 05 13:22:25 basebuntu systemd[1]: networking.service: Unit entered failed state.
Sep 05 13:22:25 basebuntu systemd[1]: networking.service: Failed with result 'exit-code'.

```
I'm probably missing something simple but it's been a while since I've configured network interfaces manually in Linux and even then it was mostly Centos.

---

### Post by vman76nj on 2016-09-05
I'll add that I stopped the NetworkManager service as well.

---

### Post by chili555 on 2016-09-05
> /etc/network/interfaces after I manually add the devices:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# Wifi Interface
auto wlx681ca2027102 I suggest you add a few things here:```
/etc/network/interfaces after I manually add the devices:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
iface eth0 inet dhcp

# Wifi Interface
auto wlx681ca2027102
iface  wlx681ca2027102 inet dhcp
wpa-ssid <your_network>
wpa-psk <your_secret_key>
```Restart the interface:```
sudo ifdown wlx681ca2027102 && sudo ifup -v wlx681ca2027102
```Did you connect?```
ping -c3 www.ubuntu.com
```

---

### Post by wildmanne39 on 2016-09-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

