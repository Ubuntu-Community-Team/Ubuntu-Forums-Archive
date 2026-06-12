---
title: "How can I make my wireless auto reconnect if/when it disconnects?"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by Yourname on 2006-12-17
Hello,

The question basically sums it all.
But in the event that my laptop loses it's wireless connection to my AP/router.. how can I make it reconnect by itself?

(The laptop is going to be a wireless server, hence the automation)


Thanks.

---

### Post by hal10000 on 2006-12-17
Here is a little script that works on my computer. You have to adapt the ip address to the right one for your router. On my network the AP and router are one unit. The ip-address of my router/AP is 192.168.1.1 
The script is called wirelesstest.
You also have to start the cron daemon at boot-time for the script to work.
Here it is:
```

#!/bin/bash
# FILENAME: /usr/bin/wirelesstest
# note the _backticks_ in the next line
if ! `ping -c3 192.168.1.1 >/dev/null 2>&1` ; then
/etc/init.d/networking restart
fi
exit 0

```
The script tests the reachability of you router by doing 3 pings and if this fails, it just restarts networking.

Copy (resp. create) this script (as root) in /usr/bin directory and make root the owner of the file:
```
sudo chown root:root /usr/bin/wirelesstest
```
Make the script executable:
```
sudo chmod u+x /usr/bin/wirelesstest
```

Next, start the cron daemon: (if it is not already started)
```
sudo /etc/init.d/cron start
```
Then edit root's crontab: (resp. create a new crontab for root)
```
sudo crontab -e
```
Put the following line at the end of the (new?) crontab:
```

* * * * *       /usr/bin/wirelesstest

```
This tests every minute if your network is connected.
If the script should run e.g. only every five minutes write to root's crontab:
```
5 * * * *       /usr/bin/wirelesstest
```
To make the cron daemon start on boot-time you have to run your boot-manager and activate cron (the gnome bootUp-manager is a great sh*t, so you better do it manually or use KDE-->systemsettings-->Advanced-->Service config, I dont know exact english menu-names, because mine is in german).
To do it manually:
```

sudo ln -s /etc/init.d/cron /etc/rcS.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rcS.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc0.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc1.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc1.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc2.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc2.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc3.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc3.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc4.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc4.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc5.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc5.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc6.d/K89cron

```

Test the configuration by manually stop networking:
```
 sudo /etc/init.d/networking stop
```
Then wait a minute (or whatever time time you have chosen in your crontab) and see if it auomatically reconnects after the chosen time.
To see if the cron-settings in the /etc/rcX.d/ directories are correct you have to restart the computer.

I hope it works for you.

---

### Post by Yourname on 2007-04-30
Hey man,

Sorry about the long, long and really fast reply, heh. But no one really helps here. Or atleast my threads go unanswered, so I had given up till I saw it today.

Anyway, tried it on Feisty.  It doesn't seem to be working.
But then, networking restart only looks on eth0, so I thought to leave that out. 
dhclient rausb0 doesn't get it connected either.

Only ifup rausb0 gets it connected.
So, I changed the crontab file to:

ifdown rausb0
ifup rausb0
fi
exit 0

And after doing a /etc/init.d/networking stop, the connection never comes back up.
I think cron is running, but I don't know how to check if it is, other than top and ps x where it isn't shown.

---

### Post by hal10000 on 2007-05-03
> I think cron is running, but I don't know how to check if it is, other than top and ps x where it isn't shown

You have to do [COLOR="Red"]ps ax[/COLOR] to test wether cron is running.

---

### Post by Yourname on 2007-05-04
> **hal10000 said:**
> You have to do [COLOR="Red"]ps ax[/COLOR] to test wether cron is running.

It is running.
But then, why isn't it working?

---

### Post by BoyOfDestiny on 2007-05-05
> **hal10000 said:**
> Here is a little script that works on my computer. You have to adapt the ip address to the right one for your router. On my network the AP and router are one unit. The ip-address of my router/AP is 192.168.1.1 
The script is called wirelesstest.
You also have to start the cron daemon at boot-time for the script to work.
Here it is:
```

#!/bin/bash
# FILENAME: /usr/bin/wirelesstest
# note the _backticks_ in the next line
if ! `ping -c3 192.168.1.1 >/dev/null 2>&1` ; then
/etc/init.d/networking restart
fi
exit 0

```
The script tests the reachability of you router by doing 3 pings and if this fails, it just restarts networking.

Copy (resp. create) this script (as root) in /usr/bin directory and make root the owner of the file:
```
sudo chown root:root /usr/bin/wirelesstest
```
Make the script executable:
```
sudo chmod u+x /usr/bin/wirelesstest
```

Next, start the cron daemon: (if it is not already started)
```
sudo /etc/init.d/cron start
```
Then edit root's crontab: (resp. create a new crontab for root)
```
sudo crontab -e
```
Put the following line at the end of the (new?) crontab:
```

* * * * *       /usr/bin/wirelesstest

```
This tests every minute if your network is connected.
If the script should run e.g. only every five minutes write to root's crontab:
```
5 * * * *       /usr/bin/wirelesstest
```
To make the cron daemon start on boot-time you have to run your boot-manager and activate cron (the gnome bootUp-manager is a great sh*t, so you better do it manually or use KDE-->systemsettings-->Advanced-->Service config, I dont know exact english menu-names, because mine is in german).
To do it manually:
```

sudo ln -s /etc/init.d/cron /etc/rcS.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rcS.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc0.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc1.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc1.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc2.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc2.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc3.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc3.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc4.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc4.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc5.d/K89cron
sudo ln -s /etc/init.d/cron /etc/rc5.d/S89cron
sudo ln -s /etc/init.d/cron /etc/rc6.d/K89cron

```

Test the configuration by manually stop networking:
```
 sudo /etc/init.d/networking stop
```
Then wait a minute (or whatever time time you have chosen in your crontab) and see if it auomatically reconnects after the chosen time.
To see if the cron-settings in the /etc/rcX.d/ directories are correct you have to restart the computer.

I hope it works for you.

This worked amazingly thank you. I put it on a wireless machine being used for a server (with sshfs etc)

The only difference to your instructions is I just added this to /etc/crontab

*  *    * * *   root    /usr/bin/wirelesstest

That did the trick! :)

---

### Post by Yourname on 2007-05-05
BoyOfDestiny, I did the same thing you said you did and it worked!
Thanks a lot.. thanks for the original helper too!!! Really appreciate it. :)

---

### Post by clapiotte on 2008-03-02
thanks for the cron trick, it helped. However, a new difficulty is the USB key shuts off and I have to manually remove it and reconnect to have the network work again. Any trick to disconnect/reconnect by software?

Laurent.

---

### Post by oobe-feisty on 2008-07-14
thanks heaps hal10000 for you response i found that script really usefull 
as i dont want to use network manager

---

### Post by knedlyk on 2008-07-21
It works fine! I my case of rt73 wlan drivers I had to change a little this script:

```

#!/bin/bash
# FILENAME: /usr/bin/wirelesstest
# note the backticks in the next line
if ! `ping -c3 192.168.0.1 >/dev/null 2>&1` ; then

/etc/init.d/networking stop

/sbin/modprobe -r rt73

sleep 5s

/sbin/modprobe rt73

/etc/init.d/networking start

fi
exit 0

```


And to have this script started every 5 minutes, there is special option for cron: ```
*\5 * * * * /usr/local/bin/wirelesstest 
```.

---

