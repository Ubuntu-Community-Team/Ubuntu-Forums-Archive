---
title: "Unstable wifi - 14.10 - intel centrino N2200"
date: 2014-12-30
forum: Networking &amp; Wireless
---

### Post by immanuelb on 2014-12-30
My wifi is very unstable and slow. It disconnects frequently. Seems it is a very common problem from the threads here. I attached is the wireless-info.txt. Please help me fix this so I can fully transition to Ubuntu.
Thank you.

[ATTACH=CONFIG]258898[/ATTACH]

---

### Post by praseodym on 2014-12-30
Disable the N-mode and the queue of the driver:

```
echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```
Reboot. This looks also weird:
> ```

                   IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : [COLOR="#FF0000"]TKIP[/COLOR] CCMP
                        Authentication Suites (1) : PSK
```
Change to pure WPA2-AES ([COLOR="#FF0000"]CCMP[/COLOR]) in your router interface, check the manual.

---

### Post by immanuelb on 2014-12-30
Did that but still problem persists. It has disconnected twice since your post and this reply.

Ran the script again after your suggestion.

[ATTACH=CONFIG]258900[/ATTACH]

---

### Post by praseodym on 2014-12-30
[ipv6] method=auto

"Ignore" IPv6 in the network manager profile

---

### Post by immanuelb on 2014-12-31
Done that also but it still keeps disconnecting.

---

### Post by Maximilian_F._Blas on 2014-12-31
are you running on HP or Lenovo. I have a similar problem in a thread of mine but mine is actually hard locked off.

---

### Post by immanuelb on 2014-12-31
Lenovo Y480. What do you mean by hard locked off? No internet connection at all or not able to change settings of some sort?

---

### Post by Maximilian_F._Blas on 2014-12-31
It's a driver bug from lenovo. I had your symptoms before it happened. Get that computer off your hands ASAP hundreds have been affected. It's very hard to fix and quite daunting. It's been days and I'm still working on it. If there's a warranty USE IT NOW.

---

### Post by Maximilian_F._Blas on 2014-12-31
And don't ever buy lenovo or hp. They don't have a clue what they are doing to be honest.

---

### Post by jeremy31 on 2014-12-31
> **Maximilian_F._Blas said:**
> It's a driver bug from lenovo. I had your symptoms before it happened. Get that computer off your hands ASAP hundreds have been affected. It's very hard to fix and quite daunting. It's been days and I'm still working on it. If there's a warranty USE IT NOW.

Most of the hard block issues can be solved by blacklisting ideapad_laptop on the models that are affected.  You can check with ```
sudo modprobe -r ideapad_laptop
``````
sudo rfkill unblock all
```

I am using a Lenovo G710 and I don't have any issue with the hard block even with ideapad_laptop loaded

immanuelb: the last wireless-info file still shows your router using mixed mode encryption (CCMP+TKIP), it would be nice to see if conditions improve with CCMP only

---

### Post by immanuelb on 2015-01-01
Yeah I did change it. I ran the code again and I see only CCMP. I still have the disconnects all the time.

[ATTACH=CONFIG]258914[/ATTACH][HTML][/HTML]

---

### Post by praseodym on 2015-01-01
Lets try Wicd instead of the network manager

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Choose **wlan0** as interface name and **wext** as driver

---

