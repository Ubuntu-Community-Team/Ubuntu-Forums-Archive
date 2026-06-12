---
title: "Netfilter patch-o-matic fails"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by sullenx on 2008-06-25
Hello, 
    I want to compile ipt_ROUTE into my kernel, but patch-o-matic is not working. 

I downloaded:

 patch-o-matic-ng-20080521.tar.bz2
and
iptables-20080521.tar.bz2

When i do the 
```
./runme pending
```

It asks for the KERN_DIR, which i set to /usr/src/linux. But when i it asks for the IPTABLES_DIR, i set it to the directory i untared the source, and it complains: 
/usr/src/iptables-20080521 doesn't look like a iptables source code directory to me.

Any help is appreciated.

---

### Post by SpaceTeddy on 2008-06-26
i don't know the solution, but if you find one i am *very* interested in this as i have the same problem. 
But knowing this forum, an answer to a question like this is highly improbable... 

sorry for not being of any help...

---

### Post by sullenx on 2008-06-26
As it turns out, in the README file, this version of patch-o-matic calls out for iptables 1.27, which is extremly old (june 2002?).  I downloaded this source of iptables, and the script was happy with that.  Of course, i don't understand how this version of patch-o-matic built on may 2008 is looking for a 6 year old source of iptables?

---

### Post by SpaceTeddy on 2008-06-27
well, that would explain why the compiling does not work. I guess the only guys that can help there are the ones from the netfilter mailing list. I'll see if i can get around to sign up there and post this question. 

thanks for the input.

---

### Post by sherl0ck on 2008-06-30
hi, pom latest works with apt-get source iptables

---

