---
title: "How to see when ubuntu was installed?"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by robro on 2011-04-18
Hello ubuntu community,
I am trying to find a way to see when I installed ubuntu (no real reason, just curios) and am stumped at finding out a way, I have searched through the preferences, administration, system tools
and cant seem to find anything :|

Thanks for the help

---

### Post by mathgeek2000 on 2011-04-18
> **robro said:**
> I am trying to find a way to see when I installed ubuntu (no real reason, just curios) and am stumped at finding out a way, I have searched through the preferences, administration, system tools
and cant seem to find anything :|


Assuming your system clock is set correctly, try opening a bash shell, and typing:

```
ls -ld /lost*
```

This should give you the date and time the ext<n> partitions were first formatted. For example, for my 3 partitions:

```
jonas@Galileo:~$ ls -ld /lost*
drwx------ 2 root root 16384 2010-12-27 08:28 /lost+found
jonas@Galileo:~$ ls -ld /boot/lost*
drwx------ 2 root root 12288 2010-12-27 08:28 /boot/lost+found
jonas@Galileo:~$ ls -ld /home/lost*
drwx------ 2 root root 16384 2010-12-27 08:29 /home/lost+found
jonas@Galileo:~$ 
```

---

### Post by Rubi1200 on 2011-04-18
Another way is to check syslog:

```
sudo grep ubiquity /var/log/installer/syslog | less
```

There is a TON of information there, but it will give you the install date.

---

### Post by robro on 2011-04-18
Ahh thanks works perfectly :)

---

### Post by Rubi1200 on 2011-04-19
> **robro said:**
> Ahh thanks works perfectly :)
No problem, you are more than welcome :-)

By the way, which command worked perfectly? First one, the one I posted or both? Good to know for future reference and all.

---

### Post by matt_symes on 2011-04-19
Hi

> **Rubi1200 said:**
> No problem, you are more than welcome :-)

By the way, which command worked perfectly? First one, the one I posted or both? Good to know for future reference and all.

They both work well Rubi.

```
matthew@matthew-laptop:~/Downloads$ ls -ld /lost*
drwx------ 2 root root 16384 2011-04-08 02:13 /lost+found
matthew@matthew-laptop:~/Downloads$ 
```

```
matthew@matthew-laptop:~/Downloads$ sudo head -n2 /var/log/installer/syslog 
Apr  8 01:02:31 ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr  8 01:02:31 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1269" x-info="http://www.rsyslog.com"] (re)start
matthew@matthew-laptop:~/Downloads$ 
```

Excellent work.

Kind regards

---

