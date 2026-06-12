---
title: "ath9k wireless as AP/Master, issues with dnsmasq"
date: 2017-03-19
forum: Networking &amp; Wireless
---

### Post by orion_134 on 2017-03-19
[http://paste.ubuntu.com/24206714](http://paste.ubuntu.com/24206714)

I have my WAN router connected to my eth0 and I would like to output an AP from wlan0.  I want all traffic, to include all DNS, to remain in the vpn tunnel.  I want the wlan0 to issue DHCP on a 192.168.5.100-150 subnet while wlan0 retains static ip of whatever, right now it's DHCP from the WAN router.

Using this guide: [https://ubuntuforums.org/showthread.php?t=1663788](https://ubuntuforums.org/showthread.php?t=1663788)

dnsmasq.conf (had these uncommented while trying to get it to work, but it killed my dns translations)

```
#dhcp-range=net:wlan0,192.168.5.100,192.168.5.150,255.255.255.0,1440m
#dhcp-option=wlan0,3,192.168.5.1
#dhcp-option=wlan0,6,208.67.222.222,208.67.220.220
```

hostapd.conf (for some reason has a '~' at the end)

```
interface=wlan0
driver=nl80211

ssid=test

channel=6
hw_mode=g

auth_algs=1
wpa=3
wpa_passphrase=super_secret
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP

wme_enabled=1
ieee80211n=1
ht_capab=[HT40+][SHORT-GI-40][DSSS_CCK-40]
```

ap_ctl.sh to bring up AP

```
#!/bin/bash


# broadcasting interface
BROADCAST="wlan0"

# receiving interface broadcast is connected to
RECEIVE="eth0"

if [[ $1 == "-0" || $1 == "--start" ]]
 then
 ## start hostapd
 echo "Starting hostapd"
 echo "    You can view the log at /var/log/hostapd.log"

 # launch hostapd daemon
 hostapd -d /etc/hostapd/hostapd.conf > /var/log/hostapd.log &

 ## start dhcp server
 echo "Starting dnsmasq"

 # set IP address
 ifconfig $BROADCAST 192.168.5.1
 sleep 2

 # launch dhcpd3 daemon
 # echo "INTERFACES=$BROADCAST" > /etc/default/dhcp
 # dhcpd3 $BROADCAST &
 dnsmasq

elif [[ $1 == "-1" || $1 == "--stop" ]]
 then
 # send signal 2 to hostapd and dhcpd3
 killall -2 hostapd  dnsmasq

elif [[ $1 == "-2" || $1 == "--ics" ]]
 then
 # create iptables rules
 iptables -A FORWARD -i $RECEIVE -o $BROADCAST -s 192.168.5.1/24 -m conntrack --ctstate NEW -j ACCEPT
 iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
 iptables -A POSTROUTING -t nat -j MASQUERADE

 # set kernel variable(s)
 echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

 # edit kernel configuration
 cp /etc/sysctl.conf /etc/sysctl.conf.ap_ctl
 echo "net.ipv4.conf.default.forwarding=1" >> /etc/sysctl.conf
 echo "net.ipv4.conf.all.forwarding=1" >> /etc/sysctl.conf

 # restart networking
 /etc/init.d/networking restart

elif [[ $1 == "-3" || $1 == "--noics" ]]
 then
 # remove iptables rules
 iptables -D FORWARD 1
 iptables -D FORWARD 1

 # set kernel variable(s)
 echo 0 > /proc/sys/net/ipv4/conf/all/forwarding

 # revert kernel configuration
 mv -i /etc/sysctl.conf.ap_ctl /etc/sysctl.conf

 # restart networking
 /etc/init.d/networking restart

else
 echo $0
 echo "A tool to manage hostapd and dhcpd3"
 echo "Usage:"
 echo "    -0 --Start    Start hostapd and dhcpd3"
 echo "    -1 --stop    Stop hostapd and dhcpd3 with signal 2"
 echo "    -2 --ics    Activate internet connection sharing"
 echo "            between specified interfaces"
 echo "    -3 --noics    Undo internet connection sharing settings"
fi

exit 0
```

Error when running the script is encountered when dnsmasq is executed:

dnsmasq: failed to create listening socket for port 53: Address already in use

Here is the netstat/ss

```
root@user:~# ss -uanp | grep 53
UNCONN     0      0                 127.0.1.1:53                       *:*      users:(("dnsmasq",7042,4))
```

That is running even if I stop dnsmasq.

Any ideas?

---

### Post by orion_134 on 2017-03-19
Update, it works.  Now to try to get the VPN working
Had to comment out dns=dnsmasq in NetworkManager.conf
Uncommented the above options in dnsmasq.conf, although Network Manager and dhclient nameservers are trumping the dnsmasq as I never see a return from either of those addresses.

---

