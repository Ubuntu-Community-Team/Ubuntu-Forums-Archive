---
title: "What options shall be used to find courier-imap port"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-12-11
Hi folks,


Ubuntu 7.04 server amd64



I need to find the port used by courier-imap which is running on this server


$ apt-cache policy courier-imap```

courier-imap:
  Installed: 4.1.1.20060828-5ubuntu1
  Candidate: 4.1.1.20060828-5ubuntu1
  Version table:
 *** 4.1.1.20060828-5ubuntu1 0
        500 http://us.archive.ubuntu.com feisty/universe Packages
        100 /var/lib/dpkg/status

```


$ sudo netstat -ta | grep imap```

tcp6       0      0 *:imaps                 *:*                     LISTEN     
tcp6       0      0 *:imap2                 *:*                     LISTEN     

```


$ sudo netstat -ntulp | grep :25```

tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     4897/master         
tcp6       0      0 :::25                   :::*                    LISTEN     4897/master

```


To my understanding 143 should be IMAP port

$ sudo netstat -ntulp | grep :143```

tcp6       0      0 :::143                  :::*                    LISTEN     4751/couriertcpd  

```


$ telnet localhost 143```

Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2005 Double Precision, Inc.  See COPYING for distribution information.

```
w/o hello greeting !!!


What options should be up to find courier-imap port?  TIA


B.R.
satimis

---

