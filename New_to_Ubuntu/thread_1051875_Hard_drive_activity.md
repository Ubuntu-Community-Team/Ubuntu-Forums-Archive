---
title: "Hard drive activity"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by randogauci on 2009-01-27
Hi
I have recently upgraded from 8.04 to 8.10 on an AMD64 desktop, and now the hard drive activity light shows continued activity even when the computer is idle for some time.
I did a sudo top and "kjournald" seems to be constantly active. What is it? and is this causing too much wear & tear on the drive? can it be stopped?
Regards
ron:D

---

### Post by scragar on 2009-01-27
kjournald is the system for avoiding possible data loss from powercuts etc.

If you are using the disk a lot then it is common for it to be running. I would be curious to see what is using the disk so much though.

0h, don't just kill this, no matter what anyone recommends, unless there is no other choice. This process is not the cause of your disk activity, it is a result of it.

---

### Post by randogauci on 2009-01-27
thanks for that...
How do I find out what is actually constantly accessing the drive?
The drive light is flickering continuously even when I am not doing anything at all.
It was not doing this when I had Ubuntu 8.04......
I also have other computers with Ubuntu 8.10 and they do not exhibit the same symptoms...
HELP!!!

---

### Post by sdennie on 2009-01-28
You could use:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Then,

```

tail -f /var/log/syslog

```

That should show you what is writing to the disk.  To turn the log spam off use:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

You could also take a look at this guide for a possible way to decrease disk activity: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998")

---

### Post by syga on 2009-01-28
Constant hard drive activity was my biggest complaint with any Linux distro on my Dell AMD64 laptop. The biggest improvements came when I changed to the ext2 filesystem, enabled and configured Laptop-Mode tools and disabled services that I don't need. 

My laptop disk activity is now quieter than Windows and when websurfing, the fan rarely turns on.

---

### Post by randogauci on 2009-01-28
> **sdennie said:**
> You could use:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Then,

```

tail -f /var/log/syslog

```

That should show you what is writing to the disk.  To turn the log spam off use:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

You could also take a look at this guide for a possible way to decrease disk activity: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998")
 Hi, Thanks again for your help. This is what I got and I don't quite understand what I amd looking for here:
ron@AMD-UB804:~$ sudo sh -c "echo 0 > /proc/sys/vm/block_dump"
ron@AMD-UB804:~$ tail -f /var/log/syslog
Jan 28 21:30:01 AMD-UB804 /USR/SBIN/CRON[16571]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 21:33:15 AMD-UB804 ntpd[6617]: synchronized to 91.189.94.4, stratum 2
Jan 28 21:35:27 AMD-UB804 ntpd[6617]: time reset +2.325616 s
Jan 28 21:39:01 AMD-UB804 /USR/SBIN/CRON[16756]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan 28 21:40:01 AMD-UB804 /USR/SBIN/CRON[16813]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 21:43:53 AMD-UB804 ntpd[6617]: synchronized to 91.189.94.4, stratum 2
Jan 28 21:50:01 AMD-UB804 /USR/SBIN/CRON[17012]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 21:51:22 AMD-UB804 ntpd[6617]: time reset +2.360834 s
Jan 28 22:00:01 AMD-UB804 /USR/SBIN/CRON[17210]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 22:02:02 AMD-UB804 ntpd[6617]: synchronized to 91.189.94.4, stratum 2
  
ron@AMD-UB804:~$ sudo sh -c "echo 0 > /proc/sys/vm/block_dump"
[sudo] password for ron: 
ron@AMD-UB804:~$ tail -f /var/log/syslog
Jan 28 21:35:27 AMD-UB804 ntpd[6617]: time reset +2.325616 s
Jan 28 21:39:01 AMD-UB804 /USR/SBIN/CRON[16756]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan 28 21:40:01 AMD-UB804 /USR/SBIN/CRON[16813]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 21:43:53 AMD-UB804 ntpd[6617]: synchronized to 91.189.94.4, stratum 2
Jan 28 21:50:01 AMD-UB804 /USR/SBIN/CRON[17012]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 21:51:22 AMD-UB804 ntpd[6617]: time reset +2.360834 s
Jan 28 22:00:01 AMD-UB804 /USR/SBIN/CRON[17210]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 22:02:02 AMD-UB804 ntpd[6617]: synchronized to 91.189.94.4, stratum 2
Jan 28 22:07:25 AMD-UB804 ntpd[6617]: time reset +2.381257 s
Jan 28 22:09:01 AMD-UB804 /USR/SBIN/CRON[17481]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Regards
Ron

---

### Post by randogauci on 2009-01-28
> **randogauci said:**
> Hi, Thanks again for your help. This is what I got and I don't quite understand what I amd looking for here:
ron@AMD-UB804:~$ sudo sh -c "echo 0 > /proc/sys/vm/block_dump"
ron@AMD-UB804:~$ tail -f /var/log/syslog
Jan 28 21:30:01 AMD-UB804 /USR/SBIN/CRON[16571]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 21:33:15 AMD-UB804 ntpd[6617]: synchronized to 91.189.94.4, stratum 2
Jan 28 21:35:27 AMD-UB804 ntpd[6617]: time reset +2.325616 s
Jan 28 21:39:01 AMD-UB804 /USR/SBIN/CRON[16756]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan 28 21:40:01 AMD-UB804 /USR/SBIN/CRON[16813]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 21:43:53 AMD-UB804 ntpd[6617]: synchronized to 91.189.94.4, stratum 2
Jan 28 21:50:01 AMD-UB804 /USR/SBIN/CRON[17012]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 21:51:22 AMD-UB804 ntpd[6617]: time reset +2.360834 s
Jan 28 22:00:01 AMD-UB804 /USR/SBIN/CRON[17210]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 22:02:02 AMD-UB804 ntpd[6617]: synchronized to 91.189.94.4, stratum 2
  
ron@AMD-UB804:~$ sudo sh -c "echo 0 > /proc/sys/vm/block_dump"
[sudo] password for ron: 
ron@AMD-UB804:~$ tail -f /var/log/syslog
Jan 28 21:35:27 AMD-UB804 ntpd[6617]: time reset +2.325616 s
Jan 28 21:39:01 AMD-UB804 /USR/SBIN/CRON[16756]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan 28 21:40:01 AMD-UB804 /USR/SBIN/CRON[16813]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 21:43:53 AMD-UB804 ntpd[6617]: synchronized to 91.189.94.4, stratum 2
Jan 28 21:50:01 AMD-UB804 /USR/SBIN/CRON[17012]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 21:51:22 AMD-UB804 ntpd[6617]: time reset +2.360834 s
Jan 28 22:00:01 AMD-UB804 /USR/SBIN/CRON[17210]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan 28 22:02:02 AMD-UB804 ntpd[6617]: synchronized to 91.189.94.4, stratum 2
Jan 28 22:07:25 AMD-UB804 ntpd[6617]: time reset +2.381257 s
Jan 28 22:09:01 AMD-UB804 /USR/SBIN/CRON[17481]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Regards
Ron
Hi again
I did all the work in the link you provided, all seemed to work OK, rebooted but there is no difference in the HD activity light!!!

---

### Post by scragar on 2009-01-28
You missed the point, firstly you need to write the first line, not the last one. The first one turns on debuging, the second shows what it says, and the last line turns it off again to save it.

