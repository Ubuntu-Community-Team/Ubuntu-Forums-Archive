---
title: "No upload speed using Qualcomm Atheros QCA6174 in ubuntu 17.10."
date: 2019-01-28
forum: Networking &amp; Wireless
---

### Post by dmeuser on 2019-01-28
I recently bought a new Dell XPS 9560 and I am using it with a dualboot  with ubuntu 17.10 and Win10. Everything works fine except of the upload  speed in my home network.

Using Win10 I get something like 4.5 Mbit/s for the upload. For ubuntu I  only get values below 0.2 Mbit/s (measured with speedtest-cli).  Speedtest by Ookla is not even able to measure any upload speed, even  though the download speed is fine.

This problem only occurs in my home network while at the university network and other networks everything works fine.

The requested script output can be found here: [https://paste.ubuntu.com/p/XjS8RgY3Js/](https://paste.ubuntu.com/p/XjS8RgY3Js/)

---

### Post by howefield on 2019-01-28
May not make a difference to the actual issue but as 17.10 has reached end of life, best to install a currently supported release and see if the issue remains.

---

### Post by dmeuser on 2019-01-28
I am aware that 17.10 has reach the end of its lifetime, but I was following the respin for the my dell model: [https://github.com/stockmind/dell-xps-9560-ubuntu-respin](https://github.com/stockmind/dell-xps-9560-ubuntu-respin)
This seems to be not stable for 18.04 so I would like to stick to 17.10.

---

### Post by dmeuser on 2019-01-28
I just did a fresh install of ubuntu 18.04 as you suggested. At first the upload speed looked quite promising (about 5 Mbit/s).
But after a while the same problem occurs as described above. I really don know what to do.

---

### Post by jeremy31 on 2019-01-28
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
Those cards don't like power management being enabled

---

### Post by dmeuser on 2019-01-29
I solved the problem following the fix in [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1520343/comments/22](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1520343/comments/22)

The powermanagemet is still enable.

---

