---
title: "vnstat - still not enough data collected"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-05-13
Hi Everyone,

I recently started playing with Xubuntu 11.04 and like it quite a bit.
I'm having trouble with vnstat though.

I have it working in Ubuntu 10.10 but I can't seem it get it to work in Xubuntu.

I ran the command
```
sudo vnstat -u -i eth0
```

and I've checked the databse eth0 which is in /var/lib/vnstat/
is owned by root but readable and writable by everyone.

I still get the error message that not enough data has been collected.  It's been over an hour since it should have started collecting.  I am connected to the internet via eth0.

Any idea?

Thank you for any help.  I appreciate it.

---

### Post by Toz on 2011-05-13
What is the result of:```
sudo /etc/init.d/vnstat status
```
If you get a not running message, then:```
sudo /etc/init.d/start
```
What is the result of:```
vnstat -l -i eth0
```

---

### Post by GrouchyGaijin on 2011-05-13
> **Toz said:**
> What is the result of:```
sudo /etc/init.d/vnstat status
```
If you get a not running message, then:```
sudo /etc/init.d/start
```
What is the result of:```
vnstat -l -i eth0
```

Thanks for the reply!  Actually shortly after I posted this I started getting data in vnstat.  This sounds stupid, but I tried a few more things and I guess I hit the right one.  Now if I could remember what exactly that was.

In any case, thank you for helping!

---

