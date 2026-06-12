---
title: "script using multiple telnet sessions?"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by gregrun on 2008-09-25
Below is a shortened, basic script I have written to backup some switch configs using telnet(these switches do not have ssh). I can run this script from the command line without any problems. However, when I add this executable to crontab, only the first config will copy. 

A couple things that I do not quite understand:
   If this were a permissions/environment issue, the first config should not have copied.
   Both echo'd lines are redirected, meaning the entire script is being read. It's not aborted after the first copied config
   I think the format should work because it works from the command line.

Any help would be appreciated. 

#!/bin/bash
usr=admin
pass=password
cmd1='copy config tftp address x.x.x.x filename sw/'
cmd2='copy running tftp address x.x.x.x filename sw/'
#cmd will copy config to /tftpboot/sw directory


nam3=LocationA;            sw3=10.10.10.10
nam4=LocationB;             sw4=10.10.10.11
nam5=LocationC;                sw5=10.10.10.12

echo "Starting script" >> /tmp/backup.log

{ sleep 2; echo $usr; sleep 1; echo $pass; sleep 1; echo $cmd1"$nam3.`date +%Y%m%d`"; sleep 40; echo $cmd2"$nam3.txt.`date +%Y%m%d`"; sleep 5
} | telnet $sw3

{ sleep 2; echo $usr; sleep 1; echo $pass; sleep 1; echo $cmd1"$nam4.`date +%Y%m%d`"; sleep 40; echo $cmd2"$nam4.txt.`date +%Y%m%d`"; sleep 5
} | telnet $sw4

echo "testing redirect " >> /tmp/backup.log

{ sleep 2; echo $usr; sleep 1; echo $pass; sleep 1; echo $cmd1"$nam5.`date +%Y%m%d`"; sleep 40; echo $cmd2"$nam5.txt.`date +%Y%m%d`"; sleep 5
} | telnet $sw5

---

### Post by ghostdog74 on 2008-09-25
if you have Perl or Python installed on the machine you initiate telnet, you can use telnet modules, such as [this](http://www.google.com.sg/search?hl=en&q=Net%3A%3ATelnet&btnG=Google+Search&meta=) or [this](http://www.google.com.sg/search?hl=en&q=Python+telnetlib&btnG=Google+Search&meta=).
They have better error control over your telnet session and more reliable than using telnet client from the shell.

---

### Post by gregrun on 2008-09-25
Can this all be done within one script? If so, I will definitely look into it.

---

### Post by ghostdog74 on 2008-09-26
yes of course.

---

