---
title: "internet is not working after software updates"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by nikhil.deshmukh on 2011-09-08
Hi All

i have ubuntu 10.04 .
since i updated the softwares
suddenly the internet stoped working.. 

i dont understand .. i can ping the local router .. which is 192.168.0.2 but i cnnot access internet..
can anyone suggest me whats is wrong here??

---

### Post by ~!geek!~ on 2011-09-08
You are able to ping the router..You are unable to access internet!
 Are you able to check for updates using sudo apt-get update or update manager. 
If yes, its a browser problem!! Try to solve it!!

---

### Post by nikhil.deshmukh on 2011-09-08
thanks for your reply 
but i am not able to connect to the updates and update manager

---

### Post by 3rdalbum on 2011-09-08
Give this a go:

[http://www.chrislees.info/ubuntu/opendns.shtml](http://www.chrislees.info/ubuntu/opendns.shtml)

It sounds like, for whatever reason, you're having a DNS problem.

---

### Post by nikhil.deshmukh on 2011-09-08
hi 
Thanks for your reply 
i checked but no luck.. 

yes even i think its a dns problem .. and i am being scratching my head for so long now...

---

### Post by mastablasta on 2011-09-08
you could try to access the old kernel by booting it on start (i think oyu need to hold shift key for the grub selection menu to appear). that would give oyu the clue as to wheather the probelm is in the kernel. 
 
also how do you connect to internet? wired or wireless (wi-fi)?

---

### Post by nikhil.deshmukh on 2011-09-08
i connect by wired

this is ifconfig

eth0      Link encap:Ethernet  HWaddr 00:24:1d:f2:fc:61  
          inet addr:192.168.0.251  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fef2:fc61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26800 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8733326 (8.7 MB)  TX bytes:24310867 (24.3 MB)
          Interrupt:26 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:252430 (252.4 KB)  TX bytes:252430 (252.4 KB)



nikhil@nikhil-desktop:~$ ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=255 time=0.296 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=255 time=0.221 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=255 time=0.227 ms
64 bytes from 192.168.0.2: icmp_seq=4 ttl=255 time=0.225 ms

---

### Post by nikhil.deshmukh on 2011-09-09
Hi
if anyone wants to debug post me the commands and i will post the results of the same

Thanks

---

### Post by fdrake on 2011-09-09
can you post the results for
```

less /var/log/syslog | grep eth0 | tail -100
nm-tool

```

---

### Post by nikhil.deshmukh on 2011-09-09
Sep  9 08:26:59 nikhil-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="795" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Sep  9 08:29:59 nikhil-desktop anacron[9864]: Job `cron.daily' terminated (mailing output)
Sep  9 08:29:59 nikhil-desktop anacron[9864]: Job `cron.weekly' started
Sep  9 08:29:59 nikhil-desktop anacron[10384]: Updated timestamp for job `cron.weekly' to 2011-09-09
Sep  9 08:29:59 nikhil-desktop sendmail[10379]: My unqualified host name (nikhil-desktop) unknown; sleeping for retry
Sep  9 08:30:01 nikhil-desktop CRON[10391]: (root) CMD (php /var/www/ticket_imp/mysqldump/download_mysql_backups.php)
Sep  9 08:30:01 nikhil-desktop CRON[10394]: (nikhil) CMD (curl "http://www.ticketlocal.com/cron_release_cart_locks.php")
Sep  9 08:30:01 nikhil-desktop CRON[10393]: (nikhil) CMD (curl "http://www.ticketlocal.com/casino/show_release_holds.php" # JOB_ID_1)
Sep  9 08:30:08 nikhil-desktop anacron[9864]: Job `cron.weekly' terminated (mailing output)
Sep  9 08:30:09 nikhil-desktop sendmail[10430]: My unqualified host name (nikhil-desktop) unknown; sleeping for retry
Sep  9 08:31:00 nikhil-desktop sendmail[10379]: unable to qualify my own domain name (nikhil-desktop) -- using short name
Sep  9 08:31:00 nikhil-desktop sendmail[10379]: p89310WN010379: from=root, size=205, class=0, nrcpts=1, msgid=<201109090301.p89310WN010379@nikhil-desktop>, relay=root@localhost
Sep  9 08:31:00 nikhil-desktop sm-mta[10431]: p893108u010431: from=<root@nikhil-desktop>, size=463, class=0, nrcpts=1, msgid=<201109090301.p89310WN010379@nikhil-desktop>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Sep  9 08:31:00 nikhil-desktop sendmail[10379]: p89310WN010379: to=root, ctladdr=root (0/0), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30205, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p893108u010431 Message accepted for delivery)
Sep  9 08:31:00 nikhil-desktop sm-mta[10432]: p893108u010431: to=<root@nikhil-desktop>, ctladdr=<root@nikhil-desktop> (0/0), delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30684, dsn=2.0.0, stat=Sent
Sep  9 08:31:09 nikhil-desktop sendmail[10430]: unable to qualify my own domain name (nikhil-desktop) -- using short name
Sep  9 08:31:09 nikhil-desktop sendmail[10430]: p893194X010430: from=root, size=207, class=0, nrcpts=1, msgid=<201109090301.p893194X010430@nikhil-desktop>, relay=root@localhost
Sep  9 08:31:09 nikhil-desktop sm-mta[10434]: p89319vo010434: from=<root@nikhil-desktop>, size=465, class=0, nrcpts=1, msgid=<201109090301.p893194X010430@nikhil-desktop>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Sep  9 08:31:09 nikhil-desktop sendmail[10430]: p893194X010430: to=root, ctladdr=root (0/0), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30207, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p89319vo010434 Message accepted for delivery)
Sep  9 08:31:09 nikhil-desktop anacron[9864]: Normal exit (2 jobs run)
Sep  9 08:31:09 nikhil-desktop sm-mta[10435]: p89319vo010434: to=<root@nikhil-desktop>, ctladdr=<root@nikhil-desktop> (0/0), delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30686, dsn=2.0.0, stat=Sent
Sep  9 08:33:22 nikhil-desktop sm-mta[10438]: p879AR6l014283: to=<techsupport@rediff.com>, ctladdr=<www-data@nikhil-desktop> (33/33), delay=1+17:52:54, xdelay=00:00:42, mailer=esmtp, pri=22620571, relay=rediff.com. [64.27.53.172], dsn=4.0.0, stat=Deferred: Connection timed out with rediff.com.
Sep  9 08:33:22 nikhil-desktop sm-mta[10438]: p8798uwF014241: to=<techsupport@rediff.com>, ctladdr=<www-data@nikhil-desktop> (33/33), delay=1+17:54:26, xdelay=00:00:00, mailer=esmtp, pri=22620571, relay=rediff.com., dsn=4.0.0, stat=Deferred: Connection timed out with rediff.com.
Sep  9 08:33:22 nikhil-desktop sm-mta[10438]: p877k0PH013785: to=<techsupport@rediff.com>, ctladdr=<www-data@nikhil-desktop> (33/33), delay=1+19:17:22, xdelay=00:00:00, mailer=esmtp, pri=23430571, relay=rediff.com., dsn=4.0.0, stat=Deferred: Connection timed out with rediff.com.
Sep  9 08:33:22 nikhil-desktop sm-mta[10438]: p877caT1013749: to=<techsupport@rediff.com>, ctladdr=<www-data@nikhil-desktop> (33/33), delay=1+19:24:46, xdelay=00:00:00, mailer=esmtp, pri=23430571, relay=rediff.com., dsn=4.0.0, stat=Deferred: Connection timed out with rediff.com.
Sep  9 08:33:22 nikhil-desktop sm-mta[10438]: p85CYbr1028464: to=<techsupport@rediff.com>, ctladdr=<www-data@nikhil-desktop> (33/33), delay=3+14:28:44, xdelay=00:00:00, mailer=esmtp, pri=46740576, relay=rediff.com., dsn=4.0.0, stat=Deferred: Connection timed out with rediff.com.
Sep  9 08:33:22 nikhil-desktop sm-mta[10438]: p857eqar027123: to=<techsupport@rediff.com>, ctladdr=<www-data@nikhil-desktop> (33/33), delay=3+19:22:30, xdelay=00:00:00, mailer=esmtp, pri=49350575, relay=rediff.com., dsn=4.0.0, stat=Deferred: Connection timed out with rediff.com.
Sep  9 08:33:22 nikhil-desktop sm-mta[10438]: p857eCrZ027119: to=<techsupport@rediff.com>, ctladdr=<www-data@nikhil-desktop> (33/33), delay=3+19:23:09, xdelay=00:00:00, mailer=esmtp, pri=49350575, relay=rediff.com., dsn=4.0.0, stat=Deferred: Connection timed out with rediff.com.
Sep  9 08:33:22 nikhil-desktop sm-mta[10438]: p857W2OS027034: to=<techsupport@rediff.com>, ctladdr=<www-data@nikhil-desktop> (33/33), delay=3+19:31:20, xdelay=00:00:00, mailer=esmtp, pri=49440575, relay=rediff.com., dsn=4.0.0, stat=Deferred: Connection timed out with rediff.com.
Sep  9 08:33:22 nikhil-desktop sm-mta[10438]: p857TtUF026970: to=<techsupport@rediff.com>, ctladdr=<www-data@nikhil-desktop> (33/33), delay=3+19:33:26, xdelay=00:00:00, mailer=esmtp, pri=49440575, relay=rediff.com., dsn=4.0.0, stat=Deferred: Connection timed out with rediff.com.
Sep  9 08:33:22 nikhil-desktop sm-mta[10438]: p857XKaE027056: to=<techsupport@rediff.com>, ctladdr=<www-data@nikhil-desktop> (33/33), delay=3+19:30:01, xdelay=00:00:00,

