---
title: "Network Startup Script MAC Address 16.04"
date: 2017-02-21
forum: Networking &amp; Wireless
---

### Post by bluevalley2 on 2017-02-21
I am trying to run a startup script, in Ubuntu 16.04, that randomizes the MAC address at startup. I followed the instructions here [https://ubuntuforums.org/showthread.php?t=1724802](https://ubuntuforums.org/showthread.php?t=1724802) but the startup script is not changing the address.

The MAC address DOES change when I enter the commands in the terminal (using [FONT=courier new]sudo[/FONT]), so it must be something about doing it while booting. I did chmod and update-rc.d on the file and I have made other startup scripts that work fine.

I used the example script provided and changed the device names to reflect those of my comp.

```

#!/bin/bash

### BEGIN INIT INFO
# Provides:          macchanger
# Required-Start:    $network $syslog
# Required-Stop:     $network $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Changes the MAC address at boot time.
# Description:       Changes the ethernet and wireless cards MAC addresses
#                    that begins with a real manufacturers MAC (the first 3
#                    segments) and randomize the next 3 segments. 
### END INIT INFO


# Disable the network devices
ifconfig eth0 down
ifconfig wlan0 down


# Spoof the mac addresses
/usr/bin/macchanger -r eth0
/usr/bin/macchanger -e wlan0


# Re-enable the devices
ifconfig eth0 up
```


Thank you.

---

### Post by DuckHook on 2017-02-22
Welcome to the forums, bluevalley2.

In computing terms, the thread you are using is ancient and its instructions are obsolete. init.d is a System V methodology. Since then, Ubuntu has adopted and dropped Upstart and is now on to systemd. The following website provides a good explanation of their differences: [https://linuxjourney.com](https://linuxjourney.com)

I am not knowledgeable enough in init magic to be able to give you any technical help. You will have to read up on systemd startup scripting to script what you want to do on systemd. However, your post is a good example of why old threads should be not followed without a whole lot of current verification and parallel investigation.

---

### Post by bluevalley2 on 2017-03-01
-


I got some help from the great linuxbabe.com.


-
> As noted in the Ubuntu Forum guide, Network Manager resets changes made by macchnager. Did you know that as of Network Manager 1.4, you can generate a random MAC address upon each connection?

Ubuntu 16.04 has Network Manager 1.2 unfortunately. You can replace it with wicd. To change MAC address at startup, you can create a systemd service file.

sudo nano /etc/systemd/system/macspoof.service

Put the following text into the file. Replace %i with your network interface name.

[Unit]
Description=macchanger on %i
Wants=network-pre.target
Before=network-pre.target
BindsTo=sys-subsystem-net-devices-%i.device
After=sys-subsystem-net-devices-%i.device

[Service]
ExecStart=/usr/bin/macchanger -e %i
Type=oneshot

[Install]
WantedBy=multi-user.target

Save and close the file. Then enable this service.

sudo systemctl enable macspoof.service

Restart your computer and you will have a spoofed MAC address.

I hope this helps someone else.


-

---

