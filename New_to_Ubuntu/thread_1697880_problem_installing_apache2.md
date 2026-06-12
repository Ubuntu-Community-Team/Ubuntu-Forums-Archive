---
title: "problem installing apache2"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-03-01
hi everyone
  i am trying to install apache2 in my ubuntu 10.10
but i am getting following error
Setting up apache2-mpm-worker (2.2.16-1ubuntu3.1) ...
 * Starting web server apache2                                                  (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]
invoke-rc.d: initscript apache2, action "start" failed.
Setting up apache2 (2.2.16-1ubuntu3.1) ...


anybody knows whats the solution
thanx in advance

---

### Post by vivek.pandey on 2011-03-01
i also searched for /etc/apache2 but cannot find neither can i find /var/log/apache2
any help?

---

### Post by vivek.pandey on 2011-03-02
any help?

---

### Post by indytim on 2011-03-02
So why don't you start by telling us how you "installed" apache?

-IndyTim / DataMan

---

### Post by vivek.pandey on 2011-03-02
installation was simply from terminal
sudo apt-get install apache2
even
sudo apt-get install lamp-server^
gives the same error and fails to start

---

### Post by slooksterpsv on 2011-03-02
Can you copy and paste the output of the following (if you run it from terminal):

```

cat /etc/hosts

```

I'm not sure what's going on, but it almost looks like it doesn't have an IP Address to bind to.

Hmmm... maybe not, do you already have apache? Run the following in terminal and paste the results here:
```

sudo dpkg -l | grep apache

```

Hmm.... I'll see if I can find any additional information, sorry for just asking for more instead of having a direct solution.


EDIT: Maybe information from this thread will help: [http://ubuntuforums.org/archive/index.php/t-1636667.html](http://ubuntuforums.org/archive/index.php/t-1636667.html)

---

### Post by vivek.pandey on 2011-03-02
> **slooksterpsv said:**
> Can you copy and paste the output of the following (if you run it from terminal):

```

cat /etc/hosts

```

I'm not sure what's going on, but it almost looks like it doesn't have an IP Address to bind to.

Hmmm... maybe not, do you already have apache? Run the following in terminal and paste the results here:
```

sudo dpkg -l | grep apache

```

Hmm.... I'll see if I can find any additional information, sorry for just asking for more instead of having a direct solution.
output for first command
vivek@NEO:~$ cat /etc/hosts
182.156.97.59	NEO	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	NEO	localhost6.localdomain6	localhost6
127.0.1.1	NEO

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

for second command

vivek@NEO:~$ sudo dpkg -l | grep apache
[sudo] password for vivek: 
ii  apache2                              2.2.16-1ubuntu3.1                                 Apache HTTP Server metapackage
ii  apache2-mpm-prefork                  2.2.16-1ubuntu3.1                                 Apache HTTP Server - traditional non-threaded model
ii  apache2-utils                        2.2.16-1ubuntu3.1                                 utility programs for webservers
ii  apache2.2-bin                        2.2.16-1ubuntu3.1                                 Apache HTTP Server common binary files
ii  apache2.2-common                     2.2.16-1ubuntu3.1                                 Apache HTTP Server common files
ii  libapache2-mod-auth-mysql            4.3.9-13ubuntu1                                   Apache 2 module for MySQL authentication
ii  libapache2-mod-php5                  5.3.3-1ubuntu9.3                                  server-side, HTML-embedded scripting language (Apache 2 module)

---

### Post by augustuen on 2011-03-02
This is quite easily that Apache2 is not able to bind to the socket. A possible explanation is that you have some kind of other server that uses port 80. I don't know if this works, but could you post the output of (sudo) netstat -anp?

---

### Post by vivek.pandey on 2011-03-02
> **augustuen said:**
> This is quite easily that Apache2 is not able to bind to the socket. A possible explanation is that you have some kind of other server that uses port 80. I don't know if this works, but could you post the output of (sudo) netstat -anp?

hey thanx it was aol server..i uninstalled it restarted my lapi but there is still a problem when i type localhost now i get an error which says i dont have permissions to access on this server..the problem is i cant find apache log file in /var/log

---

