---
title: "Unable to surf in internet with wireless, Intel Corporation Wireless 7260, Ubuntu 14."
date: 2014-08-19
forum: Networking &amp; Wireless
---

### Post by fra-dordei on 2014-08-19
Hi all, I am having troubles surfing in internet using a wireless connection. Ethernet connection works properly. I have an ASUS UX301L and Ubuntu 14.04.1 LTS. I installed Ubuntu around 2 months ago alongside windows 8.1 and the wireless worked properly. Since yesterday instead I have the problem that the computer seems to be able to connect to a wireless, it shows me the message that the connection is established, but when I open a browser it is unable to connect to any web page (I tried different browsers with the same result). On windows 8.1 wireless is instead working properly. I attach the result I get after running the wireless script ([ATTACH]255629[/ATTACH]).

Thanks a lot for your help.

---

### Post by varunendra on 2014-08-19
Welcome to the forums fra-dordei!

Please open a terminal (Ctrl-Alt-T) and try this -
```
sudo iwconfig wlan0 power off
```
Then try to reconnect and see if it lets you browse now. If not, check the output of the following command -
```
iwconfig
```
..and make sure "Power Management" is off (that is what the first command tries to do). You may have to check it at regular intervals. If it helps initially but turns back on automatically, we can try a couple of tricks to make it off permanently.

However, if it doesn't seem to help, please try this -
```
echo "options iwlmvm power_scheme=1" | sudo tee /etc/modprobe.d/iwlmvm.conf
```
Then reboot and see if it makes the connection any better. Also check the output of "iwconfig" to make sure "Power Management" is still "off". If not, run the first command to do so, and try reconnecting.

For now, please just try these two and report back. If the problem persists, please also attach the fresh output of wireless_script. However, I suggest trying a slightly different version of the wireless_script this time, as it provides a little more information : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by chili555 on 2014-08-19
You have both wireless and ethernet connected at the same time! I have no doubt that your system is a bit confused! Please shut down the computer, detach the ethernet, start the computer and run and post:```
nm-tool
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.google.com
```Thanks.

---

### Post by fra-dordei on 2014-08-20
Hi all, thanks for your replies! I used the command:

sudo iwconfig wlan0 power off

and afterwards I was able to connect using the wireless with a normal speed, at least from work, I will check again this afternoon from home to be sure that the problem is solved. 
Apologise for the confusion with the ethernet and wireless running together, I attach a fresh output of the wireless script [ATTACH]255660[/ATTACH] and here you are the output of the command suggested by chili555

