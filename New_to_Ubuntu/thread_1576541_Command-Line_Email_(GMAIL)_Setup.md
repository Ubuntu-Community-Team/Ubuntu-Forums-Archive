---
title: "Command-Line Email (GMAIL) Setup"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-09-17
Hey all, Im pretty new to C.L.I/text editing work. So maybe its a bit old-fashioned but Im interested in learning how to send email via the command line. I am running 10.04 32 bit

Situation: I have followed the explicit and step-by-step actions at [http://klenwell.com/is/UbuntuCommandLineGmail](http://klenwell.com/is/UbuntuCommandLineGmail)   

Question: Upon completion, when trying to send a test email to myself via gmail (from CLI) I get the following error: "msmtp: no recipients found". In CLI below it asks me to explicitly pick a mailx to download. I think I already have mailx as when I type mailx I get "no mail for primary". 

Note: on another thread, [http://ubuntuforums.org/showthread.php?t=780509&page=2](http://ubuntuforums.org/showthread.php?t=780509&page=2) ,  someone received same error of :msmtp: no recipients found". Apparently there was a problem in that they got mailx from mailutils. Could this be an issue. Thanks in advance!

Here is my work```
:~$ sudo apt-get install msmtp mailx
[sudo] password for: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msmtp is already the newest version.
Package mailx is a virtual package provided by:
  mailutils 1:2.1+dfsg1-4ubuntu1
  heirloom-mailx 12.4-1.1
  bsd-mailx 8.1.2-0.20090911cvs-2ubuntu1
You should explicitly select one to install.
E: Package mailx has no installation candidate
:~$ gedit ~/.msmtprc
:~$ chmod 600 ~/.msmtprc
:~$ gedit ~/.mailrc
:~$ echo -e "testing email from the command line" > /tmp/test_email
:~$ mailx -s "mailx gmail test"xxxx@gmail.com < /tmp/test_email
msmtp: no recipients found

``` here is ~/.msmtprc ```
# config options: http://msmtp.sourceforge.net/doc/msmtp.html#A-user-configuration-file
defaults
logfile /tmp/msmtp.log

# gmail account
#account gmail
auth on
host smtp.gmail.com
port 587
user xxxxxx@gmail.com
password xxxxxx
from xxxxxx@gmail.com
tls on
tls_trust_file /usr/share/ca-certificates/mozilla/Equifax_Secure_CA.crt

# set default account to use (not necessary with single account)
#account default : gmail
```and here is ~/.mailrc   ```
  # set smtp for mailx

# gmail account (default)
# $ mailx -s "subject line" -a /path/attachment recipient@email.com < /path/body.txt
set from="xxxxxx@gmail.com (xxxxx)"
set sendmail="/usr/bin/msmtp"
set message-sendmail-extra-arguments="-a gmail"
```

---

### Post by andrewthomas on 2010-09-19
Package mailx is a virtual package provided by:
  mailutils 1:2.1+dfsg1-4ubuntu1
  heirloom-mailx 12.4-1.1
  bsd-mailx 8.1.2-0.20090911cvs-2ubuntu1
**You should explicitly select one to install.**
 
You need to pick one of the above and install it.

---

