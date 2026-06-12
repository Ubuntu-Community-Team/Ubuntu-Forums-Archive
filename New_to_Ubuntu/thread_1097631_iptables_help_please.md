---
title: "iptables help please?"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by cairnzi on 2009-03-16
hi people, can somebody tell me how to (simply) stop iptables replying to ICMP Echo requests? have searched google to no avail so hoping i can get the awnser here straight from the horses mouth so to speak;) 

Cheers.

---

### Post by billgoldberg on 2009-03-16
It's possible with UFW.

See here:

[https://answers.launchpad.net/ufw/+question/26585](https://answers.launchpad.net/ufw/+question/26585)

---

### Post by blueridgedog on 2009-03-16
This is best done with a gui if you are not aware of the meaning.

But, the command line would be something like:

```
/sbin/iptables -A INPUT -p icmp --icmp-type echo-request -j DROP
```

Follow Bill's link and you should be able to set something up.

---

### Post by cairnzi on 2009-03-16
@blueridgedog,billgoldberg many thanks thats it sorted, cheers.:KS

---

### Post by lovinglinux on 2009-03-16
This could help with other commands

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

---

