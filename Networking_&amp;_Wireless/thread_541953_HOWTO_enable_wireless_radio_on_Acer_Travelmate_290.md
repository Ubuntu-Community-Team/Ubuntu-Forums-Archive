---
title: "HOWTO enable wireless radio on Acer Travelmate 290 series"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by noob12 on 2007-09-03
This HOWTO provides instructions for how to enable the wireless radio on an Acer Travelmate 290 series laptop using the Intel Pro Wireless 2200 card.

This HOWTO applies to you (only) if you have this model of laptop and you are unable to enable the wireless radio. You can confirm this condition by checking whether you see messages like the following in your dmesg output.
```

ipw2200: Detected Intel PRO/Wireless 2200 Network Connection
eth1: Radio is disabled by RF switch.

```
and the command
```

cat /sys/class/net/*/device/rf_kill

```
shows the value 2, and you cannot get this to change using the hardware switch.

This HOWTO was tested by a user on an Acer Travelmate 292 LMi with Intel Pro / Wireless 2200BG card and running kernel version 2.6.20-16-generic, which has acerhk module 0.5.34 and ipw2200 1.2.0.  It probably applies equally to other 290 series laptops with the same network card, running the same or more recent kernels.  It might not work on kernels with earlier versions of these modules.

If you are using the *same* series laptop and have trouble or feedback from using these instructions, please post back to this thread.

If you have a different Acer laptop, you might be able to solve your problem by generalizing from this and using tips from the rfswitch laptop matrix here: [http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix) and instructions on the ipw driver sites on sourceforge.   However, if you have problems and need help, you should probably start a new thread for that.

This HOWTO is only intended to get the wireless radio enabled.  If this works to get your radio enabled but you have other issues getting connected by wireless, please start a new thread for help.

**Load ipw2200 with led=1 option**

```

echo "options ipw2200 led=1" | sudo tee -a /etc/modprobe.d/options

```
This tells the system to load ipw2200 with the led=1 option when it normally loads.

Because this device is an ethernet device on the pci bus, it may be getting initialized in initrd.  So it is best to do this as well.
```

sudo update-initramfs -u

```

**Setting up acerhk to load at boot with your options**

Note that this is a similar command but is a different file from the previous one.  So copy and paste from the box below.  This command appends to the /etc/modules file, so it assumes that you have no existing line for acerhk in the /etc/modules file; this is true in a fresh installation, but if you've been playing with acerhk already, remove any existing acerhk line from that file.
```

echo "acerhk force_series=290 usedritek=1" | sudo tee -a /etc/modules

```

**Setting the wirelessled state manually via procfs at boot**

```

xhost +
sudo gedit /etc/init.d/acerhkwireless

```
Put the following content verbatim in this file
```

#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          acerhkwireless
# Required-Start:    mountkernfs $local_fs
# Required-Stop:    $local_fs
# Default-Start:     S
# Default-Stop:      0 6
### END INIT INFO
case "$1" in
start|restart|force-reload)
    /bin/echo "1"  > /proc/driver/acerhk/wirelessled
    ;;
stop)
   /bin/echo "0"  > /proc/driver/acerhk/wirelessled
   ;;
*)
   echo "Usage: /etc/init.d/acerhkwireless start|stop|restart|force-reload"
   exit 1
   ;;
esac

exit 0

```

Save the file and exit.  Then run

```

sudo chmod a+x /etc/init.d/acerhkwireless
sudo ln -s /etc/init.d/acerhkwireless /etc/rcS.d/S39acerhkwireless

```
Now reboot.   This script will normally run before networking.  

[Side Note: If you always intend to keep the wireless in roaming mode, a much simpler approach is possible to replace the script installed in this last section.  You can just edit the file /etc/rc.local and put the command **echo 1 > /proc/driver/acerhk/wirelessled** somewhere in that script.  The separate boot script recommended here works in more general circumstances since it will always run before networking starts.]

You can verify that you have solved the hardware RF switch issue by checking that
```

cat /sys/class/net/*/device/rf_kill

```
shows a 0 or a 1 (not a 2).

---

### Post by 315234 on 2007-09-04
For 64bit Acers, you will need acer_acpi rather than acerhk.

Get it here: [http://code.google.com/p/aceracpi/](http://code.google.com/p/aceracpi/)

And use the following command to turn on the radio:
```
echo 'enabled : 1' >> /proc/acpi/acer/wireless
```

---

### Post by brienc on 2008-01-28
THANK YOU, noob12!  That worked perfectly!

---

### Post by belgos on 2008-02-12
SUPER, thanks a lot!

---

### Post by vitivy on 2008-03-31
Thanks! I have been having a really long day trying to find a way to swich on my wireless, trying almost everything... Cant believe, that I've stumbled across this after so long. Works perfectly for me, big thanks indeed.

---

### Post by anderssl on 2008-04-15
Omg - thanks a lot for this guide, which for once was understandable even for us dummies... I have an Acer Travelmate 4500 (4501, to be precise), had the same problem and following this guide solved it!

I just had to change one line - the one that reads:
```
echo "acerhk force_series=290 usedritek=1" | sudo tee -a /etc/modules
```
(of course) had to be changed to
```
echo "acerhk force_series=4500 usedritek=1" | sudo tee -a /etc/modules
```

Presumably others with similar Acer models can try to follow the guide and just insert the appropriate series number?

Anyway, thanks again!

---

### Post by PeteZA on 2008-05-18
Just wanted to add a big thanks. Also got it working on the travelmate 4500

---

### Post by josepm on 2008-05-27
I just wanted to add another BIG Thanks. You made my day! Before this, I had to boot my 290 with windows to turn on the wireless card and then reboot it to Ubuntu. :-)

---