Your log isn't exactly usefull right now, since you've not turned on debuging before posting it. Once we see what is using the hard drive we can advise.

---

### Post by skymera on 2009-01-28
You sure it's not tracker just scanning and indexing files?

---

### Post by randogauci on 2009-01-28
Hello again, Thanks for your patience, I have done it again and this is the output until I stopped it...

Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.830775] kjournald(2334): WRITE block 17511504 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.830780] kjournald(2334): WRITE block 17501408 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.830785] kjournald(2334): WRITE block 17503704 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.830790] kjournald(2334): WRITE block 17511512 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.830794] kjournald(2334): WRITE block 17501416 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.830798] kjournald(2334): WRITE block 17503712 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.830803] kjournald(2334): WRITE block 17511520 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.839703] firefox(7140): READ block 80330616 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.849624] firefox(7140): READ block 80389456 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.860065] firefox(7140): READ block 80391456 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.869877] firefox(7140): READ block 80243496 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.876107] firefox(7140): READ block 80207496 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.882970] firefox(7140): READ block 80391480 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.883375] firefox(7140): READ block 80308104 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.894166] firefox(7140): READ block 80391488 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.894390] firefox(7140): READ block 80245000 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.903567] firefox(7140): READ block 80306344 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.913269] firefox(7140): READ block 80391496 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.920081] firefox(7140): READ block 80244248 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.927371] firefox(7140): READ block 80254104 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.931608] firefox(7140): READ block 80246768 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.935018] firefox(7140): READ block 80308352 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.940011] firefox(7140): READ block 80587976 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.941154] kjournald(2334): WRITE block 250832 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.941161] kjournald(2334): WRITE block 250840 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.941165] kjournald(2334): WRITE block 250848 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.941169] kjournald(2334): WRITE block 250856 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.941173] kjournald(2334): WRITE block 250864 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.941177] kjournald(2334): WRITE block 250872 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.941181] kjournald(2334): WRITE block 250880 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.941185] kjournald(2334): WRITE block 250888 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.941189] kjournald(2334): WRITE block 250896 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.941193] kjournald(2334): WRITE block 250904 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.945486] firefox(7140): READ block 80586792 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.948180] firefox(7140): READ block 80594064 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.950350] firefox(7140): READ block 80587960 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.950680] firefox(7140): READ block 80292496 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.962800] firefox(7140): READ block 80585080 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.973364] firefox(7140): READ block 80493776 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.977758] firefox(7140): READ block 80395424 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.987672] firefox(7140): READ block 80584792 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.988220] firefox(7140): READ block 80209280 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.998378] firefox(7140): READ block 80584616 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1012.998665] firefox(7140): READ block 80333880 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.001700] firefox(7140): READ block 80208632 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.006399] firefox(7140): READ block 80584608 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.006825] firefox(7140): READ block 80249808 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.016003] firefox(7140): READ block 80589816 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.026516] firefox(7140): READ block 80339496 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.032598] firefox(7140): READ block 80484856 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.043093] firefox(7140): READ block 80476728 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.052521] firefox(7140): READ block 80252448 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.053561] kjournald(2334): WRITE block 250912 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.059974] firefox(7140): READ block 80471976 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.064935] firefox(7140): READ block 80594904 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.069367] firefox(7140): READ block 80594104 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.075252] firefox(7140): READ block 80471984 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.075620] firefox(7140): READ block 80246088 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.084143] firefox(7140): READ block 80593968 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.084464] firefox(7140): READ block 80471992 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.084831] firefox(7140): READ block 80210304 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.094980] firefox(7140): READ block 80475576 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.102483] firefox(7140): READ block 80484944 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.110162] firefox(7140): READ block 80475640 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.113037] firefox(7140): READ block 80381616 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.122439] firefox(7140): READ block 80344328 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.130441] firefox(7140): READ block 80292288 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.136631] firefox(7140): READ block 80595968 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.137197] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.137217] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.137234] mythbackend(5687): WRITE block 19589320 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.137280] kjournald(2334): WRITE block 17503712 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.137288] kjournald(2334): WRITE block 17501416 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.137294] kjournald(2334): WRITE block 17511520 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.137299] kjournald(2334): WRITE block 17501424 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.137306] kjournald(2334): WRITE block 17503720 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.137310] kjournald(2334): WRITE block 17511528 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.150932] firefox(7140): READ block 80335512 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.155410] firefox(7140): READ block 80592696 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.164712] firefox(7140): READ block 80595984 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.165113] firefox(7140): READ block 80302032 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.171700] firefox(7140): READ block 80595992 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.171935] firefox(7140): READ block 80592760 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.172413] firefox(7140): READ block 80246280 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.177530] firefox(7140): READ block 80596040 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.184962] firefox(7140): READ block 80596240 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.187107] firefox(7140): READ block 80593000 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.194551] firefox(7140): READ block 80596080 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.195043] firefox(7140): READ block 80474256 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.202972] firefox(7140): READ block 80595072 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.205530] firefox(7140): READ block 80596168 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.205981] firefox(7140): READ block 80249624 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.246270] firefox(7140): READ block 80473344 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.255422] firefox(7140): READ block 80308032 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.256624] kjournald(2334): WRITE block 250920 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.256632] kjournald(2334): WRITE block 250928 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.256639] kjournald(2334): WRITE block 250936 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.256643] kjournald(2334): WRITE block 250944 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.256647] kjournald(2334): WRITE block 250952 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.256651] kjournald(2334): WRITE block 250960 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.256655] kjournald(2334): WRITE block 250968 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.256659] kjournald(2334): WRITE block 250976 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.256663] kjournald(2334): WRITE block 250984 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.256668] kjournald(2334): WRITE block 250992 on sdb4
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.266519] firefox(7140): READ block 80385112 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.275928] firefox(7140): READ block 80473416 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.282615] firefox(7140): READ block 80474176 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.293406] firefox(7140): READ block 80384928 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.293779] firefox(7140): READ block 80473424 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.294259] firefox(7140): READ block 80477984 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.334374] firefox(7140): READ block 80473440 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.334605] firefox(7140): READ block 80477928 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.335072] firefox(7140): READ block 80384760 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.337965] firefox(7140): READ block 80473448 on sdb5
Jan 29 12:16:47 AMD-UB804 kernel: [ 1013.338272] firefox(7140): READ block 80249304 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.349024] firefox(7140): READ block 80253928 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.352666] firefox(7140): READ block 80482912 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.356824] firefox(7140): READ block 80389944 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.364827] firefox(7140): READ block 80492480 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.365292] kjournald(2334): WRITE block 251000 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.375534] firefox(7140): READ block 80483224 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.378951] firefox(7140): READ block 80591080 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.385047] firefox(7140): READ block 80483696 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.392687] firefox(7140): READ block 80393680 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.397274] firefox(7140): READ block 80491832 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.407863] firefox(7140): READ block 80486792 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.415482] firefox(7140): READ block 80590552 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.427031] firefox(7140): READ block 80591752 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.435006] firefox(7140): READ block 80486832 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.440858] firefox(7140): READ block 80588616 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.443964] firefox(7140): READ block 80303200 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.452395] firefox(7140): READ block 80310368 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.455011] firefox(7140): READ block 80389696 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.461797] firefox(7140): READ block 80302640 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.470013] firefox(7140): READ block 80311528 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479128] firefox(7140): READ block 80404368 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479364] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479377] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479383] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479398] mythbackend(5687): WRITE block 19589320 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479447] kjournald(2334): WRITE block 17503720 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479455] kjournald(2334): WRITE block 17501424 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479460] kjournald(2334): WRITE block 17511528 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479465] kjournald(2334): WRITE block 17501432 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479470] kjournald(2334): WRITE block 17503728 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479474] kjournald(2334): WRITE block 17511536 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479478] kjournald(2334): WRITE block 17501536 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479484] kjournald(2334): WRITE block 17503736 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.479488] kjournald(2334): WRITE block 17511544 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.486948] firefox(7140): READ block 80305928 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.496028] firefox(7140): READ block 80247784 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.503824] firefox(7140): READ block 80247968 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.507317] firefox(7140): READ block 80302192 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.513583] firefox(7140): READ block 80305952 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.521236] firefox(7140): READ block 80303360 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.528970] firefox(7140): READ block 80589128 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.533975] firefox(7140): READ block 80307816 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.546080] firefox(7140): READ block 80242832 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.555567] firefox(7140): READ block 80585944 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.565538] firefox(7140): READ block 80247664 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.576945] firefox(7140): READ block 80253464 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.578658] firefox(7140): READ block 80334248 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.585822] firefox(7140): READ block 80445448 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.587115] kjournald(2334): WRITE block 251008 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.587128] kjournald(2334): WRITE block 251016 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.587134] kjournald(2334): WRITE block 251024 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.587138] kjournald(2334): WRITE block 251032 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.587142] kjournald(2334): WRITE block 251040 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.587146] kjournald(2334): WRITE block 251048 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.587150] kjournald(2334): WRITE block 251056 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.587154] kjournald(2334): WRITE block 251064 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.587158] kjournald(2334): WRITE block 251072 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.587162] kjournald(2334): WRITE block 251080 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.595415] firefox(7140): READ block 80445496 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.595870] firefox(7140): READ block 80334264 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.596176] firefox(7140): READ block 80466056 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.601492] firefox(7140): READ block 80251464 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.610118] firefox(7140): READ block 80471752 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.616760] firefox(7140): READ block 80483592 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.623749] firefox(7140): READ block 80304760 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.631374] firefox(7140): READ block 80471760 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.631726] firefox(7140): READ block 80494016 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.635822] firefox(7140): READ block 80252640 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.676147] firefox(7140): READ block 80589560 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.687707] firefox(7140): READ block 80247248 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.696737] firefox(7140): READ block 80338208 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.697223] kjournald(2334): WRITE block 251088 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.705956] firefox(7140): READ block 80249216 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.712976] firefox(7140): READ block 80247328 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.722564] firefox(7140): READ block 80242656 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.727966] firefox(7140): READ block 80206008 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.736761] firefox(7140): READ block 80247376 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.739692] firefox(7140): READ block 80210280 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.742389] firefox(7140): READ block 80252728 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.751819] firefox(7140): READ block 80394200 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.761400] firefox(7140): READ block 80209808 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.769329] firefox(7140): READ block 80248312 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.776785] firefox(7140): READ block 80394240 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.786699] firefox(7140): READ block 80251640 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.796173] firefox(7140): READ block 80245600 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.798497] firefox(7140): READ block 80394416 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.805190] firefox(7140): READ block 80251672 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.805371] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.805384] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.805400] mythbackend(5687): WRITE block 19589320 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.805447] kjournald(2334): WRITE block 17503736 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.805455] kjournald(2334): WRITE block 17501536 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.805461] kjournald(2334): WRITE block 17511544 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.805466] kjournald(2334): WRITE block 17501544 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.805474] kjournald(2334): WRITE block 17503744 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.805478] kjournald(2334): WRITE block 17511552 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.809015] firefox(7140): READ block 80248096 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.809355] firefox(7140): READ block 80394440 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.809713] firefox(7140): READ block 80307704 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.818528] firefox(7140): READ block 80248256 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.825804] firefox(7140): READ block 80589928 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.834070] firefox(7140): READ block 80342112 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.872767] firefox(7140): READ block 80309640 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.877102] firefox(7140): READ block 80251904 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.881974] firefox(7140): READ block 80346280 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.885008] firefox(7140): READ block 80587864 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.890193] firefox(7140): READ block 80302264 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.896177] firefox(7140): READ block 80346424 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.904848] firefox(7140): READ block 80303040 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.915916] firefox(7140): READ block 80335048 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.916046] kjournald(2334): WRITE block 251096 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.916053] kjournald(2334): WRITE block 251104 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.916059] kjournald(2334): WRITE block 251112 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.916063] kjournald(2334): WRITE block 251120 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.916067] kjournald(2334): WRITE block 251128 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.916071] kjournald(2334): WRITE block 251136 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.916075] kjournald(2334): WRITE block 251144 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.916080] kjournald(2334): WRITE block 251152 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.916083] kjournald(2334): WRITE block 251160 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.916087] kjournald(2334): WRITE block 251168 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.920033] firefox(7140): READ block 80344240 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.925789] firefox(7140): READ block 80588152 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.934837] firefox(7140): READ block 80312592 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.940332] firefox(7140): READ block 80344448 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.945094] firefox(7140): READ block 80588024 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.945569] firefox(7140): READ block 80344504 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.945863] firefox(7140): READ block 80206064 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.953234] firefox(7140): READ block 80209144 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.959050] firefox(7140): READ block 80253840 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.964412] firefox(7140): READ block 80253128 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.975378] firefox(7140): READ block 80252552 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.986299] firefox(7140): READ block 80253688 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.987090] kjournald(2334): WRITE block 251176 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1013.995883] firefox(7140): READ block 80333392 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.006673] firefox(7140): READ block 80593208 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.018631] firefox(7140): READ block 80591896 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.025658] firefox(7140): READ block 80333624 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.034491] firefox(7140): READ block 80593184 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.043410] firefox(7140): READ block 80489864 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.046799] firefox(7140): READ block 80346744 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.058219] firefox(7140): READ block 80474632 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.062305] firefox(7140): READ block 80432528 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.064776] firefox(7140): READ block 80593160 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.076316] firefox(7140): READ block 80595904 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.079820] firefox(7140): READ block 80472760 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.087664] firefox(7140): READ block 80592472 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.091928] firefox(7140): READ block 80308936 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100532] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100554] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100572] mythbackend(5687): WRITE block 19589320 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100597] firefox(7140): READ block 80210136 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100651] kjournald(2334): WRITE block 17503744 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100666] kjournald(2334): WRITE block 17501544 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100677] kjournald(2334): WRITE block 17511552 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100687] kjournald(2334): WRITE block 17501552 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100697] kjournald(2334): WRITE block 17503752 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100705] kjournald(2334): WRITE block 17511560 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100712] kjournald(2334): WRITE block 17501560 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100719] kjournald(2334): WRITE block 17503760 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.100727] kjournald(2334): WRITE block 17511568 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.105833] kjournald(2334): WRITE block 251184 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.105849] kjournald(2334): WRITE block 251192 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.105857] kjournald(2334): WRITE block 251200 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.105864] kjournald(2334): WRITE block 251208 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.105871] kjournald(2334): WRITE block 251216 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.105879] kjournald(2334): WRITE block 251224 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.105886] kjournald(2334): WRITE block 251232 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.105894] kjournald(2334): WRITE block 251240 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.105902] kjournald(2334): WRITE block 251248 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.105909] kjournald(2334): WRITE block 251256 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.113782] firefox(7140): READ block 80254768 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.119326] firefox(7140): READ block 80247288 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.128735] firefox(7140): READ block 80589200 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.129343] kjournald(2334): WRITE block 251264 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.140689] firefox(7140): READ block 80205504 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.152469] firefox(7140): READ block 80247280 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.152875] firefox(7140): READ block 80309864 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.162665] firefox(7140): READ block 80306032 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.169412] firefox(7140): READ block 80309888 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.169706] firefox(7140): READ block 80307184 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.176991] firefox(7140): READ block 80242280 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.187927] firefox(7140): READ block 80252392 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.196074] firefox(7140): READ block 80472264 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.204940] firefox(7140): READ block 80472168 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.205387] firefox(7140): READ block 80312368 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.211489] firefox(7140): READ block 80472272 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.212019] firefox(7140): READ block 80313472 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.218233] firefox(7140): READ block 80472280 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.218537] firefox(7140): READ block 80586864 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.226918] firefox(7140): READ block 80384264 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.235043] firefox(7140): READ block 80472296 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.235339] firefox(7140): READ block 80483640 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.238664] firefox(7140): READ block 80313240 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.248604] firefox(7140): READ block 80302872 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.249305] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.249323] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.249351] mythbackend(5687): WRITE block 19589320 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.249433] kjournald(2334): WRITE block 17503760 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.249446] kjournald(2334): WRITE block 17501560 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.249455] kjournald(2334): WRITE block 17511568 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.249464] kjournald(2334): WRITE block 17501568 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.249474] kjournald(2334): WRITE block 17503768 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.249482] kjournald(2334): WRITE block 17511576 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.261674] kjournald(2334): WRITE block 251272 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.261691] kjournald(2334): WRITE block 251280 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.261699] kjournald(2334): WRITE block 251288 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.261706] kjournald(2334): WRITE block 251296 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.261712] kjournald(2334): WRITE block 251304 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.261719] kjournald(2334): WRITE block 251312 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.261725] kjournald(2334): WRITE block 251320 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.261732] kjournald(2334): WRITE block 251328 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.261738] kjournald(2334): WRITE block 251336 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.261745] kjournald(2334): WRITE block 251344 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.261842] firefox(7140): READ block 80311520 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.262506] kjournald(2334): WRITE block 251352 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.267564] firefox(7140): READ block 80473320 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.275984] firefox(7140): READ block 80331168 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.285092] firefox(7140): READ block 80205952 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.290599] firefox(7140): READ block 80473336 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.301796] firefox(7140): READ block 80207760 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.306731] firefox(7140): READ block 80208344 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.314929] firefox(7140): READ block 80304472 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.328090] firefox(7140): READ block 80248888 on sdb5
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.328917] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.328944] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.328974] mythbackend(5687): WRITE block 19589320 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.329069] kjournald(2334): WRITE block 17503768 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.329089] kjournald(2334): WRITE block 17501568 on sdb4
Jan 29 12:16:48 AMD-UB804 kernel: [ 1014.329099] kjournald(2334): WRITE block 17511576 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.373851] firefox(7140): READ block 80589056 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.386704] firefox(7140): READ block 80303456 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.401706] firefox(7140): READ block 80491792 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.412026] firefox(7140): READ block 80589024 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.419426] firefox(7140): READ block 80305000 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.431151] firefox(7140): READ block 80305336 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.435614] firefox(7140): READ block 80588992 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.437628] firefox(7140): READ block 80302328 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.482299] firefox(7140): READ block 80305448 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.482509] kjournald(2334): WRITE block 251360 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.482522] kjournald(2334): WRITE block 251368 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.482533] kjournald(2334): WRITE block 251376 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.482542] kjournald(2334): WRITE block 251384 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.482549] kjournald(2334): WRITE block 251392 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.489670] firefox(7140): READ block 80253952 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.490301] kjournald(2334): WRITE block 251400 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.498051] firefox(7140): READ block 80333056 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.509112] firefox(7140): READ block 80209320 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.517101] firefox(7140): READ block 80346984 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.525403] firefox(7140): READ block 80333296 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.528411] firefox(7140): READ block 80346912 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.529084] firefox(7140): READ block 80302976 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.572236] firefox(7140): READ block 80249904 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.577185] firefox(7140): READ block 80340376 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.621317] firefox(7140): READ block 80473464 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.621697] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.621721] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.621730] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.621758] mythbackend(5687): WRITE block 19589320 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.621839] kjournald(2334): WRITE block 17503768 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.621855] kjournald(2334): WRITE block 17501568 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.621865] kjournald(2334): WRITE block 17501576 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.621880] kjournald(2334): WRITE block 17511576 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.621890] kjournald(2334): WRITE block 17503776 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.621898] kjournald(2334): WRITE block 17511584 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.635801] firefox(7140): READ block 80206296 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.644392] firefox(7140): READ block 80312688 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.655478] firefox(7140): READ block 80336584 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.662150] firefox(7140): READ block 80306448 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.677831] sudo(7243): dirtied inode 563342 (passdb.tdb) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.679063] sudo(7243): dirtied inode 563346 (group_mapping.ldb) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.679259] sudo(7243): dirtied inode 563346 (group_mapping.ldb) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.679924] sudo(7243): dirtied inode 563342 (passdb.tdb) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.679969] sudo(7243): WRITE block 18155288 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.680015] sudo(7243): WRITE block 18155296 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.706640] firefox(7140): READ block 80243200 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.713328] firefox(7140): READ block 80249560 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.722634] firefox(7140): READ block 80249328 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.726343] firefox(7140): READ block 80393000 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.731824] firefox(7140): READ block 80313864 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.739217] firefox(7140): READ block 80246640 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.739389] kjournald(2334): WRITE block 251408 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.739401] kjournald(2334): WRITE block 251416 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.739412] kjournald(2334): WRITE block 251424 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.739419] kjournald(2334): WRITE block 251432 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.739426] kjournald(2334): WRITE block 251440 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.739433] kjournald(2334): WRITE block 251448 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.739439] kjournald(2334): WRITE block 251456 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.739447] kjournald(2334): WRITE block 251464 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.739454] kjournald(2334): WRITE block 251472 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.739460] kjournald(2334): WRITE block 251480 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.743936] firefox(7140): READ block 80247568 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.757301] kjournald(2334): WRITE block 251488 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.757620] kjournald(2334): WRITE block 17503776 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.757632] kjournald(2334): WRITE block 17501576 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.757642] kjournald(2334): WRITE block 17511584 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.757651] kjournald(2334): WRITE block 17501584 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.757661] kjournald(2334): WRITE block 17503784 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.757668] kjournald(2334): WRITE block 17511600 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.758027] firefox(7140): READ block 80265272 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.761611] kjournald(2334): WRITE block 251496 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.761624] kjournald(2334): WRITE block 251504 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.761633] kjournald(2334): WRITE block 251512 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.761639] kjournald(2334): WRITE block 251520 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.761646] kjournald(2334): WRITE block 251528 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.761654] kjournald(2334): WRITE block 251536 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.761661] kjournald(2334): WRITE block 251544 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.761668] kjournald(2334): WRITE block 251552 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.761676] kjournald(2334): WRITE block 251560 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.761683] kjournald(2334): WRITE block 251568 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.796541] firefox(7140): READ block 80208608 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.806758] firefox(7140): READ block 80254168 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.808330] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.808353] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.808379] mythbackend(5687): WRITE block 19589320 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.815891] firefox(7140): READ block 80472208 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.826575] firefox(7140): READ block 80384720 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.830852] firefox(7140): READ block 80381320 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.835511] firefox(7140): READ block 80595328 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.843147] firefox(7140): READ block 80472224 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.852001] firefox(7140): READ block 80387680 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.861578] firefox(7140): READ block 80472256 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.861891] firefox(7140): READ block 80586912 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.866278] firefox(7140): READ block 80302320 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.877257] kjournald(2334): WRITE block 251576 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.877779] sudo(7243): dirtied inode 563342 (passdb.tdb) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.877847] kjournald(2334): WRITE block 17503784 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.877859] kjournald(2334): WRITE block 17501584 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.877868] kjournald(2334): WRITE block 17511600 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.877877] kjournald(2334): WRITE block 17501592 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.877885] kjournald(2334): WRITE block 17503792 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.877905] sudo(7243): WRITE block 18155288 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.879935] firefox(7140): READ block 80303544 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.881609] kjournald(2334): WRITE block 251584 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.881622] kjournald(2334): WRITE block 251592 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.881629] kjournald(2334): WRITE block 251600 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.881637] kjournald(2334): WRITE block 251608 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.881644] kjournald(2334): WRITE block 251616 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.881654] kjournald(2334): WRITE block 251624 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.881661] kjournald(2334): WRITE block 251632 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.881668] kjournald(2334): WRITE block 251640 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.881675] kjournald(2334): WRITE block 251648 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.881980] sudo(7243): WRITE block 18155264 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.900291] firefox(7140): READ block 80404456 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.906660] firefox(7140): READ block 80487096 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.913986] firefox(7140): READ block 80404464 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.914502] firefox(7140): READ block 80593808 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.922790] firefox(7140): READ block 80243664 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.927258] firefox(7140): READ block 80404824 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.937476] firefox(7140): READ block 80305576 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.944120] firefox(7140): READ block 80252088 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.954332] firefox(7140): READ block 80292304 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.960518] firefox(7140): READ block 80254600 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.963751] firefox(7140): READ block 80252112 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.971392] firefox(7140): READ block 80254528 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.978209] firefox(7140): READ block 80254504 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.978697] firefox(7140): READ block 80252136 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.988429] firefox(7140): READ block 80254472 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.989185] firefox(7140): READ block 80254456 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.989482] firefox(7140): READ block 80252176 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.990211] firefox(7140): READ block 80254448 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.990967] firefox(7140): READ block 80252216 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.991352] firefox(7140): READ block 80254432 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.992084] firefox(7140): READ block 80308432 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.998817] firefox(7140): READ block 80310152 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.999249] kjournald(2334): WRITE block 251656 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1014.999416] sudo(7243): WRITE block 18155288 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.003941] firefox(7140): READ block 80305312 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.006104] firefox(7140): READ block 80305488 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.009492] firefox(7140): READ block 80254000 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.012863] firefox(7140): READ block 80475944 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.025162] firefox(7140): READ block 80475968 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.025609] firefox(7140): READ block 80250464 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.033485] firefox(7140): READ block 80210088 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.042584] firefox(7140): READ block 80475840 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.048728] firefox(7140): READ block 80302960 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.048988] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.049004] mythbackend(5687): dirtied inode 565614 (mythbackend.log) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.049018] mythbackend(5687): WRITE block 19589320 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.049077] kjournald(2334): WRITE block 17511608 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.049088] kjournald(2334): WRITE block 17503792 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.049098] kjournald(2334): WRITE block 17501592 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.049107] kjournald(2334): WRITE block 17501600 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.049121] kjournald(2334): WRITE block 17503800 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.049129] kjournald(2334): WRITE block 17511616 on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.058234] firefox(7140): READ block 80489880 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.067914] firefox(7140): READ block 80474600 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.073952] firefox(7140): READ block 80302968 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.083307] firefox(7140): READ block 80593528 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.092858] firefox(7140): READ block 80336680 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.103293] firefox(7140): READ block 80252720 on sdb5
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.117881] sudo(7243): dirtied inode 563342 (passdb.tdb) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.118583] syslogd(4899): dirtied inode 522617 (auth.log) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.118600] syslogd(4899): dirtied inode 522617 (auth.log) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.118608] syslogd(4899): dirtied inode 522617 (auth.log) on sdb4
Jan 29 12:16:49 AMD-UB804 kernel: [ 1015.118627] syslogd(4899): WRITE block 17161296 on sdb4
Jan 29 12:17:01 AMD-UB804 /USR/SBIN/CRON[7254]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

