---
title: "rsync from ubuntu on the wan to ubuntu on cloud"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by Meronj on 2011-03-15
Hi 

I would like to backup my files from a Ubuntu server (on the Wan) to a Ubuntu server on the  cloud .
i'm able to ssh from my Ubuntu server to the Ubuntu server on the cloud with a public key.
when i try to rsync from my server to the cloud i get the following .

rsync -ra -e ssh -i ubuntu@"IP":/home/ubuntu/merontest/* /home/it/bemerontest/


[COLOR=Red]Permission denied (publickey).
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(454) [receiver=2.6.9][/COLOR]

please advise
Thanks 
Meron

---

### Post by marshmallow1304 on 2011-03-16
The value of rsync's -e argument has a space, so put it in quotes.

```
rsync -ra -e "ssh -i" ubuntu@"IP":/home/ubuntu/merontest/* /home/it/bemerontest/
```

---

