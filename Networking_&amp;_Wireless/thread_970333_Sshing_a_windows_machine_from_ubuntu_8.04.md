---
title: "Sshing a windows machine from ubuntu 8.04"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by kcode on 2008-11-04
I am trying do this but getting this error on following command:

```

ssh 192.168.50.103

```

```

connect to host 192.168.50.103 port 22:Connection refused

```

sshing another machine with hardy was a success.

whats the problem?

thanks

---

### Post by dustman on 2008-11-04
you can try puTTY as a SSH client, it's great. And ssh might be set to run on another port than 22 (many use 2222) to avoid unwanted intruders.

---

### Post by superprash2003 on 2008-11-04
do you have any firewall running which maybe blocking it?? are you able to ping 192.168.50.103 successfully?

---