I hope this clarifies it more...
To Skymera: I'm not sure what tracker is. Could it be closed down without harm? I am just worried that with so much activity the drive might not last as long as it could. I remember an instance where M/S XP used to index files for quick searches and that drive 'Samsung 250Gb' only lasted 14 months while an identical drive on Mandriva is still going strong after 4 years.... both machines on 24/7.

---

### Post by scragar on 2009-01-28
OK, you really need to add [noparse]```
[/noparse]...
``` tags around that.

Looks like the problem is firefox. Are you low on ram, that would explain firefox using the swap space(sdb5 is probably swap).

---

### Post by randogauci on 2009-01-29
I have 2gb of ram. I will try and stop firefox and compare again.

---

### Post by scragar on 2009-01-29
Might just be firefox accessing a local cache of images, but such heavy usage sounds unlikely, that's why I assumed swap. What are you doing in it?

---

### Post by randogauci on 2009-01-29
> **scragar said:**
> Might just be firefox accessing a local cache of images, but such heavy usage sounds unlikely, that's why I assumed swap. What are you doing in it?
Closed Firefox.. No difference... Just updated to Kernel 2.6.27-11 Generic... still the same!
Would re-installing from scratch help? The problem is I am on limited downloads and all the updates take so much of it and also takes quite some time...

