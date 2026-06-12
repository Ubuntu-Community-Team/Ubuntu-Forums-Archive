---
title: "Shutting down wireless manually, is it safe?"
date: 2005-03-30
forum: Networking &amp; Wireless
---

### Post by panabar on 2005-03-30
Hi
This morning while going through powernow deamon scripts, I noticed that there is a wireless script in /etc/acpi/ (wireless.sh) which finds and enables or disables wireless devices.  The only thing it does to disable wireless is  

```

echo -n 3 > state

```

in the wireless devices  power folder ( /sys/class/net/wlan0/device/power/ ).

This could really help me safe power for other applications because I do not connect with wireless, and I can not disable wireless because wireless button on my laptop is useless (somwhere I read that it uses a software rf_kill switch).

Does this shut down the wireless device?
Is is safe to use this to shut down the device?

---

### Post by localzuk on 2005-03-30
[QUOTE=panabar]Hi
This morning while going through powernow deamon scripts, I noticed that there is a wireless script in /etc/acpi/ (wireless.sh) which finds and enables or disables wireless devices.  The only thing it does to disable wireless is  

```

echo -n 3 > state

```

in the wireless devices  power folder ( /sys/class/net/wlan0/device/power/ ).

This could really help me safe power for other applications because I do not connect with wireless, and I can not disable wireless because wireless button on my laptop is useless (somwhere I read that it uses a software rf_kill switch).

Does this shut down the wireless device?
Is is safe to use this to shut down the device?[/QUOTE]
 I am not sure of the command you have posted but to manually shut down the wireless on my laptop I just 'sudo ifdown wlan0'. It seems to do the trick.

---

### Post by panabar on 2005-03-30
Ifdown command does not turn off the wireless device, it just deconfigures the interface (I guess, and I see my wireless light blinking). 

Some laptops have a seperate turn off wireless button which stops the wireless device from sending or recieving signal. I trying to produce this effect of seperate turn off button ( my laptop does not have a seperate turn off button, but a combination of buttons to do this job), but I don't know if the method I use works or not. I just know that issueing this command turns off the wireless light.

Here is the code of wireless.sh which inspired this thread.

```

#!/bin/bash
# Find and enable/disable wireless devices

for DEVICE in /sys/class/net/*; do
    if [ -d $DEVICE/wireless ]; then
# $DEVICE is a wireless device. Check if it's powered on:
        if [ `cat $DEVICE/device/power/state` = 0 ]; then
# It's powered on. Switch it off.
            echo -n 3 > $DEVICE/device/power/state;
        else
# It's powered off. Switch it on.
            echo -n 0 > $DEVICE/device/power/state;
        fi
    fi
done

```

Thank you for replying :)

---

### Post by alastair on 2005-03-30
Yes, shutting this down via this type of operation is fine. The wireless (radio) has a s/w switch sometimes, as designed.

---

### Post by panabar on 2005-03-30
[QUOTE=alastair]Yes, shutting this down via this type of operation is fine. The wireless (radio) has a s/w switch sometimes, as designed.[/QUOTE]


I will use this command to safe battery life and the next step is trying to find out how to negotiate 10 Mbit ethernet instead of 100.

Thank You

---

