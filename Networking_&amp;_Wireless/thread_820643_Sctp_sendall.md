---
title: "Sctp_sendall"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by ekrtt1 on 2008-06-06
Hi, I have been experimenting with SCTP protocol. I feld to compile one example from

[http://www.linuxjournal.com/article/9784](http://www.linuxjournal.com/article/9784)

but there is problem with SCTP_SENDALL through compiling in my Ubuntu with kelner 2.6.24-17-generic.


[COLOR="Red"]#include <stdio.h>
#include <stdlib.h>
#include <strings.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>

#include <netinet/sctp.h>
.
.
.
.

/* send it back out to all associations */

bzero(&sinfo, sizeof(sinfo));
sinfo.sinfo_flags |= SCTP_SENDALL;

sctp_send(sockfd, buf, nread,// (struct sockaddr *) &client_addr, 1,
&sinfo, 0);[/COLOR]

Notice by autor of example:
The SCTP_SENDALL flag has been introduced only recently into SCTP and is not in current kernels (up to 2.6.21.1), but it should make it into the 2.6.22 kernels.

My error:
‘SCTP_SENDALL’ undeclared (first use in this function)

Is possible to use this flag anyway in Ubuntu??

Thanks Tom

---

### Post by ekrtt1 on 2008-06-06
+

---

