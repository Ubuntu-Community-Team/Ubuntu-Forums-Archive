---
title: "vsftpd timeout problems"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by xunthait on 2011-05-21
Hello,

I am a newbie with Linux. Okay... I played around with some desktop  Ubuntu versions and everything was.. "nice", but - I am ashame - I am a  Windows User :-)

Now I wanted to setup a server with Apache and vsftpd, all configured  and controlled over SSH. An rather crazy experiment for a newbie, but I  am nearly through it on my own. The main reason for this is the old  hardware: Pm 1,5Ghz, 512MB RAM, 8GB USB-Stick as HDD.

Apache is running well, vsftpd is installed and running, all fine.

Long time I didnt get a file via FTP to the server, because of a critic  failure. Several configurations on the vsftpd.conf-file and hours of  reading in the world wide web and I found the problem: As easy, as I  ever would have thought... chmod 777 ftp-dir.

Now the ftp works fine and impressing quick, but I have the following  problem: The timeout is within 5 seconds, also while transferring files.  Therefore it doesnt matter, whether the connection is idled or a  transfer is running.

So a huger file starts to transfer for 5 seconds and the connection is  closed. Resuming the transfer works fine, but it shouldnt be, that the  files are transferred with 10MB/s for 5s, the reconnect takes also about  5s and then the transfer is resumed. Especially, when later on the ftp  is connected from outside.

Has anybody an idea?

The vsftpd.conf-file:
listen=YES
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem

The log-file tells, that all is fine...

I am connecting from a Windows Box with Filezilla.

FileZilla tells (translated):
Connecting, Welcome message, Answer 220 Welcome ....
USER ----
331 Please specify the password.
PASS ----
226 Transfer complete.
230 Login successful.
OPTS UFT8 ON
200 Always in UTF8 mode.
Connected.
Start Upload of file
CWD /var/www
250 Directory successfully changed.
TYPE I
200 Switching to Binary mode.
PASV
227 Entering Passive Mode (192,168,x,x,227,187)
APPE file
150 Ok to send data.
226 Tranfser complete.

Between the last two lines the transfer stops after a few seconds,  FileZilla waits for a few seconds without transfer and then tries a  reconnect to resume the transfer.


Thank you very much in advance and sorry about my bad English, I am from Germany...

---

### Post by ApOgEEs on 2011-05-26
Vsftpd has two settings for timeout in the configuration file.

```
idle_session_timeout=600
data_connection_timeout=120
```

Uncomment these settings and make whatever changes you want regarding timeout.

---

### Post by xunthait on 2011-05-26
Thank you for the tip. The problem is even stranger...

First of all, is a time about 5-10s also far to low for the standard values?

Secondly... The problem occures only in the inner network. When starting a ftp-upload from an outside pc, the connection is stable und works fine. Within the own network not.

So it could be the router, or? But is there a possibility, that there are disconnects or problems working with the 100MBit/s network - reaching about 80MBit/s and all is fine when using the outside internet connection - limited to 1MBit/s connection? Also the router works with Linux (but no DD-WRT or OpenWRT, the original FW).

Strange thing...

---

### Post by bioterror on 2011-05-27
Have you tried any other way to move files to that computer inside your lan?

You could try scp for example.
I would like to know if it will stall or get disconnected too.

If that happens, then it might be hardware related problem.

---

