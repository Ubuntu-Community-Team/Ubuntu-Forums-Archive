---
title: "Problems with SSH/RSH and Telnet"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by CFDuser on 2008-09-09
Hi

Sorry for asking a question which probably has an easy answer. I've just installed Ubuntu for the sole reason of running a CFD code (A scientific tool). This code (OPenFOAM) only runs on Linux platforms. 

When I run the installation check I get the following error:

"
Pinging_ubuntu           Successful                                   yes 
Pinging_localHost        Successful                                   yes 
Test_rsh:                Unsuccessful_connection_refused*             yes
Test_ssh:                Unsuccessful_connection_refused*             yes
FATAL ERROR: No remote shell available.
             OpenFOAM 1.5 environment requires either ssh and/or rsh.
             Contact your system administrator.
"


I checked the script and found out that the problem arises from the following command:

"Telnet ubuntu 222"
which gives the following output: 

"
Trying 127.0.1.1...
telnet: Unable to connect to remote host: Connection refused
"

So it seems that telnet is installed and running, but for some reason, I'm not able to make a connection to ubuntu, which is my own hostname. Don't ask me why OpenFOAM needs to be able to make such a connection - it just does.

Do I need to install SSH or RSH, and - if so - how do I do this. I also suspect that the connection need to be password free. 

Thanks in advance

CFDuser

---

### Post by Iowan on 2008-09-09
I take it you changed the port? I tried the same command on my machine and got the same result (also same result without specifying port - default to 23)

SSH? [https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

---

### Post by CFDuser on 2008-09-09
Hi Iowan

In fact the command works on my machine with the default port:

"Telnet ubuntu"

I'll try to install SSH.


Thanks

---

