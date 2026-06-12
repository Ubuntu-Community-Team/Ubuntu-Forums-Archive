---
title: "Just need to know what are these ports all about.."
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2008-09-24
I have Hardy, I read a few days ago about hackers penetrating into other system through some open ports. I did a nmap scan on my system and came across some ports. But I can't figure about what are they all about. So, I would be glad if someone could tell me what are they all about.

result of 
```
 nmap -p- -A -T4 localhost
```
```
Starting Nmap 4.53 ( http://insecure.org ) at 2008-09-25 01:22 IST
SCRIPT ENGINE: rpcinfo.nse is not a file.
SCRIPT ENGINE: Aborting script scan.
Interesting ports on localhost (127.0.0.1):
Not shown: 65529 closed ports
PORT      STATE SERVICE     VERSION
22/tcp    open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)
25/tcp    open  smtp        Exim smtpd 4.69
139/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
4488/tcp  open  unknown
58757/tcp open  ssl/unknown
Service Info: Host: sahni-laptop; OS: Linux

Service detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 122.684 seconds

```

---

### Post by jonobr on 2008-09-24
Good idea to just google or go to Iana and look at well known port numbers.

Theres oodles of info around on what different ports do and mean, Theres a lot of talented folks here if you believe you think you have an open port, that could be exploited they may give advice,
however, I recommend do some investigation yourself and figure out what you have running

---

### Post by Iowan on 2008-09-24
The first three tell you what service is running (or what normally runs there).  The last one looks like ssl - the other one???

---

### Post by sheffrem on 2008-09-24
22/tcp    open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)

This port is used for making secure connection over networks, like you can login to a different computer while having a secure and protected communication with it. It replace services like FTP, Telnet which allow transmission between computers to be read in plain text. The service that run on that port is call sshd. run  services-admin  in terminal and in the list you will see it.



port 25 is for SMTP(Simple Mail Transmission Protocol) and is used to send email. Its a mail server just like yahoo has a mail server, but SMTP is motsly used on local machines to send messages regarding the system status, that is if the administrator put his email in the system configuration files, the system will send him/her a message using SMTP.

139 and 449 are both used by SAMBA to share files and printers mainly with windows machines.

58757 is used by SSL (Secure Socket Layer). This protocol is used by other protocol like TCP/IP suite to encrypt connections.


Anybody seeing a mistake in my comment, let me know.

---

### Post by eentonig on 2008-09-24
Pretty self explanating if you ask me.

> PORT      STATE SERVICE     VERSION
22/tcp    open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)
25/tcp    open  smtp        Exim smtpd 4.69
139/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
445/tcp   open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
4488/tcp  open  unknown
58757/tcp open  ssl/unknown


22 = Your ssh server
25 =  your mail server
139, 445 = your network file sharing serviced by the package samba
58757 =  some ssl service you have running

4488 = some other server you've got running. Probably something like an webserver on a non-standard  port? (just guessing)

Since Ubuntu comes with no public ports activated (because there are no public services offered by default), if any of these are not from services you installed/activated yourselves (or the person who manages your system), you have a problem.

EDIt: Never mind. sheffrem already excplained

---

### Post by sheffrem on 2008-09-24
22/tcp    open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1.2 (protocol 2.0)

This port is used for making secure connection over networks, like you can login to a different computer while having a secure and protected communication with it. It replace services like FTP, Telnet which allow transmission between computers to be read in plain text. The service that run on that port is call sshd. run  services-admin  in terminal and in the list you will see it.



port 25 is for SMTP(Simple Mail Transmission Protocol) and is used to send email. Its a mail server just like yahoo has a mail server, but SMTP is motsly used on local machines to send messages regarding the system status, that is if the administrator put his email in the system configuration files, the system will send him/her a message using SMTP.

139 and 449 are both used by SAMBA to share files and printers mainly with windows machines.

58757 is used by SSL (Secure Socket Layer). This protocol is used by other protocol like TCP/IP suite to encrypt connections.


Anybody seeing a mistake in my comment, let me know.

---

### Post by shredder12 on 2008-09-25
all of the open ports seem to be there because of certain application but i suspect the 4488 port. Could it be a trojan??
Actually i also have apache2 running on my system. Though i have stopped it but the ports is still there( after another scan). so, what could it be??
help please..

---

### Post by amac777 on 2008-09-25
To find out what programs are controlling the listening ports on your computer, use netstat:

sudo netstat -tlp

the -tlp means: t=tcp ports, l=listening ports, p=show program/pid name

---

### Post by bab1 on 2008-09-25
For a complete listing you can use:```
sudo netstat -plntu
```

---

### Post by shredder12 on 2008-09-25
hey i got it..
the 4488 port was used by my linuxdcpp..newaz..thanks for all u guys help..

---

