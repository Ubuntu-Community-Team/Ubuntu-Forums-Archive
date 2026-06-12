---
title: "list unsuccessful connection attempts"
date: 2023-12-17
forum: Networking &amp; Wireless
---

### Post by dieter-erich on 2023-12-17
Hi,
    how can I list all (unsuccessful) attempt at accessing my ubuntu mate 22.04 box from the internet? All I tried (ie.g. "last" and number of scripts extracting info from the log files) failed to reveal e.g. wrong PW entries. For example, when I tried to ssh in my box from remote by using a wrong PW this does not figure in the list. I'd like to get IP address , time of access-attempt, port number and eventually the country of origin. On an old machine I registered many such attempts and now I see none, which appears very suspect.
Thanx for hints and forgive me if you find another post with a similar text that I thought to have posed but coul not find anymore!

---

### Post by TheFu on 2023-12-17
You can enable firewall logging, but beware, you will quickly fill up all storage with that.  Monitoring every port that does nothing bad to the overall security of your system isn't an effective use of time.  Being more selective about the stuff you look for - based on the network services you actually run - would be smarter.  For example, I look for ssh attempts and use fail2ban to block abusive attempts for a week after they make just a few failed attempts.  

I had to reboot today due to a UPS failure, but here's the current ssh-banned count.
```
$ fail2ban-ban-list 
Total Bans:
1800
Unique Bans:
595
```

That count is after just 2h47m and just for ssh. Nothing else.

Every different method of access will have different logs, but you might be able to look at the log journals using **journalctl** with a compound regex to get what you seek.  All text-based logs are really provided by the log journals introduced with systemd on Ubuntu around 2016.  Journalctl is an amazing tool, so I'd encourage you do use that rather than grepping text logs.

---

### Post by Doug S on 2023-12-17
> **dieter-erich said:**
> For example, when I tried to ssh in my box from remote by using a wrong PW this does not figure in the list. I'd like to get IP address , time of access-attempt, port number and eventually the country of origin.

Your example should have resulted in a few lines of information in /var/log/auth.log. Example:

```
Dec 17 08:28:18 s19 sshd[26380]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.111.122  user=doug
Dec 17 08:28:18 s19 sshd[26380]: pam_winbind(sshd:auth): getting password (0x00000388)
Dec 17 08:28:18 s19 sshd[26380]: pam_winbind(sshd:auth): pam_get_item returned a password
Dec 17 08:28:18 s19 sshd[26380]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_AUTH_ERR (7), NTSTATUS: NT_STATUS_WRONG_PASSWORD, Error message was: When trying to update a password, this return status indicates that the value provided as the current password is not correct.
Dec 17 08:28:18 s19 sshd[26380]: pam_winbind(sshd:auth): user 'doug' denied access (incorrect password or invalid membership)
Dec 17 08:28:20 s19 sshd[26380]: Failed password for doug from 192.168.111.122 port 56663 ssh2
Dec 17 08:28:25 s19 sshd[26380]: pam_winbind(sshd:auth): getting password (0x00000388)
Dec 17 08:28:25 s19 sshd[26380]: pam_winbind(sshd:auth): pam_get_item returned a password
Dec 17 08:28:25 s19 sshd[26380]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_AUTH_ERR (7), NTSTATUS: NT_STATUS_WRONG_PASSWORD, Error message was: When trying to update a password, this return status indicates that the value provided as the current password is not correct.
Dec 17 08:28:25 s19 sshd[26380]: pam_winbind(sshd:auth): user 'doug' denied access (incorrect password or invalid membership)
Dec 17 08:28:27 s19 sshd[26380]: Failed password for doug from 192.168.111.122 port 56663 ssh2
Dec 17 08:28:33 s19 sshd[26380]: pam_winbind(sshd:auth): getting password (0x00000388)
Dec 17 08:28:33 s19 sshd[26380]: pam_winbind(sshd:auth): pam_get_item returned a password
Dec 17 08:28:33 s19 sshd[26380]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_AUTH_ERR (7), NTSTATUS: NT_STATUS_WRONG_PASSWORD, Error message was: When trying to update a password, this return status indicates that the value provided as the current password is not correct.
Dec 17 08:28:33 s19 sshd[26380]: pam_winbind(sshd:auth): user 'doug' denied access (incorrect password or invalid membership)
Dec 17 08:28:35 s19 sshd[26380]: Failed password for doug from 192.168.111.122 port 56663 ssh2
Dec 17 08:28:37 s19 sshd[26380]: Connection reset by authenticating user doug 192.168.111.122 port 56663 [preauth]
Dec 17 08:28:37 s19 sshd[26380]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.111.122  user=doug
```

---

### Post by dieter-erich on 2023-12-18
Thanx, I understand! So, I would also be happy with just getting login attempts on port 22. But how do I **find out the IP address** of the failed attempt? I only get:

xxx@XXXX:/var/log$ cat auth.log|grep failed
Dec 17 16:41:33 XXXX unix_chkpwd[654440]: password check failed for user (xxxx)

or

