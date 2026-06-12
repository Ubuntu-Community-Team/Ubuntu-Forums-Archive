---
title: "Firestarter IP detections?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2009-12-08
Something new for a change. Today my computer screen blipped and went black for only a second, then it became sluggish. I felt a bit paranoid as I was in the middle of an online transaction, so I rebooted, then started firestarter. I seldom use it coz I always forget to turn it on, wish the damned thing was automatic starting.

Moving on, I'm getting detections every 20 or so seconds, from dozens of different IP addresses and ports, this has me somewhat worried/concerned.

How safe is Linux against hacking, really?

---

### Post by ukripper on 2009-12-08
can you post output of this command:

```
netstat -nat
```

This will show all established foreign connections on specific ports or sockets

BTW, this is excellent guide to iptables to block ports that are not needed. Firstarter always gave me problem though. 
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

---

### Post by Thelasko on 2009-12-08
Firestarter is just a front end for IP tables.  IP tables is always running even when Firestarter is not.

By the way, Firestarter is quite old and no longer maintained.  I recommend GUFW instead.

---

### Post by T4K3Z0U on 2009-12-08
This is what I got.

```
~$ netstat -nat
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:51413           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:9091            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:57827           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:6000            0.0.0.0:*               LISTEN     
tcp        0      0 192.168.11.2:34600      219.112.73.136:32998    ESTABLISHED
tcp        0   1024 192.168.11.2:52803      78.94.162.254:9390      ESTABLISHED
tcp        0      0 192.168.11.2:60689      74.125.153.100:80       ESTABLISHED
tcp        0      0 192.168.11.2:42404      189.79.106.144:51413    ESTABLISHED
tcp        0      0 192.168.11.2:55018      86.149.232.1:50559      ESTABLISHED
tcp        0  11852 192.168.11.2:50014      124.168.0.124:20322     ESTABLISHED
tcp        0  12336 192.168.11.2:58809      99.226.98.126:33112     ESTABLISHED
tcp        0      0 192.168.11.2:59883      60.254.149.16:80        ESTABLISHED
tcp        0    257 192.168.11.2:50768      99.226.98.126:33112     FIN_WAIT1  
tcp        0      0 192.168.11.2:37381      67.84.29.81:21694       ESTABLISHED
tcp        0      0 192.168.11.2:54949      99.140.242.42:17766     ESTABLISHED
tcp        0      0 192.168.11.2:56486      173.171.21.33:10656     ESTABLISHED
tcp        0      0 192.168.11.2:36422      208.88.18.5:443         ESTABLISHED
tcp        0      0 192.168.11.2:43515      219.90.163.252:47132    ESTABLISHED
tcp        0      0 192.168.11.2:59884      60.254.149.16:80        ESTABLISHED
tcp6       0      0 :::51413                :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::6000                 :::*                    LISTEN   
```

What is GUFW?

---

### Post by ukripper on 2009-12-08
Can you close firefox or any other webbrowser and then run the same command and post here.

---

### Post by Thelasko on 2009-12-08
> **T4K3Z0U said:**
> What is GUFW?

It's like firestarter, but better [maintained.]("http://gufw.tuxfamily.org/screenshots.html")

---

### Post by T4K3Z0U on 2009-12-08
> **ukripper said:**
> Can you close firefox or any other webbrowser and then run the same command and post here.

This is what I got after closing firefox, TB, and transmission.

