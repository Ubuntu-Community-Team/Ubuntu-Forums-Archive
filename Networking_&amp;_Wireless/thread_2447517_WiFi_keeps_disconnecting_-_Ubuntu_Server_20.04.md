---
title: "WiFi keeps disconnecting - Ubuntu Server 20.04"
date: 2020-07-20
forum: Networking &amp; Wireless
---

### Post by zogthegreat on 2020-07-20
Hi everyone!

I'm building a NextCloud server on an old laptop for my daughter, (you would be amazed how many pictures and videos a 14 year old can take!), and I'm having problems with the WiFi. Here are the steps that I'm taking to get the WiFI working:

sudo apt install wireless-tools wpasupplicant -y
wpa_passphrase XXXXXXX XXXXXXXX | sudo tee /etc/wpa_supplicant.conf
sudo wpa_supplicant -B -c /etc/wpa_supplicant.conf -i wlp1s0
sudo dhclient wlp1s0
ip addr show wlp1s0
sudo cp /lib/systemd/system/wpa_supplicant.service /etc/systemd/system/wpa_supplicant.service
sudo nano /etc/systemd/system/wpa_supplicant.service

I comment out "#ExecStart=/sbin/wpa_supplicant -u -s -O /run/wpa_supplicant" and Alias=dbus-fi.w1.wpa_supplicant1.service and I replace it with:

ExecStart=/sbin/wpa_supplicant -u -s -c /etc/wpa_supplicant.conf -i wlp1s0

sudo systemctl enable wpa_supplicant.service

sudo nano /etc/systemd/system/dhclient.service

///////

[Unit]
Description= DHCP Client
Before=network.target
After=wpa_supplicant.service

[Service]
Type=simple
ExecStart=/sbin/dhclient wlp1s0 -v
ExecStop=/sbin/dhclient wlp1s0 -r
 
[Install]
WantedBy=multi-user.target

///////

sudo systemctl enable dhclient.service

sudo nano /etc/dhcp/dhclient.conf

///////

interface "wlp1s0" {
     send dhcp-requested-address 192.168.XX.XX;
}

///////

sudo systemctl restart dhclient

sudo nano /etc/netplan/00-installer-config.yaml

///////

network:
   ethernets:
      enp2s0:
         dhcp4: true
   version: 2
   wifis:
     wlp1s0:
     addresses: [192.168.XX.XX/24]
     gateway4: 192.168.XX.XX
     nameservers:
         addresses: [192.168.XX.XXX, 8.8.4.4, 8.8.8.8]
     access-points:
        XXXXXXXXXX:
             password: XXXXXXXXXX
     dhcp4: false

///////

(The forums system keeps removing the indentations for the .yaml, but the configuration that I have is a properly configured .yaml)

sudo netplan --debug generate 
sudo netplan apply 
sudo reboot

After I reboot, I can connect to the WiFi connection via ssh, however, the NIC keeps dropping the connection. At first I thought that maybe I had a bad NIC, but I have tried Broadcom, Atheros and Intel NIC's with the same results.

Does anyone have any suggestions on what the problem is?

Thanks!

zog

---

