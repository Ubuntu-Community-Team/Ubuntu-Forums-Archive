---
title: "need help with filezilla"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by slvfx on 2009-09-23
I downloaded filezilla onto the server to manage my files for my websites. I can't get it to connect to the server in order to start using it. I can access the server via the browser with no problem.

I reconfigured my router to my external ip address
I looked at the firewall and it is inactive
I have used ports 21 22 80 5000

this is the result no matter what i try
Status:    Connection attempt failed with "ECONNREFUSED - Connection refused by server".

Here is a screen shot of what it should be doing. Very frustrating...

[http://filezilla-project.org/images/screenshots/fz3_win_main.png](http://filezilla-project.org/images/screenshots/fz3_win_main.png)

---

### Post by halitech on 2009-09-23
so you installed an ftp client on a server to manage the files?

do you have an ftp server running on the server? do you have a gui on the server as well?

---

### Post by slvfx on 2009-09-23
> so you installed an ftp client on a server to manage the files?
yes
> do you have an ftp server running on the server? do you have a gui on the server as well?
gui was a part of the ftp client

---

### Post by halitech on 2009-09-23
the gui I'm referring to is a desktop running on X. ie Gnome, KDE, XFCE

you didn't answer if you have installed an ftp *server*

---

### Post by slvfx on 2009-09-23
Its a client....It looked like the only server one is one for windows. This is a config test i did if it helps


Connecting to probe.filezilla-project.org
Response: 220 FZ router and firewall tester ready
USER FileZilla
Response: 331 Give any password.
PASS 3.2.2.1
Response: 230 logged on.
Checking for correct external IP address
IP 72.94.246.211 hc-je-ceg-cbb
Response: 200 OK
PREP 54573
Response: 200 Using port 54573, data token 233222219
PORT 72,94,246,211,213,45
Response: 200 PORT command successful
LIST
Response: 150 opening data connection
Response: 503 Failure of data connection.
Server sent unexpected reply.
Connection closed

---

### Post by halitech on 2009-09-23
you may want to look here for a nice ftp server program and how to configure it

[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html)

---

### Post by slvfx on 2009-09-24
I installed proftpg and I also found a nice gui GADmin-proftpd 03.5 although they do have a 03.8 that is available but they don't specify ubuntu for it.

My question is that being the novice that I am I am not sure how the flow goes and where and how the ftp files get put on the server. Please don't laugh. I'm learning.

Registered through godaddy
Pointed my url through their dns to my server
forwarded my router to the server using my external ip address
(not getting the (it works page) that I get by putting in my ip address.  Problem #1 
I don't see where my url goes on gadmin where it will pick it up?  Problem #2

Any help would be very much appreciated.

Not using filezilla

---

### Post by sandyd on 2009-09-24
> **slvfx said:**
> I installed proftpg and I also found a nice gui GADmin-proftpd 03.5 although they do have a 03.8 that is available but they don't specify ubuntu for it.

My question is that being the novice that I am I am not sure how the flow goes and where and how the ftp files get put on the server. Please don't laugh. I'm learning.

Registered through godaddy
Pointed my url through their dns to my server
forwarded my router to the server using my external ip address
(not getting the (it works page) that I get by putting in my ip address.  Problem #1 
I don't see where my url goes on gadmin where it will pick it up?  Problem #2

Any help would be very much appreciated.

Not using filezilla
#1 configure port forwarding or DMZ
#2 have no idea, i use webmin

---