---

### Post by rawlinc on 2009-02-02
Stop your mythbackend end:

```
# /etc/init.d/mythbackend stop
```

Does that fix your problem with your HDD activity? I am trying to debug an issue with mythbackend causing around 10 kjournald writes per second as seen from a block_dump (echo 1 > /proc/sys/vm/block_dump). The hard drive thrashing sounds terrible and I'm sure it isn't doing much for the live of my drive. What is weird is that it doesn't do it all the time. Sometimes it does, sometimes it doesn't. Anyhow, I'm just curious to see if myth is the root of the cause for you too.

I just need to find a _proper_ solution. Some other people in the forums have run into the issue with mythbackend causing excessive hdd activity, but their solution is to uninstall mythtv. That's not really an option for me since my machine is a dedicated mythbackend server :-P.

---

### Post by randogauci on 2009-02-02
> **rawlinc said:**
> Stop your mythbackend end:

```
# /etc/init.d/mythbackend stop
```

Does that fix your problem with your HDD activity? I am trying to debug an issue with mythbackend causing around 10 kjournald writes per second as seen from a block_dump (echo 1 > /proc/sys/vm/block_dump). The hard drive thrashing sounds terrible and I'm sure it isn't doing much for the live of my drive. What is weird is that it doesn't do it all the time. Sometimes it does, sometimes it doesn't. Anyhow, I'm just curious to see if myth is the root of the cause for you too.

