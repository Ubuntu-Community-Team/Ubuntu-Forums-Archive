---
title: "wlan0 &quot;Encryption key:off&quot; --- how to turn on?"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by Andrea_44 on 2006-11-23
I have just installed Edgy, am attempting to setup an internet connection with my wireless USB adapter D-Link DWL-G122 Ver C1 (driver rt73 is installed automatically).

I typed:
```

sudo iwconfig 

wmaster0  IEEE 802.11g  Frequency:2.462 GHz
          RTS thr:off   Fragment thr = 2346 B

wlan0     IEEE 802.11g  ESSID:"linksys" 
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          RTS thr:off   Fragment thr = 2346 B
          Encryption key:off
```

Not sure how to enable the Encryption key.

The following is my /etc/network/interfaces:

```
cat /etc/network/interfaces

iface wlan0 inet dhcp
wireless-essid linksys
wireless-key xxxxxxxxx

auto wlan0

iface wmaster inet dhcp
wireless-essid linksys
wireless-key xxxxxxxxx

auto wmaster0
```

I have also tried following:

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 key open
sudo iwconfig wlan0 key xxxxxx
sudo ifconfig wlan0 up

sudo iwlist scan

wmaster0 Interface doesn't support scanning : Operation not supported

wlan0     Scan completed:
          Cell 01 - Address: 00:14:BF:EB:9F:16
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Extra:tsf=00000520b1af45e0
```

```
sudo dhclient wlan0

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:15:e9:ba:c0:25
Sending on   LPF/wlan0/00:15:e9:ba:c0:25
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
...
```

Any help will be great,

Thanks,
Andrea

---

### Post by FrodoB on 2006-11-23
This is saying that the encryption in your Access Point router is turned off. If you turn it on you will have to get the correct key into your Ubuntu setup to make a connection.

It would be easier to comment out the wireless-key lines in /etc/interfaces for now and then add encryption when everything is connecting.

---

### Post by Andrea_44 on 2006-11-23
Thanks for the reply, but um...

```
sudo iwconfig 

wlan0     IEEE 802.11g  ESSID:"linksys" 
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          RTS thr:off   Fragment thr = 2346 B
          Encryption key:off
```

I thought the command "sudo iwconfig" tells me the encryption on my USB adapter is turned off.

> This is saying that the encryption in your Access Point router is turned off.

```

sudo iwlist scan

wlan0     Scan completed:
          Cell 01 - Address: 00:14:BF:EB:9F:16
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Extra:tsf=00000520b1af45e0
```

I thought the command "sudo iwlist scan" tells me the encryption on  router(linksys) is enabled. My other wireless devices are able to make connection to the router, with the WEP encryption enabled on the router. Hence, I don't think the encryption on my router is turned off.

At the moment I am unable to obtain an IP address from the router, this is what happened when I do a "sudo dhclient wlan0"
```
sudo dhclient wlan0

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:15:e9:ba:c0:25
Sending on   LPF/wlan0/00:15:e9:ba:c0:25
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21

```

But I don't think it is a dhcp problem, since all my other wireless devices are able to make connection with the router.

I suspect it is the "Encryption key: off" in "sudo iwconfig" that maybe causing the problem... How could I enable the encryption key on the USB adapter?

Thanks,
Andrea

---

### Post by FrodoB on 2006-11-24
Strange I see that now.

You can edit the /etc/network/interfaces file and make sure that you have a record like this:

iface wlan0 inet dhcp
wireless-essid linksys
wireless-key xxxxxxxxxxxxxxxxxxxxxxx
auto wlan0


change the Xs to your real WEP key, this example is for a 128bit WEP key in hexadecimal which is 26 characters long. If you wish to use ASCII, then it must look like this:

wireless-key s:xxxxxxxxxxxxx

Which is a "s:" followed by 13 ASCII characters.

Once you have the key entered correctly then you should be able to control the connection with:

sudo ifdown wlan0

sudo ifup wlan0

---

### Post by jonfenton on 2006-11-24
Apologies if I have misunderstood your problem but I have the same adapter and I found that the default drivers that are installed with Ubuntu do not work for it. I had to disable them and install the drivers from the chip manufacturer. I now have a very stable connection using WPA.

---

### Post by FrodoB on 2006-11-24
Jonfenton is correct. Follow these instructions and the device will work quite well:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

