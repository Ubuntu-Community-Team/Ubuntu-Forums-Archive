---
title: "wireless not working one Dell Inspiron mini after loading Ubutu 14.04"
date: 2016-12-22
forum: Networking &amp; Wireless
---

### Post by mori-mike on 2016-12-22
Hi, wireless not working one Dell Inspiron mini after loading Ubutu 14.04. connects by cable - no problem. I ran some script for a previous post, and got this.
```

mike@mike-Inspiron-1012:~$ run wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
> chmod +x wireless-info && \
> ./wireless-info
No command 'run' found, did you mean:
 Command 'srun' from package 'slurm-llnl' (universe)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'qrun' from package 'torque-client-x11' (universe)
 Command 'qrun' from package 'torque-client' (universe)
 Command 'zrun' from package 'moreutils' (universe)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'grun' from package 'grun' (universe)
run: command not found
mike@mike-Inspiron-1012:~$ wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
> chmod +x wireless-info && \
> ./wireless-info
--2016-12-22 18:03:57--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 192.30.253.112, 192.30.253.113
Connecting to github.com (github.com)|192.30.253.112|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2016-12-22 18:03:58--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.16.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.16.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16156 (16K) [text/plain]
Saving to: ‘wireless-info’


100%[======================================>] 16 156      84,8KB/s   in 0,2s   


Last-modified header missing -- time-stamps turned off.
2016-12-22 18:03:59 (84,8 KB/s) - ‘wireless-info’ saved [16156/16156]


[sudo] password for mike: 


Results saved in "/home/mike/wireless-info.txt".

```

---

### Post by wildmanne39 on 2016-12-22
Please post the wireless-info.txt file created by the script, it is in your home folder, what you posted is not the file we need.
Thanks

---

### Post by RobGoss on 2016-12-22
If you can connect using a wired connection open up **software & updates** and click **additional drivers**, install the **proprietary drivers **save the changes and see how that works.

---