cat auth.log|grep Failed
Dec 17 08:54:30 XXXX sudo:    xxx : TTY=pts/5 ; PWD=/home/xxx ; USER=root ; COMMAND=/usr/bin/grep 'Failed password' /var/log/auth.log
Dec 17 09:38:33 XXXX sudo:    xxx : TTY=pts/4 ; PWD=/var/log ; USER=root ; COMMAND=/usr/bin/grep 'Failed password' /var/log/auth.log
Dec 17 09:39:39 XXXX sudo:    xxx : TTY=pts/4 ; PWD=/var/log ; USER=root ; COMMAND=/usr/bin/grep 'Failed password' /var/log/auth.log
Dec 17 11:35:12 XXXX sudo:    xxx : TTY=pts/4 ; PWD=/home/xxx ; USER=root ; COMMAND=/usr/bin/grep 'sshd.*Failed password' /var/log/auth.log
Dec 17 11:51:08 XXXX dbus-daemon[44685]: [session uid=1000 pid=44683] Failed to activate service 'org.freedesktop.secrets': timed out (service_start_timeout=120000ms)

---

### Post by TheFu on 2023-12-18
**fail2ban** logs this.  The script that provided my summary above just counts lines, but it looks for IP addresses.
```

echo "Total Bans:"
egrep NOTICE /var/log/fail2ban.log* |egrep Ban | egrep -o '[12]?[0-9]?[0-9]\.[12]?[0-9]?[0-9]\.[12]?[0-9]?[0-9]\.[12]?[0-9]?[0-9]' | sort -h |wc -l

echo "Unique Bans:"
egrep NOTICE /var/log/fail2ban.log* |egrep Ban | egrep -o '[12]?[0-9]?[0-9]\.[12]?[0-9]?[0-9]\.[12]?[0-9]?[0-9]\.[12]?[0-9]?[0-9]' | sort -hu |wc - l
```

Just don't count the lines to see the sorted IP address list.

```
...
218.107.37.70
218.211.171.143
218.211.171.143
218.255.245.10
218.255.245.10
220.205.122.62
220.205.122.62
220.247.223.56
220.247.223.56
220.71.74.158
220.71.74.158
222.124.177.148
222.124.177.148
222.127.106.130
222.127.106.130
222.127.151.169
222.127.151.169
222.173.219.2
222.173.219.2
222.211.70.20
222.237.78.200
223.17.0.181
223.17.0.181
```
is a sample. This only works for fail2ban logs and I think I've only set that up for ssh.  Tweak the script as you like to get the results you want.

---

### Post by dieter-erich on 2023-12-18
thanx! I installed fail2ban and run each of your scripts. In both cases I always get "0" Is this normal?

---

### Post by dieter-erich on 2023-12-18
Sorry, I just realized that I set ssh to an unconventional port. 
even grep NOTICE /var/log/fail2ban.log* doesn't show anything
So, it seems that I am quite save. Correct?

---

### Post by TheFu on 2023-12-18
> **dieter-erich said:**
> thanx! I installed fail2ban and run each of your scripts. In both cases I always get "0" Is this normal?

Depends on the system.  For my systems that don't have internet, but do have ssh, I still have fail2ban installed as added protection against my own stupidity.  Also, if you've changed the defaults for sshd, then I wouldn't expect it to work.

OTOH, for my internet-facing servers that have ssh, I see many, many, failures.  Play around with the commands, see what they do. Learn. Customize the output for your needs.

For example, today on a VPS that I run, 
```
$ ./fail2ban-ban-list 
Total Bans:
1323
Unique Bans:
694

```
It is a gateway system for many of my other services that run inside my home LAN, but need a public face that isn't a residential internet connection.

---

### Post by TheFu on 2023-12-18
> **dieter-erich said:**
> Sorry, I just realized that I set ssh to an unconventional port. 
even grep NOTICE /var/log/fail2ban.log* doesn't show anything
So, it seems that I am quite save. Correct?

No.  The internet isn't dumb. They trivially find ssh on any ports.  For my home system, I don't listen on the public IP on port 22/tcp either.  If I did, the numbers would be 1000x higher.

Security through obfuscation isn't a bad idea, but never trust it.  You aren't as smart as you think. ;) .... and neither am I.

---

### Post by dieter-erich on 2023-12-19
OK, but then fail2ban should at least show something! But there is nothing at all!

---

### Post by TheFu on 2023-12-19
> **dieter-erich said:**
> OK, but then fail2ban should at least show something! But there is nothing at all!

It only does what you tell it to do.  If you change where it is supposed to look and that doesn't match what it thinks, whose fault is that?

fail2ban is a generic tool for watching logs, dynamically creating firefall block rules that last for a configured period, then get removed. sshd watching wasn't the main reason it was created. It happens to work with it and with defaults, it is pre-configured to work.  If we change the defaults, it can't be expected to work.

Computers do what we ask, not what we mean.

Or

perhaps your system wasn't found on the internet and the attacks didn't start at the time?  Unlikely, but maybe.  Manually check the logs.  Perhaps your logs aren't in the format fail2ban expects?  I've not had that issue with sshd, but maybe you are running a newer version on a newer OS than I?

---