I just need to find a _proper_ solution. Some other people in the forums have run into the issue with mythbackend causing excessive hdd activity, but their solution is to uninstall mythtv. That's not really an option for me since my machine is a dedicated mythbackend server :-P.
Hi rawlinc... It worked, IO had to change it to "sudo /etc/init.d/mythtv-backend stop" and no m ore disk activity.. All I need to do now is find a way to stop it starting each time I boot. Any help would be appreciated.
We are travelling, and at times it is difficult to get on the web!
Tanks again.

---

### Post by randogauci on 2009-02-02
> **randogauci said:**
> Hi rawlinc... It worked, IO had to change it to "sudo /etc/init.d/mythtv-backend stop" and no m ore disk activity.. All I need to do now is find a way to stop it starting each time I boot. Any help would be appreciated.
We are travelling, and at times it is difficult to get on the web!
Tanks again.
Hello again
I uninstalled everything to do with Myth TV and everything is OK! I will try and install again when we get back home, I will have a bit more time then to play around a bit more. Thanks again everyone who responded, it is all appreciated..

---

### Post by Zillion on 2009-02-03
Could someone please advise me too how to get rid of constant harddisk activity? I am running a simple Ubuntu server 10 for home use (without GUI), which is most of the time idle. And by the way what are dirties inodes? thanks

