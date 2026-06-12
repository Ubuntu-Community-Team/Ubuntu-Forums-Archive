---
title: "[SOLVED] setting up fwanalog to analyse UFW log"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by adieb on 2008-07-01
does anybody know how to set up fwanalog in combination to UFW?

UFW is working great an logs all sorts of blocked packages to /var/log/messages like:

```
Jul  1 13:51:28 asgard2 kernel: [2476982.522294] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:05:98:af:6c:00:08:e2:a5:d0:80:08:00 SRC=131.220.115.10 DST=131.220.115.40 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=1328 DF PROTO=TCP SPT=58320 DPT=389 WINDOW=5840 RES=0x00 SYN URGP=0 
Jul  1 13:51:28 asgard2 kernel: [2476982.522316] [UFW BLOCK INPUT]: IN=eth0 OUT= 
MAC=00:30:05:98:af:6c:00:08:e2:a5:d0:80:08:00 SRC=131.220.115.10 DST=131.220.115.40 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=51798 DF PROTO=TCP SPT=39881 DPT=21 WINDOW=5840 RES=0x00 SYN URGP=0 

```


if i start fwanalog now it says:

```
Analog found 280 corrupt lines. Please consider sending 
/var/log/fwanalog/analog.err to balazs@tud.at 
so the author is able to fix the problem.

```

here are some lines of /var/log/fwanalog/analog.err

```

C: /var/log/messages:Jul  1 13:51:28 asgard2 kernel: [2476982.522051] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:05:98:af:6c:00:08:e2:a5:d0:80:08:00 SRC=131.220.115.10 DST=131.220.115.40 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=47629 DF PROTO=TCP SPT=37965 DPT=636 WINDOW=5840 RES=0x00 SYN URGP=0 
C:                          *
C: /var/log/messages:Jul  1 13:51:28 asgard2 kernel: [2476982.522294] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:05:98:af:6c:00:08:e2:a5:d0:80:08:00 SRC=131.220.115.10 DST=131.220.115.40 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=1328 DF PROTO=TCP SPT=58320 DPT=389 WINDOW=5840 RES=0x00 SYN URGP=0 
C:                          *
C: /var/log/messages:Jul  1 13:51:28 asgard2 kernel: [2476982.522316] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:05:98:af:6c:00:08:e2:a5:d0:80:08:00 SRC=131.220.115.10 DST=131.220.115.40 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=51798 DF PROTO=TCP SPT=39881 DPT=21 WINDOW=5840 RES=0x00 SYN URGP=0 
C:                          *
analog: Warning L: Large number of corrupt lines in logfile
  /var/log/fwanalog/fwanalog.all.log: turn debugging on or try different
  LOGFORMAT
  (For help on all errors and warnings, see /usr/share/doc/analog/docs/errors.html)
    Current logfile format:
      %S %j %u [%d/%M/%Y:%h:%n:%j] "%j%w%r%wHTTP%j" %c %b "%f" "%j" %t %v\n


```


I didn´t find anything in the internet according to fwanalog and UFW.

So here is the /etc/fwanalog/fwanlog.opts

```

outdir="/var/log/fwanalog"
logformat="iptables"
inputfiles_mask="messages*"	
inputfiles_dir="/var/log"	
inputfiles_mtime="31"		
inputfiles=`find $inputfiles_dir -maxdepth 1 -name "$inputfiles_mask" -mtime $inputfiles_mtime | sort -r`

onehost=true
sep_hosts=false
sep_packets=false
analog="analog"
date="date"		
grep="grep" 	
egrep="egrep"	
zegrep="zegrep" 
gzcat="gzcat"	
sed="sed"
perl="perl"
tcpdump="tcpdump"
timezone=`$date +%z`

```


any idea? thanks a lot ...

---

### Post by adieb on 2008-07-08
really nobody?

---

### Post by adieb on 2008-07-24
Hallo, 

due to very few information about this problem i am posting the solution here ...
The ubuntuforums-user stevotower figured out, that zgrep prints out the filename like here:
```
C: /var/log/messages:Jul  1 13:51:28 asgard2 kernel: [2476982.522051] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:05:98:af:6c:00:08:e2:a5:d0:80:08:00 SRC=131.220.115.10 DST=131.220.115.40 LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=47629 DF PROTO=TCP SPT=37965 DPT=636 WINDOW=5840 RES=0x00 SYN URGP=0 

```

But then fwanalog doesn´t understand it anymore and complains about wrong logformat.

So what you have to do is to change /bin/zgrep (it´s a script actually) in line 108.
it should look like that:
```
 files_without_matches=1;;
  (-h | --no-f*)

```

(add the "-h |").

Thank you stevotower.

---

