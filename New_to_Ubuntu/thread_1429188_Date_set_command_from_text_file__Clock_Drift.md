---
title: "Date set command from text file / Clock Drift"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by jmknash on 2010-03-13
Hi,

It's been a while since I've used my linux systems so I'm wondering if someone could help me with a simple script, I'll tell you the current scenario.

I have a mobile Debian Linux system we'll call that 'CLIENT' which doesn't have a hardware clock so the time tends to drift overtime substantially and any NTP clients are out of the question due to the aged micro computer.

On my 'CLIENT' I have created a primative Date/Time retrieving Dumping script ; 

rm /tmp/dateget.txt
scp -i /root/scpkey/id_rsa [email]root@192.168.10.1:/tmp/dateget.txt[/email] /tmp

On the Ubuntu SERVER, it's set every few minutes to dump the current time to this text file '/tmp/dateget.txt' for the CLIENT to collect via cron.

'date > /tmp/dateget.txt'

-----------------------------------------------------------------------------------------------------------------------------------------------

Now it all works but I am stuck how to automatically copy and paste the text file with the date/time inside it to the date -s command;

This is what I tried but i'm no programmer :p
date -s cat < /tmp/dateget.txt

(inside the text file is a date format for example - "Sat Mar 13 23:50:00 UTC 2010")

Normally a user would type manually to set the date:
date -s "Sat Mar 13 23:50:00 UTC 2010"

Many thanks in advance,

Jon

---

### Post by RealPSL on 2010-03-13
Try ```
date -s `cat /tmp/dateget.txt`
```. This runs the cat command first so that the date command can use it as input.

---

### Post by jmknash on 2010-03-14
hi.. it didnt seem to like that formula..

LinkStation:~# date -s `cat /tmp/dateget.txt`
date: extra operand `14'
Try `date --help' for more information.

(curent date in text file is: Sun Mar 14 20:30:00 UTC 2010)

---

### Post by jmknash on 2010-03-14
I think this works, I just modified your code a bit, it looks like its sticking when i recheck with date.

date -s "`cat /tmp/dateget.txt`"


'
LinkStation:/tmp# date -s "`cat /tmp/dateget.txt`"
Sun Mar 14 20:35:01 GMT 2010
LinkStation:/tmp# date
Sun Mar 14 20:35:02 GMT 2010
LinkStation:/tmp#
'

---

