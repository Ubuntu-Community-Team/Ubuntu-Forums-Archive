---
title: "Issues With Intel Wireless 3945abg"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by CordlezToaster on 2007-06-26
Having an issue with my intel 3945abg wireless card in ubuntu 7.04. 

It can see wireless networks but will not connect to them, both wireless networks are using wep keys.

If i do the sudo iwlist eth1 scan command this is what i get.

```
eth1      Scan completed :
          Cell 01 - Address: 00:19:BB:FE:42:ED
                    ESSID:"xether"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=83/100  Signal level=-51 dBm  Noise level=-51 dBm
                    Extra: Last beacon: 192ms ago
          Cell 02 - Address: 00:19:BB:FE:42:F7
                    ESSID:"xether"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:13
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=59/100  Signal level=-72 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 36ms ago
```
Any help would be greatly appriecated

---

### Post by chili555 on 2007-06-26
I wonder if your card is confused because it has two ESSID's named 'xether'. Let's try the following commands to tell *iwconfig* which we want:```
sudo iwconfig eth1 essid xether
sudo iwconfig eth1 ap 00:19:BB:FE:42:ED
sudo iwconfig eth1 key 0123456789
sudo dhclient eth1
```Substitute your key here. You might also try with the word 'open' or 'restricted' after the key, like this:```
sudo iwconfig eth1 key 0123456789 restricted
```

---

### Post by CordlezToaster on 2007-06-26
ill give that a shot but is the 3945abg card actually supported by ubuntu 7.04

---

### Post by chili555 on 2007-06-26
> is the 3945abg card actually supported by ubuntu 7.04Perfectly.

If you have a significant result under *ifconfig eth1* and you are getting credible scan results, which you are, you have a functioning card and driver.

I am answering this post from my Lenovo T60 with an ipw3945. It is quite easy to use.

---

### Post by CordlezToaster on 2007-06-27
> **chili555 said:**
> Perfectly.

If you have a significant result under *ifconfig eth1* and you are getting credible scan results, which you are, you have a functioning card and driver.

I am answering this post from my Lenovo T60 with an ipw3945. It is quite easy to use.

Excellent
Thanks for ya help mate ill let ya know of i go

---

### Post by CordlezToaster on 2007-06-27
Well Chilli555 IT WORKED!! much to my suprise! :)

i wonder will this be permanent or will i need to do this every time i wish to use the wireless?

---

### Post by chili555 on 2007-06-28
It will probably not be permanent. If you roam from home to coffee shop to university, then you will probably want Network Manager or wifi-radar or Wicd to manage your connections and, the trouble is, I know of no way to specify the access point's MAC address in any of these. Therefor you cannot specify which 'xether' you want to connect to.

If, on the other hand, like me, you roam from family room to bedroom to porch, you can *gksudo gedit /etc/network/interfaces* to amend it as follows:```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid xether
wireless-key 0123456789
wireless-ap 00:19:BB:FE:42:ED
```You should connect immediately to the correct access point.

Incidently, if you control these two, your life would be a bit easier if you changed the ESSID's to xether1 and xether2 or similar.

---

### Post by t4thfavor on 2007-06-28
or if they are both yours you could set up wds on them and get better coverage. Thats assuming they are both connected to the same backbone though.

I seem to always find reasons to have more blinking lights.

---

