---
title: "Strange inbound/outbound IPs on netstat"
date: 2017-02-03
forum: Networking &amp; Wireless
---

### Post by wantondude on 2017-02-03
Elo ... 
I'm just wondering. 

I've been monitoring traffic on my server and something struck as odd. 
Looking at the traffic summaries on my router I had figures where the total traffic upstream was quite larger than that downstream. 
Furthermore I checked netstat on my server and started to see unknown IP addresses connecting through port 6667.

I checked the IP address on google and of course they show up as shady. 
I don't want to be paranoid about being stalked by nasty chinese/russian hackers intent on robbing my little/old/slow server resources for nefarious Clinton emails hacking.
In any event I firewalled them. 

Still I am interested where do these come from ?

Why does ubuntu try to connect to external Ip addresses unbeknownst to me ?

Any ideas ?

Regarditos !

---

### Post by ajgreeny on 2017-02-03
Have you checked those IP addresses in a search engine? 

It might give you some clue about them from which you can work out what and where they are.

---

### Post by SeijiSensei on 2017-02-03
What is/was listening on port 6667?  The entry in /etc/services says its IRC.  Are you running an IRC server like ircd?  If not, someone else probably is.  If you did not set up IRC yourself, you should consider the entire server compromised.

---

### Post by Muhammad_Awais on 2017-02-04
here are some other irc related ports, to troubleshoot ..

$ cat /etc/services | grep irc
irc		194/tcp				# Internet Relay Chat
irc		194/udp
ircs		994/tcp				# IRC over SSL
ircs		994/udp
ircd		6667/tcp			# Internet Relay Chat
dircproxy	57000/tcp			# Detachable IRC Proxy

---

### Post by The Cog on 2017-02-04
The command ```
sudo netstat -tp
``` will show all open tcp connections and the name of the process that has the connection (look for ircd as the port name). That should tell you a lot. Also, ```
sudo netstat -ltp
``` will show all ports listening for incoming connections - just in case your box is waiting to be called.

---

### Post by wantondude on 2017-02-05
Cheerios Dudes ... 

I'll check the etc/services file. 
Something related to iRC did show up while I was investigating the thing. 

@SeijiSensei ... compromised as in totally lost control forever and nothing can be done ?  :)

---

### Post by wantondude on 2017-02-05
ok .. 

This is the output from the etc/services file 
```
root@AlbaServer:~# cat /etc/services | grep irc
**irc**        194/tcp                # Internet Relay Chat
**irc**        194/udp
**irc**s        994/tcp                # IRC over SSL
**irc**s        994/udp
**irc**d        6667/tcp            # Internet Relay Chat
d**irc**proxy    57000/tcp            # Detachable IRC Proxy
[COLOR=#FFFFFF][FONT=Menlo]root@AlbaServer:~# [/FONT][/COLOR]
```

Doesn't seem to be out of the ordinary ....

I'll try check who's listening and I'l come back to You guys ?


Regarditos

---

### Post by SeijiSensei on 2017-02-05
If someone could install an IRC server on your machine, then it's possible they have root privileges.

Now it's possible to run a server on port 6667 (or any port > 1023) as a non-root user.  So maybe they only got access to a non-root account.  But if someone has gotten sufficient access to install a server daemon of any kind on your machine, then it's not under your full control.  I would consider that compromised, yes.  Until you figure out what's going on, I would take it offline myself.

Does the command "[FONT=Courier New]ps aux | grep irc[/FONT]" bring up anything?  Is there an instance of ircd running?  If so, what account owns it?

---

### Post by wantondude on 2017-02-07
Elo, 

"ps aux | grep irc" brings this up :

root     23747  0.0  0.0  15964   924 pts/11   S+   11:00   0:00 grep --color=auto **irc**

