---
title: "Root hints in Ubuntu"
date: 2015-10-26
forum: Networking &amp; Wireless
---

### Post by papakota on 2015-10-26
Hello!
I've checked the /etc/bind/db.root text file and all the root name server IP's are current (I've checked the IP's one by one). So BIND9 reads this file and knows how to find root servers. 
The output of dig . ns command shows me this. Why I can't see in the output the actual IP addresses? Is that normal???

;; ANSWER SECTION:
.            13309    IN    NS    i.root-servers.net.
.            13309    IN    NS    e.root-servers.net.
.            13309    IN    NS    g.root-servers.net.
.            13309    IN    NS    d.root-servers.net.
.            13309    IN    NS    b.root-servers.net.
.            13309    IN    NS    a.root-servers.net.
.            13309    IN    NS    m.root-servers.net.
.            13309    IN    NS    l.root-servers.net.
.            13309    IN    NS    k.root-servers.net.
.            13309    IN    NS    j.root-servers.net.
.            13309    IN    NS    f.root-servers.net.
.            13309    IN    NS    c.root-servers.net.
.            13309    IN    NS    h.root-servers.net.


Then why some people include this in their configuration files?

zone "." {
    type hint;
    file "root.hints";
};  

OR:
 
zone "." {
          type hint;
          file "db.root";
};

---

