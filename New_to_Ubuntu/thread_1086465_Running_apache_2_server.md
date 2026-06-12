---
title: "Running apache 2 server"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by g1d2r3 on 2009-03-04
Hey,
 I installed the apache2 server at the location /home/gauresh/apache
my doing ./configure prefix=/home/gauresh/apache
But now I dont know how to run the server
because when i do "./apachectl start" in the /home/gauresh/bin folder it gives me the following error.


gauresh@gauresh-desktop:~/apache/bin$ ./apachectl start
httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

the contens of my /etc/host are

127.0.0.1 localhost
127.0.1.1 gauresh-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Please help 
Thanks in advance.

---

### Post by yeats on 2009-03-04
```
./apachectl start
```

Looks like you'll want to preface that with "sudo."  

Is there a reason you're installing Apache2 from source rather than from the repositories?  Just curious.

---

### Post by theozzlives on 2009-03-04
```
sudo /etc/init.d/apache2 start
```


It can't figure out the domain name because you haven't given it one yet [http://ubuntuforums.org/showthread.php?t=987968&highlight=apache2]("http://ubuntuforums.org/showthread.php?t=987968&highlight=apache2")

---

### Post by g1d2r3 on 2009-03-04
hey thanks 
theozzlives
 and chris

The thing worked I had to run it using sudo

thanks

---

