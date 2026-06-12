---
title: "Wi-Fi not working"
date: 2018-07-25
forum: Networking &amp; Wireless
---

### Post by robpitt on 2018-07-25
It worked during the installer but once I got Ubuntu installed the network shows up in not settings but if I click on it after some time I get a pop-up at the top of the screen saying "Activation of network connection failed".

nmcli d connect said:
Error: Connection activation failed: (53) The Wi-Fi network could be found.

---

### Post by NM5TF on 2018-07-25
please post the output of

```
nmcli c
```

 and then the output of

```
ip link
```

tommy

---

### Post by robpitt on 2018-07-25
I will do this in a couple of days time my keyboard decided to die I'm waiting on a replacement. It's hard for me to post command outputs without the Internet I have to type them with my mobile phone.

---

### Post by robpitt on 2018-07-27
nmcli c listed my wifi network and wired connection 1, ip link said (relevant adapter)
```
 
3: wlx0013ef410462: <NO-CARRIER, BROADCAST, MULTICAST, UP> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 00:13:ef:41:04:62 brd ff:ff:ff:ff:ff:ff

```

---

### Post by robpitt on 2018-07-27
It's been a long time since I used Linux, I noticed dhcpcd isn't installed. Could this be it?

---

### Post by NM5TF on 2018-07-27
> **robpitt said:**
> It's been a long time since I used Linux, I noticed dhcpcd isn't installed. Could this be it?

quite possibly....some info here [http://manpages.ubuntu.com/manpages/trusty/man8/dhcpcd5.8.html]("http://manpages.ubuntu.com/manpages/trusty/man8/dhcpcd5.8.html")

your wireless interface has NO CARRIER so dhcpcd will not connect.....

you say dhcpcd is NOT installed ???

re-install it if needed...

then try this:

```
ip link set wlx0013ef410462 up
```

more info here  [https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting.html.en]("https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting.html.en")

good luck

tommy

---

### Post by coffeefiend on 2018-07-28
If all else fails, just buy a wifi dongle. My laptop has a Realtek wireless card and is not recognized by Ubuntu. I have researched and asked questions here and nothing I have tried has been successful. So it looks like I am sticking with the dongle.

---

### Post by NM5TF on 2018-07-28
that is a viable option of course.....

it depends if the OP wants to learn about Linux networking, or just wants to take
the easy way out to get online....

up to him of course....

tommy

---

### Post by coffeefiend on 2018-07-29
Oh trust me, it definitely wasn't the easy way out for me. Like I said, I researched and tried all suggestions that came my way and nothing has worked so far. In the meantime, I have a machine that can't get on the Internet with the onboard WiFi card, so I did what I had to do until a better fix is found.

---

### Post by jeremy31 on 2018-07-30
Moved to networking

---

### Post by jeremy31 on 2018-07-30
> **coffeefiend said:**
> If all else fails, just buy a wifi dongle. My laptop has a Realtek wireless card and is not recognized by Ubuntu. I have researched and asked questions here and nothing I have tried has been successful. So it looks like I am sticking with the dongle.

```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi
```

Reboot, check EFI/BIOS to make sure Secure Boot is off, HP laptops might also have just 1 antenna wire so 
```
sudo modprobe -r rtl8723de
sudo modprobe rtl8723de ant_sel=1
iwlist scan | egrep -i 'SSID|level'
sudo modprobe -r rtl8723de
sudo modprobe rtl8723de ant_sel=2
iwlist scan | egrep -i 'SSID|level'
```

See if there is any difference between iwlist scan results for the ant_sel parameter

---

### Post by coffeefiend on 2018-07-30
Thanks, Jeremy! I'm out to sea for two weeks, but will give that a try when I get home.

---

