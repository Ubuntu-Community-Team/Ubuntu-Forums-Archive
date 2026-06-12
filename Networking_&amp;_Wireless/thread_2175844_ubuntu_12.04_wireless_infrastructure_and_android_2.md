---
title: "ubuntu 12.04 wireless infrastructure and android 2.3.5 ufw needs to be disabled"
date: 2013-09-21
forum: Networking &amp; Wireless
---

### Post by davidvandoren on 2013-09-21
Hi there!
I've got the following problem .
I successfully set up a wireless internet share through my Ubuntu 12.04 pc. 
However, I can only connect to the internet with my android phone when the ufw firewall is disabled.
I tried opening port 53, 80, 433 but nothing works. either the firewall is off or I can't go to the internet with the phone. 

Here is how I set up the wireless on Ubuntu.

```
sudo apt-get install hostapd dnsmasq
sudo service hostapd stop

sudo service dnsmasq stop
sudo update-rc.d hostapd disable
sudo update-rc.d dnsmasq disable


```


then
```
gksudo gedit /etc/dnsmasq.conf
```

insert the following
```
# Bind to only one interface
bind-interfaces
# Choose interface for binding
interface=wlan0
# Specify range of IP addresses for DHCP leasses
dhcp-range=192.168.150.2,192.168.150.10
```
save and close the window


then 
```
gksudo gedit /etc/hostapd.conf
```
add the following lines
```
# Define interface
interface=wlan0
# Select driver
driver=nl80211
# Set access point name
ssid=myname
# Set access point harware mode to 802.11g
hw_mode=g
# Set WIFI channel (can be easily changed)
channel=6
# Enable WPA2 only (1 for WPA, 2 for WPA2, 3 for WPA + WPA2)
wpa=2
wpa_passphrase=apassword


```
Save and close the window

After that

create a a sh file with the following content
```
#!/bin/bash
# Start
# Configure IP address for WLAN
sudo ifconfig wlan0 192.168.150.1
# Start DHCP/DNS server
sudo service dnsmasq restart
# Enable routing
sudo sysctl net.ipv4.ip_forward=1
# Enable NAT
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
# Run access point daemon
sudo hostapd /etc/hostapd.conf
# Stop
# Disable NAT
sudo iptables -D POSTROUTING -t nat -o eth0 -j MASQUERADE
# Disable routing
sudo sysctl net.ipv4.ip_forward=0
# Disable DHCP/DNS server
sudo service dnsmasq stop
sudo service hostapd stop
```
Save as start.sh in the home directory


Then
```
sudo sh start.sh
```
I got an error port 53  and the ip localhost already in use

New try with
```
gksudo gedit /etc/NetworkManager/NetworkManager.conf
```
and change dns=dnsmasq to #dns=dnsmasq
so it looks like this 
```
#dns=dnsmasq
```
only changed that line
Save and close


then
```
gksudo gedit /etc/sysctl.conf
```
Added the following line at the bottom 
```
net.ipv4.ip_forward=1
```

save and close then restarted the system 

```
sudo ufw diable
```

finally 
```
sudo sh start.sh
```

Android 2.3.5 can surf the internet 

However I need my firewall

What to do?
Any ideas?

Thanks!

---

