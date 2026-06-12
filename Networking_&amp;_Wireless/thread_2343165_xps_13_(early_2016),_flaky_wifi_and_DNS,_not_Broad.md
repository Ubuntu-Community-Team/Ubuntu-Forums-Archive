---
title: "xps 13 (early 2016), flaky wifi and DNS, not Broadcom-related --- how to restart DNS?"
date: 2016-11-14
forum: Networking &amp; Wireless
---

### Post by ivo-welch on 2016-11-14
I have been reading up on the many wifi issues on the xps13, 2015 model.  a 2015 xps13 is not the latest hardware, so the drivers should work.  alas, no.  I thought given Dell's generic linux interest that an xps13 would be a good bet.  canonical should take the xps13 off the list of recommended laptops. a two-year old specialized version of ubuntu is not compatible in my book.  to be recommended, a laptop should be work with the current LTS, 16.04.  my advice:

> 
    do not buy an xps13 dell laptop to run ubuntu linux.


wifi problem details: I installed 16.10, so that I am running a late kernel.

once I sleep and wakeup again, it is complete failure.  my broadcom internal wifi failed after sleep.  so I removed it and installed an edimax usb wifi.  it works but with the same symptoms, so I don't think this is broadcom's fault.  for both devices, the wifi works, but the DNS does not, because I can ssh to an external IP address.  the failure is in the DNS, and not in the wifi hardware or wifi networking.

it seems to be an incorrect protection error.  upon "dig google.com" and "nslookup google.com", it immediately comes back to tell me that the connection is refused, as if were an authorization error.  there is no further details why it was refused.  it also rejects me so fast that I am pretty sure it is something on the xps13, not on the network (which incidentally works with other computers just fine).

even an `/etc/init.d/networking restart` does not fix it.  neither does switching the wifi off and on again.  or switching to airplane more.
so, I know that the low-level stuff is working.  I know that the high-level stuff is working after bootup, but something goes wrong after sleep.  what in the world could be xps13 specific, but not hardware and wifi related??  

[B]Is there a way to use the command line to restart the DNS to make it work again?
[/B]
/iaw

PS: on occasion, I think the edimax may now be overheating and lose server connection, too, which can be fixed by briefly removing it or restarting networking.

---

### Post by chili555 on 2016-11-14
> once I sleep and wakeup again, it is complete failure. Did you try this?

[http://askubuntu.com/questions/748113/wifi-still-sleeping-when-resume/748130#748130](http://askubuntu.com/questions/748113/wifi-still-sleeping-when-resume/748130#748130)

---

### Post by ivo-welch on 2016-11-15
yes, I did, but it is still no cigar.  that is,

> 
# service network-manager restart
[ ok ] ... restarting

# dig google.com

; <<>> DIG 9.10.3-P4-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode QUERY, status: REFUSD, id:48191
'' flags: qr rd ra ad; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
...


> 
# nmcli g
STATE CONNECTIVITY WIFI-HW WIFI WWAN-HW WWAN
connected full enabled enabled enabled enabled


as well as a

> 
# nmcli radio wifi off 
# nmcli radio wifi on


---

### Post by chili555 on 2016-11-15
Let's try to troubleshoot what's going wrong here. After suspend, is Network Manager running?```
ps aux | grep -i network
```Is the driver loaded? Find the driver from:```
sudo lshw -C network
```Then check:```
lsmod | grep <driver_you_found>
```Here is a sample from my machine:```
*-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 83
       serial: xx:c5:d4:0e:64:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=[COLOR="#FF0000"]iwlwifi[/COLOR] driverversion=4.8.0-27-generic firmware=17.352738.0 ip=192.168.0.120 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:32 memory:f0400000-f0401fff

```Is power saving an issue?```
iwconfig
```Again, a sample:```
wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: XX:2B:B0:DC:45:XX
          Bit Rate=866.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          [COLOR="#FF0000"]Power Management:on[/COLOR]
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:124   Missed beacon:0

```Let's see what you have and proceed from there.

---

### Post by ivo-welch on 2016-11-15
first, let me express my appreciation for spending the time with me on tracking this down.  my network is

```

root       689  0.1  0.2 629628 18736 ?        Ssl  16:39   0:01 /usr/sbin/NetworkManager --no-daemon
nobody    2148  0.0  0.0  60156  4088 ?        S    16:50   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --cache-size=0 --conf-file=/dev/null --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
root      2910  0.0  0.0  16112  3624 ?        S    16:55   0:00 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-helper -pf /var/run/dhclient-wlx74da388fa7d5.pid -lf /var/lib/NetworkManager/dhclient-a677f8ed-ccbf-4a97-8f4b-04b9ef935edc-wlx74da388fa7d5.lease -cf /var/lib/NetworkManager/dhclient-wlx74da388fa7d5.conf wlx74da388fa7d5
ivo       3133  0.0  0.0  21296  1028 pts/0    S+   16:55   0:00 grep --color=auto -i network

```

the lshw is

```

  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlx74da388fa7d5
       serial: 74:da:38:8f:a7:d5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=4.8.0-26-generic firmware=N/A ip=172.31.46.46 link=yes multicast=yes wireless=IEEE 802.11
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:2
       logical name: wlx74da388fa7d5
       serial: 74:da:38:8f:a7:d5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=4.8.0-26-generic firmware=N/A ip=172.31.46.46 link=yes multicast=yes wireless=IEEE 802.11

```

the lsmod output is

```

rtl8192cu              65536  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        49152  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              757760  4 rtl_usb,rtlwifi,rtl8192cu,rtl8xxxu

```

the iwconfig is

```

wlx74da388fa7d5  IEEE 802.11  ESSID:"UCLA_WEB"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 24:DE:C6:F0:6C:82
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```





the power management is off.  not sure why.  I just looked into the preferences power settings, but there it says network power savings are now on.  (I had tried it with off, but this did not remedy my trouble.)

anything unusual stick out?  the wifi is clearly working.  there is something about the DNS communication losing itself.

---

### Post by chili555 on 2016-11-16
First of all, I doubt highly that this is specifically a DNS issue. I think it is really that, for some reason, you appear to be connected but are really not. You have a driver (too many, actually!), NM is running and you appear to have a valid IP address, and yet you cannot reach the internet.

I see this:> rtl8192cu              65536  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        49152  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              757760  4 rtl_usb,rtlwifi,rtl8192cu,rtl8xxxuThere are a very few drivers that both claim the same device, The driver rtl8192cu and the driver rtl8xxxu are two examples. They both claim your wireless device and, no doubt, conflict. Let's blacklist one and see if your wireless now performs as expected. Please open a terminal and do:
```
sudo -i
modprobe -r rtl8xxxu
echo "blacklist rtl8xxxu"  >>  /etc/modprobe.d/blacklist.conf
exit
```
It may take a reboot. Any improvement?

---

### Post by ivo-welch on 2016-11-16
strangely, after I installed the intel wifi modem, it has begun to work.  so, neither the broadcom nor the edimax usb wifi worked, and both had the same weird symptoms of losing DNS ("refused") after a sleep-wakeup cycle.  thanks for the help---and a piece of advice to others.  this malaise makes little sense, but it is replicable.  sigh...

---

