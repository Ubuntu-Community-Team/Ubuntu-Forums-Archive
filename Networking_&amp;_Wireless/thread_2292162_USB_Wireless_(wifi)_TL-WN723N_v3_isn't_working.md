---
title: "USB Wireless (wifi) TL-WN723N v3 isn't working"
date: 2015-08-25
forum: Networking &amp; Wireless
---

### Post by arieleoar on 2015-08-25
Hi everyone!  Here we go, i bought yesterday a usb mini wifi adapter (TP-Link TL-WN723N v3) and plugged. The situation is that i can connect to others wifi networks but i can't create an Access Point.  At this point i'm using kubuntu through metacity desktop session because KDE5 gives me problems, but that's posted in other thread.  I tried several things:  (NOTE FIRST: this device has an "softap" mode included in windows, that works very well)  *using nm-applet (GTK) i was not able to create an AP network, only gave me the option of Ad-Hoc and Infraestructure (so...)  *Used Kde5-nm-connection-manager to create an AP network, but it gave me error >  [ (32) Connection 'L30N' is not available on the device wlan0 at this time ] (then investigated thoroughly...)   *Found that maybe driver (module) r8188ue can be corrupted, so i installed/compiled the 8188ue from github (git lwfinger/rtl8188ue) but nothing has changed, the situation is the same (then..)  *Tried to install official driver/module from tplink for linux but it fails to compile so i can't try that  *Tried a variant of a post that i've found in a forum, using hostap, but it failed to create the connection with this in hostap.conf (and sudo service hostap start)  >  interface=wlan0 ssid=rtwap hw_mode=g channel=6 bridge=br0 wpa=2 wpa_passphrase=leo36987085 wpa_key_mgmt=WPA-PSK wpa_pairwise=CCMP ieee80211n=1 ht_capab=[SHORT-GI-20][SHORT-GI-40][HT40]    So i've run out of tries, there is something else i can do?  Here i leave a sys description:  Kubuntu 15.04 32bits kernel=3.19.0-25-generic  lsusb:  >  Bus 001 Device 007: ID 0bda:8179 Realtek Semiconductor Corp.   ifconfig:  >  wlan0     Link encap:Ethernet  direcciónHW c4:e9:84:1a:2a:a9                                      ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1                                    Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0                                    Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0                                    colisiones:0 long.colaTX:1000                                     Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)    iwconfig: >  wlan0     unassociated  Nickname:""                                    Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated                                       Sensitivity:0/0                                      Retry:off   RTS thr:off   Fragment thr:off                                    Power Management:off                                    Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm                                    Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0                                    Tx excessive retries:0  Invalid misc:0   Missed beacon:0   lsmod:  >  module 8188eu  size 671744  used by 0   Here is a particularity: iw list post nothing in terminal output and when I try "iw wlan0 info" says >  "command failed: No such device (-19)"   Another: In iwconfig i tried to set/change (in sudo mode) the essid, the ap to auto or the nickname and i get >  "Error for wireless request "Set AP Address" (8B14) : SET failed on device wlan0 ; Operation not permitted."   If you need more info request it and i will post it :P  Regards!

---

### Post by howefield on 2015-08-26
Thread moved to the "*Networking & Wireless*" forum for a better chance of support.

---

### Post by arieleoar on 2015-08-26
Well Hello again!

I've managed to make it work! Before almost 20  hours of compling/erasing/downloading packages/trying/looking  terminal/looking phonei/etc...

For those who are in the same trouble, i will explain how i could generate an wifi AP[B]:
[/B]
Following this guide: [http://askubuntu.com/questions/180733/how-to-setup-an-access-point-mode-wi-fi-hotspot](http://askubuntu.com/questions/180733/how-to-setup-an-access-point-mode-wi-fi-hotspot)

but note this: *iw* and* iwlist* can fail to scan/get the AP that i've created, i can only see the link through [I]iwconfig

[/I]Before install hostapd i've edited the file /etc/hostapd/hostapd.conf with this parameters

> interface=wlan0 (or your device id)
driver=nl80211
ssid=<your AP name>
hw_mode=g
channel=1
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=3
wpa_passphrase=<your password>
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

but i haven't created the service "sudo service hostapd start" as the guide says, even i've made

*sudo service hostapd stop *(if the service is running already)
Theninstalled isc-dhcp-server and edited /etc/default/isc-dhcp-server the line " INTERFACES="wlan0" " (or your device id)
edited /etc/dhcp/dhcpd.conf commenting:

> # option definitions common to all supported networks&#8230;
#option domain-name &#8220;example.org&#8221;;
#option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

and adding to the ending:

> subnet 10.10.0.0 netmask 255.255.255.0 {
        range 10.10.0.2 10.10.0.16;
        option domain-name-servers 8.8.4.4, 208.67.222.222;
        option routers 10.10.0.1;
}


And added to /etc/netwrok/interfaces below:

> auto wlan0
iface wlan0 inet static
address 10.10.0.1
netmask 255.255.255.0


[B]As the guide says, if you want to connect to other devices again comment the lines added in /etc/network/interfaces

[/B]And then edited /etc/NetworkManager/NetworkManager.conf to comment the line "#dns=dnsmask" if this exist in the file

Before all this editing i've rebooted (i think this was very important :P ) and then in a terminal:

> 

[COLOR=#0000ff]sudo service isc-dhcp-server start (if it isn't started)
echo 1| sudo tee /proc/sys/net/ipv4/ip_forward
sudo iptables -t nat -A POSTROUTING -s 10.10.0.0/16 -o ppp0 -j MASQUERADE
[/COLOR]


[B]And last and important run: [I]sudo hostapd /etc/hostapd/hostapd.conf (you may need to keep the terminal window running)

[/I][/B]with this the network may be running, you can look at iwconfig if the device runs as "master" with the netname you have put

to kill it, simply open other terminal and: sudo killall hostapd.

The cons: you may have to run the commands that i've put in blue before every reboot if you want your AP working.

HOPE THIS HELPS! thanks to read!

---

