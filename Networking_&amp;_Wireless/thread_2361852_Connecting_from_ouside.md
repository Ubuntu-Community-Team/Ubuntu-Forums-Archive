---
title: "Connecting from ouside"
date: 2017-05-21
forum: Networking &amp; Wireless
---

### Post by netzonecal on 2017-05-21
I know this subject has been discussed but not really about my situation.

I have Ubuntu 16.04 up to date on a desktop wired connection to a Aztech5001_F9A7D router.  ADSL STATIC IP connection.  Globe ISP

My Laptop is Windows 7

I can connect from laptop to pc using Putty.
I can connect to pc from cell phone using  JuiceSSH

But for the life of me, i cant figure out how to properly setup the port forwarding so i can connect to pc/laptop from outside my  network.
everything i have tried has failed.

thank you in advance

---

### Post by TheFu on 2017-05-21
[https://ubuntuforums.org/showthread.php?t=1558871](https://ubuntuforums.org/showthread.php?t=1558871) talks about forwarding ssh ports.
I'm assuming ssh access is your goal?

Google found these instructions for your router. [https://portforward.com/aztech/dsl5001en/](https://portforward.com/aztech/dsl5001en/) I didn't read them.

If you need more help, then please be specific.  Hard to help when the generalities all seem correct, but we don't have any details.

If your router supports port translation, I'd strongly recommend using it and taking WAN:64022 --> LAN:22 to remove all the script-kiddies looking for access on port 22.  Makes for much cleaner logs.  Review your logs daily, regardless.  Also, using some sort of firewall blocking for unwanted ssh access would be smart, as would only allowing ssh-keys, never passwords, for remote access.
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) tries to explain more.

---

### Post by netzonecal on 2017-05-21
```
robert@Sol:~$ sudo netstat -tupan
[sudo] password for robert: 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:41608           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      972/mysqld      
tcp        0      0 0.0.0.0:44746           0.0.0.0:*               LISTEN      977/rpc.mountd  
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1632/smbd       
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      789/rpcbind     
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1151/dnsmasq    
[COLOR=#ff0000]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      959/sshd        [/COLOR]
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      21677/cupsd     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1632/smbd       
tcp        0      0 0.0.0.0:53918           0.0.0.0:*               LISTEN      977/rpc.mountd  
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:60100           0.0.0.0:*               LISTEN      977/rpc.mountd  
tcp6       0      0 :::44553                :::*                    LISTEN      977/rpc.mountd  
tcp6       0      0 :::139                  :::*                    LISTEN      1632/smbd       
tcp6       0      0 :::34379                :::*                    LISTEN      977/rpc.mountd  
tcp6       0      0 :::56750                :::*                    LISTEN      977/rpc.mountd  
tcp6       0      0 :::111                  :::*                    LISTEN      789/rpcbind     
tcp6       0      0 :::80                   :::*                    LISTEN      1410/apache2    
tcp6       0      0 :::22                   :::*                    LISTEN      959/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      21677/cupsd     
tcp6       0      0 :::445                  :::*                    LISTEN      1632/smbd       
tcp6       0      0 :::2049                 :::*                    LISTEN      -               
tcp6       0      0 :::39619                :::*                    LISTEN      -               
udp        0      0 0.0.0.0:965             0.0.0.0:*                           789/rpcbind     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           812/avahi-daemon: r
udp        0      0 0.0.0.0:46481           0.0.0.0:*                           977/rpc.mountd  
udp        0      0 0.0.0.0:50816           0.0.0.0:*                           977/rpc.mountd  
udp        0      0 0.0.0.0:38645           0.0.0.0:*                           812/avahi-daemon: r
udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:39347           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:57024           0.0.0.0:*                           977/rpc.mountd  
udp        0      0 127.0.1.1:53            0.0.0.0:*                           1151/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           13637/dhclient  
udp        0      0 0.0.0.0:111             0.0.0.0:*                           789/rpcbind     
udp        0      0 192.168.254.255:137     0.0.0.0:*                           1608/nmbd       
udp        0      0 192.168.254.105:137     0.0.0.0:*                           1608/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1608/nmbd       
udp        0      0 192.168.254.255:138     0.0.0.0:*                           1608/nmbd       
udp        0      0 192.168.254.105:138     0.0.0.0:*                           1608/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1608/nmbd       
udp        0      0 0.0.0.0:631             0.0.0.0:*                           10927/cups-browsed
udp6       0      0 :::965                  :::*                                789/rpcbind     
udp6       0      0 :::5353                 :::*                                812/avahi-daemon: r
udp6       0      0 :::2049                 :::*                                -               
udp6       0      0 :::43365                :::*                                -               
udp6       0      0 :::59766                :::*                                977/rpc.mountd  
udp6       0      0 :::39805                :::*                                977/rpc.mountd  
udp6       0      0 :::44116                :::*                                812/avahi-daemon: r
udp6       0      0 :::40753                :::*                                977/rpc.mountd  
udp6       0      0 :::111                  :::*                                789/rpcbind
```

```
robert@Sol:~$ sudo ufw status
Status: inactive
robert@Sol:~$ sudo service ssh status
&#9679; ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enab
   Active: active (running) since Sat 2017-05-20 13:45:43 PHT; 1 day 8h ago
  Process: 13760 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCE
 Main PID: 959 (sshd)
   CGroup: /system.slice/ssh.service
           &#9492;&#9472;959 /usr/sbin/sshd -D

May 21 11:49:14 Sol sshd[959]: Server listening on 0.0.0.0 port 22.
May 21 11:49:14 Sol sshd[959]: Server listening on :: port 22.
May 21 13:18:48 Sol sshd[18405]: Accepted password for root from 192.168.254.100
May 21 13:18:48 Sol sshd[18405]: pam_unix(sshd:session): session opened for user
May 21 13:20:33 Sol sshd[18483]: error: Received disconnect from 192.168.254.101
May 21 13:20:33 Sol sshd[18483]: Disconnected from 192.168.254.101 port 46809 [p
May 21 13:20:43 Sol sshd[18487]: Accepted password for root from 192.168.254.101
May 21 13:20:43 Sol sshd[18487]: pam_unix(sshd:session): session opened for user
May 21 13:21:31 Sol sshd[18537]: Accepted password for root from 192.168.254.101
May 21 13:21:31 Sol sshd[18537]: pam_unix(sshd:session): session opened for user
lines 1-18/18 (END)

```
So Firewall is innactive
Server listening on 0.0.0.0 port 22
```
robert@Sol:~$ sudo grep Port /etc/ssh/sshd_config
Port 22

```

I'll continue to read

---

### Post by TheFu on 2017-05-21
Please use 'code tags' for command output so things line up. Hard to read otherwise.

I am a little worried about your netstat output.  Having samba open to the world is a huge security issue.  smb.conf lets you lock down that access - best to limit it to internal subnets only. 

Port 22 on the LAN is fine for ssh. I use it too. That way, I can test ssh connectivity for the WAN internally by using a different port on my WAN IPs.  By setting up a ~/.ssh/config file, I don't have to know which port or even which userid is needed.  Highly recommended.
```
ssh hadar
ssh hadar.domain.com
```
Both get to hadar, but in very different ways.  The non-standard port, a keepalive and tunnel settings are automatically added for the hadar.domain.com connection, since it assumes I'm coming in from somewhere else in the world.

---

### Post by netzonecal on 2017-05-21
Hi [**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685"),

Please assume i know next to nothing  :)

I tried to read up on Hadar but could find nothing.  How do i use this option?

---

### Post by shridhar-kapshikar on 2017-05-22
You have to access your router URL to configure the port forwarding for LAN(local IP) to WAN(public IP). 
Something like this [http://www.tp-link.in/faq-134.html](http://www.tp-link.in/faq-134.html)

---

### Post by slickymaster on 2017-05-22
*Thread moved to **Networking & Wireless*** for a better fit

---

### Post by TheFu on 2017-05-22
hadar is a hostname on my network.  I setup name resolution for the LAN IP and the WAN IP using those different names. hadar and hadar.example.com  The hadar.example.com is on a public DNS available to anyone in the world using a routable, public IP.  The LAN uses non-routable, private networking subnets.

There's nothing magical happening here.

---

### Post by gordintoronto on 2017-05-22
Have you considered Teamviewer? Free for personal use, cross-platform, but proprietary. And you don't need to do anything with your router.

---

### Post by netzonecal on 2017-05-22
Silly me.  Of course Hadar is your domain.  :)  lol

```
robert@Sol:~$ ps -A | grep sshd
  959 ?        00:00:00 sshd
robert@Sol:~$ sudo ss -lnp | grep sshd
[sudo] password for robert: 
tcp    LISTEN     0      128       *:22                    *:*                   users:(("sshd",pid=959,fd=3))
tcp    LISTEN     0      128      :::22                   :::*                   users:(("sshd",pid=959,fd=4))
```

This is an image of my router port forwarding.


[https://www.google.com.ph/search?biw=1366&bih=640&tbm=isch&sa=1&q=aztech+dsl5001&oq=aztech+dsl5001&gs_l=img.3..35i39k1j0j0i24k1l8.25056.26198.0.30610.6.6.0.0.0.0.439.1037.0j3j1j0j1.5.0....0...1.1.64.img..1.4.924.4o4wu_17gwU#imgrc=uDNo_hTnY6SmjM:](https://www.google.com.ph/search?biw=1366&bih=640&tbm=isch&sa=1&q=aztech+dsl5001&oq=aztech+dsl5001&gs_l=img.3..35i39k1j0j0i24k1l8.25056.26198.0.30610.6.6.0.0.0.0.439.1037.0j3j1j0j1.5.0....0...1.1.64.img..1.4.924.4o4wu_17gwU#imgrc=uDNo_hTnY6SmjM:)

In the port forwarding i put 22 in the private and public fields.
And the IP of the ubuntu pc in the Local IP address field.  192.165.254.105.  not my static IP

---

### Post by TheFu on 2017-05-22
192.165.254.105 won't work.  Probably. are u sure that is correct?

---

### Post by netzonecal on 2017-05-22
Link encap:Ethernet  HWaddr e0:cb:4e:eb:62:be  
          inet addr:192.168.254.105  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::502a:a47f:ea5f:38e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:190953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:99028538 (99.0 MB)  TX bytes:21883744 (21.8 MB)

The IP is static and assigned to that MAC

---

### Post by TheFu on 2017-05-22
check the ip again. details matter.

---

### Post by netzonecal on 2017-05-22
oppps.  I typed the IP properly in the router.  i typed it wrong here. 192.168.254.105 is the correct IP.

[TABLE="class: smsTable"]
[TR]
[TH]Rule[/TH]
[TH]Application Name[/TH]
[TH]Public Start Port[/TH]
[TH]Public End port[/TH]
[TH]Private Start Port[/TH]
[TH]Private End port[/TH]
[TH]Local IP Address[/TH]
[TH]Protocol[/TH]
[TH]Edit[/TH]
[TH]Drop[/TH]
[/TR]
[TR]
[TD]0[/TD]
[TD]SSH[/TD]
[TD]22[/TD]
[TD]22[/TD]
[TD]22[/TD]
[TD]22[/TD]
[TD]192.168.254.105[/TD]
[TD]Both[/TD]
[TD][IMG]http://192.168.254.254/images/pen.gif[/IMG][/TD]
[TD][IMG]http://192.168.254.254/images/delete.png[/IMG][/TD]
[/TR]
[/TABLE]

---

### Post by netzonecal on 2017-05-23
Still unable to connect from outside.

---

### Post by TheFu on 2017-05-23
Try a different port on the WAN.  I suppose some ISPs might block 22/tcp.

Also, if you are testing from inside the LAN, many routers block connections to the WAN side from the LAN side. This is to prevent spoofed IPs from being able to open connection.  

$ ssh -vvv {IP}
will show how far the client is getting.
The server-side log files will show if anything is connecting at all.
Did you look at the router logs so see if the connection is even getting that far?

---

