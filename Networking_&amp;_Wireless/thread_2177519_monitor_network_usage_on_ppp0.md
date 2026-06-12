---
title: "monitor network usage on ppp0"
date: 2013-09-29
forum: Networking &amp; Wireless
---

### Post by malakar.subhendu on 2013-09-29
I use usb dongle to connect to internet and have a limited plan.
How can i monitor the total network usage of my plan for a particular month?

---

### Post by sanderj on 2013-09-29
Poor man's solution: "ifconfig". But after a system reboot the counters are reset.

You could try NTM ([http://netramon.sourceforge.net/eng/download.html](http://netramon.sourceforge.net/eng/download.html)) but I couldn't test it because I haven't got a ppp0 interface.

---

### Post by sanderj on 2013-09-29
Update:

"vnstat" works for me; it 'survives' reboots.

```
sander@HPtje:~$ vnstat

                      rx      /      tx      /     total    /   estimated
 wlan0: Not enough data available yet.
 eth0:
       Sep '13    771.17 MiB  /    3.97 MiB  /  775.15 MiB  /  814.00 MiB
         today    771.17 MiB  /    3.97 MiB  /  775.15 MiB  /    1.56 GiB

sander@HPtje:~$
```

vnstat runs a daemon which monitors the amount of traffic per interface.

```
sander@HPtje:~$ ps -ef | grep -i vnstat
vnstat    2082     1  0 11:54 ?        00:00:00 /usr/sbin/vnstatd -d --pidfile /run/vnstat/vnstat.pid
sander    3675  3398  0 11:57 pts/7    00:00:00 grep --color=auto -i vnstat
sander@HPtje:~$
```

HTH

---

### Post by sanderj on 2013-09-29
PS:

After installing "vnstati" (with an i at the end) you can also generate a graphical overview of your bandwidth usage: total traffic of today and this month, and mean traffic per hour (or day)


```
vnstati -m -vs -i eth0+wlan0 -o vnstat.png


vnstati -m -vs -i eth0+wlan0 -o vnstat-`date +%F-%T`.png
```


[IMG]http://s22.postimg.org/53y630yz5/vnstat_2013_09_29_14_32_48.png[/IMG]

With

```
vnstati -i eth1+wlan1 -d -ne -nh -o vnstat-hallo.png
```

you get a more sparce view

[IMG]http://s12.postimg.org/y90o2owu5/vnstat_hallo2.png[/IMG]


HTH

---

### Post by malakar.subhendu on 2013-09-29
NTM is a great tool. It matches my exact requirements.
vnstat is also good. have to test it.
Thanks to sanderj to provide answers.

---