```
francesca@dordei:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [UNI-WEBACCESS] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        5C:51:4F:25:24:6B

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    eduroam:         Infra, D4: D7:48:81:47:91, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2 Enterprise
    eduroam:         Infra, D4: D7:48:81:47:9E, Freq 5280 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2 Enterprise
    eduroam:         Infra, D4: D7:48:81:47:F1, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2 Enterprise
    eduroam:         Infra, D4: D7:48:81:47:FE, Freq 5220 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2 Enterprise
    eduroam:         Infra, D4: D7:48:81:48:81, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    UNI-HEIDELBERG:  Infra, D4: D7:48:81:47:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 74
    UNI-HEIDELBERG:  Infra, D4: D7:48:81:47:9F, Freq 5280 MHz, Rate 54 Mb/s, Strength 49
    UNI-WEBACCESS:   Infra, D4: D7:48:81:47:9D, Freq 5280 MHz, Rate 54 Mb/s, Strength 49
    UNI-HEIDELBERG:  Infra, D4: D7:48:81:47:F0, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    UNI-WEBACCESS:   Infra, D4: D7:48:81:47:F2, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    UNI-WEBACCESS:   Infra, D47: D48:81:48:82, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    EDV-WLAN:        Infra, 64:70:02:A3:8D:E4, Freq 2427 MHz, Rate 54 Mb/s, Strength 30
    UNI-HEIDELBERG:  Infra, D4: D7:48:81:48:80, Freq 2412 MHz, Rate 54 Mb/s, Strength 29
    UNI-HEIDELBERG:  Infra, D4: D7:48:81:47:FF, Freq 5220 MHz, Rate 54 Mb/s, Strength 20
    EDV-WLan:        Infra, 64:70:02:A3:8D:C2, Freq 2437 MHz, Rate 54 Mb/s, Strength 24
    UNI-WEBACCESS:   Infra, D4: D7:48:81:47:FD, Freq 5220 MHz, Rate 54 Mb/s, Strength 20
    *UNI-WEBACCESS:  Infra, D4: D7:48:81:47:92, Freq 2412 MHz, Rate 54 Mb/s, Strength 57

  IPv4 Settings:
    Address:         147.142.153.158
    Prefix:          24 (255.255.255.0)
    Gateway:         147.142.153.1

    DNS:             129.206.100.126
    DNS:             129.206.210.127


francesca@dordei:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=1.01 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.950 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=1.76 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.950/1.244/1.763/0.368 ms
francesca@dordei:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=48 time=13.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=48 time=13.5 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=48 time=18.7 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 13.221/15.172/18.745/2.533 ms
francesca@dordei:~$ ping -c3 [www.google.com]("http://www.google.com")
PING [www.google.com]("http://www.google.com") (74.125.136.104) 56(84) bytes of data.
64 bytes from ea-in-f104.1e100.net (74.125.136.104): icmp_seq=1 ttl=48 time=14.6 ms
64 bytes from ea-in-f104.1e100.net (74.125.136.104): icmp_seq=2 ttl=48 time=14.0 ms
64 bytes from ea-in-f104.1e100.net (74.125.136.104): icmp_seq=3 ttl=48 time=13.3 ms

--- [www.google.com]("http://www.google.com") ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 13.322/13.986/14.611/0.535 ms
```

---

### Post by chili555 on 2014-08-20
If you'd like to turn power management off in all cases, whether on battery or AC power, please post back. We'll need to amend one file and reboot.

Glad it's working!

---

### Post by fra-dordei on 2014-08-30
Hi all, unfortunately the problem is not really solved :/ It seems to work at my working place, but at home I am still not able to surf in internet. It connects apparently to the wireless, but then it is not able to open any web site. The wireless script gives back an empty file while here you are the result of the command above:

```
francesca@dordei:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [franci_germania] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        5C:51:4F:25:24:6B

  Capabilities:
    Speed:           13 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    WiFi-Repeater1:  Infra, 00:23:13:0B:F8:B4, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    *franci_germania:Infra, 00:24:B2:59:61:3B, Freq 2417 MHz, Rate 54 Mb/s, Strength 80 WPA2
    Kriegsstr.7 Hinterhof: Infra, 7E:4F:B5:F0:68:14, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Oleeessiiiaaaaa: Infra, 24:65:11:12:22:D6, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


francesca@dordei:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

francesca@dordei:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=3 ttl=47 time=821 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 1 received, 66% packet loss, time 2014ms
rtt min/avg/max/mdev = 821.953/821.953/821.953/0.000 ms
francesca@dordei:~$ ping -c3 www.google.com
PING www.google.com (173.194.116.176) 56(84) bytes of data.

--- www.google.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms


```

The cable connection is instead working fine. Thanks for your help.

Francesca

---

### Post by fra-dordei on 2014-09-01
I checked today at work again  and here I don't have any problem to connect to a wireless, so apparently the problem is only with my house wireless.....
If you have any hint it would be much appreciated :)

---

### Post by chili555 on 2014-09-01
> **fra-dordei said:**
> I checked today at work again  and here I don't have any problem to connect to a wireless, so apparently the problem is only with my house wireless.....
If you have any hint it would be much appreciated :)Here are some things you might try. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

