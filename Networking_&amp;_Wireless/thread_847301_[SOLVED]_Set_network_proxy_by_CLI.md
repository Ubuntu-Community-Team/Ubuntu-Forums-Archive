---
title: "[SOLVED] Set network proxy by CLI"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by sci-fi guy on 2008-07-02
How do I set a network proxy from the CLI?

---

### Post by sci-fi guy on 2008-07-25
Well, to answer my own question: [http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

```
Edit your /etc/bash.bashrc file as root.

Put these line at the end of your /etc/bash.bashrc file :

export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/

You can omit the username:password, if your proxy server has no password
```

---

