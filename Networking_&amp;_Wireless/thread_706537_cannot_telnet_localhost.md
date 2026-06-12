---
title: "cannot telnet localhost"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by flyinggreg on 2008-02-24
I am a newb trying to setup an email server on Server 6.06.  I understand that to test you need to be able to telnet 127.0.0.1.  I also am running WebMin to access the server config.  I cannot telnet the localhost I keep getting
```
> telnet 127.0.0.1
telnet: Unable to connect to remote host: Connection refused
Trying 127.0.0.1...
```
loopback is setup in /etc/network/interfaces
Here is netstat
```
> netstat -napt
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 127.0.0.1:60000         0.0.0.0:*               LISTEN     13160/postgrey.pid  
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:10025         0.0.0.0:*               LISTEN     2431/master         
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     24918/mysqld        
tcp        0      0 0.0.0.0:874             0.0.0.0:*               LISTEN     4084/rpc.statd      
tcp        0      0 0.0.0.0:587             0.0.0.0:*               LISTEN     2431/master         
tcp        0      0 0.0.0.0:843             0.0.0.0:*               LISTEN     11264/rpc.mountd    
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     4004/smbd           
tcp        0      0 0.0.0.0:878             0.0.0.0:*               LISTEN     4090/rpc.rquotad    
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     3327/portmap        
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     4187/perl           
tcp        0      0 0.0.0.0:465             0.0.0.0:*               LISTEN     2431/master         
tcp        0      0 192.168.1.65:53         0.0.0.0:*               LISTEN     3672/named          
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     3672/named          
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN     32250/cupsd         
tcp        0      0 0.0.0.0:5432            0.0.0.0:*               LISTEN     3974/postmaster     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     2431/master         
tcp        0      0 0.0.0.0:37113           0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN     3672/named          
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     4004/smbd           
tcp        0   1288 192.168.1.65:10000      192.168.1.66:1150       ESTABLISHED27634/index.cgi     
tcp6       0      0 :::993                  :::*                    LISTEN     13247/couriertcpd   
tcp6       0      0 :::995                  :::*                    LISTEN     1702/couriertcpd    
tcp6       0      0 :::587                  :::*                    LISTEN     2431/master         
tcp6       0      0 :::110                  :::*                    LISTEN     1655/couriertcpd    
tcp6       0      0 :::143                  :::*                    LISTEN     1420/couriertcpd    
tcp6       0      0 :::80                   :::*                    LISTEN     18233/apache2       
tcp6       0      0 :::465                  :::*                    LISTEN     2431/master         
tcp6       0      0 :::22                   :::*                    LISTEN     4022/sshd           
tcp6       0      0 :::631                  :::*                    LISTEN     32250/cupsd         
tcp6       0      0 :::5432                 :::*                    LISTEN     3974/postmaster     
tcp6       0      0 :::25                   :::*                    LISTEN     2431/master         
tcp6       0      0 ::1:953                 :::*                    LISTEN     3672/named          
tcp6       0      0 :::443                  :::*                    LISTEN     18233/apache2       
```
and ifconfig
```
> ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:90:27:36:D5:40  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:27ff:fe36:d540/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3613199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1128185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:783772343 (747.4 MiB)  TX bytes:164814075 (157.1 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:790107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:790107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:175114913 (167.0 MiB)  TX bytes:175114913 (167.0 MiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
I really need some help trying to configure an email host - sogetting this working would be GREAT help!

Thanks!

---

### Post by Eiríkr on 2008-02-24
Hey there flyinggreg --

I think telnet defaults to port 22 if you don't specify a different port; I also think that port 22 is usually bound to sshd if it's running, which will deny any telnet connection attempts.  Since you've got Webmin running, and this has port 10000 and does accept telnet connection attempts, one test of telnet connectivity is to type [font=courier]telnet localhost 10000[/font].  This should look like this:
```

username@host:~$ telnet localhost 10000
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.


```
You'll have to hit Ctrl-C to get out of this, as telnet will happily sit there doing nothing.  Anyway, once you've confirmed that you can telnet into your localhost at all, try again with whatever port you've set up your mail server to use to make sure your mail server itself is accepting connections.  For instance, Gmail's SMTP server uses port 465, so I can check my ability to connect to Gmail's server like this:

```
username@host:~$ telnet smtp.gmail.com 465
Trying 209.85.199.111...
Connected to gmail-smtp.l.google.com.
Escape character is '^]'.


```

If your mail server is accepting connections, you're good to go -- move on to the next step of configuring your server.  :)

HTH,

Eiríkr

---

### Post by flyinggreg on 2008-02-24
> **Eiríkr said:**
> Hey there flyinggreg --

I think telnet defaults to port 22 if you don't specify a different port; I also think that port 22 is usually bound to sshd if it's running, which will deny any telnet connection attempts.  Since you've got Webmin running, and this has port 10000 and does accept telnet connection attempts, one test of telnet connectivity is to type [font=courier]telnet localhost 10000[/font].  This should look like this:
```

username@host:~$ telnet localhost 10000
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.


```
You'll have to hit Ctrl-C to get out of this, as telnet will happily sit there doing nothing.  Anyway, once you've confirmed that you can telnet into your localhost at all, try again with whatever port you've set up your mail server to use to make sure your mail server itself is accepting connections.  For instance, Gmail's SMTP server uses port 465, so I can check my ability to connect to Gmail's server like this:

```
username@host:~$ telnet smtp.gmail.com 465
Trying 209.85.199.111...
Connected to gmail-smtp.l.google.com.
Escape character is '^]'.


```

If your mail server is accepting connections, you're good to go -- move on to the next step of configuring your server.  :)

HTH,

Eiríkr

YES!!  That worked!  I didn't think of trying the webmin port!  This is what I got
```
> telnet localhost 10000
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
```
I used webmin's command shell so I am guessing that's why the connection closed.

Thanks for the help on this thread and my other thread from last night.

---

### Post by Eiríkr on 2008-02-24
No trouble, glad to hear it's working for you.  :)  

Incidentally, you say you used Webmin's command shell -- do you mean clicking on Webmin's "Others" menu, then "SSH/Telnet Login"?  I've *never* been able to get that to work.  It hasn't been a big issue for me as I just use CLI ssh, or Putty from Windows, but if the Webmin applet is working for you, I'm now curious what I've done wrong on my end...

Cheers,

Eiríkr

---

### Post by flyinggreg on 2008-02-26
> **Eiríkr said:**
> No trouble, glad to hear it's working for you.  :)  

Incidentally, you say you used Webmin's command shell -- do you mean clicking on Webmin's "Others" menu, then "SSH/Telnet Login"?  I've *never* been able to get that to work.  It hasn't been a big issue for me as I just use CLI ssh, or Putty from Windows, but if the Webmin applet is working for you, I'm now curious what I've done wrong on my end...

Cheers,

Eiríkr

No, I used the Others - Command Shell.  I too can't seem to get the SSH/telnet to work either.

---

### Post by Eiríkr on 2008-02-26
Cheers then, thanks for letting me know.  :)

And if this issue is solved for you, remember to mark it [SOLVED] under in the "Thread Tools" dropdown at the top of the page.  

Cheers,

Eiríkr

---

