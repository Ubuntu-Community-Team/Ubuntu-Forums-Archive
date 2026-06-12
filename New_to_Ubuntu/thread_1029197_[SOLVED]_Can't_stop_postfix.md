---
title: "[SOLVED] Can't stop postfix"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by gerreth on 2009-01-03
Hi,

While testing postfix, i decided to send an email to a gmailadres.
The mail is never deliverd but my computer keeps trying to send it.

i ran 
```
tail -f /var/log/syslog
```
which told me:
Jan  3 12:10:23 gerreth-laptop postfix/smtp[8930]: 13884121BE: to=<**********@gmail.com>, relay=none, delay=71343, delays=71192/0.02/151/0, dsn=4.4.1, status=deferred (connect to alt1.gmail-smtp-in.l.google.com[209.85.221.179]:25: Connection timed out)

I tried
```
killall postfix
```
But that doesn't work :(

Thx for reading/helping.
.
Gerreth

---

### Post by brian_p on 2009-01-03
> **gerreth said:**
> 

I tried
```
killall postfix
```
But that doesn't work :(

```
sudo killall postfix
```

is more likely to succeed.

But I'd be inclined to do

```
sudo /etc/init.d/postfix stop
```

---

### Post by gerreth on 2009-01-03
Sudo killall didn't work.

```
sudo /etc/init.d/postfix stop
```
This thing did the job!

Thx!

---

### Post by albinootje on 2009-01-03
> **gerreth said:**
>  While testing postfix, i decided to send an email to a gmailadres.
The mail is never deliverd but my computer keeps trying to send it.
-- cut --
I tried
```
killall postfix
```
But that doesn't work :(


The ...
```

killall postfix

```
... will never work, because postfix is only the name of the project and the package. It does however consist of a few different programs.

For example on a mailserver :
```

ps auxw|grep postfix

root     20344  0.0  0.2   4820  1636 ?        Ss    2008   0:14 /usr/lib/postfix/master
postfix  20358  0.0  0.2   4936  1844 ?        S     2008   0:02 qmgr -l -t fifo -u
postfix  20375  0.0  0.3   4988  2116 ?        S     2008   0:00 tlsmgr -l -t unix -u -c
postfix   9860  0.0  0.2   4824  1636 ?        S    11:25   0:00 anvil -l -t unix -u -c
postfix  26296  0.0  0.4   5316  2964 ?        S    12:55   0:00 smtpd -n smtp -t inet -u -c -o content_filter spamfilter:
postfix  26298  0.0  0.3   4832  1952 ?        S    12:55   0:00 trivial-rewrite -n rewrite -t unix -u -c

```

If you want to check the status of the mail queue of postfix:
```

mailq

```

If you want to stop postfix :
```

/etc/init.d/postfix stop

```

See also :
```

man postfix

```

Is your ISP actually allowing the usage of port 25 by yourself ?
Or are you forced to use a different port, or just their smtp-server ?
Just wondering.

---

### Post by gerreth on 2009-01-03
> 
Is your ISP actually allowing the usage of port 25 by yourself ?
Or are you forced to use a different port, or just their smtp-server ?
Just wondering.

I'm just configuring it locally. Next stage will be connecting it to the internet. Part of giant school project. :KS

And I'm not sure i can use port 25... (how euh, can i check this?)

---

### Post by albinootje on 2009-01-03
> **gerreth said:**
> I'm just configuring it locally. Next stage will be connecting it to the internet. Part of giant school project. :KS

:)
> 
And I'm not sure i can use port 25... (how euh, can i check this?)

Here's an example in a terminal :

$ telnet smtp.gmail.com 25

Trying 66.249.93.111...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP u7sm22624993uge.57

If you get a timeout then there's something wrong :|

---

### Post by gerreth on 2009-01-03
> 

Here's an example in a terminal :

$ telnet smtp.gmail.com 25

Trying 66.249.93.111...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP u7sm22624993uge.57

If you get a timeout then there's something wrong :|

Not responding. But some things are quite screwed. Will please check my other post aswell? [-o<

[http://ubuntuforums.org/showthread.php?t=1028353](http://ubuntuforums.org/showthread.php?t=1028353)

Thx!

---

### Post by brian_p on 2009-01-03
> **gerreth said:**
> Not responding. But some things are quite screwed. 

Is there any mention of TLS in the postfix logs when sending to gmail.com?

---

### Post by brian_p on 2009-01-03
> **albinootje said:**
> :)


Here's an example in a terminal :

$ telnet smtp.gmail.com 25

Trying 66.249.93.111...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP u7sm22624993uge.57

Continuing with EHLO, MAIL FROM: etc gets interesting.

---

