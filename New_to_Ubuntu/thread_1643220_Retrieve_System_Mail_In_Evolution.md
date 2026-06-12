---
title: "Retrieve System Mail In Evolution"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by Geoff918 on 2010-12-11
I am attempting to retrieve system mail (e.g. mail <username>) through Evolution. 

Reason: I find the mail command line interface daunting and virtually unusable. The commands I read regarding mail in the man page seem not to work as advertised (obviously I'm just not entering the syntax correctly, but don't know what the syntax ought to be).

Steps taken thus far: Googled for information regarding this, and searched the Ubuntu forums for information regarding this.

What I found: 

[http://embraceubuntu.com/2006/05/25/read-emails-from-your-system-using-evolution/](http://embraceubuntu.com/2006/05/25/read-emails-from-your-system-using-evolution/)

[http://www.willsimpson.org/125/read-system-emails-from-your-system-using-thunderbird](http://www.willsimpson.org/125/read-system-emails-from-your-system-using-thunderbird)

Neither quite worked. I think there may be a permission(s) error as I need to sudo to get access to the command line mail.

> gapitman@server:~$ mail
mail: /var/mail/gapitman: Is a directory
> gapitman@server:~$ sudo mail
[sudo] password for gapitman: 
Mail version 8.1.2 01/15/2001.  Type ? for help.
"/var/mail/root": 196 messages 196 new
>N  1 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Mon Jun 21 20:06 1055/52496 Daily AIDE report for txadmin-server
 N  2 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Mon Jun 21 20:08   21/805   [rkhunter] txadmin-server - Daily report
 N  3 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Mon Jun 21 20:08   19/663   Anacron job 'cron.daily' on txadmin-server
 N  4 [EMAIL="txadmin@hvtaxi.co"]txadmin@hvtaxi.co[/EMAIL]  Mon Jun 21 22:12   16/530   *** SECURITY information for txadmin-server ***
 N  5 [EMAIL="txadmin@hvtaxi.co"]txadmin@hvtaxi.co[/EMAIL]  Mon Jun 21 22:13   16/531   *** SECURITY information for txadmin-server ***
 N  6 [EMAIL="txadmin@hvtaxi.co"]txadmin@hvtaxi.co[/EMAIL]  Mon Jun 21 22:13   16/531   *** SECURITY information for txadmin-server ***
 N  7 gapitman@hvtaxi.c  Mon Jun 21 23:14   16/636   *** SECURITY information for server.hvtaxi.org ***
 N  8 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Wed Jun 23 15:00 1055/53614 Daily AIDE report for server
 N  9 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Wed Jun 23 15:28   75/3853  [rkhunter] server - Daily report
 N 10 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Wed Jun 23 15:28   19/671   Anacron job 'cron.daily' on server.hvtaxi.org
 N 11 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Thu Jun 24 07:42 1055/53420 Daily AIDE report for server
 N 12 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Thu Jun 24 08:00   21/797   [rkhunter] server - Daily report
 N 13 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Thu Jun 24 08:00   19/671   Anacron job 'cron.daily' on server.hvtaxi.org
 N 14 gapitman@hvtaxi.c  Thu Jun 24 23:04   16/644   *** SECURITY information for server.hvtaxi.org ***
 N 15 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Tue Jun 29 16:54 1055/55168 Daily AIDE report for server
 N 16 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Tue Jun 29 17:04   35/1614  [rkhunter] server - Daily report
 N 17 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Tue Jun 29 17:04   19/671   Anacron job 'cron.daily' on server.hvtaxi.org
 N 18 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Wed Jun 30 21:43 1055/54244 Daily AIDE report for server
 N 19 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Wed Jun 30 21:50   42/2021  [rkhunter] server - Daily report
 N 20 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Wed Jun 30 21:50   19/671   Anacron job 'cron.daily' on server.hvtaxi.org
 N 21 gapitman@hvtaxi.c  Thu Jul  1 15:15   16/619   *** SECURITY information for server.hvtaxi.org ***
 N 22 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Thu Jul  1 15:32 1055/54344 Daily AIDE report for server
 N 23 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Thu Jul  1 15:51   40/1905  [rkhunter] server - Daily report
 N 24 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Thu Jul  1 15:51   19/671   Anacron job 'cron.daily' on server.hvtaxi.org
 N 25 gapitman@hvtaxi.c  Thu Jul  1 16:09   16/638   *** SECURITY information for server.hvtaxi.org ***
 N 26 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Fri Jul  2 07:42 1055/53971 Daily AIDE report for server
 N 27 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Fri Jul  2 07:56   40/1905  [rkhunter] server - Daily report
 N 28 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Fri Jul  2 07:56   19/671   Anacron job 'cron.daily' on server.hvtaxi.org
 N 29 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Sat Jul  3 07:42 1055/53928 Daily AIDE report for server
 N 30 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Sat Jul  3 07:56   40/1905  [rkhunter] server - Daily report
 N 31 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Sat Jul  3 07:56   19/671   Anacron job 'cron.daily' on server.hvtaxi.org
 N 32 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Sun Jul  4 07:48 1055/53999 Daily AIDE report for server
 N 33 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Sun Jul  4 08:12   42/2021  [rkhunter] server - Daily report
 N 34 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Sun Jul  4 08:12   19/671   Anacron job 'cron.daily' on server.hvtaxi.org
 N 35 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Mon Jul  5 16:37 1055/53795 Daily AIDE report for server
 N 36 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Mon Jul  5 17:08   42/2021  [rkhunter] server - Daily report
 N 37 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Mon Jul  5 17:08   19/671   Anacron job 'cron.daily' on server.hvtaxi.org
 N 38 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Tue Jul  6 07:42 1055/53712 Daily AIDE report for server
 N 39 [EMAIL="root@hvtaxi.com"]root@hvtaxi.com[/EMAIL]    Tue Jul  6 08:14   42/2021  [rkhunter] server - Daily report
& 
> gapitman@server:/var/mail$ ls -l
total 3424
drwxr-sr-x 2 root mail    4096 2010-09-02 15:54 gapitman
-rw------- 1 root mail 3496121 2010-12-11 15:25 root
gapitman@server:/var/mail$ > gapitman@server:/var/spool/mail$ ls -l
total 3424
drwxr-sr-x 2 root mail    4096 2010-09-02 15:54 gapitman
-rw------- 1 root mail 3496121 2010-12-11 15:25 root
gapitman@server:/var/spool/mail$

---

### Post by Geoff918 on 2010-12-11
Okay, so I found *something* out through observing my own output above. This is **definitely** a user / role problem.

When I did the following:

sudo su

to become 'root' the command line mail program allowed me to fully interact with the mail program as intended. I could delete messages, etc.

So, here's the question:

How would I chown properly so that I can retrieve the mail as normal non-sudo user? Or, should I not do this at all for security reasons?

I'm not horrible with Ubuntu or Linux, but I'm not great. My knowledge is fair to middling, and some of the constructs of ownership numbers, etc are still a bit daunting to me, though I understand the concepts.

If anyone may be able to help, I would greatly appreciate it.

Thanks!

---

