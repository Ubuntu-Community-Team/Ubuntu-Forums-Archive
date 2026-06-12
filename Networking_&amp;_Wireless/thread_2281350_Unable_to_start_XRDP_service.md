---
title: "Unable to start XRDP service"
date: 2015-06-06
forum: Networking &amp; Wireless
---

### Post by peter1897 on 2015-06-06
I have remote server with Ubuntu 14.04 to which i have access only through ssh from Cygwin. I want to create remote desktop connection from my Windows 7 machine to the remote Ubuntu server. I installed xrdp service on ubuntu server but when i check the status of the service i get this output:

```
ubuntu@ip-xx-xx-xx-xx:~$ service xrdp status
 * Checking status of Remote Desktop Protocol server xrdp                                                              [ OK ]
 * Checking status of RDP Session Manager sesman                                                                       [fail] 
```

I don't know what exactly the second entry mean but it is failing to start. Any idea why?

Also if i check the listening ports with the command **nmap localhost** the ports on which xrdp is listening are not listed.

And if i use RDP from Windows 7 and enter the IP of the ubuntu server it is not able to access it.

---

### Post by peter1897 on 2015-06-06
I found that the xrdp service is running but with other name **ms-wbt-server** and is listening on port 3389. But the **sesman** service is not running. These are the open ports:

```
ubuntu@ip-xx-xx-xx-xx:~$ nmap localhost

Starting Nmap 6.40 ( [http://nmap.org](http://nmap.org) ) at 2015-06-06 14:32 UTC
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00026s latency).
Not shown: 996 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
3389/tcp open  ms-wbt-server
```

Nmap done: 1 IP address (1 host up) scanned in 0.05 seconds

If i check the port 3389 from my Windows 7 machine with telnet it says that it can't connect to remote host:

```
$ telnet xx.xx.xx.xx 3389
Trying xx.xx.xx.xx...
telnet: Unable to connect to remote host: Connection timed out
```

And i don't have any rules set in the iptables.

Any idea why the port is not reachable? What could be blocking it?

---

