---
title: "System Log mail"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by mayagrafix on 2009-01-21
I checked my KsystemLog application and found a lot of this:

2009-01-21 09:31:53	Inspiron	nullmailer[4285]	Starting delivery: protocol: smtp host: mail. file: 1231166253.11986
2009-01-21 09:31:53	Inspiron	nullmailer[23956]	smtp: Failed: Connect failed
2009-01-21 09:31:53	Inspiron	nullmailer[4285]	Sending failed:  Host not found
2009-01-21 09:31:53	Inspiron	nullmailer[4285]	Delivery complete, 4 message(s) remain.
2009-01-21 09:32:53	Inspiron	nullmailer[4285]	Rescanning queue.

This set of instructions repeats endlessly every 24 hours. Wazzup with this?:(

---

### Post by mayagrafix on 2009-01-21
Am I posting in the wrong forum? if so please direct me to correct forum for asking repetitive system log message. 

thanks!!!

---

### Post by mayagrafix on 2009-01-21
doesn't anybody care?

---

### Post by yknivag on 2009-01-21
There are lots of people here who care but patience is a virtue!

As for your problem, it would appear your mailserver has 4 emails it can't send.  It can't send these as it can't connect to a downstream server.

Possibly these are external emails and your mailserver cannot connect to another mailserver on the internet (some ISPs block traffic on port 25).

I'm sure someone far more experienced than me will be able to tell you how to put it right!

---

### Post by mayagrafix on 2009-01-21
So basically what is wrong is that my email program is mis configured?

---

### Post by mayagrafix on 2009-01-21
I sent an email to myself to a Yahoo account and it went through OK.

---

### Post by mayagrafix on 2009-01-22
Could this be result of some bot-net? Ive read the dowandup worm has infected 9 million windows users... maybe this is the linux variant?

---

### Post by yknivag on 2009-01-22
Have you tried sending a message from the command line on the affected box?

I don't think there is a linux version of the dowandup worm...

---

### Post by mayagrafix on 2009-01-22
OK, Thanks for responding. I checked the History command in the Command Line Terminal and found this:

mail rafael < /etc/hosts

cna this command be the cause?

---

### Post by yknivag on 2009-01-22
Somewhat worrying if you didn't type it, but I'm not sure it would cause the problem.

Did you try sending an external email from CLI?

---

### Post by mayagrafix on 2009-01-22
> **yknivag said:**
> Somewhat worrying if you didn't type it, but I'm not sure it would cause the problem.

Did you try sending an external email from CLI?


Guilty on the first count, I remember typing that command. Regarding the second question, I found this:

watch &#8216;cat /proc/loadavg&#8217;

This I picked up from a Linux How to book.

Thanks for your time and patience ;)

---

### Post by yknivag on 2009-01-22
I'm sorry, I'm lost now, what has monitoring the system load got to do with the four emails your mailserver can't send?

---

