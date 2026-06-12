---
title: "wifi stopped working after update to 18.10: wlp3s0: link is not ready"
date: 2019-03-17
forum: Networking &amp; Wireless
---

### Post by spammerslammer on 2019-03-17
Hi there,

I updated from Kubuntu 18.04 to 18.10 on my Thinkpad T450s yesterday. Wifi worked all day. But when I switched on my laptop again this morning, wifi had stopped working. What can I do?

I can see the connections in the network manager, but when I try  them, it says "waiting for authorization" forever. Any ideas what I  could try?

Here is [all sorts of output from the terminal]("https://paste.ubuntuusers.de/423857/"). I think the most relevant parts are at the end, where dmesg says: "IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready"

Thanks!

---

### Post by jeremy31 on 2019-03-17
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
See if wifi works, then try
```
sudo iwconfig wlp3s0 power off
sudo iwconfig wlp3s0 txpower 18
```
Then see if it works

---

### Post by spammerslammer on 2019-03-17
Thanks. It didn't make any difference.

After the first two lines, the network manager symbol disappeared. Rebooted, checked if it worked. Same as before. Then tried the next two lines. No change. Any other ideas?

---

### Post by spammerslammer on 2019-03-17
I also get a message in the notification area: "Wireless: no secrets were provided."

---

### Post by jeremy31 on 2019-03-17
See the wireless script link in my signature and post results

---

### Post by spammerslammer on 2019-03-17
Thanks. Results here: [http://paste.ubuntu.com/p/DZRj5fMTPH/](http://paste.ubuntu.com/p/DZRj5fMTPH/)

---

### Post by jeremy31 on 2019-03-17
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
sudo iwconfig wlp3s0 power off
sudo ifconfig wlp3s0 up
sudo iwconfig wlp3s0 txpower 20
```

Anything now

---

### Post by spammerslammer on 2019-03-17
That didn't make any difference, unfortunately.

---

### Post by jeremy31 on 2019-03-17
See if it works after unplugging ethernet cable

---

### Post by spammerslammer on 2019-03-17
Nope. Not after unplugging the cable, not after executing those commands again, and not after rebooting again.

---

### Post by jeremy31 on 2019-03-17
Does your iwconfig results still show power management on?  ifconfig show interface down?  The tx-power from iwconfig showing 0 is normal for the interface being down and it is likely the reason you can't connect to wifi

---

### Post by spammerslammer on 2019-03-17
Here's the output:
```

philip@philip-ThinkPad-T450s:~/Desktop$ iwconfig
lo        no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
enp0s25   no wireless extensions.

```

---

### Post by spammerslammer on 2019-03-17
Time to install a new operating system? :( It's a pity because I otherwise like it.

---

