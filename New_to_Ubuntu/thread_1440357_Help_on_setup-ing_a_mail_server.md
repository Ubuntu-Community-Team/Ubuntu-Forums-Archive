---
title: "Help on setup-ing a mail server?"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-27
To setup a mail server,wat are all the things i need?I am a beginner i would like like to learn a lot about ubuntu and my first project is to setup a mail server..Can anyone give me some detailed information on this?Thanks in advance..

---

### Post by r-senior on 2010-03-27
a. Sendmail plus lots of patience and lots of reading.

[http://www.google.co.uk/url?sa=t&source=web&ct=res&cd=1&ved=0CAYQFjAA&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D196112&ei=k0auS9_fJ5v80wST55GWDg&usg=AFQjCNFzianiYApBrpVW_jY0Qxro08owSw]("http://www.google.co.uk/url?sa=t&source=web&ct=res&cd=1&ved=0CAYQFjAA&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D196112&ei=k0auS9_fJ5v80wST55GWDg&usg=AFQjCNFzianiYApBrpVW_jY0Qxro08owSw")

OR b. Postfix plus slightly less patience and slightly less reading. This is the default Ubuntu mail transport agent.

[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")

OR c. msmtp and moderate patience and reading, ideal if you just want easy local mail, e.g. this example for RAID alerts

[http://ubuntuforums.org/showthread.php?t=1185134]("http://ubuntuforums.org/showthread.php?t=1185134")

OR d. Something else

Maybe exim?

[https://help.ubuntu.com/community/Exim4]("https://help.ubuntu.com/community/Exim4")

You might also want things like WebMail and stuff ...

[https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer")

Whatever you do, pay attention to security if you are exposing any of these to the big bad world outside. You don't want to end up as a spam relay.

Come back in a couple of years and let us know how you are getting on. ;)

---

### Post by r_s on 2010-03-27
To me it was one of the most difficult things to do but sadly I failed, and finally I had to use someone's  server for sending mails.

---

### Post by r-senior on 2010-03-27
It's a good point. Perhaps other easier (and potentially more useful, given that most people have mail servers provided by their ISP) projects you might like to consider first would be:

a. Apache web server?
b. FTP server?
c. Samba/NFS file server?

A web interface like Webmin can ease the configuration of a lot of these but in terms of learning, there's no substitute for getting into that /etc directory.

---

### Post by karthick87 on 2010-04-01
How to setup **[COLOR=Red]Apache web server[/COLOR]**?

---

### Post by Sk41m4n on 2010-04-01
> **getyourkarthick said:**
> How to setup **[COLOR=Red]Apache web server[/COLOR]**?

Take a look here: [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp)

---