### Post by mayagrafix on 2009-01-22
Sorry for the confusion. I was trying to pin down a command from the CLI that could be causing the 4 emails the mailserver cant send. I used the history command to review the past inputs and found:
1: mail rafael < /etc/hosts
and 
2: watch ‘cat /proc/loadavg’
which as you correctly state, has nothing to do with the problem at hand. Sorry for the mix up :(

---

### Post by yknivag on 2009-01-22
It seems there are two issues here then:

1. What caused the messages to be there.

2. Why they're not delivering.

The first is difficult to tell until we know what's in them! I suspect they're probably failed cron jobs.

The second is the real issue, have you tried sending mail from the command line? Did you receive it?

---

### Post by mayagrafix on 2009-01-22
> The second is the real issue, have you tried sending mail from the command line? Did you receive it? 

A: How do you send mail from the command line?
B: Have not received mail sent from command line (is there a mail program for this akin Evolution?).

---

### Post by yknivag on 2009-01-22
In the terminal type

```
mail your@email.address
```

Type a subject and <enter> a message and <enter> TWICE and then "Ctrl D" and then <enter>

Do you receive the email?

---

### Post by yknivag on 2009-01-22
Unless you know which mail server you're running then we may have to wait for those messages to appear again tomorrow (to see if the 4 has become a 5).  If you do know the software name we can find the "flush" command to generate it now.

---

### Post by mayagrafix on 2009-01-22
rafael@Inspiron:~$ mail rafael@inspiron

The program 'mail' can be found in the following packages:
 * heirloom-mailx
 * mailutils
Try: sudo apt-get install <selected package>

bash: mail: command not found

rafael@Inspiron:~$

---

### Post by yknivag on 2009-01-22
Interesting, you don't appear to have a mail program installed and yet you appear to have 5 queueing mails. How strange!

Can you type the following in a terminal and post the output?

```
ls -ltr /var/spool/mail/
```

then

```
ls -ltr /var/spool/
```

Thanks.

---

### Post by mayagrafix on 2009-01-22
rafael@Inspiron:~$ ls -ltr /var/spool/mail/
total 0

rafael@Inspiron:~$ ls -ltr /var/spool/
total 24
drwxr-xr-x 3 root   root   4096 2007-04-15 06:51 openoffice
drwxr-xr-x 5 daemon daemon 4096 2007-04-15 06:51 cron
lrwxrwxrwx 1 root   root      7 2008-10-06 14:09 mail -> ../mail
drwxr-xr-x 2 root   root   4096 2008-10-06 19:40 anacron
drwxrwxrwt 2 root   root   4096 2008-11-26 09:34 samba
drwx--x--- 3 root   lp     4096 2009-01-14 10:11 cups
drwxr-xr-x 4 mail   root   4096 2009-01-22 13:21 nullmailer

---

### Post by yknivag on 2009-01-22
OK, can you try;

```
ls -ltr /var/spool/nullmailer/
```

---

### Post by yknivag on 2009-01-22
and also can you post the output of

```
cat /etc/nullmailer/remotes
```

---

### Post by mayagrafix on 2009-01-22
rafael@Inspiron:~$ ls -ltr /var/spool/nullmailer/
total 8
drwxr-x--- 2 mail root 4096 2009-01-05 08:37 [COLOR="RoyalBlue"]tmp[/COLOR]
drwxr-x--- 2 mail root 4096 2009-01-05 08:37 [COLOR="RoyalBlue"]queue[/COLOR]
prw--w--w- 1 mail root    0 2009-01-22 13:21 [COLOR="DarkOrange"]trigger
[/COLOR]
rafael@Inspiron:~$ cat /etc/nullmailer/remotes
mail.

---

### Post by mayagrafix on 2009-01-22
Sorry, no cigar :( from the KsystemLog:

2009-01-22 21:56:09	Inspiron	nullmailer[4304]	Rescanning queue.
2009-01-22 21:56:09	Inspiron	nullmailer[4304]	Starting delivery: protocol: smtp host: mail. file: 1231130043.31010
2009-01-22 21:56:09	Inspiron	nullmailer[12881]	smtp: Failed: Connect failed
2009-01-22 21:56:09	Inspiron	nullmailer[4304]	Sending failed:  Host not found
2009-01-22 21:56:09	Inspiron	nullmailer[4304]	Starting delivery: protocol: smtp host: mail. file: 1231128384.30124
2009-01-22 21:56:09	Inspiron	nullmailer[12882]	smtp: Failed: Connect failed
2009-01-22 21:56:09	Inspiron	nullmailer[4304]	Sending failed:  Host not found
2009-01-22 21:56:09	Inspiron	nullmailer[4304]	Starting delivery: protocol: smtp host: mail. file: 1231129317.30720
2009-01-22 21:56:09	Inspiron	nullmailer[12883]	smtp: Failed: Connect failed

---

### Post by yknivag on 2009-01-23
The content of /etc/nullmailer/remotes is incorrect, it should contain your ISP's SMTP server.

See if you can find the SMTP server address for your ISP (should be on there website and then do the following:

```

sudo mv /etc/nullmailer/remotes /etc/nullmailer/remotes.backup
gksudo gedit /etc/nullmailer/remotes

```

and then replace the:
```
mail.
```
with...
```
your.isps.mail.relay
```
(no return at the end of the line)

Save that and then see what happens, the mail should then be delivered.

NB: Your ISPs mail server is likely to be something like smtp.ispname.net but check on their website, you'll find it in the documentation on configuring email.

---

### Post by mayagrafix on 2009-01-23
Thanks for all your help. But we still have the problems. Except now it says SMTP address for mi provider. GRRRR! When Gedit opened the remotes file, it was an empty document. There was no "mail" designation to replace. I pasted the SMTP address for ISP anyway in blank document and saved. Here is what KsystemLog says now: 

2009-01-23 14:57:34	Inspiron	nullmailer[4286]	Rescanning queue.

2009-01-23 14:57:34	Inspiron	nullmailer[4286]	Starting delivery: protocol: smtp host: smtp.prodigy.net.mx file: 1231130043.31010
2009-01-23 14:57:35	Inspiron	nullmailer[12764]	smtp: Failed: 553 #5.1.8 Domain of sender address <root@Inspiron.Inspiron> does not exist
2009-01-23 14:57:35	Inspiron	nullmailer[4286]	Sending failed:  Permanent error in sending the message

2009-01-23 14:57:35	Inspiron	nullmailer[4286]	Starting delivery: protocol: smtp host: smtp.prodigy.net.mx file: 1231128384.30124
2009-01-23 14:57:35	Inspiron	nullmailer[12765]	smtp: Failed: 553 #5.1.8 Domain of sender address <root@Inspiron.Inspiron> does not exist
2009-01-23 14:57:36	Inspiron	nullmailer[4286]	Sending failed:  Permanent error in sending the message

2009-01-23 14:57:36	Inspiron	nullmailer[4286]	Starting delivery: protocol: smtp host: smtp.prodigy.net.mx file: 1231129317.30720
2009-01-23 14:57:36	Inspiron	nullmailer[12766]	smtp: Failed: 553 #5.1.8 Domain of sender address <root@Inspiron.Inspiron> does not exist
2009-01-23 14:57:36	Inspiron	nullmailer[4286]	Sending failed:  Permanent error in sending the message

2009-01-23 14:57:36	Inspiron	nullmailer[4286]	Starting delivery: protocol: smtp host: smtp.prodigy.net.mx file: 1231166253.11986
2009-01-23 14:57:36	Inspiron	nullmailer[12767]	smtp: Failed: 553 #5.1.8 Domain of sender address <root@Inspiron.Inspiron> does not exist
2009-01-23 14:57:36	Inspiron	nullmailer[4286]	Sending failed:  Permanent error in sending the message

2009-01-23 14:57:36	Inspiron	nullmailer[4286]	Delivery complete, 4 message(s) remain.

Hope we get there soon. Thanks:(

---

### Post by yknivag on 2009-01-23
OK, we're a lot nearer (although it may not seem that way)!

The failure reason now is that your ISP doesn't allow you to send email unless the sender address is valid. This is a problem as nullmailer doesn't allow you to spoof the address headers like sendmail and postfix do.

However it reveals that the messages are originating from the root user on your system (root@Inspiron.Inspiron) and so are almost certainly notifications of failed cron jobs.

You have two choices, you can either delete the messages off the system (and do this everytime it happens) or you can try and set a host and domain name on your computer which allows [email]root@host.domain[/email] to be a valid real-world address, clear these messages out and any future ones will deliver.

I can tell you how to do the first, but if you wish to do the second I'm afraid you'll need someone rather more experienced than me.

---

### Post by mayagrafix on 2009-01-23
Lets go for the first option and I'll take it from there :p

---

### Post by yknivag on 2009-01-23
Try the following:
```

sudo mv /var/spool/nullmailer/tmp /var/spool/nullmailer/tmp.bak
sudo mv /var/spool/nullmailer/queue /var/spool/nullmailer/queue.bak

```
If (and **only if**) that clears the errors and doesn't cause any issues you can do:
```

sudo rm /var/spool/nullmailer/tmp.bak
sudo rm /var/spool/nullmailer/queue.bak

```
Otherwise, the following should fix anything the first causes:
```

sudo mv /var/spool/nullmailer/tmp.bak /var/spool/nullmailer/tmp
sudo mv /var/spool/nullmailer/queue.bak /var/spool/nullmailer/queue

```

---

### Post by mayagrafix on 2009-01-23
```

sudo mv /var/spool/nullmailer/tmp /var/spool/nullmailer/tmp.bak
sudo mv /var/spool/nullmailer/queue /var/spool/nullmailer/queue.bak

```

OK, did the first two, No Joy, the KsytemLog still shows the nullmailler trying to send the 4 messages every minute.

Skipping the second set ...
```
sudo rm /var/spool/nullmailer/tmp.bak
sudo rm /var/spool/nullmailer/queue.bak
```

---

### Post by mayagrafix on 2009-01-23
Third set also failed. Still trying to send 4 messages to root@inspiron.

2009-01-23 17:41:18	Inspiron	nullmailer[4286]	Rescanning queue.
2009-01-23 17:41:18	Inspiron	nullmailer[4286]	Starting delivery: protocol: smtp host: smtp.prodigy.net.mx file: 1231130043.31010
2009-01-23 17:41:19	Inspiron	nullmailer[16219]	smtp: Failed: 553 #5.1.8 Domain of sender address <root@Inspiron.Inspiron> does not exist
2009-01-23 17:41:19	Inspiron	nullmailer[4286]	Sending failed:  Permanent error in sending the message
2009-01-23 17:41:19	Inspiron	nullmailer[4286]	Starting delivery: protocol: smtp host: smtp.prodigy.net.mx file: 1231128384.30124
2009-01-23 17:41:20	Inspiron	nullmailer[16220]	smtp: Failed: 553 #5.1.8 Domain of sender address <root@Inspiron.Inspiron> does not exist
2009-01-23 17:41:20	Inspiron	nullmailer[4286]	Sending failed:  Permanent error in sending the message
2009-01-23 17:41:20	Inspiron	nullmailer[4286]	Starting delivery: protocol: smtp host: smtp.prodigy.net.mx file: 1231129317.30720
2009-01-23 17:41:20	Inspiron	nullmailer[16221]	smtp: Failed: 553 #5.1.8 Domain of sender address <root@Inspiron.Inspiron> does not exist
2009-01-23 17:41:20	Inspiron	nullmailer[4286]	Sending failed:  Permanent error in sending the message
2009-01-23 17:41:20	Inspiron	nullmailer[4286]	Starting delivery: protocol: smtp host: smtp.prodigy.net.mx file: 1231166253.11986
2009-01-23 17:41:21	Inspiron	nullmailer[16222]	smtp: Failed: 553 #5.1.8 Domain of sender address <root@Inspiron.Inspiron> does not exist
2009-01-23 17:41:21	Inspiron	nullmailer[4286]	Sending failed:  Permanent error in sending the message
2009-01-23 17:41:21	Inspiron	nullmailer[4286]	Delivery complete, 4 message(s) remain.

---

### Post by mayagrafix on 2009-01-23
Should I restart the PC for the changes to take effect?

---

### Post by yknivag on 2009-01-24
You shouldn't need to restart, the messages are no longer in the queue to be sent!

Incidently they are sending FROM root@inspiron (the destination) isn't shown in the log entries.

Can you run
```

ls -lR /var/spool/

```
(note the options are lower case L and upper case R)

---

### Post by mayagrafix on 2009-01-25
rafael@Inspiron:~$ ls -lR /var/spool/
/var/spool/:
total 24
drwxr-xr-x 2 root   root   4096 2008-10-06 19:40 anacron
drwxr-xr-x 5 daemon daemon 4096 2007-04-15 06:51 cron
drwx--x--- 3 root   lp     4096 2009-01-14 10:11 cups
lrwxrwxrwx 1 root   root      7 2008-10-06 14:09 mail -> ../mail
drwxr-xr-x 4 mail   root   4096 2009-01-23 17:38 nullmailer
drwxr-xr-x 3 root   root   4096 2007-04-15 06:51 openoffice
drwxrwxrwt 2 root   root   4096 2008-11-26 09:34 samba

/var/spool/anacron:
total 12
-rw------- 1 root root 9 2009-01-24 08:32 cron.daily
-rw------- 1 root root 9 2009-01-05 09:11 cron.monthly
-rw------- 1 root root 9 2009-01-19 08:19 cron.weekly

/var/spool/cron:
total 12
drwxrwx--T 2 daemon daemon  4096 2007-04-15 06:55 atjobs
drwxrwx--T 2 daemon daemon  4096 2007-02-20 07:41 atspool
drwx-wx--T 2 root   crontab 4096 2006-12-20 08:46 crontabs
ls: cannot open directory /var/spool/cron/atjobs: Permission denied
ls: cannot open directory /var/spool/cron/atspool: Permission denied
ls: cannot open directory /var/spool/cron/crontabs: Permission denied
ls: cannot open directory /var/spool/cups: Permission denied

/var/spool/nullmailer:
total 8
drwxr-x--- 2 mail root 4096 2009-01-05 08:37 queue
drwxr-x--- 2 mail root 4096 2009-01-05 08:37 tmp
prw--w--w- 1 mail root    0 2009-01-23 09:01 trigger
ls: cannot open directory /var/spool/nullmailer/queue: Permission denied
ls: cannot open directory /var/spool/nullmailer/tmp: Permission denied

/var/spool/openoffice:
total 4
drwxr-xr-x 3 root root 4096 2007-04-15 06:51 uno_packages

/var/spool/openoffice/uno_packages:
total 4
drwxr-xr-x 4 root root 4096 2008-11-25 11:05 cache

/var/spool/openoffice/uno_packages/cache:
total 28
-rw-r--r-- 1 root root  1094 2008-11-25 11:05 log.txt
drwxr-xr-x 8 root root  4096 2008-10-08 12:08 registry
-rw-r--r-- 1 root root     1 2008-11-25 11:05 stamp.sys
drwxr-xr-x 4 root root  4096 2008-11-25 11:05 uno_packages
-rw-r--r-- 1 root root 12288 2008-11-25 11:05 uno_packages.db

/var/spool/openoffice/uno_packages/cache/registry:
total 24
drwxr-xr-x 2 root root 4096 2008-11-25 11:05 com.sun.star.comp.deployment.component.PackageRegistryBackend
drwxr-xr-x 3 root root 4096 2008-10-08 12:08 com.sun.star.comp.deployment.configuration.PackageRegistryBackend
drwxr-xr-x 2 root root 4096 2008-10-08 12:08 com.sun.star.comp.deployment.executable.PackageRegistryBackend
drwxr-xr-x 2 root root 4096 2008-10-08 12:08 com.sun.star.comp.deployment.help.PackageRegistryBackend
drwxr-xr-x 2 root root 4096 2008-10-08 12:08 com.sun.star.comp.deployment.script.PackageRegistryBackend
drwxr-xr-x 2 root root 4096 2008-10-08 12:08 com.sun.star.comp.deployment.sfwk.PackageRegistryBackend

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend:
total 48
-rw-r--r-- 1 root root 16384 2008-11-25 11:03 common_.rdb
-rw-r--r-- 1 root root 16384 2008-11-25 11:05 common.rdb
-rw-r--r-- 1 root root    36 2008-11-25 11:05 Linux_x86rc
-rw-r--r-- 1 root root  2048 2008-10-08 12:09 Linux_x86_.rdb
-rw-r--r-- 1 root root  2048 2008-10-08 12:09 Linux_x86.rdb
-rw-r--r-- 1 root root   220 2008-11-25 11:05 unorc

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend:
total 16
-rw-r--r-- 1 root root 12288 2008-10-27 23:45 registered_packages.db
drwxr-xr-x 3 root root  4096 2008-10-27 23:45 registry

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry:
total 4
drwxr-xr-x 3 root root 4096 2008-10-27 23:45 data

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data:
total 4
drwxr-xr-x 3 root root 4096 2008-10-27 23:45 org

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data/org:
total 4
drwxr-xr-x 3 root root 4096 2008-10-27 23:45 openoffice

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data/org/openoffice:
total 4
drwxr-xr-x 2 root root 4096 2008-10-27 23:45 TypeDetection

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registry/data/org/openoffice/TypeDetection:
total 12
-rw-r--r-- 1 root root 5647 2008-10-27 23:45 Filter.xcu
-rw-r--r-- 1 root root 2329 2008-10-27 23:45 Types.xcu

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend:
total 0

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend:
total 0

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend:
total 0

/var/spool/openoffice/uno_packages/cache/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend:
total 0

/var/spool/openoffice/uno_packages/cache/uno_packages:
total 8
-rw------- 1 root root    0 2008-10-27 23:45 lsCrVq
drwxr-xr-x 3 root root 4096 2008-10-27 23:45 lsCrVq_
-rw------- 1 root root    0 2008-11-25 11:05 N057bV
drwxr-xr-x 2 root root 4096 2008-11-25 11:05 N057bV_

/var/spool/openoffice/uno_packages/cache/uno_packages/lsCrVq_:
total 4
drwxr-xr-x 3 root root 4096 2008-10-27 23:45 writer2latex.uno.pkg

/var/spool/openoffice/uno_packages/cache/uno_packages/lsCrVq_/writer2latex.uno.pkg:
total 412
drwxr-xr-x 2 root root   4096 2008-10-27 23:45 META-INF
-rw-r--r-- 1 root root   5731 2008-10-27 23:45 w2l_filters.xcu
-rw-r--r-- 1 root root   2915 2008-10-27 23:45 w2l_types.xcu
-rw-r--r-- 1 root root 398966 2008-10-27 23:45 writer2latex.jar

/var/spool/openoffice/uno_packages/cache/uno_packages/lsCrVq_/writer2latex.uno.pkg/META-INF:
total 4
-rw-r--r-- 1 root root 600 2008-10-27 23:45 manifest.xml

/var/spool/openoffice/uno_packages/cache/uno_packages/N057bV_:
total 12
-rw-r--r-- 1 root root 11552 2008-11-20 11:59 mailmerge.py

/var/spool/samba:
total 0
rafael@Inspiron:~$

---

### Post by mayagrafix on 2009-01-25
> **yknivag said:**
> You shouldn't need to restart, the messages are no longer in the queue to be sent!

KsystemLog still shows the 4 messages cued to be sent. I tried running 

sudo mv /var/spool/nullmailer/tmp /var/spool/nullmailer/tmp.bak
sudo mv /var/spool/nullmailer/queue /var/spool/nullmailer/queue.bak

again, but no go.

---

### Post by yknivag on 2009-01-25
I'm guessing they're being generated every day.

Can you try
```

sudo ls -lR /var/spool/nullmailer

```

This should give us an idea of when the mails were generated.

---

### Post by mayagrafix on 2009-01-26
Thanx for all your efforts. Heres the latest output from the CLI:

```

rafael@Inspiron:~$ sudo ls -lR /var/spool/nullmailer
[sudo] password for rafael: 
/var/spool/nullmailer:
total 8
drwxr-x--- 2 mail root 4096 2009-01-05 08:37 queue.bak
drwxr-x--- 2 mail root 4096 2009-01-05 08:37 tmp.bak
prw--w--w- 1 mail root    0 2009-01-23 09:01 trigger

/var/spool/nullmailer/queue.bak:
total 16
-rw------- 1 mail rommel 538 2009-01-04 22:06 1231128384.30124
-rw------- 1 mail rommel 498 2009-01-04 22:21 1231129317.30720
-rw------- 1 mail rommel 499 2009-01-04 22:34 1231130043.31010
-rw------- 1 mail rommel 718 2009-01-05 08:37 1231166253.11986

/var/spool/nullmailer/tmp.bak:
total 0
rafael@Inspiron:~$ 

```

I can see the name of a second user I created (rommel) so I could log into Xfce without problems. Should I log in as that personality and execute the previous commands to clear up the nullmailer?

Note: Rafael is the original personality on this PC and Rommel has only user privileges.

---

### Post by yknivag on 2009-01-26
> **mayagrafix said:**
> I can see the name of a second user I created (rommel) so I could log into Xfce without problems. Should I log in as that personality and execute the previous commands to clear up the nullmailer?

The files belong to the system user "mail" but are assigned to the group that the user "rommel" belongs to.

They're all quite old (4th and 5th of this month) and so if you're not interested in what they are, I think you're best bet is to run the following:

```

sudo rm /var/spool/nullmailer/queue.bak/1231128384.30124
sudo rm /var/spool/nullmailer/queue.bak/1231129317.30720
sudo rm /var/spool/nullmailer/queue.bak/1231130043.31010
sudo rm /var/spool/nullmailer/queue.bak/1231166253.11986

sudo mv /var/spool/nullmailer/queue.bak /var/spool/nullmailer/queue
sudo mv /var/spool/nullmailer/tmp.bak /var/spool/nullmailer/tmp

```

This will remove the 4 mails and return the folders to the correct configuration.

---

