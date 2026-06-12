---
title: "&quot;cron no mta installed discarding output&quot;  bug"
date: 2015-02-27
forum: Networking &amp; Wireless
---

### Post by secoonder on 2015-02-27
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]                Hello
I have a cron job that runs every 3 minute on an Ubuntu 12.04 box

  $sudo crontab -e
* * * * * mylogin /pathto/file.sh
  If I run manually  file.sh, the bash script run.

But it is not run by cron.
the output tailf /var/log/syslog/

_**"cron no mta installed discarding output"**_




i install postfi x.but still not running.
i added 
* * * * * mylogin /pathto/file.sh >> /dev/null > 2>&1
again not running.

what can i do

thank you very much for your help

[/TD]
[/TR]
[/TABLE]

---

### Post by steeldriver on 2015-02-27
What is 'mylogin'? it looks like you're trying to use the format of the system-wide /etc/crontab (i.e. include a user field) in root's crontab - that's not going to work, they are two different syntaxes. 

Either use root's crontab (i.e. sudo crontab -e) and run the job as root, OR a user crontab (just crontab -e without the sudo) OR use /etc/crontab.

The mta message is irrelevant - unless you want cron to send you emails

---

### Post by secoonder on 2015-02-27
my script exatly as:
# !/bin/bash
for i in $(cat /root/x)
do 
ping -c 4 "$i" > /dev/null 2 >$1
if [ $? -ne 0 ]
then cd /root; ./openvpn.sh
fi
done

i starded manualy script.the script is run.
i added the file to crontab.my crontab is 
* /1 * * * * /root/change_line.sh > /dev/null 2 > &1

But when i added the script to crontab, i took an error at /var/log/syslog
The error is " _**cron no mta installed discarding output"**_

can you help me..Regards

---

### Post by ian-weisser on 2015-02-27
> **secoonder said:**
> my script exatly as:
# !/bin/bash
for i in $(cat /root/x)
do 
** ping -c 4 "$i" > /dev/null 2 >$1**
if [ $? -ne 0 ]
then cd /root; ./openvpn.sh
fi
done


Well, here's one problem cron is trying to tell you about:
```
$ ping -c 4 8.8.8.8 > /dev/null 2>$1
bash: $1: ambiguous redirect
```

---

### Post by secoonder on 2015-02-28
i run manually 
 ping -c 4 8.8.8.8 > /dev/null 2>$1

but i didnt take error.
but tailf /var/log/syslog output again is 
" _**cron no mta installed discarding output" **_

---

### Post by Habitual on 2015-03-01
> **secoonder said:**
> i run manually 
 ping -c 4 8.8.8.8 > /dev/null 2>$1

but i didnt take error. Doesn't make it "correct" or right.

> /dev/null 2>**&**1

```
sudo apt-get install mailx
``` to install an mta

See [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)

---

### Post by secoonder on 2015-03-03
habitual
thank you.
The problem is solved, after your help.
Thank you very much for your help :D

---

