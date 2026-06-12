---
title: "Wifi network disconnects and disappears after some time"
date: 2019-09-30
forum: Networking &amp; Wireless
---

### Post by adlerhn on 2019-09-30
I am using my Android mobile as a wifi mobile hotspot to connect to the Internet.

Once I log in, the computer automatically connects to the mobile hotspot. This works fine for minutes or hours. But at some indeterminate point in time, the computer disconnects from the wifi and at some point the wifi disappears altogether from the list of networks.

Turning the wifi off and on, or restarting my phone doesn't help. The only thing I can do at that time is to restart my computer, and then everything works, for a few minutes or hours.

I noticed this issue a few weeks ago. At that time I was on Ubuntu 19.04 (now 19.10 beta), but the issue has been present even before the upgrade.

For more information I have attached the wireless-info files when the computer is successfully connected to the wireless network "AndroidAP" ([ATTACH]284113[/ATTACH]) and when it cannot see the network ([ATTACH]284114[/ATTACH]).

How can I debug what the issue is, or somehow restart the wireless subsystem without having to restart the whole computer?

---

### Post by jeremy31 on 2019-09-30
Try ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
That will disable wifi power management

---

### Post by adlerhn on 2019-10-01
Thanks. With powersave 2 and 1 the issue occurred again. I have changed it to powersave 0 and it seems to be working fine for now. I will keep checking. [Update: no, it failed again]

---

### Post by Skaperen on 2019-10-01
i've had a similar issue.  i do not know if the cause is the same but the effect is.  my work-around was to start a background task that pings my server every 30 seconds.  one ping only ... every 30 seconds, and it stays up for days.

---

### Post by adlerhn on 2019-10-30
I have tried with the periodic ping suggested above, and it doesn't help. Every few minutes the connection still drops and I need to restart the system.

I have also tried the following:

```
sudo netplan apply

sudo systemctl restart NetworkManager.service

sudo service network-manager restart

sudo nmcli networking off
sudo nmcli networking on

sudo /etc/init.d/networking restart

sudo /etc/init.d/network-manager restart

sudo ifdown -a
sudo ifup -a
```

But nothing makes a difference. Only after restarting the whole system can I see again the wifi access point and connect to it.

Is there anything I could try next? I'd be happy if I could just execute some command after I lose the connection and not have to restart the whole system.

An issue that requires a restart every few minutes of hours is a big usability issue. There is a bug somewhere, but I don't know on which application should I open it. Network Manager? WPA Supplicant? Linux kernel?

---

### Post by dw1-4 on 2019-10-30
I had a similar experience with different network kinds. I found I need to disable IPv6 in networks not capable to deal with it. Ubuntu Network Manager obviously poisoned the whole system if there was a IPv6 "automatic" setting in environments with no v6. Which was the case in old Ethernet and is the case in wireless tech, unfortunately. 
IPv6 works brilliant with Ubuntu if the whole stuff is v6 capable. I was able to SOLVE the similar problem like yours by just deactivating IPv6 in Network Manager.

---

### Post by adlerhn on 2019-10-30
> **dw1-4 said:**
> I found I need to disable IPv6 in networks not capable to deal with it. Ubuntu Network Manager obviously poisoned the whole system if there was a IPv6 "automatic" setting in environments with no v6. Which was the case in old Ethernet and is the case in wireless tech, unfortunately. 
IPv6 works brilliant with Ubuntu if the whole stuff is v6 capable. I was able to SOLVE the similar problem like yours by just deactivating v6.

Thanks a lot for sharing this piece of advice. I will try it and see if it helps in my case.

---

### Post by adlerhn on 2019-11-02
> **dw1-4 said:**
> I had a similar experience with different network kinds. I found I need to disable IPv6 in networks not capable to deal with it. Ubuntu Network Manager obviously poisoned the whole system if there was a IPv6 "automatic" setting in environments with no v6. Which was the case in old Ethernet and is the case in wireless tech, unfortunately. 
IPv6 works brilliant with Ubuntu if the whole stuff is v6 capable. I was able to SOLVE the similar problem like yours by just deactivating IPv6 in Network Manager.

It appears I have finally been able to solve my issue thanks partly to your advice. In my case, I disabled IPv6, but that didn't made a difference. But that led me to think the issue may be related to specific network parameters.

So finally I changed in my Android phone the wifi hotspot so as to use the 2.4G wifi band (I used to use 5G instead), and now it works perfectly. I haven't had a single disconnect in more than a day, which previously used to happen multiple times per hour.

I still have no idea why was this happening, and there is something wrong in Linux and the network stack or the Intel driver, but at least I am now able to use my computer without having to restart my system all the time.

To everyone in this thread, thanks for your help.

---

