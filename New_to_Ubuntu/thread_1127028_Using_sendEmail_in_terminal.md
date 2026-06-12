---
title: "Using sendEmail in terminal"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by steve101101 on 2009-04-16
I am trying to send an email to my email account using sendEmail here is what happens though ...

```

steven@steven-desktop:~$ sendEmail -f mailaddress@yahoo.com -t mailaddress@yahoo.com -u test
Reading message body from STDIN because the '-m' option was not used.
If you are manually typing in a message:
  - First line must be received within 60 seconds.
  - End manual input with a CTRL-D on its own line.

Apr 16 01:09:45 steven-desktop sendEmail[21076]: Message input complete.
Apr 16 01:09:45 steven-desktop sendEmail[21076]: ERROR => Connection attempt to localhost:25 failed: IO::Socket::INET: connect: Connection refused
steven@steven-desktop:~$ 

```

---

### Post by HermanAB on 2009-04-16
OK, sendEmail seems similar to nullmailer and is a very simple mail forwarding agent.

It seems to be telling exactly what the problem is though.  Add the -m and the (quoted) message before pressing Enter.

```
$ sendEmail -f mailaddress@yahoo.com -t mailaddress@yahoo.com -u test -m "The message body"
```

and maybe that will work?

The next problem seems to suggest that sendEmail is in fact NOT a complete MTA and may require to install nullmailer or postfix to actually send the message:
```
ERROR => Connection attempt to localhost:25 failed: IO::Socket::INET: connect: Connection refused
```


You got to read the documentation and experiment a bit.

---

### Post by lovinglinux on 2009-04-16
> **HermanAB said:**
> The next problem seems to suggest that sendEmail is in fact NOT a complete MTA and may require to install nullmailer or postfix to actually send the message:

SendEmail doesn't require postfix or another MTA, it only requires a working smtp account on any e-mail provider. If you need to use Gmail or Yahoo Mail accounts, the you could try installing libio-socket-ssl-perl and libnet-ssleay-perl, due to the ssl authentication method. I never tried tho, because I have an account that accept smtp on port 25 without ssl.

Here is an example of sendEmail command:

```
sendEmail -f username@foo.com -t destination@foo.com -cc carboncopy@foo.com -u "Message title" -m "The body of the message" -s smtp.foo.com:25 -xu username -xp password
```

---

### Post by steve101101 on 2009-04-16
thanks both of you. I installed libio-socket-ssl-perl and libnet-ssleay-perl and then used the sendEmail command and now it works. My smtp uses ssl for security and now it works perfectly. thanks.

---

### Post by steve101101 on 2009-04-16
Everyday I am amazed at the utter power of ubuntu and its ability to do whatever you need to do. :)

---

### Post by HermanAB on 2009-04-16
Did you install sendEmail using Synaptic?  If so, then the package is broken since it should automatically install those missing libraries and you should file a bug report please. If you installed it from source, then you should consider writing a little howto guide.

---

### Post by steve101101 on 2009-04-16
I intalled it using synaptic so i guess it is broken. however i can write a how to.

---

### Post by steve101101 on 2009-04-16
here is my new howto [http://ubuntuforums.org/showthread.php?t=1127478](http://ubuntuforums.org/showthread.php?t=1127478)

---

