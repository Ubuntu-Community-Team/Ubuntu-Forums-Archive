---
title: "Ubuntu 20.04 upgraded some network-manager packages, now problems are ensuing"
date: 2020-07-12
forum: Networking &amp; Wireless
---

### Post by Mike3 on 2020-07-12
First of all, these issues only started on 20.04 after a recent network-manager upgrade (and the related components such as network-manager-gnome) and this is a laptop, HP envy m7-n101dx running 20.04. I have tried disabling power management on the device via two commands (I didn't write them down) given to me from someone on IRC. They essentially disabled power management for Wireless. Before that I was getting disconnected and had to manually reconnect to get back online. At least it's not permanent or requiring a reboot every time. I ran the command sudo lshw -C network and I apparently have an Intel Wireless 7265 card. I know these are plaguing users of the forums with issues related to their power management. But the real issue is recently it disconnected right after startup. Literally seconds after logging and directly from cold boot and the boot screen, instant disconnect. These issues have never happened on older releases or packages on this laptop. And it was gone for a while, so I was hoping it was done for. Any ideas what is going on and how to fix it? For a more detailed look at the command output, see below:

Output of sudo lshw -C network: [https://paste.ubuntu.com/p/B5dFjqJhh6/](https://paste.ubuntu.com/p/B5dFjqJhh6/)

---

### Post by praseodym on 2020-07-14
Lets try

```
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by Mike3 on 2020-07-28
Sorry for the delay. I asked on AskUbuntu and it seems fixed before I even looked here. Now a week with no disconnect. I've linked [here]("https://askubuntu.com/questions/1258738/ubuntu-20-04-upgraded-some-network-manager-packages-now-problems-are-ensuing") for those who may find it helpful.

---

### Post by Mike3 on 2020-08-15
So a month and the solution posted in the link above still holds water. Thanks for the help here, guys. Can consider this issue resolved.

---

