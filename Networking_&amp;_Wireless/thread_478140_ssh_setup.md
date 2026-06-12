---
title: "ssh setup"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by louislepperd on 2007-06-19
hi ive installed ssh and made my router ford port 22 to my computer and i can access it from another  windows computer on my network my cant open it over the internet
can anyone help
thanks in advance louis

---

### Post by zanglang on 2007-06-19
Is your network behind a router? If so, you'll have to forward port 22 from your router web interface to the computer SSH is on.

If you're not familiar with port forwarding, check your router model and look for guides on this site:
[http://portforward.com/](http://portforward.com/)

---

### Post by louislepperd on 2007-06-19
yes Ive already done that
any other ideas
thanks in advance 
Louis

---

### Post by scxtt on 2007-06-19
if you're absolutely sure you've forwarded port 22 to the INTERNAL network IP of the ssh-server, then maybe your ISP isn't playing nice ... some block port 80, maybe yours blocks 22 ...

or you messed up :p

---

### Post by Mr. C. on 2007-06-19
louislepperd,

Instead of having us guess why this isn't working, show your commands and output so that we can evaluate what is wrong.  Let's see:
[LIST]
[*]output from a **remote** telnet session to port 22 (telnet WAN_IP 22)
[*] entries from /var/log/auth.log
[*]output of netstat -nl --tcp
[/LIST]
MrC

---

### Post by louislepperd on 2007-06-19
i think i messed up
because my friend was able to do it
thanks in advance
louis

---

### Post by louislepperd on 2007-06-19
output of netstat -nl --tcp

netstat -nl --tcp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:6881            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:837             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:59837           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:44989           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     

-------------------------------------------------------------------------------------
entries from /var/log/auth.log

Jun 18 16:17:01 louis-ubuntu CRON[7003]: (pam_unix) session opened for user root by (uid=0)
Jun 18 16:17:01 louis-ubuntu CRON[7003]: (pam_unix) session closed for user root
Jun 18 17:17:01 louis-ubuntu CRON[8483]: (pam_unix) session opened for user root by (uid=0)
Jun 18 17:17:01 louis-ubuntu CRON[8483]: (pam_unix) session closed for user root
Jun 18 18:17:01 louis-ubuntu CRON[9954]: (pam_unix) session opened for user root by (uid=0)
Jun 18 18:17:01 louis-ubuntu CRON[9954]: (pam_unix) session closed for user root
Jun 18 19:17:01 louis-ubuntu CRON[11421]: (pam_unix) session opened for user root by (uid=0)
Jun 18 19:17:01 louis-ubuntu CRON[11421]: (pam_unix) session closed for user root
Jun 18 20:17:01 louis-ubuntu CRON[12884]: (pam_unix) session opened for user root by (uid=0)
Jun 18 20:17:01 louis-ubuntu CRON[12884]: (pam_unix) session closed for user root
Jun 18 21:17:01 louis-ubuntu CRON[14400]: (pam_unix) session opened for user root by (uid=0)
Jun 18 21:17:01 louis-ubuntu CRON[14400]: (pam_unix) session closed for user root
Jun 18 21:17:33 louis-ubuntu gdm[5187]: (pam_unix) session closed for user louis
Jun 19 07:32:46 louis-ubuntu gdm[5179]: (pam_unix) session opened for user louis by (uid=0)
Jun 19 08:17:01 louis-ubuntu CRON[7341]: (pam_unix) session opened for user root by (uid=0)
Jun 19 08:17:01 louis-ubuntu CRON[7341]: (pam_unix) session closed for user root
Jun 19 08:20:09 louis-ubuntu gnome-screensaver-dialog: (pam_unix) authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=louis
Jun 19 09:17:01 louis-ubuntu CRON[8793]: (pam_unix) session opened for user root by (uid=0)
Jun 19 09:17:01 louis-ubuntu CRON[8793]: (pam_unix) session closed for user root
Jun 19 10:17:01 louis-ubuntu CRON[10240]: (pam_unix) session opened for user root by (uid=0)
Jun 19 10:17:01 louis-ubuntu CRON[10240]: (pam_unix) session closed for user root
Jun 19 11:17:01 louis-ubuntu CRON[11684]: (pam_unix) session opened for user root by (uid=0)
Jun 19 11:17:01 louis-ubuntu CRON[11684]: (pam_unix) session closed for user root
Jun 19 12:17:01 louis-ubuntu CRON[13126]: (pam_unix) session opened for user root by (uid=0)
Jun 19 12:17:01 louis-ubuntu CRON[13126]: (pam_unix) session closed for user root
Jun 19 13:17:01 louis-ubuntu CRON[14573]: (pam_unix) session opened for user root by (uid=0)
Jun 19 13:17:01 louis-ubuntu CRON[14573]: (pam_unix) session closed for user root
Jun 19 14:17:01 louis-ubuntu CRON[16019]: (pam_unix) session opened for user root by (uid=0)
Jun 19 14:17:01 louis-ubuntu CRON[16019]: (pam_unix) session closed for user root
Jun 19 15:17:01 louis-ubuntu CRON[17457]: (pam_unix) session opened for user root by (uid=0)
Jun 19 15:17:01 louis-ubuntu CRON[17457]: (pam_unix) session closed for user root
Jun 19 15:54:05 louis-ubuntu sudo:    louis : TTY=unknown ; PWD=/home/louis ; USER=root ; COMMAND=/usr/sbin/synaptic
Jun 19 15:56:32 louis-ubuntu useradd[18497]: new user: name=sshd, UID=114, GID=65534, home=/var/run/sshd, shell=/usr/sbin/nologin
Jun 19 15:56:32 louis-ubuntu chage[18498]: changed password expiry for sshd
Jun 19 15:56:32 louis-ubuntu sshd[18528]: Server listening on :: port 22.
Jun 19 15:59:09 louis-ubuntu sshd[18609]: Accepted password for louis from 192.168.8.22 port 1067 ssh2
Jun 19 15:59:09 louis-ubuntu sshd[18625]: (pam_unix) session opened for user louis by (uid=0)
Jun 19 16:03:02 louis-ubuntu sshd[18625]: (pam_unix) session closed for user louis
Jun 19 16:03:22 louis-ubuntu sshd[18743]: Accepted password for louis from 192.168.8.22 port 1076 ssh2
Jun 19 16:03:22 louis-ubuntu sshd[18751]: (pam_unix) session opened for user louis by (uid=0)
Jun 19 16:06:29 louis-ubuntu sudo:    louis : TTY=pts/1 ; PWD=/home/louis ; USER=root ; COMMAND=/usr/bin/gedit
Jun 19 16:07:03 louis-ubuntu sshd[18751]: (pam_unix) session closed for user louis
Jun 19 16:07:52 louis-ubuntu sshd[18955]: Accepted password for louis from 192.168.8.22 port 1080 ssh2
Jun 19 16:07:52 louis-ubuntu sshd[18961]: (pam_unix) session opened for user louis by (uid=0)
Jun 19 16:09:24 louis-ubuntu sshd[18961]: (pam_unix) session closed for user louis
Jun 19 16:12:26 louis-ubuntu sshd[19109]: Accepted password for louis from 192.168.8.22 port 1089 ssh2
Jun 19 16:12:26 louis-ubuntu sshd[19115]: (pam_unix) session opened for user louis by (uid=0)
Jun 19 16:12:39 louis-ubuntu sshd[19115]: (pam_unix) session closed for user louis
Jun 19 16:17:01 louis-ubuntu CRON[19251]: (pam_unix) session opened for user root by (uid=0)
Jun 19 16:17:01 louis-ubuntu CRON[19251]: (pam_unix) session closed for user root
Jun 19 16:59:03 louis-ubuntu sudo:    louis : TTY=unknown ; PWD=/home/louis ; USER=root ; COMMAND=/usr/sbin/synaptic
Jun 19 17:05:28 louis-ubuntu sshd[20584]: Accepted password for louis from 192.168.8.22 port 4096 ssh2
Jun 19 17:05:28 louis-ubuntu sshd[20590]: (pam_unix) session opened for user louis by (uid=0)
Jun 19 17:17:01 louis-ubuntu CRON[20922]: (pam_unix) session opened for user root by (uid=0)
Jun 19 17:17:01 louis-ubuntu CRON[20922]: (pam_unix) session closed for user root
Jun 19 17:22:37 louis-ubuntu sshd[20590]: (pam_unix) session closed for user louis
Jun 19 18:17:01 louis-ubuntu CRON[22465]: (pam_unix) session opened for user root by (uid=0)
Jun 19 18:17:01 louis-ubuntu CRON[22465]: (pam_unix) session closed for user root
Jun 19 18:23:20 louis-ubuntu sshd[22628]: Accepted password for louis from 192.168.8.22 port 4328 ssh2
Jun 19 18:23:20 louis-ubuntu sshd[22636]: (pam_unix) session opened for user louis by (uid=0)
Jun 19 18:23:46 louis-ubuntu sshd[22636]: (pam_unix) session closed for user louis
Jun 19 19:17:01 louis-ubuntu CRON[23989]: (pam_unix) session opened for user root by (uid=0)
Jun 19 19:17:01 louis-ubuntu CRON[23989]: (pam_unix) session closed for user root
Jun 19 20:17:01 louis-ubuntu CRON[25449]: (pam_unix) session opened for user root by (uid=0)
Jun 19 20:17:01 louis-ubuntu CRON[25449]: (pam_unix) session closed for user root
Jun 19 21:17:01 louis-ubuntu CRON[26916]: (pam_unix) session opened for user root by (uid=0)
Jun 19 21:17:01 louis-ubuntu CRON[26916]: (pam_unix) session closed for user root
Jun 19 22:17:01 louis-ubuntu CRON[28366]: (pam_unix) session opened for user root by (uid=0)
Jun 19 22:17:01 louis-ubuntu CRON[28366]: (pam_unix) session closed for user root
Jun 19 23:17:01 louis-ubuntu CRON[29814]: (pam_unix) session opened for user root by (uid=0)
Jun 19 23:17:01 louis-ubuntu CRON[29814]: (pam_unix) session closed for user root
Jun 20 00:17:01 louis-ubuntu CRON[31251]: (pam_unix) session opened for user root by (uid=0)
Jun 20 00:17:01 louis-ubuntu CRON[31251]: (pam_unix) session closed for user root
Jun 20 01:17:01 louis-ubuntu CRON[32697]: (pam_unix) session opened for user root by (uid=0)
Jun 20 01:17:01 louis-ubuntu CRON[32697]: (pam_unix) session closed for user root
Jun 20 02:17:01 louis-ubuntu CRON[1675]: (pam_unix) session opened for user root by (uid=0)
Jun 20 02:17:01 louis-ubuntu CRON[1675]: (pam_unix) session closed for user root
Jun 20 03:17:01 louis-ubuntu CRON[3126]: (pam_unix) session opened for user root by (uid=0)
Jun 20 03:17:01 louis-ubuntu CRON[3126]: (pam_unix) session closed for user root
Jun 20 04:17:01 louis-ubuntu CRON[4583]: (pam_unix) session opened for user root by (uid=0)
Jun 20 04:17:01 louis-ubuntu CRON[4583]: (pam_unix) session closed for user root
Jun 20 05:17:01 louis-ubuntu CRON[6130]: (pam_unix) session opened for user root by (uid=0)
Jun 20 05:17:01 louis-ubuntu CRON[6130]: (pam_unix) session closed for user root
Jun 20 06:17:01 louis-ubuntu CRON[7568]: (pam_unix) session opened for user root by (uid=0)
Jun 20 06:17:02 louis-ubuntu CRON[7568]: (pam_unix) session closed for user root
Jun 20 06:25:01 louis-ubuntu CRON[7764]: (pam_unix) session opened for user root by (uid=0)
Jun 20 06:25:01 louis-ubuntu CRON[7764]: (pam_unix) session closed for user root
Jun 20 07:17:01 louis-ubuntu CRON[9016]: (pam_unix) session opened for user root by (uid=0)
Jun 20 07:17:01 louis-ubuntu CRON[9016]: (pam_unix) session closed for user root
Jun 20 07:30:01 louis-ubuntu CRON[9332]: (pam_unix) session opened for user root by (uid=0)
Jun 20 07:30:02 louis-ubuntu CRON[9332]: (pam_unix) session closed for user root
Jun 20 08:17:01 louis-ubuntu CRON[10647]: (pam_unix) session opened for user root by (uid=0)
Jun 20 08:17:01 louis-ubuntu CRON[10647]: (pam_unix) session closed for user root
Jun 20 08:38:58 louis-ubuntu gnome-screensaver-dialog: (pam_unix) authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=louis
Jun 20 09:17:01 louis-ubuntu CRON[12105]: (pam_unix) session opened for user root by (uid=0)
Jun 20 09:17:01 louis-ubuntu CRON[12105]: (pam_unix) session closed for user root
Jun 20 10:17:01 louis-ubuntu CRON[13552]: (pam_unix) session opened for user root by (uid=0)
Jun 20 10:17:01 louis-ubuntu CRON[13552]: (pam_unix) session closed for user root
Jun 20 11:17:01 louis-ubuntu CRON[14997]: (pam_unix) session opened for user root by (uid=0)
Jun 20 11:17:01 louis-ubuntu CRON[14997]: (pam_unix) session closed for user root
Jun 20 11:43:12 louis-ubuntu sshd[5612]: Server listening on :: port 22.
Jun 20 12:17:01 louis-ubuntu CRON[5882]: (pam_unix) session opened for user root by (uid=0)
Jun 20 12:17:01 louis-ubuntu CRON[5882]: (pam_unix) session closed for user root
Jun 20 13:17:01 louis-ubuntu CRON[5885]: (pam_unix) session opened for user root by (uid=0)
Jun 20 13:17:01 louis-ubuntu CRON[5885]: (pam_unix) session closed for user root
Jun 20 14:17:01 louis-ubuntu CRON[5888]: (pam_unix) session opened for user root by (uid=0)
Jun 20 14:17:01 louis-ubuntu CRON[5888]: (pam_unix) session closed for user root
Jun 20 15:04:01 louis-ubuntu gdm[5336]: (pam_unix) session opened for user louis by (uid=0)
Jun 20 15:14:30 louis-ubuntu sudo:    louis : TTY=pts/0 ; PWD=/home/louis ; USER=root ; COMMAND=/usr/bin/gedit
Jun 20 15:17:01 louis-ubuntu CRON[6656]: (pam_unix) session opened for user root by (uid=0)
Jun 20 15:17:01 louis-ubuntu CRON[6656]: (pam_unix) session closed for user root
Jun 20 15:19:35 louis-ubuntu gdm[5336]: (pam_unix) session closed for user louis
Jun 20 15:21:17 louis-ubuntu sshd[5389]: Server listening on 0.0.0.0 port 22.
Jun 20 15:25:57 louis-ubuntu gdm[5107]: (pam_unix) session opened for user louis by (uid=0)

---------------------------------------------------------------------------------------------------
output from a remote telnet session to port 22 (telnet WAN_IP 22)
how do i do this?
also remember i was able to access it from other computers on my net work when i used my local ip 
address 
thanks in advance
louis

---

### Post by Mr. C. on 2007-06-20
I can see from your logs that you are able to ssh connect locatlly.

I can see also that SSH is listening on all network interfaces.

This leaves a firewall to be the culprit in preventing remote access.

Get to a remote machine.  If linux/unix, just use ssh YOURWANIP.  Look at your logs to see if the connection is being made or attempted.  If Windows, Start->Run and enter cmd.  Run :

telnet YOURWANIP 22

and check your logs for access.  If you have access to the firewall logs, see if there are entries regarding this connection attempt.

MrC

---

