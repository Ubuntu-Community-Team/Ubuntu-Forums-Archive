---
title: "proftpd execute file"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by vizenmaster on 2007-04-07
Hi I was successfully setup my proftpd server that let me access from outside and in LAN. I did couple transferring to the server then I check the log. there are no logs of any connection that I made today. This is my log setup in /etc//proftpd/proftpd.conf

ScoreboardFile /var/run/proftpd.scoreboard
SystemLog /var/log/proftpd.sys
TransferLog /var/log/proftpd.xfer
ServerLog /var/log/proftpd.serv

This is the last lines on /var/log/proftpd/proftpd.log
Apr 06 23:16:12 ubuntu proftpd[6073] localhost: ProFTPD killed (signal 15)
Apr 06 23:16:12 ubuntu proftpd[6073] localhost: ProFTPD 1.3.0 standalone mode SHUTDOWN

please help, thank you

---

