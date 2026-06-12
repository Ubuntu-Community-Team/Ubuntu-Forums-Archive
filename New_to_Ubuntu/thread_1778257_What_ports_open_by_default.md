---
title: "What ports open by default?"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by 007casper on 2011-06-08
What ports open by default?

System > Administration > Network tools

Clicked on Port scan, for IP I put localhost hit scan

I got 631 open ipp

printing port ??? I dont have any printers installed.  Opened up gufw, chose simple, add rule 
> 
Deny In TCP 631

This is where the kicker comes in.  Went to my friends computer to scan ports.  He got 631 open, and also 56303.  I blocked 56303, scanned ports again.  This time I got four ports opened up, 55460, 33748, 35133 :-k

then block those ports, scanned again... then got 51533,50019,57292 opened up. 8-[

Everytime I block these new ports through gufw, and scan ports a few more ports listed as open.

???

Is there a malware on this laptop?

---

### Post by 3rdalbum on 2011-06-08
If you scan "localhost" you'll see a few ports that are only accessable through the lo (loop) network interface; in other words, they are only accessible to programs running on the same computer.

Run the same port scan from your computer to his, and you'll probably see no ports open.

---

### Post by jtarin on 2011-06-08
[Go here]("https://www.grc.com/x/ne.dll?bh0bkyd2") and get a port scan from the outside......you'll see you have nothing to worry about as 3rdalbum suggested. I don't run any firewall outside of the initially installed setup, but as added protection I'm behind a router. :)

---

### Post by yetiman64 on 2011-06-08
> **jtarin said:**
> [Go here]("https://www.grc.com/x/ne.dll?bh0bkyd2") and get a port scan from the outside......you'll see you have nothing to worry about as 3rdalbum suggested.

+1, grc is a very good service. 

Just note if you are behind a modem or routers firewall, you will need to access its settings and place your installs IP in the DMZ (demilitarized zone) first or you will not get an accurate idea of the ports open/closed on your actual install.

A hardware firewall will block grc from scanning your machine.

I have done this here on a fresh install of Ubuntu and although grc could see all the ports on my install, none were open (closed is good on a Linux machine). No services run on a default Ubuntu install that are accessible from the internet (unlike Windows). 

What you are seeing from scanning ports from within the install is as already noted, locally accessible services only. IIRC you just blocked cups daemon from working (Linux printing service) by blocking local port 631.

**Edit**: see below, most definitely remember to remove your install from the DMZ when the scanning is completed ;-)

---

### Post by jtarin on 2011-06-08
> **yetiman64 said:**
> 
Just note if you are behind a modem or routers firewall, you will need to access its settings and place your installs IP in the DMZ (demilitarized zone) first or you will not get an accurate idea of the ports open/closed on your actual install.
Then remember to put it back.:p

---

### Post by 007casper on 2011-06-08
I am also behind a modem, and router.  
> 
you will need to access its settings and place your installs IP in the DMZ (demilitarized zone) 

I am not clear what that means.  Do you want me to connect directly from the modem to the computer without a firewall?

strange enough, if I do localhost on port scan I get port 631 open.  If I do put the computer IP 192.168.1.49, I get several ports open.  I am scanning my friends computer from mine by using his connected local IP.  It is still scanning.

I also grc my computer without turning off the firewall, and also got the router, modem etc. hooked up.  It says good to go... passed... stealth.

So, those funky ports are from applications ??? what applications I wonder?

---

### Post by jtarin on 2011-06-08
> **007casper said:**
> I am also behind a modem, and router.  


I am not clear what that means.  Do you want me to connect directly from the modem to the computer without a firewall?

strange enough, if I do localhost on port scan I get port 631 open.  If I do put the computer IP 192.168.1.49, I get several ports open.  I am scanning my friends computer from mine by using his connected local IP.  It is still scanning.

I also grc my computer without turning off the firewall, and also got the router, modem etc. hooked up.  It says good to go... passed... stealth.

So, those funky ports are from applications ??? what applications I wonder?[Example.]("http://www.cyberciti.biz/faq/find-out-which-service-listening-specific-port/")


**_/etc/services file_**

/etc/services is a plain ASCII file providing a mapping between friendly textual names for internet services, and their underlying assigned port numbers and protocol types. Every networking program should look into this file to get the port number (and protocol) for its service. You can view this file with the help of cat or less command:
```
$ cat /etc/services
$ grep 110 /etc/services
$ less /etc/services
```

---

### Post by 007casper on 2011-06-09
thank you so much.

grep 110 /etc/services
pop3		110/tcp		pop-3		# POP version 3
pop3		110/udp		pop-3
kpop		1109/tcp			# Pop with Kerberos


ok... checking the ports that came up on localhost port scan, just to find out what they are for...

 grep 55460 /etc/services
 grep 33748 /etc/services
 grep 35133 /etc/services
 grep 51533 /etc/services
 grep 50019 /etc/services
 grep 57292 /etc/services

it doesn't list anything, doesn't give errors.  I wonder what those ports are set for...

---

### Post by jtarin on 2011-06-09
[Go Here.]("http://www.google.com/webhp?hl=en&tab=nw#hl=en&sugexp=ldymls&xhr=t&q=port+55460+udp&cp=5&pf=p&sclient=psy&site=webhp&source=hp&aq=0v&aqi=&aql=&oq=port+55460+&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=4730df14103ac1c5&biw=1440&bih=731") The Official Port Guide. Best on the INTERNET.

---

### Post by doas777 on 2011-06-09
those are all dynamically allocated client ports being used by an application.

