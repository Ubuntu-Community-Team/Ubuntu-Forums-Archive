---
title: "cannot connect to Yahoo IM"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by furoido on 2009-06-19
Hi guys,

For some reason, I cannot connect to Yahoo IM using Kopete or Pidgin...just get the "connecting" message, without the connection ever being made. This only suddenly started happening today (up till yesterday I had no problems) and I have no problems connecting to MSN IM, only Yahoo...

Can anyone give me some idiot-proof advice of what to check in resolving this? (I'm a still a real Ubuntu boob, so please please do make ur instructions clear and easy to follow! Thanks!)

---

### Post by pramathesh on 2009-06-19
I've been having the same problem too mince persists from the day before yesterday =((
It just shows as connecting but never connects. But works fine with my GTalk a/c. My friend using Pidgin on Windows has the same issue with Y! there as well. The client provided by Yahoo works fine on my windows machine.
Guess something wrong @ Yahoo's end.......


Experts please rectify if I'm wrong :)

---

### Post by Jazzy_Jeff on 2009-06-19
I just tried to login with Pidgin and I am having the same problem. Must be a problem on Yahoo's end.

---

### Post by furoido on 2009-06-19
Yep, sounds like a Yahoo problem...

---

### Post by pramathesh on 2009-06-19
So do we convey the problem to the Yahoo guys!?
Just wondering..... :O

---

### Post by misswham on 2009-06-19
Same problem here.

---

### Post by caravel on 2009-06-19
Run pidgin from the terminal and see what kind of output you're getting when trying to connect.

---

### Post by golusweet on 2009-06-19
Best alternative to YM is Gyachi

It supports features like photo sharing, webcam, chatroom voice etc

[https://launchpad.net/%7Eloell/+archive/ppa/+files/gyachi_1.1.70-1%7Ejaunty_i386.deb](https://launchpad.net/%7Eloell/+archive/ppa/+files/gyachi_1.1.70-1%7Ejaunty_i386.deb)

---

### Post by Lord Noxarethor on 2009-06-19
In Pidgin, modify your account (tab: Advanced) and at Pager server type: **66.163.181.189**

---

### Post by furoido on 2009-06-19
Doesn't work, Lord...

---

### Post by webmiester on 2009-06-19
I think Yahoo has changed something with their protocol.  They probably did this intentionally, for whatever purpose it may serve.  Ive seen them change some of their protocols before making their invisible online clients appear online in pidgin, etc.

---

### Post by y6FgBn)~v on 2009-06-19
I found this [link.]("http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo")

---

### Post by jonobr on 2009-06-19
Hi all

See also [This thread on the same topic]("http://ubuntuforums.org/showthread.php?t=1191064")

Cheers!

---

### Post by webmiester on 2009-06-19
> **Lord Noxarethor said:**
> In Pidgin, modify your account (tab: Advanced) and at Pager server type: **66.163.181.189**

YAHOO!!! It worked!  Thanks so much man!

---

### Post by fl0rin on 2009-06-19
> **furoido said:**
> Doesn't work, Lord...

It does work for me, though.. Seeing Lord is from Romania, as myself, I wonder if  this might be location dependent.
Try using another IP reported by the command:

```
$ host scs.msg.yahoo.com

```Good luck!

---

### Post by braete on 2009-06-19
> **Lord Noxarethor said:**
> In Pidgin, modify your account (tab: Advanced) and at Pager server type: **66.163.181.189**

thanks, now it works! (not location dependent, i am also Romanian)

---

### Post by snakeman21 on 2009-06-19
I had the same problem, I just had to switch to AIM

---

### Post by Therion on 2009-06-19
The Other Fix is here:

**[http://ubuntuforums.org/showpost.php?p=7480983&postcount=21](http://ubuntuforums.org/showpost.php?p=7480983&postcount=21)**

---

### Post by evPaseo on 2009-06-19
I was having the same problem. Nox's answer worked for me. Thanks!

---

### Post by blackxored on 2009-06-19
I'm pretty sure somebody has reported this upstream already. But anyone could attach some pidgin debug logs about the connection attempt, please?

---

### Post by furoido on 2009-06-19
pycbill's link worked for me!

---

### Post by x3qt0r on 2009-06-21
> **Lord Noxarethor said:**
> In Pidgin, modify your account (tab: Advanced) and at Pager server type: **66.163.181.189**

Worked for me.
Am from India.

FTW ubuntu!

---

### Post by x3qt0r on 2009-06-21
> **Lord Noxarethor said:**
> In Pidgin, modify your account (tab: Advanced) and at Pager server type: **66.163.181.189**

Worked for me.
Am from India.

---

### Post by LewRockwell on 2009-06-21
[http://bigbrovar.wordpress.com/2009/06/21/how-to-fix-pidgin-and-yahoo-issues/](http://bigbrovar.wordpress.com/2009/06/21/how-to-fix-pidgin-and-yahoo-issues/)

---

### Post by Lord Noxarethor on 2009-06-23
Okay guys, enough! Anyone experiencing problems please update to Pidgin 2.5.7! Good luck.

---

### Post by mackiedizon on 2009-06-23
> **Lord Noxarethor said:**
> In Pidgin, modify your account (tab: Advanced) and at Pager server type: **66.163.181.189**



worked for me..
i'm from the philippines..

---

### Post by yaniv38 on 2009-06-23
maybe your firewall is active?

---

