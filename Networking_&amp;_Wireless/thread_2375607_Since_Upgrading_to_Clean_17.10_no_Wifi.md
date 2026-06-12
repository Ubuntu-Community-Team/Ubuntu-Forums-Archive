---
title: "Since Upgrading to Clean 17.10 no Wifi"
date: 2017-10-25
forum: Networking &amp; Wireless
---

### Post by Zoot_Nerper on 2017-10-25
Hi,

I had wifi with 17.04, but not after a clean install of Ubuntu 17.10 with all updates and the Intel microcode additional driver installed. I have a Lenovo Ideapad Miix
510-121KB

If I tried:

```
sudo rm /etc/resolv.conf 
sudo ln -s /run/resolvconf/resolv.conf /etc/resolv.conf
sudo resolvconf -u
```

After the first two I lose my wired LAN, then for the third it said resolvconf did not exist. 

Reinstalled clean 17.10. Installed updates and Intel driver. Installed resolvconf. Ran the three lines above and a restart of NetworkManager and wifi was on, I could see local networks, but I could not connect to mine. Restarted the router and still no connect.

After a reboot, no wifi and it will not turn on. Ran the commands again and it still will not turn on.

I just tried this:

```
sudo dpkg-reconfigure resolvconf
```

This worked, in so much as the wifi was on but couldn't connect. Since a power-off, the wifi will not turn on.

I ran the scripts in [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) to get the wifi information and the link to the pastebin is below.

Early on in the logs it reports that some items are hard off (I can't make much sense of this a WAN is off and on in two places). The wifi is enabled in BIOS and my aircraft mode button does nothing (and never has). For example, no matter how many times I press it or for how long, my Bluetooth mouse stays connected.

[http://paste.ubuntu.com/25820373/](http://paste.ubuntu.com/25820373/)

Any additional suggestions?

-- Zoot

---

### Post by chili555 on 2017-10-26
Does your airplane mode switch or, more importantly, your wireless begin to work if you do:```
sudo modprobe -r ideapad-laptop
```If so, we'll blacklist the module and make it permanent.

---

### Post by Zoot_Nerper on 2017-10-26
It made all the difference. Wifi is turned on and I can see local networks and I can connect to them!!. The Aeroplane Mode key does nothing (not bothered about this) but I can switch Wifi off/on in the settings.

How can I make this permanent?

Thank you so much for your reply.   :)

---

### Post by Hadaka on 2017-10-26
Hi, to make it permanent,please copy and paste..
```
sudo modprobe -rf ideapad-laptop
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
boot and test wireless

---

### Post by Zoot_Nerper on 2017-10-27
All working after reboot. Brilliant!   :)

Thank you very much chilli555 and Hadaka

---

