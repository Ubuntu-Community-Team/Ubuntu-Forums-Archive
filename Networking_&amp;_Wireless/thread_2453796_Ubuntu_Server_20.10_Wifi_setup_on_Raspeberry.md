---
title: "Ubuntu Server 20.10 Wifi setup on Raspeberry"
date: 2020-11-17
forum: Networking &amp; Wireless
---

### Post by lseabra2 on 2020-11-17
[COLOR=#555555][FONT=Roboto]Hi,[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]I'm following the steps on [/FONT][/COLOR][https://discourse.ubuntu.com/t/how-to-i ... y-pi/14660]("https://discourse.ubuntu.com/t/how-to-install-ubuntu-server-on-your-raspberry-pi/14660")[COLOR=#555555][FONT=Roboto] to setup Ubuntu Server 20.10 on a Raspbery Pi 4.[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]I set up the wifi details as indicated on step "Getting setup with Wi-Fi" but I can't get it to work.[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]The file /etc/netplan/50-cloud-init.yaml is correctly generated but on running "sudo netplan --debug generate" I get the message "NetworkManager: definition wlan0 is not for us (backend1)".[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]Any ideas about what's going on?

Thanks![/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-11-17
"wlan0" is probably NOT the correct name.

---

### Post by slickymaster on 2020-11-17
Thread moved to **Networking & Wireless** for a better fit.

---

### Post by hartrumpf on 2020-11-18
The linked article is for an older version and probably not up to date for 20.10.

If you can use the desktop image (ubuntu-20.10-preinstalled-desktop-arm64+raspi.img), I can recommend it because the installer configured WLAN without any problems.

---

### Post by chili555 on 2020-11-18
> **lseabra2 said:**
> [COLOR=#555555][FONT=Roboto]Hi,[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]I'm following the steps on [/FONT][/COLOR][https://discourse.ubuntu.com/t/how-to-i ... y-pi/14660]("https://discourse.ubuntu.com/t/how-to-install-ubuntu-server-on-your-raspberry-pi/14660")[COLOR=#555555][FONT=Roboto] to setup Ubuntu Server 20.10 on a Raspbery Pi 4.[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]I set up the wifi details as indicated on step "Getting setup with Wi-Fi" but I can't get it to work.[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]The file /etc/netplan/50-cloud-init.yaml is correctly generated but on running "sudo netplan --debug generate" I get the message "NetworkManager: definition wlan0 is not for us (backend1)".[/FONT][/COLOR]

[COLOR=#555555][FONT=Roboto]Any ideas about what's going on?

Thanks![/FONT][/COLOR]May we see the exact netplan yaml file?

Is Network Manager actually installed?

```
sudo dpkg -s network-manager | grep Status

```If it is installed, it will be easier to manage the wireless with NM than netplan.

Also, please show us:

```
ip addr show
```

---

