---
title: "Wireless card problem with old Fujitsu Amilo L7320GW laptop, Lubuntu 18.04"
date: 2018-11-26
forum: Networking &amp; Wireless
---

### Post by dadaisnotdead on 2018-11-26
Hi everyone!

I'm trying to make a friend's old Fujitsu Amilo L7320GW laptop work (it used to have Win XP and now I installed Lubuntu 18.04 on it)
However, the wifi doesn't seem to work so far. It connects to the network but there is still no internet. 

I've spent a few days googling and reading the forum to make it work but nothing seemed to help so far...

I've uploaded the result of the wireless script here:

[http://paste.ubuntu.com/p/SkVWppNHp3/](http://paste.ubuntu.com/p/SkVWppNHp3/)

Thanks for any advice in advance!

---

### Post by praseodym on 2018-11-26
Lets try

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Edit: Also change the encryption mode in your router to WPA2-AES (CCMP) ,no mixed mode WPA/WPA2

---

### Post by dadaisnotdead on 2018-11-27
Thank you for your reply!!
It really did solve the issue!

I set my router to WPA2+PSK (that was the only other option, I wonder if it's the same ?!)

After running:
```
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

The network indicator said "Wi-Fi is disabled by hardware switch"
Neither pressing Fn + F2 (the wifi switch on this laptop) nor running "sudo rfkill unblock all" seemed to resolve it

But I did a reboot and after that it worked like a charm!

Thanks again! :)

---

### Post by dadaisnotdead on 2018-11-27
I spoke a bit too soon...

After another restart the problem occurred again... I ran your recommended commands and restarted but I still don't have internet

I ran the wireless script again, here is the result:
[http://paste.ubuntu.com/p/cvKjVF3HTt/](http://paste.ubuntu.com/p/cvKjVF3HTt/)

---

### Post by chili555 on 2018-11-27
> **dadaisnotdead said:**
> I spoke a bit too soon...

After another restart the problem occurred again... I ran your recommended commands and restarted but I still don't have internet

I ran the wireless script again, here is the result:
[http://paste.ubuntu.com/p/cvKjVF3HTt/](http://paste.ubuntu.com/p/cvKjVF3HTt/)Hmmm. Your script suggests that you do have internet:> 3: wlp0s6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp0s6' [IF2]> brd <MAC address>
    inet [COLOR="#FF0000"]192.168.0.24[/COLOR]/24 brd 192.168.0.255 scope global dynamic noprefixroute wlp0s6
       valid_lft 3019sec preferred_lft 3019sec
    inet6 [COLOR="#FF0000"]2a02:ab88:2483:7d00:9e0f:18de:e155:52ef[/COLOR]/64 scope global dynamic noprefixroute 
       valid_lft 1075412sec preferred_lft 470612sec
    inet6 fe80::f92b:9226:7ea0:3fc0/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
With the ethernet detached, let's see:```
ping -c3 192.168.0.1
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```...and then post the result.

---

### Post by dadaisnotdead on 2018-11-27
First all three of them replied with "connect: Network is unreachable"

But then out of curiosity I did another reboot... and then bamm! I've got internet again. It's really odd... it's like Schroedinger's wifi card (one can not know if there will be internet until the system boots up). 
Funnily enough the internet didn't stay with me... it went away again few minutes after the reboot.

Here are the results directly after the restart:

```

$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.


--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2052ms


$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=122 time=14.0 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 1 received, 66% packet loss, time 2001ms
rtt min/avg/max/mdev = 14.090/14.090/14.090/0.000 ms
$ ping -c3 www.ubuntu.com
PING www.ubuntu.com (91.189.89.103) 56(84) bytes of data.
64 bytes from www-ubuntu-com.privet.canonical.com (91.189.89.103): icmp_seq=1 ttl=55 time=41.7 ms
64 bytes from www-ubuntu-com.privet.canonical.com (91.189.89.103): icmp_seq=2 ttl=55 time=35.9 ms
64 bytes from www-ubuntu-com.privet.canonical.com (91.189.89.103): icmp_seq=3 ttl=55 time=46.6 ms


--- www.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 35.948/41.454/46.698/4.395 ms

```

---

### Post by chili555 on 2018-11-27
When it is *not *working, please run:```
dmesg | grep -e ath -e wlp
```Copy and paste it into a text document, hook up the ethernet and post it here.

---

### Post by dadaisnotdead on 2018-11-27
Here's the response I got with no internet:

```

[   25.223330] ath5k 0000:00:06.0: enabling device (0010 -> 0012)
[   25.223602] ath5k 0000:00:06.0: registered as 'phy0'
[   26.564144] ath: EEPROM regdomain: 0x30
[   26.564148] ath: EEPROM indicates we should expect a direct regpair map
[   26.564151] ath: Country alpha2 being used: AM
[   26.564152] ath: Regpair used: 0x30
[   26.626930] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   26.656225] ath5k 0000:00:06.0 wlp0s6: renamed from wlan0
[   34.009888] IPv6: ADDRCONF(NETDEV_UP): wlp0s6: link is not ready
[   34.025211] IPv6: ADDRCONF(NETDEV_UP): wlp0s6: link is not ready
[   34.200902] IPv6: ADDRCONF(NETDEV_UP): wlp0s6: link is not ready
[   36.532308] wlp0s6: authenticate with ac:22:05:7a:38:64
[   36.539696] wlp0s6: send auth to ac:22:05:7a:38:64 (try 1/3)
[   36.655474] wlp0s6: authenticated
[   36.656001] wlp0s6: associating with AP with corrupt probe response
[   36.657264] wlp0s6: associate with ac:22:05:7a:38:64 (try 1/3)
[   36.680186] wlp0s6: RX AssocResp from ac:22:05:7a:38:64 (capab=0x411 status=0 aid=1)
[   36.680326] wlp0s6: associated
[   36.928101] IPv6: ADDRCONF(NETDEV_CHANGE): wlp0s6: link becomes ready

```

---

### Post by chili555 on 2018-11-27
> wlp0s6: associating with AP with corrupt probe responseVery interesting. Is your router set to WPA2-AES only and not mixed mode and certainly not TKIP? Is it set to a fixed channel, not autoselect?

---

### Post by dadaisnotdead on 2018-11-28
Yes, it is set to WPA2 only with AES. I made a screenshot
[IMG]https://imgur.com/4PRYD2t[/IMG][IMG]https://i.imgur.com/4PRYD2t.png[/IMG]

---

