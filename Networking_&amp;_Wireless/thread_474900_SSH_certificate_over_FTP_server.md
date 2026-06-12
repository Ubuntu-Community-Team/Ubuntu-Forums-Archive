---
title: "SSH certificate over FTP server"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by Gagle on 2007-06-15
Hi,

Mainly with the help of this thread : [http://ubuntuforums.org/showthread.php?t=79588&highlight=ssh+certificate](http://ubuntuforums.org/showthread.php?t=79588&highlight=ssh+certificate)
by Frodon , I setup successfully a FTP server inside my NAT (also accessible outside my LAN).  I then decided to encrypt the transmission using SSH certificates.   There again everything went as planned until the next connection tryout(using gftp).  

The user and password authentification went well, but then a connection error stating, in layman's term, that the certificate had been authentified by the same person  that created the certificate.

Technically :  Error 19 :  Self signed certificate in certificate chain

Please note that the  server.key and the ca.key creation both require up to a certain point personal identification and I assured myself not to give the same answers to both prompts.

Now, I'm pretty sure this issue was treated/solved/fixed somewhere in these forums by my searches have been in vain.

regards,

Gagle

---

### Post by Skivache on 2008-01-22
I would be very interested in a solution for this problem (if you found one yourself), or if someone knew a possible solution.  I am planning on setting up an ftp server of my own soon and would like to make the connection as secure as possible.

---

### Post by kirsche on 2008-01-22
did you try importing this cert as a trusted one?

---

