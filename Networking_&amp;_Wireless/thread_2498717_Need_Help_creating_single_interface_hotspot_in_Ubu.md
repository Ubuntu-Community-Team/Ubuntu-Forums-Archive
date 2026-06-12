---
title: "Need Help creating single interface hotspot in Ubuntu 24.04"
date: 2024-06-25
forum: Networking &amp; Wireless
---

### Post by sr4uc132vg3hy0c8x2yl on 2024-06-25
Have been trying it for a while in 22.04, with no success. im using an external alfawus036acm adapter and tried the create_ap method or creating custom hostapd files with the chatbot. create_ap at least maked the ap visible, but one couldnt connect to it, now on a pretty fresh installation it does nothing.

```
sudo create_ap wlan1 wlan1 x Passphrase                                      
Config dir: /tmp/create_ap.wlan1.conf.5RUm7eF8
PID: 20830
cp: warning: behavior of -n is non-portable and may change in future; use --update=none instead
cp: warning: behavior of -n is non-portable and may change in future; use --update=none instead
Network Manager found, set ap0 as unmanaged device... DONE
Creating a virtual WiFi interface... ap0 created.

ERROR: Your adapter can not transmit to channel 1, frequency band 2.4GHz.


Doing cleanup.. done


```

As i dont understand much from what is going on or failing, while beeing optimistic that the adapter should be capable doing this im finaly asking online. If you need more information, just let me now, ill provide it as quick as possible. Would be happy if i could finaly manage this longlasting frustration.

In anyway have a nice day and thanks in advance

---

### Post by jeremy31 on 2024-06-25
Moved to Networking and Wireless
See the wireless script link in my signature and post results

---

### Post by currentshaft on 2024-06-25
We aren't in front of your computer and don't know what "create_ap" is nor who is "the chatbot". Please explain things clearly and don't make us guess.

To act an a hotspot, you need three things:
1. A capable network interface
2. IP forwarding enabled
3. A service to provide DHCP and DNS

From the output you have shared, you've failed at step 1: "ERROR: Your adapter can not transmit to channel 1, frequency band 2.4GHz."

So, what type of card is it and why is it incompatible? (Try the "lshw" command for clues)

---

