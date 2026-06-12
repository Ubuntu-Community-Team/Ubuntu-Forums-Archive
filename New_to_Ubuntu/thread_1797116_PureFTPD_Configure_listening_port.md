---
title: "PureFTPD Configure listening port"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by oscarper on 2011-07-04
Hi Everyone.

I am using Pure-FTPD over Ubuntu Natty Desktop.
I have been able to setup the FTP server successfully, however I am not able to change the port from default 21 to 37801 on my server.

Have been looking for several days to different ways to do this, but none of the suggested solutions worked for me.

Can anyone help me get this through?

BTW I am new to Ubuntu/Linux

Thanks and regards
Oscar

---

### Post by oscarper on 2011-07-05
Hi All..

Any ideas? I would really appreciate someone with experience to help me.

Thanks

---

### Post by gmargo on 2011-07-05
Create a file named **/etc/pure-ftpd/conf/Bind** with the following content and then restart the ftp server:
```

,37801

```All the files under **/etc/pure-ftpd/conf/** are translated by the **/usr/sbin/pure-ftpd-wrapper** script into command line arguments for the **/usr/sbin/pure-ftpd** program.  

The "Bind" file content becomes the "-S" option for pure-ftpd.

---

### Post by oscarper on 2011-07-05
Thank you gmargo. I have done that and I can connect only directly from my localhost. if I do 

ftp localhost 37801 I get to connect.

Now the problem is I cannot connect from outside localhost, on DOS, on Browsers, etc...

Any ideas? Is there any other configuration missing?

I was able to connect with default 21 port.

---

### Post by gmargo on 2011-07-05
It should be listening on all interfaces.  Try **netstat** to check the listener.  Here it is on my system:
```

$ sudo netstat -tnulp | grep 37801
tcp        0      0 0.0.0.0:37801           0.0.0.0:*               LISTEN      1235/pure-ftpd (SER
tcp6       0      0 :::37801                :::*                    LISTEN      1235/pure-ftpd (SER

```

Is your firewall blocking connections from other machines?

---

### Post by oscarper on 2011-07-05
It seems to be listening on my system as well 

> # sudo netstat -tnulp | grep 37801
tcp        0      0 0.0.0.0:37801           0.0.0.0:*               LISTEN      24116/pure-ftpd (SE
tcp6       0      0 :::37801                :::*                    LISTEN      24116/pure-ftpd (SE


Not sure I cannot access from outside. 
I have FW the ports on Router already

Not sure how to check for firewall

---