Seems like root is the owner. 
Also when I listened using netstat -plnt I get an httpd process listening on port 6667..

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:6667            0.0.0.0:*               LISTEN      3594/httpd         
tcp        0      0 127.0.0.1:139           0.0.0.0:*               LISTEN      668/smbd        
tcp        0      0 192.168.0.100:139       0.0.0.0:*               LISTEN      668/smbd        
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      2472/perl       
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1135/dnsmasq    
tcp        0      0 192.168.0.100:53        0.0.0.0:*               LISTEN      1100/named      
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1100/named      
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      731/vsftpd: LISTENE
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1019/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      18915/cupsd     
tcp        0      0 0.0.0.0:5432            0.0.0.0:*               LISTEN      1973/postgres   
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1100/named      
tcp        0      0 127.0.0.1:445           0.0.0.0:*               LISTEN      668/smbd        
tcp        0      0 192.168.0.100:445       0.0.0.0:*               LISTEN      668/smbd        
tcp6       0      0 :::53                   :::*                    LISTEN      1100/named      
tcp6       0      0 :::22                   :::*                    LISTEN      1019/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      18915/cupsd     
tcp6       0      0 :::5432                 :::*                    LISTEN      1973/postgres   
tcp6       0      0 ::1:953                 :::*                    LISTEN      1100/named

Funny thing is I can't find the httpd.conf file, most probably due to my rookie-ness.... 


Cheers :)

---

### Post by SeijiSensei on 2017-02-07
No, the result you posted is the command you ran.  There apparently is no ircd running, but someone has hung a web server daemon on your port 6667.

It should have process number 3594; use ps or top to find it.

Have you not blocked access to this port yet?  It sounds like you've left the machine running in its current state.  At least stop people from exploiting you with this iptables command:
```
sudo iptables -I INPUT -p tcp --dport 6667 -j REJECT
```
until you have figured out what is going on.

---

### Post by The Cog on 2017-02-07
> "ps aux | grep irc" brings this up :
root 23747 0.0 0.0 15964 924 pts/11 S+ 11:00 0:00 grep --color=auto irc

That's the grep part of your own query running - ignore it. 

See the line in netstat listening on irc port 6667? process id 3594.
You can find out where the executable file is with the command:
```
realpath /proc/3594/exe
```
I suspect it's not really a webserver.

You could try to connect to it and see what it says.
Try the command:
```
nc localhost 6667
```
If it speaks to you straight away, it would be interesting to see what it says. If it doesn't say anything immediately, try entering this line:
```
GET /
```
and see if it says anything.

---

### Post by wantondude on 2017-02-08
Domo arigato Sensei ... Thx Cog .. 

The Dude Abides ....

... will post updates :) 

K

---

### Post by wantondude on 2017-02-08
OK ..

I think I found the fxxker... 

A while ago I created a user for our scanning machine to upload scanned documents onto our server, so as not to have to user windows shares. 
Thing is I forgot that the password I used for the scan-user was ... ehm not very difficult to crack.

The parasite turned out to be of ukrainian origin, or at least that's what's configured in the config files. 

The service which was setup was a MUH Irc bouncer. 

For now I renamed the 2 directories containing the executables and config files. 

Directory 1 /scan/lib/

**2**  **config**  cron.d  dir  **f**  **h**  h.c  **init**  **inst**  ips  log  mess  muhrc  **restart**  **run**  **run2**  servers  **y**

Directory 2  /scan/.ICE-UNIX/

**autorun**  ehar.seen  **install**  LinkEvents  **logs**  **pico**  **r**  **run**  **-sh**  **start**  **update**  zmeu.cron  zmeu.dir  **zmeu.help**  **zmeu.ini**  zmeu.pid  zmeu.user  zmeu.user1

I removed the execution of the program from the crontab. 

I am ready to delete the 2 directories, but I was just wondering if You'd have any advice on where to look for some other traces of this parasite ?
Since there is some information to be had in these directories it would be a shame to lose it. 

Any advice ?


Cheers, Big Cheers ..... 

K

---

