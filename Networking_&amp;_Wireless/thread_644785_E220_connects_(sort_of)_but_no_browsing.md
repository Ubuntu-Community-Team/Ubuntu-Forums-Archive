---
title: "E220 connects (sort of?) but no browsing"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by zz12 on 2007-12-19
Have scanned though most threads trying to find out how to configure Kubuntu (Gutsy Gibbon) to use Huawei E220.  I am using the following script to configure the USB connection:

#!/bin/bash
sudo modprobe -r uhci_hcd
sudo modprobe uhci_hcd
 
echo "Waiting kernel to detect modem device"
 
# Wait till the kernel recognizes our E220
while true; do
 
        # Read log
        tail -n 20 /var/log/messages  > access.history
        sleep 1
        tail -n 20 /var/log/messages  > access.current
 
        LOG=`diff access.history access.current | grep ">" | tr -d ">"`
 
        # Check if it is detected
        if [[ "$LOG" =~ "converter now attached to ttyUSB1" ]]; then
                echo "Modem device detected, dialing..."
                # If it is, get out of the loop immedietly
                break
        fi
done
 
rm access.history access.current
 
# Start dialing
sudo wvdial Tele2
------------------
This seems to work OK.  I have all three ttyUSB devices.  I then I use the following wvdial.conf to connect.  Honestly I have not tested the pin section yet, don't know if it works.  Rebooting from Windows seems to leave the modem open so I can access it without PIN.

[Dialer defaults]
Modem = /dev/ttyUSB0
[Dialer Tele2]
Modem = /dev/ttyUSB0
Baud = 460800
Stupid Mode = 1
Init2 = AT+CGDCONT=1,"IP","mobileinternet.tele2.se"
Phone = *99#
Username = *
Password = *
New PPPD = yes
Auto DNS = 1

[Dialer pin]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = AT+CPIN=0000

This seems to work, the modem connects, I get two DNS addresses, and two IP addressses.  No errors.  I can now ping and do nslookup on internet addresses.  I can even start an ftp.

However, the browser (konqueror) can not connect.  Neither can I see or do anything interesting in or with the Knetworkbrowser. Searched again in the forums and tried the following.

hans@HANS-LAPTOP:~$ route -n
Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

hans@HANS-LAPTOP:~$ sudo route add default gw 10.64.64.64
[sudo] password for hans:

hans@HANS-LAPTOP:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

I am not an expert but it does not look right.  Tried also to change default gateway in the network setting graphical interface to use gateway 10.64.64.64.

Still no browser.  What have I done wrong?  Please help, I have already lost more than one day.

---

### Post by buntubunny on 2007-12-20
Have you tried using Firefox instead?

I have also connected using Huawei E220 modem, but received an error while connecting with Konqueror. The error was in the form:

[INDENT]An error occurred while loading [http://www.google.com:](http://www.google.com:)
Could not connect to host [http://www.google.com/](http://www.google.com/).
[/INDENT]

Instead, Firefox works just fine.

Does anyone know why this happens?

---

