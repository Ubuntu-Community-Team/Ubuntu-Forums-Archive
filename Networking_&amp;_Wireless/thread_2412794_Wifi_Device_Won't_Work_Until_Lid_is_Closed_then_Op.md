---
title: "Wifi Device Won't Work Until Lid is Closed then Opened"
date: 2019-02-17
forum: Networking &amp; Wireless
---

### Post by jnabasny on 2019-02-17
I recently did a fresh install of Lubuntu on an old MacBook Pro from 2010. The wifi wasn't working, so I followed the instructions on the top answer here and was able to get it up and running under certain conditions:

[https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

After installing the driver, I enabled it using the Driver Manager GUI tool and wifi seemed to work. When I restarted, however, the wifi wouldn't work (could not even search for networks) until I closed and then opened the laptop lid. Magically, the wifi was enabled again and automatically connected to my last wifi network. This is a workable situation, but very inconvenient. I'm wondering if I'm overlooking an easy fix to this problem.

Here is my wireless info when NOT working: [https://pastebin.com/nBmp8YUs](https://pastebin.com/nBmp8YUs)
Here is my wireless info when working: [https://pastebin.com/hq2BMX2t](https://pastebin.com/hq2BMX2t)

---

### Post by praseodym on 2019-02-17
SecureBoot is turned off?

---

### Post by jnabasny on 2019-02-17
> **praseodym said:**
> SecureBoot is turned off?

Yes, MacBook Pro's made prior to 2018 do not support SecureBoot.

---

### Post by praseodym on 2019-02-17
Lets try
```

sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by jnabasny on 2019-02-17
> **praseodym said:**
> Lets try
```

sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

I tried it after a reboot and there was no change.

---

### Post by praseodym on 2019-02-17
Lets try a new systemd-unit
```

sudo touch /etc/systemd/system/wifi-resume.service
gksudo gedit /etc/systemd/system/wifi-resume.service
```
Add these lines

```
[Unit]
Description=Restart networkmanager at resume
After=suspend.target
After=hibernate.target
After=hybrid-sleep.target

[Service]
Type=oneshot
ExecStart=/bin/systemctl restart network-manager.service

[Install]
WantedBy=suspend.target
WantedBy=hibernate.target
WantedBy=hybrid-sleep.target
```

save, close the editor and try it again

---

### Post by jnabasny on 2019-02-17
> **praseodym said:**
> Lets try a new systemd-unit
```

sudo touch /etc/systemd/system/wifi-resume.service
gksudo gedit /etc/systemd/system/wifi-resume.service
```
Add these lines

```
[Unit]
Description=Restart networkmanager at resume
After=suspend.target
After=hibernate.target
After=hybrid-sleep.target

[Service]
Type=oneshot
ExecStart=/bin/systemctl restart network-manager.service

[Install]
WantedBy=suspend.target
WantedBy=hibernate.target
WantedBy=hybrid-sleep.target
```

save, close the editor and try it again

Unfortunately this has also not produced any change. :(

---

### Post by praseodym on 2019-02-17
Ok, revert it:

```
sudo rm /etc/systemd/system/wifi-resume.service
```
Lets try
```

sudo touch /lib/systemd/system-sleep/wakeon_suspend.sh
gksudo gedit /lib/systemd/system-sleep/wakeon_suspend.sh
```
Add these lines
```

#!/bin/sh
case $1/$2 in
  pre/*)
    echo "activate $2..."


     /bin/systemctl stop network-manager.service
      /sbin/modprobe -rf wl

    ;;
  post/*)
    echo "wakeup from $2..."

     /sbin/modprobe wl

       /bin/systemctl start network-manager.service
    ;;
esac
```
Save, close the editor and run

```
sudo chmod a+x /lib/systemd/system-sleep/wakeon_suspend.sh
```

---

### Post by jnabasny on 2019-02-17
Still no change after that. After reboot, I even tried to run the script manually and it didn't work. 

If I use a command to suspend and then wake (such as: sudo rtcwake -m mem -s 5), then the wifi will start up. If all else fails, I can just run this when the user logs in, but I realize it's a very inelegant solution and delays the startup. Not to mention it doesn't solve whatever the problem is.

---

