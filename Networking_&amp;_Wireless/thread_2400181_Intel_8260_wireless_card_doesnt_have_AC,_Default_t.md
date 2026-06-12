---
title: "Intel 8260 wireless card doesnt have AC, Default to A or G"
date: 2018-09-03
forum: Networking &amp; Wireless
---

### Post by gido5731 on 2018-09-03
I am unable to use AC wireless with my drivers. I can confirm because my router reports me as using a or g (varies on each negotiation) and because iw list|grep -i vht returns empty. I did turn off `n` because of the well documented problem of instability.

---

### Post by jeremy31 on 2018-09-03
If you changed iwlwifi.conf to add 11n_disable=1 change that to 11n_disable=8

---

### Post by gido5731 on 2018-09-03
Now it says its AC capable (vht is there) but Im unable to connect to my wireless network (wpa2) with network manager (says device isnt ready) or ifup...

---

### Post by jeremy31 on 2018-09-03
See the wireless script link in my signature and post results

---

### Post by gido5731 on 2018-09-03
[http://paste.ubuntu.com/p/QDH25SkRFS/](http://paste.ubuntu.com/p/QDH25SkRFS/)

---

### Post by jeremy31 on 2018-09-04
Do ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot, that command should keep wifi power management disabled for the Intel

---

### Post by gido5731 on 2018-09-10
Nope, back to disconnecting issues, and although the guy who setup my wifi isnt here I dont think im on AC (~40 megs from local machine)

---

### Post by chili555 on 2018-09-11
Wow! You have two wireless devices with no less than three probably conflicting drivers. I frankly don't understand how this even works, much less how you can tell what the Intel is doing or not doing.

Please clarify.


Is AS701.NET a dual band 2.4 and 5 GHz router set to the awful auto channel select? If it were my router, I'd seperate the bands to 2.4 GHz and 5 GHz and rename the 5 GHz segment, something like AS701.NET_5. Ask your Intel to connect to the 5 GHz segment only and I'm pretty confident that you'll get AC speeds. My Intel 7260 certainly does.

---

### Post by gido5731 on 2018-09-14
Yes, it is dual band, Im not sure why but my `networking guy` is very  persistent on no splitting them. at that time yes I did have a second  wireless card (usb realtek one, n speeds only) so I can connect and  stuff. Also I still am having disconnecting issues (tested with just the  intel card.)

---

### Post by chili555 on 2018-09-14
With the USB wireless detached, please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi disable_11ac=Y
```Is the connection stable? If so, we'll make it persistent.

Your Realtek wireless has two conflicting drivers. You will get better performance with one of them blacklisted.```
sudo -i
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit
```I wouldn't use the USB and the internal both at the same time.

---

