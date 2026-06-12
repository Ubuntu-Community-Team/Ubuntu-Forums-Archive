---
title: "strange issue"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by Malegnis on 2008-01-22
i have an ubuntu server up. i have apache2 working as well as proftpd. 

now when i go to mydomain.com it takes me right to my webserve, no problemsr. but when i try to access my ftp, via ftp.mydomain.com i will get a login box as usual, only i will never connect. BUT if im at home, and i type 192.168.1.19:<my port> i can connect to my ftp server right away. i have the ports forwarded correctly. i have everything in order (to my knowledge) on my router. but im completely baffled.

any help would be greatly appreciated.

EDIT:
this is my connectiion information while useing filezilla.

Status:	Resolving IP-Address for soupchan.org
Status:	Connecting to <my ip:port>...
Status:	Connection established, waiting for welcome message...
Response:	220 MAL-SER
Command:	USER WebMaster
Response:	331 Password required for WebMaster.
Command:	PASS **********
Response:	230 Anonymous access granted, restrictions apply.
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 MDTM
Response:	 REST STREAM
Response:	 SIZE
Response:	211 End
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is current directory.
Command:	TYPE I
Response:	200 Type set to I
Command:	PASV
Response:	227 Entering Passive Mode (192,168,1,1,239,126).
Status:	Server sent passive reply with unroutable address. Using server address instead.
Command:	LIST


and i have no listing of any files and cannot interact with anything.

---

### Post by kirsche on 2008-01-22
I think this error gives a clue:

Status: Server sent passive reply with unroutable address. Using server address instead.

Your ftp server seems to send a RFC1918 address for the PASV connection, which is not reachable from the outside (usually)

---

### Post by dmkuster on 2008-01-27
I'm having exactly this same problem.

Did you ever find a solution?

I'm sure it's got to do with setting the correct options in proftpd.conf...

---

### Post by fr33flyer on 2008-01-27
Passive mode requires more than just ports 20/21 (FTP I believe) to connect. It usually pulls one unprivileged port out of it's hat and trys to use it as the passive data channel. 1st try to configure your ftp server to only use a few ports for this feature and then forward them accordingly. Otherwise most ftp application have a "use passive mode" option, which can be unchecked.

Hope this helps

---

### Post by dmkuster on 2008-01-28
I have a router with firewall and NAT, and I believe it's set up correctly.  It is forwarding ports 20 - 21 and 60000 - 65535.

In my proftpd.conf file I have PassivePorts set to 60000 - 65535.  I've played around with MasqeradeAddress but whatever I put there doesn't seem to work.  I've tried putting my LAN address, 192.168.1.156, and I've also tried putting myhostname.hopto.org which should resolve to the IP my router shows to the outside world.

In all cases, filezilla on my windows box can connect and login, but then immediately disconnects with the "Server sent passive reply with unroutable address. Using server address instead" error message.

Any thoughts???  :confused:

---

### Post by dmkuster on 2008-01-28
> **dmkuster said:**
> I have a router with firewall and NAT, and I believe it's set up correctly.  It is forwarding ports 20 - 21 and 60000 - 65535.

In my proftpd.conf file I have PassivePorts set to 60000 - 65535.  I've played around with MasqeradeAddress but whatever I put there doesn't seem to work.  I've tried putting my LAN address, 192.168.1.156, and I've also tried putting myhostname.hopto.org which should resolve to the IP my router shows to the outside world.

In all cases, filezilla on my windows box can connect and login, but then immediately disconnects with the "Server sent passive reply with unroutable address. Using server address instead" error message.

Any thoughts???  :confused:

OK, I tried accessing my FTP server from work and it works!  I don't understand why it doesn't work on my home LAN, but it probably has something to do with the router port forwarding.

But here's the problem -- I can transfer files TO my linux box at home, but I can't retrieve files FROM my linux box.  :confused:

I'm running the filezilla client here at work and when I try to fetch a file it just hangs with this cryptic error message:

Status:	Directory listing successful
Status:	Starting download of /upload/HDRSource WW1401/csmdriver/warp/development/src/bts/wwdrv/csdt/src/csdt.c
Status:	ftpcontrolsocket.cpp(1764): Waiting for replies to skip before sending next command...   caller=0p1844028

Any ideas???

Thanks for the help!

---

### Post by CMCDragonkai on 2008-05-17
Go into Filezilla Interface. Go into Passive Mode Settings. Look for the change to Dont use external ip for local connections. Uncheck that, and try again.

---

