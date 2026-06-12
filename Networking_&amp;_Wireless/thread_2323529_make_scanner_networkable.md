---
title: "make scanner networkable"
date: 2016-05-06
forum: Networking &amp; Wireless
---

### Post by pedro_rodriguez2 on 2016-05-06
My scanner works fine with xsane. No problems.

I am using a program called Formreturn, which makes and reads multiple choice question forms. Its scanner program, [http://swingsane.com/](http://swingsane.com/) needs a networkable scanner. Swing Sane can not detect my scanner. Also I can not add my scanner in the Swing Sane program. If I click 'add scanner' and enter 127.0.0.1  I get this in the client console:

> Discovery complete
127.0.1.1:6566 - Connection refused
Querying pedro-275E4E-275E5E (127.0.1.1:6566)
Discovery complete
127.0.0.1:6566 - Connection refused
Querying localhost (127.0.0.1:6566)
Discovery complete
127.0.1.1:6566 - Connection refused

Something is blocking the connection.

Trying to enable my scanner for networking, even though it is actually just on my laptop, not a network as such, I am running into problems.

I followed the steps here:

[https://help.ubuntu.com/community/sane](https://help.ubuntu.com/community/sane)

and here:

[https://help.ubuntu.com/community/SaneDaemonTutorial](https://help.ubuntu.com/community/SaneDaemonTutorial)

near the end, I get this:

> pedro@pedro-275E4E-275E5E:~$ sudo service saned status
&#9679; saned.service
   Loaded: masked (/dev/null; bad)
   Active: inactive (dead)
pedro@pedro-275E4E-275E5E:~$

and this:

> pedro@pedro-275E4E-275E5E:~$ sudo service saned restart
Failed to restart saned.service: Unit saned.service is masked.
pedro@pedro-275E4E-275E5E:~$

How do I unmask saned.service? Can I do that? Will that cause other problems?

---

