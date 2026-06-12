---
title: "vnstat"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by VpNKBQLjz0 on 2015-01-29
I installed vnstat on my dedicated server running Ubuntu Server 11. It continues to give me the error no matter what I do:
**eth0: Not enough data available yet.**


So I removed it with:

```
[FONT=system]$ apt-get remove vnstat
$ apt-get purge vnstat
dpkg: warning: while removing vnstat, directory '/var/lib/vnstat' not empty so not removed
$ rm -rf /var/lib/vnstat[/FONT]
```

Then to re-install:

```
[FONT=system]$ apt-get install vnstat

After this operation, 242 kB of additional disk space will be used.
Selecting previously unselected package vnstat.
(Reading database ... 41721 files and directories currently installed.)
Preparing to unpack .../vnstat_1.11-2_amd64.deb ...
Unpacking vnstat (1.11-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up vnstat (1.11-2) ...
 * Starting vnStat daemon vnstatd                                               Zero database found, adding available interfaces...
"eth0" added, 100 Mbit bandwidth limit.
"dummy0" added, 100 Mbit bandwidth limit.
"bond0" added, 100 Mbit bandwidth limit.
"ip6tnl0" added, 100 Mbit bandwidth limit.
"tunl0" added, 100 Mbit bandwidth limit.
-> 5 interfaces added. Limits can be modified using the configuration file.
                                                                         [ OK ][/FONT]

```

Now I try to set permissions so all users can use it:

```
[FONT=system]$ chmod o+x /usr/bin/vnstat
$ chmod o+wx /var/lib/vnstat/[/FONT]

```
Now vnstat should be ready to run to monitor 'eth0'

```
[FONT=system]$ vnstat -u -i eth0[/FONT]
[FONT=system]Info: Traffic rate for "eth0" higher than set maximum 100 Mbit (180->2475, r393557 t257406), syncing.[/FONT]

```

```
[FONT=system]$ vnstat -d[/FONT]
**eth0: Not enough data available yet.**
```

What am I doing wrong... why can't I see results for that command? No matter what I type vnstat doesn't show any information at all...

Subsequently I check if the daemon is running:

```
$ /etc/init.d/vnstat status
* vnStat daemon is running
```

So guys... what on earth am I doing wrong?

---

### Post by ajgreeny on 2015-01-29
[FONT=tahoma][SIZE=1]Let's see the output of **vnstat --iflist**

Can you also show us the content of **/etc/vnstat.conf** which you may need to edit as a result of the info output you get when trying to run it.
[/SIZE][/FONT][FONT=system][FONT=tahoma][SIZE=2][SIZE=1]```
$ vnstat -u -i eth0
Info: Traffic rate for "eth0" higher than set maximum 100 Mbit (180->2475, r393557 t257406), syncing.
```

I use vnstat in conky and to run it as user I have used command ```
sudo chmod u+s /usr/bin/vnstat
```so it might be worth using that to replace your command.  I have looked at **man chmod** to see any differences between your chmod command and mine, but it hasn't really helped

Just out of interest, what happens if you run vnstat as root with ```
sudo vnstat
```[/SIZE]
[/SIZE][/FONT]
[/FONT]

---

### Post by slickymaster on 2015-01-29
*Moved to the ***Networking & Wireless*** sub-forum*

---

