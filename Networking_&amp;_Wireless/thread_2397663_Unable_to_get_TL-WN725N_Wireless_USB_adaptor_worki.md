---
title: "Unable to get TL-WN725N Wireless USB adaptor working.  No-Carrier/Configuring"
date: 2018-08-01
forum: Networking &amp; Wireless
---

### Post by cerzi on 2018-08-01
Hi all,

Pretty stumped by this so perhaps someone here can offer a hint in the right direction.  First, here's cat 01-netcfg.yaml in netplan/

```


network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.1.145/24]
      gateway4: 192.168.1.254
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
  wifis:
    wlx503eaa650a66:
      dhcp4: no
      dhcp6: no
      gateway4: 192.168.1.254
      addresses: [192.168.1.145/24]
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
      access-points:
        [ssid name]:
          password: [password]



```

This applies fine with no errors.  However, the interface does not appear to be running.
iwconfig:
```
wlx503eaa650a66  unassociated  ESSID:""  Nickname:"<WIFI@REALTEK>"          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
ifconfig
```

enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.145  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::e2d5:5eff:fe3e:6e63  prefixlen 64  scopeid 0x20<link>
        ether e0:d5:5e:3e:6e:63  txqueuelen 1000  (Ethernet)
        RX packets 20101  bytes 14888750 (14.8 MB)
        RX errors 0  dropped 1588  overruns 0  frame 0
        TX packets 8708  bytes 880442 (880.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 217  bytes 14036 (14.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 217  bytes 14036 (14.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlx503eaa650a66: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 50:3e:aa:65:0a:66  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
networkctl
```

IDX LINK             TYPE               OPERATIONAL SETUP
  1 lo               loopback           carrier     unmanaged
  5 enp2s0           ether              routable    configured
  9 wlx503eaa650a66  wlan               no-carrier  configuring

```

However, running 'iwconfig wlx503eaa650a66  essid "[network name]" seems to kick the interface into gear a bit, as it then can at least see the router:
ifconfig
```

wlx503eaa650a66: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.145  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::523e:aaff:fe65:a66  prefixlen 64  scopeid 0x20<link>
        ether 50:3e:aa:65:0a:66  txqueuelen 1000  (Ethernet)
        RX packets 1  bytes 251 (251.0 B)
        RX errors 0  dropped 2136  overruns 0  frame 0
        TX packets 7  bytes 698 (698.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
ifconfig
```

wlx503eaa650a66  IEEE 802.11bgn  ESSID:"[network name]"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 84:A4:23:16:88:94
          Bit Rate:72.2 Mb/s   Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-42 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
networkctrl
```

IDX LINK             TYPE               OPERATIONAL SETUP
  1 lo               loopback           carrier     unmanaged
  5 enp2s0           ether              routable    configured
  9 wlx503eaa650a66  wlan               routable    configured

```

But if I unplug the ethernet and try to ping google, after a short pause the output is
**Temporary failure in name resolution**


I've manually installed the 8188eu drivers but this doesn't seem to help.  I've also got the wpa_supplaments package, but running this command provides the following output:
sudo wpa_supplicant -B -i wlx503eaa650a66 -c /etc/wpa_supplicant/wpa_supplicant.conf
```

Successfully initialized wpa_supplicant
nl80211: Driver does not support authentication/association or connect commands
nl80211: deinit ifname=wlx503eaa650a66 disabled_11b_rates=0
wlx503eaa650a66: Failed to initialize driver interface

```

I'm just about out of ideas now, so any help you guys can offer would be massively appreciated.

Thanks!

---

### Post by chili555 on 2018-08-01
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.1.[COLOR="#FF0000"]145[/COLOR]/24]
      gateway4: 192.168.1.254
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
  wifis:
    wlx503eaa650a66:
      dhcp4: no
      dhcp6: no
      gateway4: 192.168.1.254
      addresses: [192.168.1.[COLOR="#FF0000"]145[/COLOR]/24]
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
      access-points:
        [ssid name]:
          password: [password]
```They can't both have the same address. Also, I'd re-order the wireless stanza to place the address above the gateway.

---

### Post by cerzi on 2018-08-01
Oops, I had actually updated it to different addresses after spotting that.  But good call on the re-order!

I'm not sure whether it was that or some other thing I tinkered with, but networkctl now shows the wlan as routable and configured.  However, still facing the problem of "Temporary failure in name resolution" when I try to ping google.  Indeed, when I try to ping the router I get **Destination Host Unreachable** so there's clearly still something fundamentally wrong happening, alas.

---

### Post by chili555 on 2018-08-01
Please check here:```
cat /usr/share/doc/netplan.io/[COLOR="#FF0000"]examples[/COLOR]/wireless.yaml
```It says:```
network:
  version: 2
  renderer: networkd
  wifis:
    wlp2s0b1:
      dhcp4: no
      dhcp6: no
      addresses: [192.168.0.21/24]
      gateway4: 192.168.0.1
      nameservers:
        addresses: [192.168.0.1, 8.8.8.8]
      access-points:
        "network_ssid_name":
          password: "**********"
```In other words, there is a space after the comma and before the second DNS nameserver. I wonder if that is a problem.

I do know that netplan is picky and wants all these details to be precise. It seems to lack the "oh, well, you know what I mean" feature.

Please change that and then do:```
sudo netplan apply
```and then try:```
ping -c3 192.168.1.254
ping -c3 8.8.8.8
```

---

### Post by cerzi on 2018-08-01
No luck unfortunately.  I should add that ethernet works fine using the above netplan, so the problem seems to be elsewhere.

---

### Post by chili555 on 2018-08-01
Which driver is loaded now, the compiled version or the native version?```
lsmod | grep 8188
```Are there any clues in the log?```
cat /var/log/syslog | grep -e wlx -e 8188
```

---

### Post by cerzi on 2018-08-01
Pretty sure the compiled version is what is currently loaded, lsmod shows:
```
8188eu                737280  0
```

Lots of stuff to sift through in the logs though, a couple of things stand out:
```

Aug  2 02:13:12 rig001 systemd-networkd[643]: wlx503eaa650a66: Interface name change detected, wlx503eaa650a66 has been renamed to wlan0.
Aug  2 02:13:12 rig001 wpa_supplicant[916]: wlx503eaa650a66: Failed to initialize driver interface

```

Something seem fishy about the name changes?

Thanks for the help!

full log
```

Aug  2 00:30:39 rig001 systemd-networkd[1991]: wlx503eaa650a66: Lost carrier
Aug  2 00:30:39 rig001 kernel: [11752.875798] R8188EU: INFO indicate disassoc
Aug  2 00:30:47 rig001 kernel: [11761.370165] R8188EU: INFO indicate disassoc
Aug  2 00:31:03 rig001 kernel: [11776.751101] IPv6: ADDRCONF(NETDEV_UP): wlx503eaa650a66: link is not ready
Aug  2 00:31:20 rig001 kernel: [11794.591020] R8188EU: INFO assoc success
Aug  2 00:31:20 rig001 kernel: [11794.591289] IPv6: ADDRCONF(NETDEV_CHANGE): wlx503eaa650a66: link becomes ready
Aug  2 00:31:20 rig001 systemd-networkd[1991]: wlx503eaa650a66: Gained carrier
Aug  2 00:31:20 rig001 systemd-networkd[1991]: wlx503eaa650a66: Could not set route: Network is unreachable
Aug  2 00:31:22 rig001 systemd-networkd[1991]: wlx503eaa650a66: Gained IPv6LL
Aug  2 00:32:33 rig001 kernel: [11867.260443] R8188EU: INFO indicate disassoc
Aug  2 00:32:33 rig001 systemd-networkd[1991]: wlx503eaa650a66: Lost carrier
Aug  2 00:33:24 rig001 ModemManager[915]: <info>  (net/wlx503eaa650a66): released by modem /sys/devices/pci0000:00/0000:00:14.0/usb1/1-3
Aug  2 00:33:24 rig001 kernel: [11918.265922] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
Aug  2 00:33:24 rig001 kernel: [11918.295298] r8188eu 1-3:1.0 wlx503eaa650a66: renamed from wlan0
Aug  2 00:33:24 rig001 systemd-networkd[2207]: wlan0: Interface name change detected, wlan0 has been renamed to wlx503eaa650a66.
Aug  2 00:33:24 rig001 systemd-networkd[2207]: wlx503eaa650a66: IPv6 successfully enabled
Aug  2 00:33:25 rig001 kernel: [11918.670132] IPv6: ADDRCONF(NETDEV_UP): wlx503eaa650a66: link is not ready
Aug  2 00:33:25 rig001 systemd[1]: Started WPA supplicant for netplan wlx503eaa650a66.
Aug  2 00:33:25 rig001 wpa_supplicant[2245]: nl80211: deinit ifname=wlx503eaa650a66 disabled_11b_rates=0
Aug  2 00:33:25 rig001 wpa_supplicant[2245]: wlx503eaa650a66: Failed to initialize driver interface
Aug  2 00:33:25 rig001 systemd[1]: netplan-wpa@wlx503eaa650a66.service: Main process exited, code=exited, status=255/n/a
Aug  2 00:33:25 rig001 systemd[1]: netplan-wpa@wlx503eaa650a66.service: Failed with result 'exit-code'.
Aug  2 02:13:12 rig001 systemd[1]: Found device RTL8188EUS 802.11n Wireless Network Adapter.
Aug  2 02:13:12 rig001 systemd-networkd[643]: wlx503eaa650a66: Interface name change detected, wlx503eaa650a66 has been renamed to wlan0.
Aug  2 02:13:12 rig001 systemd-networkd[643]: wlan0: Interface name change detected, wlan0 has been renamed to wlx503eaa650a66.
Aug  2 02:13:12 rig001 systemd-networkd[643]: wlx503eaa650a66: IPv6 successfully enabled
Aug  2 02:13:12 rig001 systemd[1]: Started WPA supplicant for netplan wlx503eaa650a66.
Aug  2 02:13:12 rig001 wpa_supplicant[916]: nl80211: deinit ifname=wlx503eaa650a66 disabled_11b_rates=0
Aug  2 02:13:12 rig001 wpa_supplicant[916]: wlx503eaa650a66: Failed to initialize driver interface
Aug  2 02:13:12 rig001 systemd[1]: netplan-wpa@wlx503eaa650a66.service: Main process exited, code=exited, status=255/n/a
Aug  2 02:13:12 rig001 systemd[1]: netplan-wpa@wlx503eaa650a66.service: Failed with result 'exit-code'.
Aug  2 02:13:12 rig001 kernel: [    5.759059] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
Aug  2 02:13:12 rig001 kernel: [    6.052066] usbcore: registered new interface driver r8188eu
Aug  2 02:13:12 rig001 kernel: [    6.311835] r8188eu 1-3:1.0 wlx503eaa650a66: renamed from wlan0
Aug  2 02:13:12 rig001 kernel: [    6.633066] R8188EU: Firmware Version 11, SubVersion 1, Signature 0x88e1
Aug  2 02:13:12 rig001 kernel: [    7.050156] IPv6: ADDRCONF(NETDEV_UP): wlx503eaa650a66: link is not ready

```

---

### Post by chili555 on 2018-08-02
If you temporarily try the native driver, is there any change?```
sudo modprobe -r 8188eu
sudo modprobe r8188eu
```Followed by:```
cat /var/log/syslog | grep -e wlx -e net
```I don't think that the renaming is significant.

Please conduct your test with the ethernet detached.

Does the interface scan?```
sudo iwlist scan
```We needn't see the results, just tell us if it sees your network or tell us if there is an error or other interesting message.

May I assume that Network Manager is not running here?

---

### Post by cerzi on 2018-08-02
modrobe -r 8188eu causes the interface to disappear from iwconfig/networkctl etc - so I'm guessing that means the driver is indeed doing its thing, unless something else needs to be done to attempt to re-enable the native one.  Logs show:
```

Aug  2 14:20:57 rig001 dbus-daemon[939]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.0' (uid=100 pid=675 comm="/lib/systemd/systemd-networkd " label="unconfined")
Aug  2 14:21:02 rig001 systemd[1492]: Closed GnuPG network certificate management daemon.
Aug  2 14:21:05 rig001 systemd[1592]: Listening on GnuPG network certificate management daemon.
Aug  2 14:21:19 rig001 ModemManager[924]: <info>  (net/wlx503eaa650a66): released by modem /sys/devices/pci0000:00/0000:00:14.0/usb1/1-3
Aug  2 14:21:19 rig001 systemd-networkd[675]: Could not update link, ignoring: No such device
Aug  2 14:22:25 rig001 kernel: [  431.986731] r8188eu 1-3:1.0 wlx503eaa650a66: renamed from wlan0
Aug  2 14:22:25 rig001 systemd-networkd[675]: wlan0: Interface name change detected, wlan0 has been renamed to wlx503eaa650a66.
Aug  2 14:22:25 rig001 systemd-networkd[675]: lo: Link is not managed by us
Aug  2 14:22:25 rig001 systemd-networkd[675]: wlx503eaa650a66: IPv6 successfully enabled
Aug  2 14:22:25 rig001 networkd-dispatcher[936]: WARNING:Unknown index 4 seen, reloading interface list
Aug  2 14:22:26 rig001 kernel: [  432.384980] IPv6: ADDRCONF(NETDEV_UP): wlx503eaa650a66: link is not ready

```
(this was while ethernet was unplugged)

And yeah - iwlist scan works fine - should probably have mentioned that.  Again, setting the essid manually with iwconfig seems to bring the interface to life, as it gets an IP and recognizes the network name.  But nothing appearing on the router, and no actual connection can be made.

NetworkManager not installed

---

### Post by cerzi on 2018-08-02
Another thing to note is I can get to a similar state using iwconfig <interface> essid <wifi not defined in netplan>.  So it would appear the interface isn't even attempting to authenticate with the wireless network.  Or it is, but doing so extremely quietly.

---

### Post by chili555 on 2018-08-02
> Another thing to note is I can get to a similar state using iwconfig <interface> essid <wifi not defined in netplan>. So it would appear the interface isn't even attempting to authenticate with the wireless network. Or it is, but doing so extremely quietly.I don't understand. Are you saying that the wireless connects based on your iwconfig command? And it gets an IP address??

Does it simply get the IP address that you specified?

There is no way you can connect without supplying the WPA2 password. There is also no way to specify a WPA2 password with the command iwconfig. iwconfig will take the argument 'key' which implies a WEP key. As WEP is quite insecure, we all stopped using it ten years ago.

Just because you told the system what SSID you want to connect to and what IP address you want doesn't mean that the transaction is complete or successful. 

Please try:```
sudo netplan generate
sudo netplan apply
```Please note and post any errors or warnings. Then show us:```
cat /var/log/syslog | grep -i network | tail -n 15
```

---

### Post by praseodym on 2018-08-02
Are we sure about the chipset?
```

lsusb
lsmod
```rtl8188cu is also possible

---

### Post by cerzi on 2018-08-02
lsusb:
```
Bus 001 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
```
I'm guessing RTL8188EUS is the same as eu?

Syslog after netplan generate/apply
```

Aug  2 22:35:39 rig001 systemd-networkd[1487]: enp2s0: Gained IPv6LL
Aug  2 22:35:39 rig001 systemd-networkd[1487]: Enumeration completed
Aug  2 22:35:39 rig001 systemd[1]: Started Network Service.
Aug  2 22:35:39 rig001 systemd-networkd[1487]: wlx503eaa650a66: Could not find udev device: No such device
Aug  2 22:35:39 rig001 systemd-networkd[1487]: wlx503eaa650a66: Failed
Aug  2 22:35:39 rig001 systemd-networkd[1487]: Could not add new link, ignoring: No such device
Aug  2 22:35:39 rig001 systemd-networkd[1487]: lo: Link is not managed by us
Aug  2 22:35:39 rig001 systemd-networkd[1487]: enp2s0: Could not set route: Network is unreachable
Aug  2 22:35:39 rig001 systemd-networkd[1487]: wlan0: Interface name change detected, wlan0 has been renamed to wlx503eaa650a66.
Aug  2 22:35:39 rig001 systemd-networkd[1487]: lo: Link is not managed by us
Aug  2 22:35:39 rig001 systemd-networkd[1487]: wlx503eaa650a66: IPv6 successfully enabled
Aug  2 22:35:39 rig001 networkd-dispatcher[916]: WARNING:Unknown index 4 seen, reloading interface list
Aug  2 22:35:42 rig001 systemd-networkd[1487]: enp2s0: DHCPv4 address 192.168.1.147/24 via 192.168.1.254
Aug  2 22:35:42 rig001 dbus-daemon[884]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.13' (uid=100 pid=1487 comm="/lib/systemd/systemd-networkd " label="unconfined")
Aug  2 22:35:42 rig001 systemd-networkd[1487]: enp2s0: Configured

```

No, the wireless doesn't actually connect through iwconfig - it just appears to actually be doing something. Just reported on it as it's the only thing that seems to give any semblance of a green light here, but yeah pretty meaningless really :(


This is basically as far as things get in networkctl:
```

IDX LINK             TYPE               OPERATIONAL SETUP
  1 lo               loopback           carrier     unmanaged
  2 enp2s0           ether              routable    configured
  6 wlx503eaa650a66  wlan               no-carrier  configuring

```

---

### Post by cerzi on 2018-08-02
Tried using drivers from here instead
[https://github.com/quickreflex/rtl8188eus](https://github.com/quickreflex/rtl8188eus)

But same problems unfortunately.  Driving me a bit mad at this point!

Edit: should also add, on boot there's a 2min stall "A start job is running for Wait For Network to Be Confingured" - and this happens when ethernet is plugged in also.  Could be related to the pains I'm having?

---

### Post by chili555 on 2018-08-03
Why don't we go back to basics. Which interface are you hoping to use full time once this is fixed? The wireless?

If so, please amend your netplan file to:```
network:
  version: 2
  renderer: networkd
   wifis:
     wlx503eaa650a66:
       dhcp4: yes
       dhcp6: yes
       access-points:
         "ssid name":
           password: "password"
```Next, do:```
sudo netplan generate
sudo netplan apply
```Reboot and show us:```
iwconfig
cat /var/log/syslog | grep -e network -e wlx
ifconfig
```

---

### Post by cerzi on 2018-08-03
Apologies for the photos -

ifconfig:
[IMG]https://i.imgur.com/imJmq4p.jpg[/IMG]

iwconfig:

[IMG]https://i.imgur.com/JsfAKKz.jpg[/IMG]

syslog:

[IMG]https://i.imgur.com/YaxMVCg.jpg[/IMG][IMG]https://i.imgur.com/MBMOUfo.jpg[/IMG]

Is it possible that I just have a duff adapter?

---

### Post by cerzi on 2018-08-06
Still completely stumped by this - if anyone has any suggestions on other things to try, would really appreciate it!

---

### Post by praseodym on 2018-08-06
Lets try

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by cerzi on 2018-08-07
Unfortunately no use - I'm using network.d so my NetworkManager/conf.d is empty, and network-manager itself was removed a while go as part of the endless struggle to get this thing working.

---

### Post by cerzi on 2018-08-10
bump - don't suppose anyone else has any ideas for avenues to explore?

---

