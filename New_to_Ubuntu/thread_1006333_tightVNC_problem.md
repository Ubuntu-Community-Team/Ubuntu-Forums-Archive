---
title: "tightVNC problem"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by khaosgott on 2008-12-09
Hey guys, 
Im trying to use the built-in VNC server in order to connect to my home Ubuntu desktop from work.
To bypass the Work firewall, I'm running the XtightVNC server on port 443 ( Xtightvnc -httpport 443 )

now, here is the problem:

when im trying to open a FIREFOX window in order to connect to my home pc, im reaching the VNC login window, and after applying the password, im receiving "Network error: could not connect to server: XXX.XXX.XXX.XXX on port 5905" 

netstat -an show the following: 

```
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:5905            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:52595           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:6005            0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN

```

so it appears that port 5905 is there.

I have few questions, where the port 5905 came from in the first place? and why this sudden port redirection from 443 to 5905?

also, worth to mention that my whole LAN is behind NAT FW, but there is an appropriate access rule to allow this type of connection.

thanks for any ideas,

K.

---

### Post by superprash2003 on 2008-12-09
hope this gives you an idea [http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html](http://prash-babu.blogspot.com/2008/06/how-to-access-your-ubuntu-machine-from.html)

---

### Post by khaosgott on 2008-12-09
well, thanks for the link.
i followed the orders, and everything appears to be set as described, but eventually I get the Java applet error, about not finding the needed class.
the class files are there with 544 permissions.

help please? :-)

---

### Post by superprash2003 on 2008-12-10
did you try this from another pc.. is java installed in that pc.. the java runtime..

---

### Post by khaosgott on 2008-12-10
yep.
all my attempts take place on few other PC's.

actually, there is a bit of a progress.
now, i get to run the java applet, login with the password, and then I get the encouraging message that im "connected to server"... and thats it.

ideas?

---

### Post by khaosgott on 2008-12-10
yep.
all my attempts take place on few other PC's.

actually, there is a bit of a progress.
now, i get to run the java applet, login with the password, and then I get the encouraging message that im "connected to server"... and thats it.

ideas?

---

### Post by superprash2003 on 2008-12-11
ensure that port 5900 is open.. use this online port scanner [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by Kareeser on 2008-12-11
In my experience, the porte required for the VNC interface and the web interface are different.

5900 for the client, 5800 for a web browser. I could be wrong.

---

### Post by khaosgott on 2008-12-11
i dont see that neither of this ports are open actually...

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:5801            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:59610           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp        1      0 192.168.1.3:57919       72.14.221.19:80         CLOSE_WAIT 
tcp        1      0 192.168.1.3:57920       72.14.221.19:80         CLOSE_WAIT 
tcp        0      0 192.168.1.3:48127       64.4.36.56:1863         ESTABLISHED
tcp        0      0 192.168.1.3:57921       72.14.221.19:80         ESTABLISHED
tcp        0      0 192.168.1.3:34496       207.46.111.83:1863      ESTABLISHED
tcp6       0      0 :::5900                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN

---

### Post by superprash2003 on 2008-12-12
thats where your problem lies.. have you port forwarded 5900 properly?

---

### Post by khaosgott on 2008-12-12
this is the ubuntu output, not the router output.
the port is forwarded correctly in the router, and i think its more of a OS misconfiguration, since i get the same results locally.

---

### Post by JKBurton on 2008-12-12
I had the "connects, then nothing" problem. It looks to me like a protocol parsing bug where the two vncs compare version numbers to see which protocol to use.

In my case, one side was v3.16 and the other v3.8, and the software was interpreting 3.16 as 3.1.6, a lower version number than 3.8, and it got all confused.

I just pulled a different current vncviewer executable from the web, and it works fine. Best I can recall, I got mine from [http://www.karlrunge.com/x11vnc/ssvnc.html#download](http://www.karlrunge.com/x11vnc/ssvnc.html#download)

Hope this helps!

---

