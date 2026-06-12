---
title: "fetchmail duplicate"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by hangab on 2010-10-12
Hello,

I've managed to set up my small homeserver (Ubuntu 10.04  x86), most of my desires could be handled with the help of ebox  (zentyal). Only one "small" problem remained.



Situation:
I have to collect letters from external mail accounts  (I could either use POP3 or IMAP).
I  use fetchmail, however I should leave the mails on the server (as a  backup) which is collected by another pc (with MS outlook) many times  per day and deleted 3-5 days later. During this time it can also occur,  that someone has to check the mails on the isp-s webmail surface. 

Problem:
Let's use IMAP:
If  I use the 'keep' option I can leave the mails on the server. But  fetchmail is not going to download if either the other server or someone  on the isp-s webmail has read the mail. Fetchmail sees as seen. If I  also use 'fetchall' option fetchmail will generate lots of duplicates.

Why not POP3:
If  I use the pop3 proto with the 'uidl' and 'keep' option I will get those  mails whitch have been marked seen on any of the other surfaces but  unfotunately if fetchmail is restarted (on any reason) next time it will  make a full fetching (as if I used fetchall option).


The  perfect solution would check the mails on the ISP-s server and would  download  those which have not been downloaded by fetchmail (even if they  are marked as seen). Delete duplicates after downloading would easily cause very high trafic, since ocasionaly the daily email can be 50 mb. It seems bad idea to download with each fetching.

Fetchmail is  daemon, and I am afraid the ISP would be upset if I set fetchmail to run  in every 5 seconds (whitch still wouldn't be perfect).



I hope someone has any clue for solving this problem.

Thanks for thinking 
Gabor

---

### Post by hangab on 2010-10-13
Another full day of googling I find the right mailing list , I should have started here, but I thought that someone else came across with this problem:

[http://lists.berlios.de/pipermail/fetchmail-devel/2009-January/001043.html](http://lists.berlios.de/pipermail/fetchmail-devel/2009-January/001043.html)

Solution is rather a workaround...

1. Download 6.3.9 source

2. modify 'uid.c' according the mail list

3. compile according INSTALL

4. replace fetchmail in /usr/bin/ to the one in /usr/local/bin

5. restart fetchmail

I haven't tested the workaround too long, so 
be carefull with it. The problem at least has gone :)

---

