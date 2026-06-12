---
title: "Help with WN725"
date: 2015-02-05
forum: Networking &amp; Wireless
---

### Post by wripet on 2015-02-05
Since my standard AR242 Wireless adapter never really worked properly under Ubuntu 14.04 LTS, I wanted to give the TL-WN725n a try. But besides the WLAN-Stick being recognized by the system, pretty much nothing works. I tried turning off the encryption on my router and tried connecting, but not really any success. My routers address is 192.168.178.1, SSID is FRITZBOX

/etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
              address 192.168.2.1

auto wlan1
iface wlan1 inet static
              address 192.168.178.2
              netmask 255.255.255.0
              gateway 192.168.178.1
              wireless-ssid FRITZBOX

```

Part of the output of iwconfig

```

wlan1    unassociated  Nickname:"<WIFI@REALTEK>"
         Mode:Managed  Frequency=2.446 GHz   Access Point: Not-Associated
         Sensitivity:0/0
         Retry:off      RTS thr:off    Fragment  thr:off
         Encryption key:off
         PowerManagement:off
         Link Quality:0  Signal level: 0  Noise level:0

```

---

### Post by chili555 on 2015-02-05
In your router, what is the range of the DHCP pool? Does it include 192.168.178.2? It shouldn't. If it does, select a static IP outside the DHCP pool. 192.168.178.102, for example.

Is Network Manager installed and running? Why not use it and skip all the changes in /etc/network/interfaces?

If you set a static IP, you are responsible for DNS nameservers, too. You have none declared.

---

### Post by wripet on 2015-02-05
Thanks for the reply,

first of all: I don't have a GUI, so no network manager.

The routers DHCP pool starts at 20, so there can't be a conflict. I added the line "dns-nameservers 192.168.178.1 8.8.8.8" to /etc/network/interfaces, removed everything from /etc/resolvconf, as well as /etc/resolv.conf and did a dpkg-reconfigure resolvconf.

Still no luck after a reboot. The WLAN doesn't even show up when calling iwconfig. Seems as if wlan1 doesn't even connect. As said, no encryption on the wlan.

---

### Post by chili555 on 2015-02-05
Let's look at a few other things:```
iwconfig
lspci -nn | grep 0280
```Thanks.

---

### Post by wripet on 2015-02-05
As you wish:

iwconfig:

```

wlan1     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The lspci command didn't produce any 0280-related output. Seems like no wireless card is found. But why the wlan1 entry in iwconfig? When i plug in the WLAN-stick and check with lsusb, it appears with and entry.

BTW: Thanks for the help! Really somewhat lost here.

---

### Post by chili555 on 2015-02-05
> **wripet said:**
> As you wish:

iwconfig:

```

wlan1     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The lspci command didn't produce any 0280-related output. Seems like no wireless card is found. But why the wlan1 entry in iwconfig? When i plug in the WLAN-stick and check with lsusb, it appears with and entry.

BTW: Thanks for the help! Really somewhat lost here.LOLOL! By all means, please let us see:```
lsusb
```

---

### Post by wripet on 2015-02-05
> **chili555 said:**
> LOLOL! By all means, please let us see:```
lsusb
```

After plugging the Stick in, the entry

```

Bus 001 Device 015: ID 0bda:8179 Realtek Semiconductor Corp.

```

appeared.

---

### Post by chili555 on 2015-02-05
Your device uses the driver r8188eu. I assume, since you have a wlan1, that it is loaded:```
lsmod | grep r8188eu
```If you have a driver and an interface, namely wlan1, then I ussume the only problem is getting it to connect. Please try:```
sudo ifdown wlan1 && sudo ifup -v wlan1 
```The flag -v for verbose should produce some output telling us what's wrong. Please copy it down or photograph it or anything so we can see it.

If it looks like it may have succeeded, then test:```
ping -c3 192.168.178.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```Finally, please double-check the gateway address 192.168.178.1 on some other device. I've made a few understandable typos over the years and would hate to see that actually it's 192.168.[COLOR="#FF0000"]187[/COLOR].1!

---

### Post by wripet on 2015-02-05
Routers address is 192.168.178.1, Gateway is set to the same in /etc/network/interfaces.

lsmod:

```
r8188eu               814658  0 
```

sudo ifdown wlan1 && sudo ifup -v wlan1:

```
grep: /etc/resolv.conf: No such file or directory
Configuring interface wlan1=wlan1 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
ip addr add 192.168.178.2/255.255.255.0 broadcast 192.168.178.255       dev wlan1 label wlan1
ip link set dev wlan1   up
 ip route add default via 192.168.178.1  dev wlan1 
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/avahi-daemon
grep: /etc/resolv.conf: No such file or directory
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant

```

Oh, I forgot, ping still not working, Destination Host Unreachable in all 3 cases.

---

### Post by chili555 on 2015-02-05
Any clue here?```
dmesg | grep -e r8188eu -e wlan
```> grep: /etc/resolv.conf: No such file or directoryWeird. Not sure if it's keeping you from connecting.

---

### Post by wripet on 2015-02-05
> **chili555 said:**
> Any clue here?```
dmesg | grep -e r8188eu -e wlan
```Weird. Not sure if it's keeping you from connecting.

Don't really know what it means, but looks suspicious:

```
[    3.841474] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[    3.974018] usbcore: registered new interface driver r8188eu
[    4.896694] systemd-udevd[323]: renamed network interface wlan0 to wlan1
[    5.679048] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[14822.676387] systemd-udevd[22824]: renamed network interface wlan0 to wlan1
[14823.158515] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[15682.510086] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[15699.555570] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[15717.040877] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[15781.831534] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[15929.894483] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[15950.443692] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[16186.523834] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[17964.519900] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready

```

Edit: I thought the addrconf might come from the device on eth0, did a "ifconfig eth0 down", but no difference.

Edit: The IPv6 error seems really strange to me, I disabled ipv6 in /etc/sysctl.conf:

```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

---

### Post by chili555 on 2015-02-06
The IPv6 errors simply mean that the system was unable to get an IPv6 address. That also happens, of course, when you are unable to obtain *any* address.

May I see:```
sudo iwlist wlan1 scan
```Trim away all but your network and obscure your MAC address like this:```
Cell 01 - [COLOR="#FF0000"]Address: xx:D7:19:41:54:xx[/COLOR]
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000011ef593124
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```Next, let's try to address the resolv.conf issue. May we see:```
ls -l /etc/resolv.conf
ls -l /run/resolvconf/resolv.conf
ls /etc | grep reso
```One or more of those may end in an error, but I'd like to see which and what the error is.

Is there any sign of life with:```
sudo dhclient wlan1
```Thanks.

---

