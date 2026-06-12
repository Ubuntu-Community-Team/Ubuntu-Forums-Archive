---
title: "my ftp speeds seem capped?"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by raffytaffy on 2007-04-10
i have a 10mb down / 500Kbps up connection. However my gftp seems to be capped @ max up speed of 50-60kbps. I have made sure my firewall was off...also tried with adding rules to allow it. .nothing buged . i tried using windows ( please dont hate me for that) i was just making sure that my ISP wasnt capping it...its not...in windows it went to 450 up speed Kbps. yet my poor gftp cant seem to get above 50-60Kbps with upload speed. my d/l speeds dont seem effected. they are within normal range. is this a common bug perhaps? can anyone shed some light on this perhaps?

---

### Post by dmizer on 2007-04-10
try a different client.  places > connect to server > change your service type to the appropriate ftp configuration, fill in all the rest of the details and hit connect.

this should make a folder on your desktop for you to browse your ftp connection.  try dragging and dropping a file in to see what kind of upload speed you get then.

---

### Post by raffytaffy on 2007-04-10
ok i have tried a few others as u suggested. Kftpgrabber , YAFTp ( in case youre wondering i have kde installed along with gnome..so i can use both apps :P . Now the speeds seem faster on those 2...they fluctuate between 30-100 and idle.  i will continue making adjustments to see if anything works,.

---

### Post by dbott67 on 2007-04-10
I just ran a test from gFTP and it's reporting 81 kilobytes (KB) per second (which equates to ~640 kilobits (Kb) per second).  I just uploaded a 5 MB file in about 1 minute.  

```
STOR /bott_ftp/wmv/tux020.pdf 
125 Data connection already open; Transfer starting.
226 Transfer complete.
Successfully transferred /home/dbott/tux020.pdf at 80.82 KB/s
SITE CHMOD 644 /bott_ftp/wmv/tux020.pdf
```Are you certain that gFTP is reporting kiloBITS per second rather than kiloBYTES per second (60 KB/s x 8 bits/byte = 480 Kbps)?

-Dave

---

### Post by raffytaffy on 2007-04-10
just tried
-> 45.66 KB/s

took about 5 mins to transfer one 5mb song~
takes a few seconds on windows hmmm

---

### Post by dmizer on 2007-04-11
on the off chance ... have you disabled ipv6?

add:
blacklist ipv6

to /etc/modprobe.d/blacklist
then reboot.

---

### Post by raffytaffy on 2007-04-11
> **dmizer said:**
> on the off chance ... have you disabled ipv6?

add:
blacklist ipv6

to /etc/modprobe.d/blacklist
then reboot.

no differance without ipv6 :(

---

### Post by dbott67 on 2007-04-11
> **raffytaffy said:**
> just tried
-> 45.66 KB/s

took about 5 mins to transfer one 5mb song~
takes a few seconds on windows hmmm

The 45.66 KB/s equates to 365 kb/s (which is slightly low, but not unreasonable based on many factors).  Ethernet does have some overhead and contention that can lower max troughput to approx. 70% capacity (500 kbps x 70% = 350 kpbs).  This seems to agree with what gFTP is reporting.

The time (5 minutes for a 5 MB file) does not (nor does just a few seconds for Windows, though).  Basically a 5 MB file is 5120 KB.  Multiplying 5120 by 8 bits per byte gives us 40,960 kilobits.  Divide that by 365 kb/s and we get 112 seconds (slightly less than 2 minutes).  

2 minutes seems reasonable for 45 KB/s, as the test from my machine took about 1 minute last night and I was getting about 80 KB/s.

Can you go to [http://www.speedtest.net/](http://www.speedtest.net/) and post your results:

[[IMG]http://www.speedtest.net/result/111875832.png[/IMG]]("http://www.speedtest.net")

This is my result from work.

-Dave

---

### Post by raffytaffy on 2007-04-11
[[IMG]http://www.speedtest.net/result/111887585.png[/IMG]](http://www.speedtest.net)

---

### Post by dbott67 on 2007-04-11
Well, if those results are from your Ubuntu computer, all is definitely well! :)  Your browser is reporting max speeds, so that is good.

As for why gFTP reports somewhat normal speeds (~365 kbps / 45 KBps) yet takes twice as long to actually perform the upload is beyond me.  Is it just to a specific server or everywhere.  Can you try uploading a file to a different server and time the upload?

Also, you may want to try uninstalling gftp & purging the settings.  Then re-install and see what happens.

-Dave

---

### Post by raffytaffy on 2007-04-11
yes. this is from buntu box. i tried to uninstall / purge / reinstall. dif servers ( a few dif ones) same speed lol.:confused:

---

### Post by dbott67 on 2007-04-11
Just to confirm, you only find the slowdown in gFTP, correct?

If so, maybe you can try one of the other FTP clients:
```
sudo apt-get install filezilla
```
or use the command-line program lftp
```
lftp -u username www.xxx.yyy.zzz
```
```
dbott@edgy:~$ lftp -u dbott 24.244.yyy.xxx
Password: 
lftp dbott@24.244.yyy.xxx:~> ls        
05-09-06  08:35AM       <DIR>          backup
03-19-05  02:06PM       <DIR>          bott
11-21-01  02:10PM       <DIR>          college
11-21-01  02:10PM       <DIR>          ftp_log
11-18-03  10:15AM       <DIR>          gatekeep_temp
03-21-05  12:28PM       <DIR>          info_nia
05-12-02  03:09PM       <DIR>          PaulC
lftp dbott@24.244.yyy.xxx:/> 

```
Check the man pages for full usage.

-Dave

---

### Post by dbott67 on 2007-04-11
double-post

---

### Post by raffytaffy on 2007-04-11
ok filezilla alot faster. cool. problem solved...somewhat eh..but ty

---

