---
title: "Can't connect to proftpd behind nat"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by nburns on 2007-01-19
I'm having trouble correctly accessing my personal ftp server.  If I access it using 'active' mode, it's fine, but when I switch to passive, it errors out.

```

230 welcome !!!
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful
150 Opening ASCII mode data connection for file list
media
welcome.msg
226 Transfer complete.
20 bytes received in 0.0046 seconds (4.27 Kbytes/s)
ftp> passive
Passive mode on.
ftp> ls
421 Service not available, remote server has closed connection
Passive mode refused. Try PORT
No control connection for command: Transport endpoint is not connected
ftp> 

```

In proftpd.conf, I've setup the 'PassivePorts' directive to just use 6000 - 65535.  I also set the MasqueradeAddress to my ftp's url.

On my router, I'm forwarding all ports from 1024 - 65535 (just to rule that out) in addition to port 21 obviously.

Any ideas??

---

### Post by nburns on 2007-01-20
Problem has been solved.

Turns out it was a combination of things.  First, despite my router telling me otherwise, the passive set of ports were actually forwarding to the incorrect box behind the router.  Once I rebooted the router, all was good on that front - thanks 'netcat'!

Also, I had to pull out the 'MasqueradeAddress' directive from proftpd.conf.  Despite everything saying I needed it when behind a NAT, it was actually hurting me.  I don't understand why, but I had to remove it.

Hope this helps others that run into similar problems.

---

### Post by dzul1983 on 2007-02-27
thanks man.. this helped me out of the PASV mode not working.. didnt realize removing the MasqueradeAddress would solve the problem.. I can access the server locally, but am having some trouble via dyndns.. not sure what the problem is, but I keep getting a "wrong password" error.. even though the password is correct..

any ideas?

EDIT: one more thing, I can't seem to upload anything.. even locally.. I get a permission denied error.. I have chmod 777 to the ftp folder..

---

### Post by dzul1983 on 2007-02-27
ah.. nevermind.. silly me.. I had a DenyAll instead of AllowAll for the STR command.. hahaha..

now to get it working with dyndns..

---

