---
title: "IP addresses, Remote Access, and Samba"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by Madhatter14641 on 2006-12-07
I have been trying to set up a remote access server for a bit now, trolling the forums and what not. I set up a samba server (as I just want to access a folder from another computer that's running windows) and as long as I use the ip address 192.168.0.5 (the one given to me by my router), it works just fine (from within our home network). When I get my external IP address from some website and try to use that, it doesn't work. I think it's the IP for the router, but I'm not sure (and am quite green behind the ears when it comes to networking). 

My ifconfig output looks like this:
[INDENT]
eth0      Link encap:Ethernet  HWaddr 00:15:F2:33:2C:14  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe33:2c14/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:19048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13755933 (13.1 MiB)  TX bytes:5463271 (5.2 MiB)
          Interrupt:209 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700 (700.0 b)  TX bytes:700 (700.0 b)
[/INDENT]

The router does dynamic IP and DNS assignments I believe.

Any ideas? :-k

---

### Post by Iowan on 2006-12-08
I'm certainly no expert, but here's my nickel's worth:
To access the machine from outside the network, the router will need to port forward.  (You may want to give the server a static address - if it gets a different one from the router, port forwarding will no longer work.)

---

### Post by dbott67 on 2006-12-08
As Iowan states, it is a port issue.

Samba uses ports 137-139 and those would need to be opened on your router and forwarded to 192.168.0.5.  Of course, this means that any script kiddie that goes rolling on by would be able to beat on your poor little server.

If you want safe & secure remote access to your files, you could enable SSH on your server and open up a port on your router that forwards to your internal server.  You could then use a free program such as WinSCP (secure copy) to access your files.  *See my note below about port  22.*

My recommendation would be this (it's what I do):

1. Install SSH on your server (default port 22 is okay)
```
sudo apt-get install ssh
```
2. On your router, forward TCP port 2222 (or some other non-standard port) to 192.168.0.5 on port 22 (the proper SSH port).
3. On the remote machine, download & install [WinSCP]("http://winscp.net/").
4. Configure WinSCP to connect to your home IP on port 2222.
5. Enjoy safe, secure access to your files!

*Note: SSH uses port 22, but every script kiddie knows that & they'll beat on it til the cows come home.  It's okay to let your server use port 22, but don't use that port on your router... pick some arbitrary number (like 2222) and forward that to your server on port 22.*

See attached screen shot of me using WinSCP (over port 2222) to connect to my home Linux computer running SSH on port 22.  Also attached is the screenshot of the port forward rule.

-Dave

---

### Post by Madhatter14641 on 2006-12-09
Hey, thanks! This sounds like exactly what I was looking for. :D 

It was driving me bonkers!

---

### Post by kbayly on 2006-12-13
I posted this answer to my own question a few months back. I think it applies to what you are talking about.

This is a working method to remotely mount a samba share securely through ssh on a server behind a router...

1. Forward the necessary ports on your router to the ip address of your local machine. For ssh the port is 22. For samba the port is 139.

2. Properly configure your samba server and your ssh server settings on your local machine. There are plenty of tutorials out there for this, and remoting doesnt require any special configurations.

3. Get a static domain name from dyndns.org. This service syncs with your ISP's dynamic IP and updates as the IP changes.

4. For WINDOWS: Download Putty, an easy and powerful ssh client ([http://www.chiark.greenend.org.uk/~sgtatham/putty/)](http://www.chiark.greenend.org.uk/~sgtatham/putty/)).

- create a new Putty session. the host name should the dyndns.org domain that you registered. name the session whatever you want.

-tunnel your samba traffic. choose Connection > SSH > Tunnels. Check Local ports accept connections from other hosts. Check Remote ports do the same (SSH-2 Only). Source port is 139. destination is yourhostname:139 (whatever you registered with dyndns.org, followed by :139). Click "Local" and "Auto". Go back to Session and click "save"

-Connect to your machine through ssh/putty.

Now that you can ssh, here's the tricky stuff. Since windows uses port 139 for windows file sharing, you need to disable this service. open a command prompt and type "net stop server". if you want to restart it later after you close your SSH tunnel, just type "net start server".

Next tricky part- you need to modify your "hosts" and "lmhosts.sam" file located in C:\WINDOWS\system32\drivers\etc.

Open the C:\WINDOWS\system32\drivers\etc\windows\hosts file and add the line:

* 127.0.0.1 localhost

Open the C:\WINDOWS\system32\drivers\etc\windows\lmhosts file and add the line:

* 127.0.0.1 sambaserver

Alright, ssh to the server with Putty, and then mount your network drive like so:

Windows Explorer > Tools > Map Network Drive

\\127.0.0.1\sharedfolder

It's more convenient if you windows username and samba username are the same, otherwise you will need to choose the "log in as different user" option.

Give it a second, and the drive should map! you need to map a drive for each sharedfolder you have on your samba server.

FOR MAC OSX:

This is MUCH simpler.

open a terminal and type:

ssh -L 139:localhostip:139 dyndns.orghostname -l username

the local host ip is whatever local IP you forwarded ports 22 and 139 to. The dyndns.orghostname is whatever domain name you got from dyndns.org. username is whatever your username is on the samba server.

for example:

ssh -L 139:192.168.0.13:139 joesmith.dyndns.org -l jsmith

oh yeah, to open ports you need to have root priveledges, so either login as root with su, or preface the command with sudo.

then mount your drive-
Finder > Go > Connect to Server

Server address - smb://127.0.0.1/sharedfolder

you should be ready to rock!

---

### Post by koenn on 2006-12-13
> **dbott67 said:**
> 
If you want safe & secure remote access to your files, you could enable SSH on your server and open up a port on your router that forwards to your internal server.  You could then use a free program such as WinSCP (secure copy) to access your files.  *See my note below about port  22.*
on port 2222.

[ ... ]

*Note: SSH uses port 22, but every script kiddie knows that & they'll beat on it til the cows come home.  It's okay to let your server use port 22, but don't use that port on your router... pick some arbitrary number (like 2222) and forward that to your server on port 22.*


This is an example of "security through obscurity" : you think you can mislead the script kiddies by choosing an arbitrary port in stead of a 'well-known' port. It may work for 0.3 % of the script kiddies. The other 97.7 % will have a recent port scanner that not only checks for open ports, put also probes the service listening on that port to determine what it is. 
If port 2222 shows 'open' on a scan and is forwarded to port 22 on a server where ssh is listining, the scanner will report that port 2222 is open and has ssh behind it (+ probably make and version number so one can use the matchin expoits, if there are any).

You're security will depend on the ssh configuration, not on changing the ports. other than that, it's a good idea to use ssh in stead of opening file sharing to the whole world.

---

### Post by dbott67 on 2006-12-13
I would agree that it falls under the 'security through obscurity' mantra, however, most scanners do not scan every port --- only the well-known 'default' ports.  To scan otherwise would take an inordinate amount of time, and the hackers only want the 'low-hanging fruit'.

When I had my router forwarding port 22 to my computer, I used to get hundreds of attempts per night.  After switching to port 2222 --- a grand total of 0 attempts (only me from work).

```
Dec 11 14:26:21 thedrake sshd[6065]: Server listening on :: port 22.
Dec 11 22:32:29 thedrake sshd[6065]: Received signal 15; terminating.
Dec 11 22:34:06 thedrake sshd[4650]: Server listening on :: port 22.
Dec 12 12:56:06 thedrake sshd[26224]: Accepted password for dbott from 24.xxx.yyy.zzz port 1220 ssh2
Dec 12 12:56:06 thedrake sshd[26230]: (pam_unix) session opened for user dbott by (uid=0)
Dec 12 14:36:30 thedrake sshd[26230]: (pam_unix) session closed for user dbott
Dec 12 16:39:20 thedrake sshd[31663]: Accepted password for dbott from 24.xxx.yyy.zzz port 3649 ssh2
Dec 12 16:39:20 thedrake sshd[31667]: (pam_unix) session opened for user dbott by (uid=0)
Dec 12 16:43:24 thedrake sshd[4650]: Received signal 15; terminating.
Dec 12 16:44:45 thedrake sshd[4646]: Server listening on :: port 22.
Dec 12 18:17:33 thedrake sshd[4646]: Received signal 15; terminating.
Dec 12 18:18:44 thedrake sshd[4582]: Server listening on :: port 22.
```

Anyhow, good security requires a multi-layered approach:
- Good passwords
- turn off unneeded services
- keep OS up-to-date
- keep apps up-to-date
- firewall & AV where appropriate
- and don't eat yellow snow (I mean, don't install untrusted software)

-Dave

---

### Post by koenn on 2006-12-15
OK, in such a context (that multi-layer thing), I agree :-)

---

