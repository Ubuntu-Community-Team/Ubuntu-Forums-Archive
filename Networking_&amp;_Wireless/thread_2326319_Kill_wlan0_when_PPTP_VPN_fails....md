---
title: "Kill wlan0 when PPTP VPN fails..."
date: 2016-05-30
forum: Networking &amp; Wireless
---

### Post by CVGH on 2016-05-30
Hi!

I picked this script up here a few years back:


```
#!/bin/sh
# use tail - /var/log/syslog in terminal to check if it is executed, the four lines help you spot easily
#  Put file in /etc/NetworkManager/dispatcher.d/ and chmod 755 it...
logger -s XXXXXXXXXX
logger -s $1
logger -s $2
logger -s XXXXXXXXXX




if [ $2 = "vpn-down" ]
then
# Shut down eth0 when vpn fails (change eth0 to your nic)
# ifconfig eth1 down
# this will turn off your wireless networking completely
ip link set wlan0 down 
fi

```
Does not seem to work on Ubuntu 14.04.4?

When I disconnect the VPN, wifi still works.

I don't see anything with the tail - /var/log/syslog either.

Thanks!

---

### Post by Fire_Chief on 2016-06-06
Hi CVGH,

Let's just verify a few things on the system first.
- Does the logger command work from the terminal?
- What is managing the VPN? NetworkManager? 
- Is the wifi interface still named wlan0?
- Have the logs for the VPN Manager moved to a separate file in /var/log ? If not, do you see **any** syslog messages about the VPN at all (connected, disconnected, key exchange, route added, etc)? Seems odd that it would not log the activity somewhere.
- Is the script executable? Is it run via a cron job every few minutes or something? What triggers the script?

Cheers!

---

### Post by CVGH on 2016-06-08
Hi!

Logger command returns ==> standard input <== so I don't know what is going on there...
I start the VPN using Network manager from the panel.
It is wlan0.
Not sure where to find the VPN manager logs but will look around..
Script was chmod 755.
I'm not sure what triggers it.
I will see if I can find the original post here:

[http://ubuntuforums.org/showthread.php?t=1688987](http://ubuntuforums.org/showthread.php?t=1688987)

Brian

---

### Post by Fire_Chief on 2016-06-08
Good find! So just make sure the script is in the right directory as mentioned...
> chmod to 755 as root, put in the /etc/NetworkManager/dispatcher.d/ directory

I think it might work better to comment out the ip link line, uncomment the ifconfig line and change the eth1 to wlan0.

---

### Post by CVGH on 2016-06-10
This worked fine on 12.04 but no longer works on 14.04

---

