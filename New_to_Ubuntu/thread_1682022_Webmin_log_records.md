---
title: "Webmin log records"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by sujeewa on 2011-02-05
Dear All,

our web server(obuntu 8.10 web server) webmin log records are as below.


------------------------------------------------------------------------------------------

Feb  5 09:55:02 firefoxlanka sshd[18660]: Accepted password for user from **[COLOR=red]202.129.232.195[/COLOR]** port 13402 ssh2Feb  5 09:55:02 firefoxlanka sshd[18660]: pam_unix(sshd:session): session opened for user user by (uid=0)Feb  5 09:56:01 firefoxlanka CRON[18812]: pam_unix(cron:session): session opened for user user by (uid=0)Feb  5 09:56:01 firefoxlanka CRON[18812]: pam_unix(cron:session): session closed for user userFeb  5 09:57:01 firefoxlanka CRON[18880]: pam_unix(cron:session): session opened for user user by (uid=0)Feb  5 09:57:01 firefoxlanka CRON[18880]: pam_unix(cron:session): session closed for user userFeb  5 09:58:01 firefoxlanka CRON[18948]: pam_unix(cron:session): session opened for user user by (uid=0)Feb  5 09:58:01 firefoxlanka CRON[18948]: pam_unix(cron:session): session closed for user userFeb  5 09:58:36 firefoxlanka sudo:     user : TTY=pts/0 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/apt-get remove --purge php5Feb  5 09:58:53 firefoxlanka sudo:     user : TTY=pts/0 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/apt-get remove --purge phpFeb  5 09:59:01 firefoxlanka CRON[19019]: pam_unix(cron:session): session opened for user user by (uid=0)Feb  5 09:59:01 firefoxlanka CRON[19019]: pam_unix(cron:session): session closed for user userFeb  5 09:59:31 firefoxlanka sudo:     user : TTY=pts/0 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/apt-get remove --purge php5.0Feb  5 09:59:42 firefoxlanka sudo:     user : TTY=pts/0 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/apt-get remove --purge phpFeb  5 10:00:01 firefoxlanka CRON[19106]: pam_unix(cron:session): session opened for user user by (uid=0)Feb  5 10:00:01 firefoxlanka CRON[19105]: pam_unix(cron:session): session opened for user root by (uid=0)Feb  5 10:00:01 firefoxlanka CRON[19106]: pam_unix(cron:session): session closed for user userFeb  5 10:00:01 firefoxlanka CRON[19105]: pam_unix(cron:session): session closed for user rootFeb  5 10:00:41 firefoxlanka sudo:     user : TTY=pts/0 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/apt-get remove --purge php-cliFeb  5 10:00:53 firefoxlanka sudo:     user : TTY=pts/0 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/apt-get remove --purge php5-cliFeb  5 10:01:01 firefoxlanka CRON[19196]: pam_unix(cron:session): session opened for user user by (uid=0)Feb  5 10:01:01 firefoxlanka CRON[19196]: pam_unix(cron:session): session closed for user userFeb  5 10:01:14 firefoxlanka sudo:     user : TTY=pts/0 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/apt-get remove --purge php5-mysqlFeb  5 10:01:55 firefoxlanka sudo:     user : TTY=pts/0 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/apt-get remove --purge php5-commonFeb  5 10:02:01 firefoxlanka CRON[19456]: pam_unix(cron:session): session opened for user user by (uid=0)Feb  5 10:02:01 firefoxlanka CRON[19456]: pam_unix(cron:session): session closed for user userFeb  5 10:03:01 firefoxlanka CRON[19587]: pam_unix(cron:session): session opened for user user by (uid=0)Feb  5 10:03:01 firefoxlanka CRON[19587]: pam_unix(cron:session): session closed for user userFeb  5 10:04:01 firefoxlanka CRON[19655]: pam_unix(cron:session): session opened for user user by (uid=0)

---------------------------------------------------------------------------

please help me to understand above records.

Thanks in advance.

---

### Post by kellemes on 2011-02-05
It seems someone has been purging php from the system using the webmin interface.

---

