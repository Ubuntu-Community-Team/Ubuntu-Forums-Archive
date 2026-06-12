---
title: "Unable to access apache default webpage after install"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by albertwt on 2010-11-12
HiAll,

any idea why i can't access the Tomcat6 default website after i do the install ?

```

ERROR
The requested URL could not be retrieved
While trying to retrieve the URL: http://10.2.3.189/

The following error was encountered:
Connection to 10.2.3.189 Failed
The system returned:
    (111) Connection refused

```

```

Setting up authbind (1.2.0build3) ...

**root@SSV:~# /etc/init.d/tomcat6 restart**
 * Stopping Tomcat servlet engine tomcat6                           [ OK ]
 * Starting Tomcat servlet engine tomcat6       Using CATALINA_BASE:   /var/lib/tomcat6
Using CATALINA_HOME:   /usr/share/tomcat6
Using CATALINA_TMPDIR: /tmp/tomcat6-tmp
Using JRE_HOME:        /usr/lib/jvm/java-6-sun
Using CLASSPATH:       /usr/share/tomcat6/bin/bootstrap.jar
                                                                    [ OK ]
**root@SSV:~# ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:50:56:89:1b:30
          inet addr:10.2.3.189  Bcast:10.2.3.255  Mask:255.255.254.0
          inet6 addr: fe80::250:56ff:fe89:1b30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9034478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:262700983 (262.7 MB)  TX bytes:11947055 (11.9 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1344 (1.3 KB)  TX bytes:1344 (1.3 KB)

**root@SSV:~# netstat -tulpn**
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      966/sshd
tcp6       0      0 :::8080                 :::*                    LISTEN      8231/java
tcp6       0      0 :::22                   :::*                    LISTEN      966/sshd
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN      8231/java
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           7210/avahi-daemon:
udp        0      0 0.0.0.0:59756           0.0.0.0:*                           7210/avahi-daemon:
udp        0      0 0.0.0.0:68              0.0.0.0:*                           949/dhclient3

root@SSV:~#

```

any kind of help would be greatly appreciated.

Thanks,

Albert

---

### Post by bioterror on 2010-11-12
Can you connect to [http://127.0.0.1/](http://127.0.0.1/) from that computer?
What IP Addresses is the Apache listening?

---

### Post by theozzlives on 2010-11-12
Do you have port 80 forwarded in your router to the web server?

---

### Post by albertwt on 2010-11-12
> **bioterror said:**
> Can you connect to [http://127.0.0.1/](http://127.0.0.1/) from that computer?
What IP Addresses is the Apache listening?

Thanks man for the reply
I still couldn't find out why i can't connect on port 80 after the service restart ?

I just found out that port 8080 is now working and i can see:
It works ! --> so glad finally.

---

### Post by theozzlives on 2010-11-12
> **albertwt said:**
> Thanks man for the reply
I still couldn't find out why i can't connect on port 80 after the service restart ?

I just found out that port 8080 is now working and i can see:
It works ! --> so glad finally.

Cool deal dude! Now mark this Thread as solved.

---

### Post by albertwt on 2010-11-12
> **theozzlives said:**
> Cool deal dude! Now mark this Thread as solved.

yes, glad to hear that, so in order to access it on port 80 what shall I do ?

---

### Post by theozzlives on 2010-11-12
> **albertwt said:**
> yes, glad to hear that, so in order to access it on port 80 what shall I do ?

Your router setup should have port forwarding. In my old setup I had port 80, HTTP > 192.168.1.6 which is where my server was. So all HTTP traffic went to that computer only.

---

### Post by albertwt on 2010-11-12
> **theozzlives said:**
> Your router setup should have port forwarding. In my old setup I had port 80, HTTP > 192.168.1.6 which is where my server was.

Router ? hm... i thought that there is something that i can edit inside the text file ?

---

### Post by theozzlives on 2010-11-12
> **albertwt said:**
> Router ? hm... i thought that there is something that i can edit inside the text file ?

Let me guess, you only have one machine. Do you have a static IP?

---

### Post by albertwt on 2010-11-12
> **theozzlives said:**
> Let me guess, you only have one machine. Do you have a static IP?

yes exactly, this machine got static IP already.

---

### Post by theozzlives on 2010-11-12
> **albertwt said:**
> yes exactly, this machine got static IP already.

Do you have it entered in your network manager? I got the network timed out. Do you have your gateway and subnet mask entered correctly?

---

