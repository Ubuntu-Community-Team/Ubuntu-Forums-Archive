---
title: "Share Sprint EVDO Internet"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by acorn22 on 2008-05-25
I have a Sprint U727 EVDO card working on a Hardy install (finally) and am trying to share this to other computers with my ethernet port through a router.

The only way I could get my EVDO card to work for internet is to unplug my ethernet cord. The first step is to figure out how to have both plugged in at once and still get internet. Then, through my rounter I have to find a way to share internet to other computers on the network (winxp and/or linux).

Any ideas of where I should start?

Thanks

---

### Post by Ogonzz on 2008-05-28
I'm also trying to find a solution to this problem...

I'd like to create a network and share the connection.

---

### Post by Wej on 2008-05-28
> **acorn22 said:**
> I have a Sprint U727 EVDO card working on a Hardy install (finally) and am trying to share this to other computers with my ethernet port through a router.

The only way I could get my EVDO card to work for internet is to unplug my ethernet cord. The first step is to figure out how to have both plugged in at once and still get internet. Then, through my rounter I have to find a way to share internet to other computers on the network (winxp and/or linux).

Any ideas of where I should start?

Thanks

May I inquire as to how you were able to the U727 working? I can't find any recent documentation. I have determined that the airprime driver in my kernel already supports the device, I just can't get a ppp0 device on my system.

As for your problem, you are probably just having a routing issue. You need to set the default gateway for your system with the U727 card to be the gateway that the EVDO connection returns.

---

### Post by acorn22 on 2008-06-04
to get it working I basically just followed the instructions sprint offers at sprint.com/downloads (I think) in a PDF. One thing to note is that I used wvdail and it worked much better. Also, it took about a week to find out that when you do the eject command for the u27 device on my computer you need to use "sd0" as the device to ecject (not cd0).

Here's my wvdial.conf ```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 4608800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
IDSN = 0
Modem Type = USB Modem
Phone = #777
Username = ''
Password = ''
Carrier Check = no
Stupid Mode = yes
New PPPD = yes

```

---

### Post by nowhere@cox.net on 2008-06-05
I wrote a quick script to connect and disconnect the modem. You should follow the above advice to set up wvdial. I then added a custom launcher to the gnome panel and I added "Network Monitor 2.12.1" to the notification area. This little app monitors ppp and indicates when you are connected.

toggle_evdo.sh
```
#!/bin/bash

executable="wvdial"
device="/dev/sr1"
drive="/media/MICROSD"

string=$(ps -ef | grep "${executable}" | grep -v grep)
 
if [[ ${string} = "" ]]
then
#    echo "not running"
    eject ${device} 2>/dev/null 
    sleep 5
    wvdial
else
#    echo "running"
    pid_to_kill=$(ps -ef | grep "${executable}" | grep -v grep | awk '{print $2}')
    kill ${pid_to_kill}  2>/dev/null
    eject ${drive} 2>/dev/null 
fi

exit 0
```

Just change the mount points for the devices and off you go!

In case you don't know, this device has a built in CDROM emulation that must mount then be unmounted in order for the modem to trigger and be recognized. In gutsy, I had to recompile the airprime driver with the device setting for the U727 but they are loaded OOB in Hardy.

Hope this helps someone!

---

