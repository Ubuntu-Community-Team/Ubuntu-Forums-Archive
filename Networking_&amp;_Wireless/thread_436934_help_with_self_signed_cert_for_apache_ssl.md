---
title: "help with self signed cert for apache ssl"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by namelessone on 2007-05-08
So I followed the [Ubuntu server guide's]("http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html") instructions to setting up apache with ssl, but it doesn't seem to be working.

after typing the command
```
openssl req -new -key server.key -out server.csr
```
it asked me a bunch of questions. Since I am doing this for educational purposes, I don't have a fqdn so for the CommonName i typed 127.0.1.1 because when i restarted apache this is what it said it was going to use that for the ServerName.

I finished following all the instructions, and then restarted apache. Then I went over to my other machine and typed the address into firefox, but it gave me the following error
> 
172.16.0.2 has sent an incorrect or unexpected message. error code -12263

can anyone help me see what I did wrong?

here's the relevant snippet of my /var/log/apache2/error.log in case it helps

```
...-- resuming normal operations
[Tue May 08 9:34:59 2007] [error] [client 172.16.0.3] invalid method in request \x16\x03\x01
```

---

### Post by boosarker on 2007-05-08
If you done the same as me you'll have missed the top line to add to /etc/apache2/sites-available/default :

"SSLEngine on"

---

### Post by namelessone on 2007-05-08
no, i typed all that stuff. I know ssl is on because I initially had something else for the CommonName and there was an error message in the log file telling me that. When I changed it to 127.0.1.1, the error went away.

---

### Post by namelessone on 2007-05-10
After much chagrin, I finally figured it out! All I needed was this:

NameVirtualHost *:443

---

