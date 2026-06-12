---
title: "IOGEAR GWU625 wireless adapter on Ubuntu Server 12.04.3 LTS?"
date: 2014-03-06
forum: Networking &amp; Wireless
---

### Post by Hanjaya on 2014-03-06
Hi,

I would like to install IOGEAR GWU625 USB wireless adapter on Ubuntu server 12.04.3 LTS. 

I emailed the IOGEAR support for instruction and they refused to help because he said that it is stated officially only for Win, Mac, and Fedora10. Can anyone help please?

Thanks.

hc.

---

### Post by chili555 on 2014-03-06
I believe the driver for your device depends on your kernel version; that is, earlier kernels don't have it and later do. Please insert the device and run:```
lsusb
```Is your device enumerated 0bda:8172? If so, it works with the driver r8712u. Did it load automagically?```
lsmod | grep r87
```If not, post your kernel version and we'll propose a solution:```
uname -r
```If it did load, was a wireless interface created, ideally wlan0?```
iwconfig
```If so, edit your /etc/network/interfaces file something like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid <your_ssid>
wpa-psk <your_secret_key>
dns-nameservers 8.8.8.8 192.168.1.1
```Of course, select an address outside the range used by the DHCP server in the router and substitute your exact details here.

Get the system to read and use the changes:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```See if you have a connection:```
ping -c3 www.google.com
```

---

### Post by Hanjaya on 2014-03-08
Hi,

I did all the steps and it seemed like to work. I saw blinking on the adapter but when I ping Google, it said: unknown host [www.Google.com](www.Google.com).

Not sure what happened.

Hc.

---

### Post by Hanjaya on 2014-03-08
Should the wpa-psk be the ASCII paraphrase or the hex ?

Well, anyway I tried both but not working.

Hc.

---

### Post by chili555 on 2014-03-08
> **Hanjaya said:**
> Should the wpa-psk be the ASCII paraphrase or the hex ?

Well, anyway I tried both but not working.

Hc.Uh oh. Generally, when someone asks about ASCII or hex, the implication is that they are not using the very secure WPA2 but the very *IN*secure WEP. Is that the case here? If so, please stop everything you are doing and change the encryption in the router to WPA2-AES right now!

If this is a router over which you do not have administrative rights; for instance, a connection provided by a landlord, then please stop everything you are doing and write a note to the provider to protest and ask that they not expose your data to an insecure, easily hackable WEP connection. While you wait for the router to be changed, assuming the encryption is actually WEP, change the file to:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid <your_ssid>
wireless-key <your_key_in_hex>
dns-nameservers 8.8.8.8 192.168.1.1
```Please post back and tell me that I am mistaken and you are not using WEP. You might as well leave your credit card in a shoebox on the front steps.

---

### Post by Hanjaya on 2014-03-09
Hi,

Yes, I use WPA, not WEP.

sudo ifdown wlan0 && sudo ifup -v wlan0

```

Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-said "xxxxx" -- OK
wpa_supplicant: wpa-oak **** -- OK
wpa_supplicant: enabling network block 0 -- OK
up addr add 192.168.1.100/255.255.255.0 broadcast +   dev wlan0 label wlan0
ip link set dev wlan0 up
ip route add default via 192.168.1.1 metric 100 dev wlan0
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant

```

ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

hc.

---

### Post by chili555 on 2014-03-09
> wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-s[COLOR="#FF0000"]a[/COLOR]id "xxxxx" -- OK
wpa_supplicant: wpa-[COLOR="#FF0000"]oa[/COLOR]k **** -- OK
wpa_supplicant: enabling network block 0 -- OKDo you have a typographical error in your interfaces file? Please retrace your steps and correct if needed.> wpa-psk be the ASCII paraphrase or the hex ?Since you've verified that you are using WPA, I am even more confused. The entry at wpa-psk needs to be the WPA pre-shared key in plain txt. In other words in the router, if you set the key to be, for example, I10v3Mary, then the line in /etc/network/interfaces should be:```
wpa-psk I10v3Mary
```After you attempt to connect, is there any clue here?```
dmesg | grep wlan
```Finally, have you confirmed, by looking at the network settings on other computers in the same network, that my suggested settings; 192.168.1.100, etc., etc. are appropriate?

---

### Post by Hanjaya on 2014-03-10
Hi Chili,

I got it working. I just input the wrong IP & Gateway addresses before.

Thank you so much.

hc.

---

### Post by Iowan on 2014-03-10
If it stays fixed, please consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by Hanjaya on 2014-03-10
Hi Iowan,

Sorry I was looking to close the thread earlier but could not figure out. I closed it now. Thanks.

hc.

---