```

Feb  3 11:08:20 zillions kernel: [ 2806.716453] kjournald(2230): WRITE block 971538616 on md1
Feb  3 11:08:20 zillions kernel: [ 2806.716466] kjournald(2230): WRITE block 971538624 on md1
Feb  3 11:08:20 zillions kernel: [ 2806.716477] kjournald(2230): WRITE block 971538632 on md1
Feb  3 11:08:20 zillions kernel: [ 2806.716487] kjournald(2230): WRITE block 971538640 on md1
Feb  3 11:08:20 zillions kernel: [ 2806.723792] kjournald(2230): WRITE block 971538648 on md1
Feb  3 11:08:20 zillions kernel: [ 2806.784049] apache2(4629): dirtied inode 33106 (sess_e9bd6826f3971013a8fca4f67b724d98) on md1
Feb  3 11:08:20 zillions kernel: [ 2806.795735] apache2(4629): dirtied inode 33700 (access.log) on md1
Feb  3 11:08:20 zillions kernel: [ 2806.795790] apache2(4629): dirtied inode 33700 (access.log) on md1
Feb  3 11:08:21 zillions kernel: [ 2806.930064] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:21 zillions kernel: [ 2806.930163] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:26 zillions kernel: [ 2812.040067] kjournald(2230): WRITE block 979208 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.040119] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:26 zillions kernel: [ 2812.040209] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:26 zillions kernel: [ 2812.064962] kjournald(2230): WRITE block 1289904 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.064985] kjournald(2230): WRITE block 1290136 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.064995] kjournald(2230): WRITE block 1289912 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.065005] kjournald(2230): WRITE block 1290144 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.065015] kjournald(2230): WRITE block 1163552 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.065025] kjournald(2230): WRITE block 1374408 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.067604] kjournald(2230): WRITE block 971538656 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.067628] kjournald(2230): WRITE block 971538664 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.067638] kjournald(2230): WRITE block 971538672 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.067648] kjournald(2230): WRITE block 971538680 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.067658] kjournald(2230): WRITE block 971538688 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.067669] kjournald(2230): WRITE block 971538696 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.067680] kjournald(2230): WRITE block 971538704 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.067690] kjournald(2230): WRITE block 971538712 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.067699] kjournald(2230): WRITE block 971538720 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.067709] kjournald(2230): WRITE block 971538728 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.071203] kjournald(2230): WRITE block 971538736 on md1
Feb  3 11:08:26 zillions kernel: [ 2812.280059] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:26 zillions kernel: [ 2812.280135] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:31 zillions kernel: [ 2817.040069] kjournald(2230): WRITE block 979208 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.040122] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:31 zillions kernel: [ 2817.040212] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:31 zillions kernel: [ 2817.065009] kjournald(2230): WRITE block 1289912 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.065030] kjournald(2230): WRITE block 1290144 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.065040] kjournald(2230): WRITE block 979216 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.065050] kjournald(2230): WRITE block 1289736 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.065061] kjournald(2230): WRITE block 1163552 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.065070] kjournald(2230): WRITE block 1374408 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067777] kjournald(2230): WRITE block 971538744 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067800] kjournald(2230): WRITE block 971538752 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067810] kjournald(2230): WRITE block 971538760 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067820] kjournald(2230): WRITE block 971538768 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067829] kjournald(2230): WRITE block 971538776 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067838] kjournald(2230): WRITE block 971538784 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067847] kjournald(2230): WRITE block 971538792 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067856] kjournald(2230): WRITE block 971538800 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067866] kjournald(2230): WRITE block 971538808 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067877] kjournald(2230): WRITE block 971538816 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067889] kjournald(2230): WRITE block 971538824 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.067898] kjournald(2230): WRITE block 971538832 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.071849] kjournald(2230): WRITE block 971538840 on md1
Feb  3 11:08:31 zillions kernel: [ 2817.280056] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:31 zillions kernel: [ 2817.280130] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:33 zillions kernel: [ 2819.920179] pdflush(205): WRITE block 0 on md1
Feb  3 11:08:33 zillions kernel: [ 2819.920300] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:33 zillions kernel: [ 2819.920389] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:34 zillions kernel: [ 2819.942835] pdflush(205): WRITE block 794632 on md1
Feb  3 11:08:34 zillions kernel: [ 2819.942860] pdflush(205): WRITE block 795048 on md1
Feb  3 11:08:34 zillions kernel: [ 2819.942876] pdflush(205): WRITE block 968776 on md1
Feb  3 11:08:34 zillions kernel: [ 2819.942906] pdflush(205): WRITE block 1049328 on md1
Feb  3 11:08:34 zillions kernel: [ 2819.942922] pdflush(205): WRITE block 1191232 on md1
Feb  3 11:08:34 zillions kernel: [ 2819.942936] pdflush(205): WRITE block 1318920 on md1
Feb  3 11:08:34 zillions kernel: [ 2820.160054] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:34 zillions kernel: [ 2820.160127] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:36 zillions kernel: [ 2822.040079] kjournald(2230): WRITE block 979216 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.040134] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:36 zillions kernel: [ 2822.040223] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:36 zillions kernel: [ 2822.048813] kjournald(2230): WRITE block 1289912 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.048833] kjournald(2230): WRITE block 1290144 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.048843] kjournald(2230): WRITE block 1289920 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.048853] kjournald(2230): WRITE block 1290152 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.048862] kjournald(2230): WRITE block 1163552 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.048872] kjournald(2230): WRITE block 1374408 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.048881] kjournald(2230): WRITE block 979224 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051406] kjournald(2230): WRITE block 971538848 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051432] kjournald(2230): WRITE block 971538856 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051447] kjournald(2230): WRITE block 971538864 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051459] kjournald(2230): WRITE block 971538872 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051473] kjournald(2230): WRITE block 971538880 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051486] kjournald(2230): WRITE block 971538888 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051498] kjournald(2230): WRITE block 971538896 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051512] kjournald(2230): WRITE block 971538904 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051524] kjournald(2230): WRITE block 971538912 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051536] kjournald(2230): WRITE block 971538920 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051552] kjournald(2230): WRITE block 971538928 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.051565] kjournald(2230): WRITE block 971538936 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.052591] kjournald(2230): WRITE block 971538944 on md1
Feb  3 11:08:36 zillions kernel: [ 2822.260051] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:36 zillions kernel: [ 2822.260123] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:41 zillions kernel: [ 2827.040069] kjournald(2230): WRITE block 979224 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.040130] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:41 zillions kernel: [ 2827.040226] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:41 zillions kernel: [ 2827.065100] kjournald(2230): WRITE block 1289920 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.065118] kjournald(2230): WRITE block 1290152 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.065130] kjournald(2230): WRITE block 1289928 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.065140] kjournald(2230): WRITE block 1290160 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.065153] kjournald(2230): WRITE block 1163552 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.065165] kjournald(2230): WRITE block 1374408 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.066338] kjournald(2230): WRITE block 971538952 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.066353] kjournald(2230): WRITE block 971538960 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.066363] kjournald(2230): WRITE block 971538968 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.066373] kjournald(2230): WRITE block 971538976 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.066382] kjournald(2230): WRITE block 971538984 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.066391] kjournald(2230): WRITE block 971538992 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.066403] kjournald(2230): WRITE block 971539000 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.066412] kjournald(2230): WRITE block 971539008 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.066425] kjournald(2230): WRITE block 971539016 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.066437] kjournald(2230): WRITE block 971539024 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.066947] kjournald(2230): WRITE block 971539032 on md1
Feb  3 11:08:41 zillions kernel: [ 2827.270047] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:41 zillions kernel: [ 2827.270118] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:46 zillions kernel: [ 2832.240541] kjournald(2230): WRITE block 979224 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.240618] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:46 zillions kernel: [ 2832.240714] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:46 zillions kernel: [ 2832.265165] kjournald(2230): WRITE block 1289928 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.265186] kjournald(2230): WRITE block 1290160 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.265197] kjournald(2230): WRITE block 979232 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.265207] kjournald(2230): WRITE block 1163552 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.265217] kjournald(2230): WRITE block 1374408 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.265229] kjournald(2230): WRITE block 1289600 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266564] kjournald(2230): WRITE block 971539040 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266584] kjournald(2230): WRITE block 971539048 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266597] kjournald(2230): WRITE block 971539056 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266607] kjournald(2230): WRITE block 971539064 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266616] kjournald(2230): WRITE block 971539072 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266630] kjournald(2230): WRITE block 971539080 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266639] kjournald(2230): WRITE block 971539088 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266649] kjournald(2230): WRITE block 971539096 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266660] kjournald(2230): WRITE block 971539104 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266669] kjournald(2230): WRITE block 971539112 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266682] kjournald(2230): WRITE block 971539120 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.266693] kjournald(2230): WRITE block 971539128 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.267248] kjournald(2230): WRITE block 971539136 on md1
Feb  3 11:08:46 zillions kernel: [ 2832.470054] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:46 zillions kernel: [ 2832.470127] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:48 zillions kernel: [ 2834.920146] pdflush(205): WRITE block 979232 on md1
Feb  3 11:08:49 zillions kernel: [ 2834.920222] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:49 zillions kernel: [ 2834.920320] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:49 zillions kernel: [ 2834.921727] syslogd(4230): dirtied inode 25073 (syslog) on md1
Feb  3 11:08:49 zillions kernel: [ 2834.942997] syslogd(4230): dirtied inode 25073 (syslog) on md1
Feb  3 11:08:49 zillions kernel: [ 2834.943025] syslogd(4230): dirtied inode 25073 (syslog) on md1
Feb  3 11:08:49 zillions kernel: [ 2834.943046] pdflush(205): WRITE block 1289928 on md1
Feb  3 11:08:49 zillions kernel: [ 2834.943061] syslogd(4230): dirtied inode 24831 (kern.log) on md1
Feb  3 11:08:49 zillions kernel: [ 2834.943077] pdflush(205): WRITE block 1289936 on md1
Feb  3 11:08:49 zillions kernel: [ 2834.943151] syslogd(4230): dirtied inode 24831 (kern.log) on md1
Feb  3 11:08:49 zillions kernel: [ 2834.943167] syslogd(4230): dirtied inode 24831 (kern.log) on md1
Feb  3 11:08:49 zillions kernel: [ 2834.943173] pdflush(205): WRITE block 1290160 on md1
Feb  3 11:08:49 zillions kernel: [ 2834.943204] syslogd(4230): dirtied inode 25273 (debug) on md1
Feb  3 11:08:49 zillions kernel: [ 2834.943211] pdflush(205): WRITE block 1290168 on md1
Feb  3 11:08:49 zillions kernel: [ 2834.943239] syslogd(4230): dirtied inode 25273 (debug) on md1
Feb  3 11:08:49 zillions kernel: [ 2834.943253] syslogd(4230): dirtied inode 25273 (debug) on md1
Feb  3 11:08:49 zillions kernel: [ 2835.150051] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:49 zillions kernel: [ 2835.150124] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:52 zillions kernel: [ 2838.718591] kjournald(2230): WRITE block 979232 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.718691] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:52 zillions kernel: [ 2838.718788] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:52 zillions kernel: [ 2838.743066] kjournald(2230): WRITE block 1289936 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.743089] kjournald(2230): WRITE block 1290168 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.743100] kjournald(2230): WRITE block 1163552 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.743110] kjournald(2230): WRITE block 1374408 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.743119] kjournald(2230): WRITE block 1374416 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.743129] kjournald(2230): WRITE block 979240 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744310] kjournald(2230): WRITE block 971539144 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744327] kjournald(2230): WRITE block 971539152 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744338] kjournald(2230): WRITE block 971539160 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744348] kjournald(2230): WRITE block 971539168 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744358] kjournald(2230): WRITE block 971539176 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744369] kjournald(2230): WRITE block 971539184 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744379] kjournald(2230): WRITE block 971539192 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744389] kjournald(2230): WRITE block 971539200 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744399] kjournald(2230): WRITE block 971539208 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744411] kjournald(2230): WRITE block 971539216 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744421] kjournald(2230): WRITE block 971539224 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744431] kjournald(2230): WRITE block 971539232 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744441] kjournald(2230): WRITE block 971539240 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.744451] kjournald(2230): WRITE block 971539248 on md1
Feb  3 11:08:52 zillions kernel: [ 2838.745130] kjournald(2230): WRITE block 971539256 on md1
Feb  3 11:08:53 zillions kernel: [ 2838.950065] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:53 zillions kernel: [ 2838.950172] md1_raid1(2178): WRITE block 1943752320 on sdb2
Feb  3 11:08:56 zillions kernel: [ 2842.798036] mysqld(4391): dirtied inode 41599 (users.MYD) on md1
Feb  3 11:08:56 zillions kernel: [ 2842.798075] mysqld(4391): dirtied inode 41599 (users.MYD) on md1
Feb  3 11:08:56 zillions kernel: [ 2842.798157] mysqld(4391): dirtied inode 41598 (users.MYI) on md1
Feb  3 11:08:56 zillions kernel: [ 2842.798175] mysqld(4391): dirtied inode 41598 (users.MYI) on md1
Feb  3 11:08:58 zillions kernel: [ 2844.010074] kjournald(2230): WRITE block 979240 on md1
Feb  3 11:08:58 zillions kernel: [ 2844.010146] md1_raid1(2178): WRITE block 1943752320 on sda2
Feb  3 11:08:58 zillions kernel: [ 2844.010242] md1_raid1(2178): WRITE block 1943752320 on sdb2

```

