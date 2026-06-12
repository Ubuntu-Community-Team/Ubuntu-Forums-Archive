---
title: "Find external IP terminal"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by Bananasdoom on 2010-12-27
I need to know my external IP so that I can host a minecraft server, use RDP and many other things I have used [www.whatismyip.com]("http://ubuntuforums.org/www.whatismyip.com") to get this information but is there a terminal command for this because ```
ifconfig
``` only shows my local address.

---

### Post by Verbeck on 2010-12-27
edit; after googgling a little bit, found a better one;
```

wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'

```

---

### Post by Bananasdoom on 2010-12-27
> **Verbeck said:**
> edit; after googgling a little bit, found a better one;
```

wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'

```

Thanks for that it did not work completely, I was able to get my ip by going via there simplified automated page

```
$ curl www.whatismyip.com/automation/n09230945.asp 
```

---

### Post by bodhi.zazen on 2010-12-27
How about simply:

```
curl ifconfig.me
```

---

### Post by OliverHaslam on 2012-06-02
> **bodhi.zazen said:**
> How about simply:
 
```
curl ifconfig.me
```
 
 
Old post, I know, but just wanted to say thanks for this. I've been wanting something like this so I could write a script to check my web server's current IP and email me if it changes for domain forwarding purposes. This is perfect.
 
Cheers!

---

