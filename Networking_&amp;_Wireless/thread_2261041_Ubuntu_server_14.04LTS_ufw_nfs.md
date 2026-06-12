---
title: "Ubuntu server 14.04LTS ufw nfs"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by Frank P on 2015-01-15
I have a small LAN with a pc configured as an nfs client and another as a nfs server. Both are running ufw. Ports 111 & 2049 are open.
If the ufw is enabled the directory is not mounted; if I disable ufw on the server it mounts.

What other ports do I have to open to allow it to be mounted?

Also since the LAN is behind a router that has no open incoming ports do I really need to run a firewall

Thanks

Frank

---

### Post by Doug S on 2015-01-16
> **Frank P said:**
> What other ports do I have to open to allow it to be mounted?I don't know, but I would use a packet sniffer (tcpdump, or wireshark) to figure it out. Say your client was at 192.168.3.7, and the network interface was at eth0, I would run this on the server:```
sudo tcpdump -n -tttt -i eth0 host 192.168.3.7
```then observe what ports and traffic are involved when you try to access from the client.> **Frank P said:**
> Also since the LAN is behind a router that has no open incoming ports do I really need to run a firewallI don't think so. It depends on how worried you are about attacks from within your LAN.

---

### Post by Frank P on 2015-01-17
Doug
 I followed your advice and tried tcpdump. It took a while to figure it out but I (think) I got a list of the ports used. Monitoring a manual mount request 111 & 2049 showed up as expected. Port 820 also showed up but allowing it didn't help - the mount still times out. There were also a bunch of high numbered ports - 42010, 55764, 34630 that I didn't try opening; I  think they are random ports.

I've seen some messages here - via google, that suggest changing the boot scripts for services that use random ports to some fixed unused port but I hesitate to try it. Are you familiar with that?
Can you suggest anything else to try

Thanks

Frank

---

### Post by Doug S on 2015-01-17
For your server, what does this reveal? (example from my server):```
doug@doug-64:~/tcpdump$ [COLOR=#ff0000]sudo netstat -tulpn[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1712/smbd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1502/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1712/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      5341/apache2
tcp        0      0 173.180.45.4:53         0.0.0.0:*               LISTEN      1311/named
tcp        0      0 192.168.111.1:53        0.0.0.0:*               LISTEN      1311/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1311/named
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1188/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1566/master
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      1311/named
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      5341/apache2
udp        0      0 173.180.45.4:53         0.0.0.0:*                           1311/named
udp        0      0 192.168.111.1:53        0.0.0.0:*                           1311/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           1311/named
udp        0      0 0.0.0.0:67              0.0.0.0:*                           1356/dhcpd
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1059/dhclient3
udp        0      0 192.168.111.255:137     0.0.0.0:*                           1257/nmbd
udp        0      0 192.168.111.1:137       0.0.0.0:*                           1257/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1257/nmbd
udp        0      0 192.168.111.255:138     0.0.0.0:*                           1257/nmbd
udp        0      0 192.168.111.1:138       0.0.0.0:*                           1257/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1257/nmbd
```Aren't the high numbered ports from the client? It will use high numbered ports for stuff. Perhaps post some examples, so we can better understand the context.

---

### Post by Doug S on 2015-01-17
To answer your actual question.> **Frank P said:**
> I've seen some messages here - via google, that suggest changing the boot scripts for services that use random ports to some fixed unused port but I hesitate to try it. Are you familiar with that?I'm not. I have been doing some reading, and it seems a strange way to do things. There is another [thread]("http://ubuntuforums.org/showthread.php?t=2261263") you might want to watch.

---

### Post by Frank P on 2015-01-18
Doug
 Haven't figured out how to get my output into the message yet. As soon as I do I'll send it. I did see some of the high number ports mentioned in some of the other threads
Thanks
Frank

---

### Post by Frank P on 2015-01-20
Doug

Below is a print out from rpcinfo showing which ports are being Listened to and whether they're open in ufw. nffs is running. You'll see the some of the high numbered ports being listened to are not open in ufw . Any ideas
(I still can't get only the code into a code block 
Thanks
Frank

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name Status
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -                Allow in
tcp        0      0 0.0.0.0:38375           0.0.0.0:*               LISTEN      1347/rpc.mountd  Not listed
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      561/smbd         Allow in
tcp        0      0 0.0.0.0:52364           0.0.0.0:*               LISTEN      1347/rpc.mountd  Not listed
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      509/rpcbind      Allow in
tcp        0      0 0.0.0.0:46130           0.0.0.0:*               LISTEN      -                Not listed
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      1049/vsftpd      Allow in
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1237/sshd        Allow in
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN      14293/cupsd      Allow in
tcp        0      0 0.0.0.0:38362           0.0.0.0:*               LISTEN      1347/rpc.mountd  Not listed
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      561/smbd         Allow in
tcp        0      0 0.0.0.0:47133           0.0.0.0:*               LISTEN      525/rpc.statd    Not listed
tcp6       0      0 :::2049                 :::*                    LISTEN      -                Allow in
tcp6       0      0 :::48645                :::*                    LISTEN      1347/rpc.mountd   Not listed 
tcp6       0      0 :::48965                :::*                    LISTEN      525/rpc.statd    Not listed 
tcp6       0      0 :::38630                :::*                    LISTEN      1347/rpc.mountd   Not listed
tcp6       0      0 :::37960                :::*                    LISTEN      1347/rpc.mountd   Not listed
tcp6       0      0 :::139                  :::*                    LISTEN      561/smbd         Allow in
tcp6       0      0 :::111                  :::*                    LISTEN      509/rpcbind      Allow in
tcp6       0      0 :::59190                :::*                    LISTEN      -                 Not listed
tcp6       0      0 :::22                   :::*                    LISTEN      1237/sshd        Allow in
tcp6       0      0 :::631                  :::*                    LISTEN      14293/cupsd      Allow in
tcp6       0      0 :::445                  :::*                    LISTEN      561/smbd         Allow in

---

### Post by Frank P on 2015-01-21
I originally posted this in the Networks forum but I decided to ask it here as well since it hasn't been resolved. (if this is considered bad forum etiquette I'll remove it)

I have a small LAN with a pc configured as an nfs client and another as a nfs server. Ports 111 & 2049 are open on the server.
 If the ufw is enabled the directory is not mounted on the client; if I disable ufw on the server, it mounts. The ufw log shows that it blocked when the firewall is active.

What else can I check


 Thanks

---

### Post by newbie-user on 2015-01-21
ufw is blocking the ports. You have to allow ports 111 and 2049 through the firewall.```
sudo ufw allow 111
``````
sudo ufw allow 2049
```

---

### Post by Frank P on 2015-01-21
As I mentioned in the message - ports 111 & 2049 are open
Here is the list for ufw (still can't figure out how to just get the code in the code box)
Code:
[code]22                         ALLOW       Anywhere
139                        ALLOW       Anywhere
445                        ALLOW       Anywhere
137                        ALLOW       Anywhere
138                        ALLOW       Anywhere
111                        ALLOW       Anywhere
2049                       ALLOW       Anywhere
631                        ALLOW       Anywhere
21/tcp                     ALLOW       Anywhere
22 (v6)                    ALLOW       Anywhere (v6)
139 (v6)                   ALLOW       Anywhere (v6)
445 (v6)                   ALLOW       Anywhere (v6)
137 (v6)                   ALLOW       Anywhere (v6)
138 (v6)                   ALLOW       Anywhere (v6)
111 (v6)                   ALLOW       Anywhere (v6)
2049 (v6)                  ALLOW       Anywhere (v6)
631 (v6)                   ALLOW       Anywhere (v6)
21/tcp (v6)                ALLOW       Anywhere (v6)

---

### Post by Doug S on 2015-01-21
Hi Frank,

You would have to allow those ports in ufw. I am an iptables person and not a ufw person, so I don't know how. (But many many readers do use UFW, and I'm sure one will help.)

The added worry is, and from what little I have read, those high numbered ports will keep changing unless you limit the range in your nfs config files. (I might be wrong thou.) The suggestion is to limit them to some range of ports and open that range in UFW.

---

### Post by Frank P on 2015-01-21
Doug,

Unfortunately that seems to confirm what I read when I googled some older message. I really didn't want to do that. I'm surprised that it's not mentioned on the man page or tutorials for setting up nfs.
Since I'm only using that server as a nas I'll just disable ufw when I'm backing up.
I'll mark this solved. 

Thanks for your help

Frank

---

### Post by Doug S on 2015-01-21
> **Frank P said:**
> I originally posted this in the Networks forum but I decided to ask it here as well since it hasn't been resolved. (if this is considered bad forum etiquette I'll remove it)Yes, Frank it is bad etiquette. Perhaps a moderator will be kind enough to put the two threads together.

You didn't tell the whole story, learned on the old thread, with this new posting, but I see that someone mentioned how to open ports on UFW.

---

### Post by Frank P on 2015-01-21
Doug,
I didn't mean to mislead anyone. I appreciate your help. I did mentioned in either my first or second post that I had read about opening the higher numbered ports and changing the login scripts but that I didn't want to try it because it didn't make sense to me - still doesn't because its not officially documented anywhere. I didn't realize that all the forums were moderated/viewed by the same people, and thought that maybe Security might have been a better place to post
Know better now
Thanks
Frank

---

### Post by steeldriver on 2015-01-21
[I][B]Threads merged
[/B][/I]
FWIW I just had a play with this, and this seems to work for me:

[https://wiki.debian.org/SecuringNFS](https://wiki.debian.org/SecuringNFS)

Basically it describes how to configure nfs-kernel-server so that rpc.mountd listens on a fixed port (they choose 32767) - then you can open just that additional port in UFW

---

### Post by Frank P on 2015-01-21
Okay, I guess I have to go that way if I don't want to enable/disable ufw when I want to do back ups. I'm surprised though that it's not mentioned in the tutorials for setting up nfs. It would have save me, and some others a lot of time 
Thanks
Frank

---