### Post by sr4uc132vg3hy0c8x2yl on 2024-06-26
coulndt paste the file, output of wireless-info.txt is now on [https://paste.ubuntu.com/p/2cPP5HT8MJ/](https://paste.ubuntu.com/p/2cPP5HT8MJ/)

---

### Post by sr4uc132vg3hy0c8x2yl on 2024-06-26
Network interface/card info should be visible now on the pastebin i provided, forwarding is enabled, dns service should be systemd. Create_ap from [https://github.com/oblique/create_ap](https://github.com/oblique/create_ap) was submitted as a possible solution in similiar problems and chatbot is chatgpt, which for me wasnt helpful either.

---

### Post by jeremy31 on 2024-06-26
May want to try [https://github.com/lakinduakash/linux-wifi-hotspot](https://github.com/lakinduakash/linux-wifi-hotspot)

---

### Post by sr4uc132vg3hy0c8x2yl on 2024-06-26
remember trying this one on 22.04 then. first run now gave: 
```

pkexec --user root create_ap wlan1 wlan1 'MyAccessPoint' '12345678' --mkconfig /etc/create_ap.conf --freq-band 2.4 -g 10.42.0.1 
Config options written to '/etc/create_ap.conf'
cp: warning: behavior of -n is non-portable and may change in future; use --update=none instead
cp: warning: behavior of -n is non-portable and may change in future; use --update=none instead

Error: Failed to run hostapd, maybe a program is interfering.
If an error like 'n80211: Could not configure driver mode' was thrown
try running the following before starting create_ap:
    nmcli r wifi off
    rfkill unblock wlan
Command not found or exited with error status
pkexec --user root create_ap wlan1 wlan1 'MyAccessPoint' '12345678' --mkconfig /etc/create_ap.conf --freq-band 2.4 -g 10.42.0.1 
Config options written to '/etc/create_ap.conf'
cp: warning: behavior of -n is non-portable and may change in future; use --update=none instead
cp: warning: behavior of -n is non-portable and may change in future; use --update=none instead

(hostapd is masked by system as far as i know unmasking requires creating the conf file)


```
doesnt fails after running
```

nmcli r wifi off
rfkill unblock wlan

pkexec --user root create_ap wlan1 wlan1 'MyAccessPoint' '12345678' --mkconfig /etc/create_ap.conf --freq-band 2.4 -g 10.42.0.1 
Config options written to '/etc/create_ap.conf'
cp: warning: behavior of -n is non-portable and may change in future; use --update=none instead
cp: warning: behavior of -n is non-portable and may change in future; use --update=none instead



```

but wifi is disabled so no internet access and devices cant connect to ap (ip configuration error)
doing nmcli r wifi on, while linux-wifi-hotspot is still running, prevents wlan1 from connecting to the network, only wlan0 connects back. Clients still face ip onfiguration error. 

Thanks for the quick suggestion.

---

### Post by currentshaft on 2024-06-26
What is providing DHCP? Or are clients setting static IPs?

I would start just by running hostapd directly and seeing if clients can complete a WPA connection.

Once that's confirmed to work, move on to IP assignment, then DNS.

---

### Post by sr4uc132vg3hy0c8x2yl on 2024-06-26
so i have started configuring the parts like described here [https://askubuntu.com/a/324785](https://askubuntu.com/a/324785). my chipset is not atheros like he sayd it needs to be but basic is the same for my ? heres the file content which needed to be added, almost the same but changed interface occuriences to wlan1 and the ip/gateway to whats on my network now.heres how it looks..

hostapd
```

DAEMON_CONF="/etc/hostapd/hostapd.conf"

interface=wlan1

### Set your bridge name ###
bridge=br0
driver=nl80211
country_code=DE
ssid=AP
channel=11
wpa=2
wpa_passphrase=MyWiFiPassword
## Key management algorithms ##
wpa_key_mgmt=WPA-PSK
## Set cipher suites (encryption algorithms) ##
## TKIP = Temporal Key Integrity Protocol
## CCMP = AES in Counter mode with CBC-MAC
wpa_pairwise=TKIP
rsn_pairwise=CCMP
## Shared Key Authentication ##
auth_algs=1
## Accept all MAC address ###
macaddr_acl=0
ignore_broadcast_ssid=0
hw_mode=g


```

/etc/network/interfaces

```

# Wireless wlan1
allow-hotplug wlan1
iface wlan1 inet manual

# Setup bridge 
auto br0
iface br0 inet static
    bridge_ports wlan1
    address 100.124.24.238
    netmask 255.254.0.0
    gateway 100.124.0.1
    dns-nameservers 100.124.0.1

```

/etc/default/udhcpd

```

  GNU nano 7.2       /etc/default/udhcpd                 
# Comment the following line to enable
# (under systemd use `systemctl enable udhcpd.service' i>
#DHCPD_ENABLED="no"

# Options to pass to busybox' udhcpd.
#
# -S    Log to syslog
# -f    run in foreground
start 192.168.0.102         #These IPs must to be in the>
end 192.168.0.117
interface wlan1

opt dns 100.124.0.1         #Your current default route >
option subnet 255.255.255.0
opt router 100.124.0.101    #This IP must to be in the s>
option  domain  localhost
#DHCPD_OPTS="-S"


```

and /etc/wpa_supplicant.conf

```

ctrl_interface=/var/run/wpa_supplicant
network={
  ssid="my_wifi_network"
  key_mgmt=WPA-PSK
  proto=WPA
  pairwise=CCMP
  group=CCMP
  psk="mypassphrase"
}


```

started uhcpd hostapd nothing shows up plus im confused as i dont know how my wifi is still working after this, despite i commented out wlan1 static in interfaces file. But after doing all of this im stuck again.

---

