---
title: "Mail from Anacron??"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by mvalviar on 2009-01-10
I've set up my mail so that I'll be receiving mail from my system. And I'm regularly getting:
```

From: 	Anacron <root@ubuntu>
To: 	root@ubuntu
Subject: 	Anacron job 'cron.daily' on ubuntu
Date: 	Thu,  8 Jan 2009 05:14:51 +0800 (PHT)


run-parts: /etc/cron.daily/apt exited with return code 1

```

I this something I should worry about? What can I do to correct it?

Thanks in advance. More power to our community.

---

### Post by stanz on 2009-01-10
You've setup a server?

Please offer more detailed information about your system & install.

:)

 				 				[**Ubuntu Server 7.10: OpenLDAP + SAMBA Domain Controller**]("http://ubuntuforums.org/showthread.php?t=640760&highlight=return+code")

---

### Post by cerealtx on 2009-01-10
if i understand correctly what your saying u setup a mailserver on your computer, all cron is a command that is run through terminal at a certain time, and it returrnign the 1 = true saying that what ever it is doing it did it could be checking mail/send mail/ ect

---

### Post by unutbu on 2009-01-10
Searching /etc/cron.daily/apt for the string "exit 1" yields 
```

if ! apt-get check -q -q 2>/dev/null; then
    exit 1
fi
```

Here is one way you can test if this is thorn which is causing apt to bail-out early and cron to send you mail:

Open a terminal and run:
```

sudo apt-get check; echo $?
```

On a normal system you would see 

```
Reading package lists...
Building dependency tree...
Reading state information...
0
```

The "0" indicates that apt-get check exited normally. 
If you see some other value, then this is the cause of the problem.
If this is the case, post the output and perhaps one of us will know what to do.

---

### Post by mvalviar on 2009-01-11
Sorry for the confusion. This is just a simple desktop set-up. I installed postfix because I do php coding and wanted to test mail functions. During set up it asked if I want to receive mail meant for root. I accepted the default yes. Then I set up Evolution to fetch my mail from the spool. I'm getting this mail I believe in a weekly interval.

```

mvalviar@ubuntu:~$ sudo apt-get check; echo $?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0

```

Thanks.

---

### Post by unutbu on 2009-01-11
Okay, I should have read the comments in /etc/cron.daily/apt. 
In particular:

```
# check if we can lock the cache and if the cache is clean
# There's a reasonable chance that someone is already running an apt
# frontend that has locked the cache, so exit quietly if it is locked.
if ! apt-get check -q -q 2>/dev/null; then
    exit 0
fi
```

Later on it uses the same condition with "exit 1".

So my guess is that some other process is using the apt cache while /etc/cron.daily/apt is being run, and this is what causes it to exit with return code 1.

Does this sound possible?

PS. If you like tinkering and want to pin down exactly where in the script apt is failing, you could add a logger command like this to the apt script:

```

if ! apt-get check -q -q 2>/dev/null; then
    logger -t 'My Debug' 'Got to first exit 1'
    exit 1
fi
```

and a little later in the code:
```

if ! apt-get check -q -q 2>/dev/null; then
    logger -t 'My Debug' 'Got to second exit 1'
    exit 1
fi
```

The logger commands will produce a message written to /var/log/syslog.

---

### Post by mvalviar on 2009-01-11
Here's what I know: A process returning a non-zero value means something is up and that crons are something that the OS runs regularly. If its something that the OS wants me to know then maybe I should look into it. But should I worry too much about it?

---