---

### Post by WatchingThePain on 2009-02-03
Get more Ram should do it. Turn of paging or better still..the paging or journal file can be moved to a different volume. Sounds like the drive is getting 'thrashed' trying to make up for lack of RAM.

---

### Post by Zillion on 2009-02-03
> **WatchingThePain said:**
> Get more Ram should do it. Turn of paging or better still..the paging or journal file can be moved to a different volume. Sounds like the drive is getting 'thrashed' trying to make up for lack of RAM.

I have 2GB of ram of which 1700MB is free according to top. 

What would make the difference in moving the journal file to another volume? I have only 2 harddisks, each 1 GB in raid 1.

---

### Post by wesc on 2009-03-12
> **randogauci said:**
> Hello again
I uninstalled everything to do with Myth TV and everything is OK! I will try and install again when we get back home, I will have a bit more time then to play around a bit more. Thanks again everyone who responded, it is all appreciated..

Regarding the myth backend generating massive amounts of disk activity, I believe that is a result of having the daemon running without having successfully completed the MySQL configuration for myth.  I was seeing the exact same problem and getting the myth backend fully configured to successfully access the MySQL database fixed the problem completely.

---

### Post by mtbdrew on 2009-04-28
> **wesc said:**
> Regarding the myth backend generating massive amounts of disk activity, I believe that is a result of having the daemon running without having successfully completed the MySQL configuration for myth.  I was seeing the exact same problem and getting the myth backend fully configured to successfully access the MySQL database fixed the problem completely.

