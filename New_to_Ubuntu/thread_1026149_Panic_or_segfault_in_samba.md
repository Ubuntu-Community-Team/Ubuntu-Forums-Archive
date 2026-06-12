---
title: "Panic or segfault in samba"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by shankhs on 2008-12-30
Last night my ubuntu system hanged!!!!!!!I did not know what was happening so changed tty by pressing <alt>+<ctrl>+F2 there I saw I have 53 mails in /var/shankhs/mail and all the mails have this:
```

From root@shankhs-desktop [COLOR="Red"]Mon Dec 29 22:25:18 2008[/COLOR]
Return-path: <root@shankhs-desktop>
Envelope-to: root@shankhs-desktop
Delivery-date: Mon, 29 Dec 2008 22:25:18 +0530
Received: from root by shankhs-desktop with local (Exim 4.69)
	(envelope-from <root@shankhs-desktop>)
	id 1LHLOg-00049s-GW
	for root@shankhs-desktop; Mon, 29 Dec 2008 22:25:18 +0530
To: root@shankhs-desktop
Subject: Panic or segfault in Samba
Message-Id: <E1LHLOg-00049s-GW@shankhs-desktop>
From: root <root@shankhs-desktop>
Date: Mon, 29 Dec 2008 22:25:18 +0530
Status: O

The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for PID [COLOR="Red"]27841[/COLOR] (/usr/sbin/smbd).

This means there was a problem with the program, such as a segfault.
Below is a backtrace for this process generated with gdb, which shows
the state of the program at the time the error occurred.  The Samba log
files may contain additional information about the problem.

If the problem persists, you are encouraged to first install the
samba-dbg package, which contains the debugging symbols for the Samba
binaries.  [COLOR="Red"]Then submit the provided information as a bug report to
Ubuntu by visiting this link:[/COLOR]
[https://launchpad.net/ubuntu/+source/samba/+filebug]("https://launchpad.net/ubuntu/+source/samba/+filebug")

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb75c36d0 (LWP 27841)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7af5430 in __kernel_vsyscall ()
#0  0xb7af5430 in __kernel_vsyscall ()
#1  0xb77075e3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb76a475b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb789750d in system () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7cc45f1 in smb_panic () from /usr/sbin/smbd
#5  0xb7caf013 in ?? () from /usr/sbin/smbd
#6  <signal handler called>
#7  0xb7ca0720 in rep_strlcpy () from /usr/sbin/smbd
#8  0xb7cd3592 in connections_fetch_entry () from /usr/sbin/smbd
#9  0xb7b75230 in yield_connection () from /usr/sbin/smbd
#10 0xb7b9dded in close_cnum () from /usr/sbin/smbd
#11 0xb7b7b584 in conn_close_all () from /usr/sbin/smbd
#12 0xb7b624fd in ?? () from /usr/sbin/smbd
#13 0xb7b626f1 in exit_server_cleanly () from /usr/sbin/smbd
#14 0xb7b9aaad in ?? () from /usr/sbin/smbd
#15 0xb7b9c90b in ?? () from /usr/sbin/smbd
#16 0xb7b9d17f in smbd_process () from /usr/sbin/smbd
#17 0xb7b64adf in main () from /usr/sbin/smbd
The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]

```
I still dont know what to do!!!
Is this a bug? if yes then how to post it ? What is backtrace ?
Please help!

---

### Post by shankhs on 2008-12-30
Please help me I think Io have found a bug in samba...
I am not sure about it so I need help.

---

### Post by shankhs on 2008-12-31
I wanted to know if this is at all a bug or not OR if its a bug this has been fixed or not???
Since nobody is interested not even here: [http://ubuntuforums.org/showthread.php?t=8631](http://ubuntuforums.org/showthread.php?t=8631)
So I am finally reporting it as abug.

---

### Post by shankhs on 2009-01-01
While reporting the bug I found that many guys have reported the similar bug and they had the similar problems.The bug's importance is still undecided.
What should I do should I install ubuntu again or wait for the bug to fix???
Generally how long does it take to fix a bug?
Please help.
Thank You

---

### Post by shankhs on 2009-01-02
Hi guys Please help I cannot believe that I am the only one who has this bug!!!

---

### Post by wwuster on 2009-01-09
> **shankhs said:**
> Hi guys Please help I cannot believe that I am the only one who has this bug!!!

I get this bug also. It happens about once per hour. I get an email to root saying that it has happened:

> The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for PID 7646 ().

This means there was a problem with the program, such as a segfault.
However, the executable could not be found for process 7646.
It may have died unexpectedly, or you may not have permission to debug
the process.


---

### Post by 1jackjack on 2009-02-22
yer i get this too 3-4 times a week. anybody made any progress with this problem?

cheers,
jack

---

### Post by informixtc on 2009-04-14
I am experiencing a similar problem.

Ubuntu 8.04.2
Linux kernel 2.6.24-24-generic
Samba 3.0.28a-1ubuntu4.8


The Samba 'panic action' script, /usr/share/samba/panic-action,
was called for PID 29504 ().

Every time someone accesses the shared folder from windows, similar error appears.

---

### Post by boblu on 2009-11-08
I also have the same problem in Ubuntu 9.10

And it also appears every time someone accesses the shared folder from windows

Can someone explain this?

---

### Post by danzaslap on 2010-10-13
Hello everyone,
  I also get this exact message.  I get emails sent to root within 10 seconds of a user accessing samba shares via a windows box.  Errors don't prevent access but there is a delay.  Im assuming its due to smbd restarting?

Did anyone resolve this issue?

Also, i'm running Ubuntu 10.04.

++BUMP++

---

### Post by luvshines on 2010-10-13
What logs do smbd generate when this happens ??

---

### Post by danzaslap on 2010-10-14
[SOLVED]
Probably should have started my own thread!!

Well, 
I deleted the samba config generated by the gui stored at
/var/lib/samba/usershares

 and created my own vanilla config at /etc/samba/smb.conf

Here's a link to seting up vanilla configs
[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)

The errors went away.  Yay for me.

---

