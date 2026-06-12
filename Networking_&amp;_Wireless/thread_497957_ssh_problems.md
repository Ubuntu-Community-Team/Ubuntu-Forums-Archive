---
title: "ssh problems"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by nnpoop on 2007-07-10
hey guys

I have 6.10,I'm trying to be able to locally (in the same local network) ssh into my ubuntu box. sshd starts on startup, port scanning myself confirms that it's running. ifconfig tells me that my local ip is 192.168.0.101. From the same box, if I ssh myself (eg, ssh localhost, ssh 127.0.0.1, ssh 192.168.0.101) I am prompted with a login. But if I try to log in from my windows box (local ip 192.168.0.100), via putty, i get a "connection error: connection timed out" message. It should be noted that if I ping the ubuntu box from the windows box, it replies to pings...

anyone else had this problem?

thanks in advance,
nnp**p

---

### Post by KyleBrandt on 2007-07-10
Are you running the port scan from your ubuntu box (server) or windows box (client)?

---

### Post by nnpoop on 2007-07-10
Running the port scan from the ubuntu box.

---

### Post by KyleBrandt on 2007-07-10
It might be helpful to run the from windows if you can.  I just installed the openssh-server package, and was able to connect without any problems using putty on my windows mobile pocket pc.  Perhaps windows firewall? You could try shutting that off temporarly to eliminate a variable.  Or you are specifying the wrong port in putty?  I don't know if have mismatched ssh types would cause that error, .ie. putty is set to ssh1 when it should be set to ssh2...

---

### Post by nnpoop on 2007-07-10
i just downloaded nmap for windows and ran nmap -sV 192.168.0.101

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-07-10 21:29 Eastern Daylight
Time
All 1697 scanned ports on 192.168.0.101 are filtered
MAC Address: *************** (Asustek Computer)

Service detection performed. Please report any incorrect results at [http://insec](http://insec)
ure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 48.719 seconds

Dunno why... I remember unsuccessfully attempting to setup shared folders on ubuntu, and changing some networking setting. Don't remember which ones, but could that have affected this?

---

### Post by KyleBrandt on 2007-07-10
> **nnpoop said:**
> i just downloaded nmap for windows and ran nmap -sV 192.168.0.101

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-07-10 21:29 Eastern Daylight
Time
All 1697 scanned ports on 192.168.0.101 are filtered
MAC Address: *************** (Asustek Computer)

Service detection performed. Please report any incorrect results at [http://insec](http://insec)
ure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 48.719 seconds

Dunno why... I remember unsuccessfully attempting to setup shared folders on ubuntu, and changing some networking setting. Don't remember which ones, but could that have affected this?

Sorry I am not really sure...  It seems to me somewhere along the line the port is being blocked.  If all your firewalls are off on windows, it would have to be either the router or the linux box.  You are not running something like firestarter on your ubuntu box are you?  What kind of router do you have?

---

### Post by Mr. C. on 2007-07-11
Show the output from:
```

iptables --list
grep ListenAddress /etc/ssh/sshd_config
```

MrC

---