So what did you have to do to complete the MySql setup? I used the Mythbuntu install disk as well as the apt-get to install MythTV and both have the hard drive activity issues.

---

### Post by 99_rover on 2009-04-28
I have the same problem

my dump is

Apr 28 23:36:16 steve-desktop kernel: [49124.516389] pdflush(23): WRITE block 62390280 on sdb2
Apr 28 23:36:16 steve-desktop kernel: [49124.516400] pdflush(23): WRITE block 62390288 on sdb2
Apr 28 23:36:16 steve-desktop kernel: [49124.516408] pdflush(23): WRITE block 62390304 on sdb2
Apr 28 23:36:16 steve-desktop kernel: [49124.516420] pdflush(23): WRITE block 62439552 on sdb2
Apr 28 23:36:17 steve-desktop kernel: [49125.066735] chipcardd4(3541): dirtied inode 4026531840 (mounts) on proc
Apr 28 23:36:21 steve-desktop kernel: [49129.516094] pdflush(23): WRITE block 76735464 on sdb2
Apr 28 23:36:21 steve-desktop kernel: [49129.516157] pdflush(23): WRITE block 76748128 on sdb2
Apr 28 23:36:21 steve-desktop kernel: [49129.520771] syslogd(2709): dirtied inode 4784195 (syslog) on sdb2
Apr 28 23:36:21 steve-desktop kernel: [49129.520802] syslogd(2709): dirtied inode 4784195 (syslog) on sdb2
Apr 28 23:36:21 steve-desktop kernel: [49129.520811] syslogd(2709): dirtied inode 4784195 (syslog) on sdb2
Apr 28 23:36:32 steve-desktop kernel: [49139.712782] chipcardd4(3541): dirtied inode 4026531840 (mounts) on proc
sudo sh -c "echo 0 > /proc/sys/vm/block_dump"
Apr 28 23:36:46 steve-desktop kernel: [49154.516101] pdflush(23): WRITE block 78856328 on sdb2
Apr 28 23:36:46 steve-desktop kernel: [49154.516168] pdflush(23): WRITE block 78856320 on sdb2
Apr 28 23:36:46 steve-desktop kernel: [49154.516204] pdflush(23): WRITE block 77082344 on sdb2
Apr 28 23:36:46 steve-desktop kernel: [49154.516229] pdflush(23): WRITE block 77082336 on sdb2
Apr 28 23:36:46 steve-desktop kernel: [49154.521153] syslogd(2709): dirtied inode 4784388 (kern.log) on sdb2
Apr 28 23:36:46 steve-desktop kernel: [49154.521172] syslogd(2709): dirtied inode 4784388 (kern.log) on sdb2
Apr 28 23:36:46 steve-desktop kernel: [49154.521179] syslogd(2709): dirtied inode 4784388 (kern.log) on sdb2
Apr 28 23:36:46 steve-desktop kernel: [49154.521198] syslogd(2709): dirtied inode 4784443 (debug) on sdb2
Apr 28 23:36:46 steve-desktop kernel: [49154.521209] syslogd(2709): dirtied inode 4784443 (debug) on sdb2
Apr 28 23:36:46 steve-desktop kernel: [49154.521215] syslogd(2709): dirtied inode 4784443 (debug) on sdb2
Apr 28 23:36:47 steve-desktop kernel: [49155.032075] chipcardd4(3541): dirtied inode 4026531840 (mounts) on proc
Apr 28 23:36:56 steve-desktop kernel: [49164.308069] chipcardd4(3541): dirtied inode 4026531840 (mounts) on proc
Apr 28 23:36:56 steve-desktop kernel: [49164.516095] pdflush(23): WRITE block 76748128 on sdb2
Apr 28 23:36:56 steve-desktop kernel: [49164.520577] syslogd(2709): dirtied inode 4784195 (syslog) on sdb2
Apr 28 23:36:56 steve-desktop kernel: [49164.520605] syslogd(2709): dirtied inode 4784195 (syslog) on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.000234] kjournald(735): WRITE block 76748128 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.000278] kjournald(735): WRITE block 78856328 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.000291] kjournald(735): WRITE block 77082344 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001021] kjournald(735): WRITE block 116200 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001055] kjournald(735): WRITE block 116208 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001067] kjournald(735): WRITE block 116216 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001073] kjournald(735): WRITE block 116224 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001078] kjournald(735): WRITE block 116232 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001084] kjournald(735): WRITE block 116240 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001089] kjournald(735): WRITE block 116248 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001094] kjournald(735): WRITE block 116256 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001100] kjournald(735): WRITE block 116264 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001106] kjournald(735): WRITE block 116272 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001111] kjournald(735): WRITE block 116280 on sdb2
Apr 28 23:37:06 steve-desktop kernel: [49174.001954] kjournald(735): WRITE block 116288 on sdb2

Any thoughts??

---

### Post by mtbdrew on 2009-07-20
Anyone know how to correctly setup MySql for MythTV?

---

### Post by mtbdrew on 2009-07-22
Anyone?

---