first, run and post back
```
sudo netstat -ntlup
```this will show you your current connections, and the ports that are listening for new connections. these last are the only ports you are worried about. if a port is in use by a connection it is very very hard to hijack (with a modern linux kernel) so those are all safe.
another class of safe connection we will see, are localhost connections used by the processes running on your PC, to share information with eachother. do not interfer with these or your apps will not run right.

here is an excerpt of mine:
```

user@host:~$ sudo netstat -ntlup
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 [COLOR=Red]0.0.0.0[/COLOR]:3689            0.0.0.0:*               LISTEN      1703/mt-daapd
tcp        0      0 [COLOR=SeaGreen]127.0.0.1[/COLOR]:3306          0.0.0.0:*               LISTEN      1347/mysqld
tcp        0      0 [COLOR=SeaGreen]127.0.0.1[/COLOR]:139           0.0.0.0:*               LISTEN      3715/smbd
tcp        0      0 [COLOR=RoyalBlue]192.168.XX.YY[/COLOR]:139       0.0.0.0:*               LISTEN      3715/smbd
tcp        0      0[COLOR=Red] 0.0.0.0[/COLOR]:8080            0.0.0.0:*               LISTEN      1960/python
tcp        0      0 [COLOR=Red]0.0.0.0[/COLOR]:80              0.0.0.0:*               LISTEN      1779/apache2
tcp        0      0 [COLOR=SeaGreen]127.0.0.1[/COLOR]:7634          0.0.0.0:*               LISTEN      1529/hddtemp

```in the local address column, we have 3 types of addresses: 

[LIST]
[*][COLOR=Red]0.0.0.0[/COLOR]: a **listening **port for any connection attempt. **These ****are the ports you want to lock down**.
[*][COLOR=Blue]192.168...[/COLOR] : a **listening port** for my lan only. it is already locked down for my needs.
[*][COLOR=SeaGreen]127.0.0.1[/COLOR] : a **local port**. leave these alone. they cannot be accessed.
[/LIST]
this output comes from my server, so as you can see, I have a mt-daap service, a smbd service, a python service, and an apache server running, and listening for new connections. I know all these services and why they are there, but you will probably not have any services at all, so we should review any you find. the important thing to note, is that these are global listening ports, used to create a new connection by any remote party that can reach your server.

I also have a hddtemp service listener on 1529, but this is a localhost-only service (note: it is listening on the loopback so can only be accessed from localhost) which is used by my Hardware Sensors Monitor applet, so it can ask the kernel for the temperature.
this kind of connection is essential to the correct function of your PC, so just leave em alone.

anyway show us what you've got and we;ll see whats going on.

---

### Post by 007casper on 2011-06-09
my computer

```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1226/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      1226/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1130/dhclient   
udp        0      0 0.0.0.0:55495           0.0.0.0:*                           1008/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1008/avahi-daemon:
```

I will get my friends computer netstat -ntlup tomorrow

---

### Post by doas777 on 2011-06-09
based on that output, you're fine. theres nothing in there that you need to worry about. 

if you are directly connected to the internet, then perhaps blocking avahi might not be a horrible idea, but shouldn't strictly be necessary. the cupsd is safe (localhost only), and the dhclient is required to allow dhcp responses to reach you.

---

### Post by 007casper on 2011-06-09
and my friends computer has the similar netstat.  We are both directly connected to online

friend's computer has similar output
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1226/cupsd      
tcp6       0      0 ::1:631                 :::*                    LISTEN      1226/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1130/dhclient   
udp        0      0 0.0.0.0:55495           0.0.0.0:*                           1008/avahi-daemon: 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1008/avahi-daemon:
```

saw this on wikipedia [http://en.wikipedia.org/wiki/Zero_configuration_networking](http://en.wikipedia.org/wiki/Zero_configuration_networking)
> Because mDNS operates under a different trust model than unicast DNS&#8212;trusting the entire network rather than a designated DNS server&#8212;it is vulnerable to spoofing attacks by any system within the multicast IP range. Like SNMP and many other network management protocols, it can also be used by attackers to quickly gain detailed knowledge of the network and its machines.

to block avahi, I did
sudo ufw deny 55495/udp
sudo ufw deny 5353/udp

then, checked netstat again, this time I got "r" at the end of avahi-daemon and a port number 42465
```

udp        0      0 0.0.0.0:42465           0.0.0.0:*                           973/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           973/avahi-daemon: r
```

what is r?  how do I block avahi properly?

thank you so much



is that correct?

---

### Post by doas777 on 2011-06-09
well, first off, your paradigm for firewall rules is backward. you should block all incoming connections except those specified. since you don't have any network services, just set ufw to a default deny and leave it at that. 

I personally woudl install gufw, delete all your current block rules, and make it look like this:
[http://gufw.tuxfamily.org/wp-content/uploads/2010/04/gufw_screenshot2.png](http://gufw.tuxfamily.org/wp-content/uploads/2010/04/gufw_screenshot2.png)

that is pretty much as secure as you need to be.

---

### Post by 007casper on 2011-06-09
awesomeness.  Thank you.

973/avahi-daemon: r
what is the r at the end?  I didnt have that a few hours ago

---

### Post by doas777 on 2011-06-09
I don;t honestly know what it means, but my first guess is it means the socket is owned by a root process, or that it means restricted. the only reference I can find to it anywhere is here in man netstat:
> 
PID/Program name
       Slash-separated pair of the process id (PID) and process  name  of  the
       process  that  owns  the  socket.   --program  causes this column to be
       included.  You will also need superuser privileges to see this informa&#8208;
       tion  on sockets you don't own.  This identification information is not
       yet available for IPX sockets.


I've googled around a bit, and suprisingly most unixes do not support --program at all. weird.

---

### Post by 007casper on 2011-06-10
thank you I really appreciate your help

---

