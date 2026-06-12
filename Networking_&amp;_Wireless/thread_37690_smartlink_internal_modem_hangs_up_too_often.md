---
title: "smartlink internal modem hangs up too often"
date: 2005-05-28
forum: Networking &amp; Wireless
---

### Post by xxfrankxx on 2005-05-28
I installed the modules as described here:
[http://ubuntuforums.org/showpost.ph...56&postcount=34](http://ubuntuforums.org/showpost.ph...56&postcount=34)
It works but it hangs up very often, many times just in the first minute of connection, it rarely also happened that the connection lasted for hours.
I don't think it is a phone line problem since in windows it does not happen.

Does anyone experience the same problem?
Any suggestion?
frank

---

### Post by xristos on 2005-05-28
Check your /etc/ppp/options file and comment out ( put # where the line starts ) everything that has to do with lcp-echo-request or something like that .

---

### Post by xxfrankxx on 2005-05-28
thanx, i'll try it and let you know the results.

Frank

---