---

### Post by fdrake on 2011-09-09
what do you get with

```
dig -t google.com
```

---

### Post by nikhil.deshmukh on 2011-09-09
nikhil@nikhil-desktop:~$ dig -t google.com
;; Warning, ignoring invalid type google.com

; <<>> DiG 9.7.0-P1 <<>> -t google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: FORMERR, id: 11158
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;.				IN	NS

;; Query time: 0 msec
;; SERVER: 192.168.0.2#53(192.168.0.2)
;; WHEN: Fri Sep  9 11:43:44 2011
;; MSG SIZE  rcvd: 17

---

### Post by Wim Sturkenboom on 2011-09-09
in the browser address bar
[http://74.125.233.19](http://74.125.233.19)

should give you google

If so, definitely a dns problem

If not, can you ping 74.125.233.19? Make sure the firewall does not block icmp (ping).

---

### Post by nikhil.deshmukh on 2011-09-09
no result 

In Browser its says
The connection has timed out

nikhil@nikhil-desktop:~$ ping 74.125.233.19
PING 74.125.233.19 (74.125.233.19) 56(84) bytes of data.
this is not giving any responses

---

### Post by kunal00731 on 2011-09-09
Hi  Nikhil ,

This  definitely looks like a DNS problem. If you are using a wired connection , can you tell me which one you are using. Is it reliance or tata indicom? Also I would suggest you to look at the network manager and see what  it is displaying.

Next run this command :

lsusb

and post the output.

---

### Post by nikhil.deshmukh on 2011-09-09
hi i am using airtel
well i am the only one who use ubuntu everyone else is on windows
it was working earlier but i changed my software resources to korea..
and then the problem starts

lsusb  shows
Bus 005 Device 002: ID 046d:c05b Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by kunal00731 on 2011-09-09
[FONT=Times New Roman][SIZE=4]Nikhil ,

I think your modem is not getting detected. 
As I have told, have you looked into your network manager in ubuntu , does this say that you are connected ? 

I implore you to do that at first and also install gnome-pp using any other connection if possible.

Go through  this link , it consists the how to for installing gnome-pp and detecting and configuring your analog modem .

[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

check out the terminals /dev/tty0 and /dev/tty1 to see whether your modem is mounted there or not.

Hope it works and if it does not tell me what is the output of this command:

[/SIZE][/FONT]**[FONT=Times New Roman][SIZE=4]gksudo nm-applet[/SIZE][/FONT]**
[COLOR=Black]
[/COLOR][SIZE=3][COLOR=Black]You might get  2 network connection icons. One is the one that is active, the  other one is not and has an exclamation mark against it.[/COLOR][/SIZE]

  [SIZE=3]Right click and choose "about" and it will tell you  what connection it has.[/SIZE]
[FONT=Times New Roman][SIZE=4]

[/SIZE][/FONT]

---

