---
title: "Wifi speeds much slower than on windows"
date: 2017-10-11
forum: Networking &amp; Wireless
---

### Post by redler7 on 2017-10-11
Hello, I am a brand new ubuntu user and so far I love it, with one exception. My wifi connection is pretty terrible in proportion to what I got before I switched from windows. On a solid ethernet connection I get around 500 down, 50 up, on both ubuntu and windows, and on the regular wifi connection I would get around 250/50 on windows.

On ubuntu so far I have gotten speeds around 1.5 down 1 up over wifi which is terrible compared to before. To clarify my router is a duel band 2.4ghz/5ghz router, so there are two separate wifi channels to connect to and ubuntu only picks up the 2.4ghz one, which if I recall, I got the 5ghz one on windows.

Like I said, I am new to linux, so if I need to provide you with information from the terminal I will provide you with it as fast as possible.

Network controller: Ralink corp. RT5390R 802.11bgn PCIe Wireless Network Adapter

Thank you!

---

### Post by TheFu on 2017-10-11
There is a wireless-info script in these forums.  Please find it, run it, and post the link to the generated output for help. [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) has more details, if you need them.

5Ghz doesn't work well through obstructions, BTW.  I'm assuming the windows estimates are from the exact same location.  As you know, wired ethernet is always better to use, when available.  Better for many, many, reasons, not just performance, but security too.

---

### Post by redler7 on 2017-10-11
Yes, I am using the laptop in the same exact location(s), and the only reason I am not using an Ethernet connection is because this laptop is mainly used off of a desk area and more for casual use/coding.

Here is the wireless-info file that was generated through the script you asked for, [https://pastebin.com/Bv0MufTJ](https://pastebin.com/Bv0MufTJ)

Thanks for the help!

---

### Post by praseodym on 2017-10-11
Lets try
```

sudo iwconfig wlo1 power off
```
Try channel 11 in your router and
```

echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```

---

### Post by jeremy31 on 2017-10-11
I would try ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
systemctl restart network-manager.service
```
To disable wifi power management as network manager can enable it without changing this.  If you still have issues, try disabling Wireless-N on the wifi router as chili555 has had some luck with that

---

### Post by redler7 on 2017-10-11
Thank you Jeremy and praseodym for the help, I tired both of your solutions and afterwards I do feel the connection is much stronger as websites are much more responsive and while watching livestreams like twitch/netflix, it doesn't buffer as much as before.

The speedtests show a much better 6-9 mbps, which is still much less than on windows, but it is still much better than before so there is much benefit from your fixes. For you second piece of advice Jeremy, how would I go about disabling Wireless-N, and what is that exactly? 

If anyone has any ideas to further fix my issue, I would be very thankful.

---

### Post by jeremy31 on 2017-10-12
Did you also use praseodym's advice?

---

### Post by redler7 on 2017-10-12
yes

---

### Post by denismc on 2017-10-12
Forgive me if this is dumb but have you disabled ipv6 and test the wifi speeds:

```
sudo su
echo "#disable ipv6" >> /etc/sysctl.conf
echo "net.ipv6.conf.all.disable_ipv6 = 1" >> /etc/sysctl.conf
echo "net.ipv6.conf.default.disable_ipv6 = 1" >> /etc/sysctl.conf
echo "net.ipv6.conf.lo.disable_ipv6 = 1" >> /etc/sysctl.conf
```

---