```
~$ netstat -nat
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:57827           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:6000            0.0.0.0:*               LISTEN     
tcp        0      0 192.168.11.2:46678      188.126.64.3:80         TIME_WAIT  
tcp        0      0 192.168.11.2:57030      72.14.203.113:80        TIME_WAIT  
tcp        0      0 192.168.11.2:34347      83.86.232.54:43183      TIME_WAIT  
tcp        0      0 192.168.11.2:34600      219.112.73.136:32998    ESTABLISHED
tcp        0      0 192.168.11.2:52803      78.94.162.254:9390      TIME_WAIT  
tcp        0      0 192.168.11.2:53335      86.149.232.1:50559      TIME_WAIT  
tcp        0      0 192.168.11.2:55575      69.16.253.67:80         TIME_WAIT  
tcp        0      0 192.168.11.2:60127      93.97.65.147:25743      FIN_WAIT2  
tcp        0      0 192.168.11.2:44369      99.140.242.42:17766     TIME_WAIT  
tcp        0      0 192.168.11.2:53775      99.226.98.126:33112     TIME_WAIT  
tcp        0    148 192.168.11.2:51963      189.79.106.144:51413    FIN_WAIT1  
tcp        0      0 192.168.11.2:50014      124.168.0.124:20322     TIME_WAIT  
tcp        0      0 192.168.11.2:44503      38.102.35.243:80        FIN_WAIT2  
tcp        0      0 192.168.11.2:55628      72.167.82.11:995        TIME_WAIT  
tcp        0      0 192.168.11.2:37381      67.84.29.81:21694       TIME_WAIT  
tcp        0      0 192.168.11.2:38869      203.97.33.210:110       TIME_WAIT  
tcp        0      0 192.168.11.2:36422      208.88.18.5:443         TIME_WAIT  
tcp        0      0 192.168.11.2:55584      69.16.253.67:80         TIME_WAIT  
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::6000                 :::*                    LISTEN 
```

I presume the one that was still established was Skype.

---

### Post by T4K3Z0U on 2009-12-11
> **Thelasko said:**
> It's like firestarter, but better [maintained.]("http://gufw.tuxfamily.org/screenshots.html")

I've installed GUFW but don't know how to activate it. It doesn't show up under the internet column, via applications.

---

### Post by BigB'sLinux on 2009-12-12
> **T4K3Z0U said:**
> I've installed GUFW but don't know how to activate it. It doesn't show up under the internet column, via applications.

  If I were you I would stick to Firestarter for now if your comfortable with it. Ninety nine percent of your netstat scan connections with TIME WAIT are basically probably left over dead connections left hanging when you closed your browser or dropped your irc client ,etc .     >  tcp  0      0 192.168.11.2:34600      219.112.73.136:32998    ESTABLISHED    ^^This would be the only suspect connection I can see, but tt could be explained by a torrent client, ftp data, any other connection you may have to a server. I would manually close the port connection then re-netstat and see if your still holding a high port connection to another ip before you get too worried. It could be explained by many things    

 Edit: running rKhunter could also help with checking if you have a back door installed. If you dont have it you can install it with apt-get. It will alert you to modified files and permissions and actual rk's.

---

### Post by 3rdalbum on 2009-12-12
If Firestarter is set to block all incoming connections, then you have nothing to worry about. Firestarter has blocked them.

Incidentally, this is one reason why I tell people not to use Firestarter - it scares people when they see the log of blocked connections and they think the Russian Mafia is hacking them. Gufw can be found under 'System - Administration - Firewall Configuration' and the underlying firewall is always running.

Not that you need a firewall if nothing is listening to incoming connections.

---

### Post by Thelasko on 2009-12-12
GUFW should be under system>administration>firewall.

Incidentally, I find that rkhunter only adds to paranoia.  It comes up with lots of meaningless warning messages, that turn up to be nothing.

If you use rkhunter, make sure you read the log files.   The output from the program alone will make you nervous.

---

### Post by T4K3Z0U on 2009-12-12
> **3rdalbum said:**
> 
Incidentally, this is one reason why I tell people not to use Firestarter - it scares people when they see the log of blocked connections and they think the Russian Mafia is hacking them. 

LOL Russian Mafia.

My main problem was that my screen went black, kinda the same it does when it reboots, only it didn't reboot. Then it was sluggish. I've heard when things like that happen, you might be being hacked. So I started firewall, then got all those messages, which made me more paranoid.

Incidentally, it happened twice in the last 10mins (The black screen that is) and my Num Lk light keeps turning on and off intermittently. Seems like really odd behaviour, especially with a newish machine.

Doesn't seem to be any instructions on how to use Gufw.

---

