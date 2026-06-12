---
title: "Automatic and scheduled pppoe (DSL) connection manager"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by ario on 2008-05-06
Hi every body.
I have released a free and open source bash script in sourceforge.net to manage your pppoe connections and reconnect them if dropped, full scheduled and automatically.

You can download this from:
[https://sourceforge.net/projects/autoppp/](https://sourceforge.net/projects/autoppp/)


Heres the release notes:
```

This release is tested under Ubuntu 7.10 and 8.04.
Script connects automatically to ppp peer dsl-provider by running command 
pon dsl-provider. but from 3 o'clock to 7 o'clock every they this will connect to a
secondary ppp connection file named: fdsl-provider. this will be helpfull if you have an
 alternate connection to automatically connect to it at night maybe for nightmare
 downloading.

Make two proper account
=============================
You should make to proper account to use with autoppp.
So if you already have the dsl-provider account start here and use "pppoeconf" command
to create you DSL account again but this time be sure to disable "Turn on this account
 at boot time" at the end of blue screen wizard. then goto "/etc/ppp/peers" in a
 superuser nautilus by running command: "gksudo nautilus" and then make a backup copy of
 your newly created dsl-provider file by copy and then paste it at the same folder. New 
file must be named: "dsl-provider (copy). repeat steps above and create new DSL account 
by pppoeconf and again say NO to "Enable this account automatically at boot time..." at
 the end of wizard. go to "/etc/ppp/peers" in a superuser nautilus by running command:
 "gksudo nautilus" and you will see your new dsl-provider file and your previously 
backup of "dsl-provider (copy)". Rename one of these files by selecting it and press F2 
in nautilus to "fdsl-provider" for nightmare connection and one other to "dsl-provider"
 for normal daily connection. script use these files as its two alternate connections.


Automatic running script:
=============================
No you should schedule autoppp script to run whenever system starts. You can use it by 
extract autoppp file from this archive to for example your home directory and make a 
startup link for this shell script file in you session manager (System\Preferences\Sessions).

Automatic shutdown scheduling
=============================
you may schedule your computer to shutdown automatically for example at 7 o'clock to 
prevent your scheduled downloads to use your premium daily account bandwith after 7 
o'clock. For this you may run command: "sudo crontab -e" at a terminal and add the line:
00 07 * * * /sbin/shutdown -P now
please note the capital P at the end of command. I think the "P" after command must 
typed by pressing shift our caps-lock.

Automatic connection check
=============================
Script also checks internet connections 10 seconds after each connecting to dsl-provider
 or fdsl-provider by pinging www.google.com (The poor google:D ). if ping failed you may
 disconnected our pon failed. so script disconnects and reconnects again and again until
 make your connection stable. it will check again your connection each 1 minute.
you can change all settings of timers (for example one minutes or 10 seconds) and DSL 
account names at the first lines of script.

Log File
=============================
You can see scripts log file at same directory you extracted script. Log file is: "autoppp.log"

```
Please don't forget to report bugs in source forge page and your very valuable nice comments here.
Good Luck!

---

### Post by legolas_w on 2008-06-24
Thank you for your script and I think it will resolve my problem too.
Can you please explain whether you have USB modem or ethernet modem?

I tried to use pppoeconf in order to create the pppoe connection but it say that it can not find ppoe provider.

right now I configured my modem to connect to the adsl provider and I use Ethernet mode.


Thanks

---

### Post by ario on 2010-07-10
I'm using ethernet mode too. So the problem seems not to be related to autoppp script.
You can find a solution for your problem if you search more in this site:)

---

### Post by bazerka on 2010-11-09
Does this work with Ubuntu v. 10.10?

---

