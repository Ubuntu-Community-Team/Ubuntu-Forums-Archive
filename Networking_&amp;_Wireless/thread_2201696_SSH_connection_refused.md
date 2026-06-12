---
title: "SSH connection refused"
date: 2014-01-25
forum: Networking &amp; Wireless
---

### Post by joe53 on 2014-01-25
Yesterday I set up ssh on my system, I was able to connect to ssh on the system via localhost, via network from my Android phone,  and via Internet from my Android phone. I shut down my computer for the night and today I am unable to connect via ssh at all,  even on the system using 
ssh hostname@localhost:22
i just receive a connection refused error

---

### Post by Iowan on 2014-01-25
Verify that the SSH server is running: **ps -ef | grep sshd**

---

### Post by joe53 on 2014-01-25
Command returns 
"Hostname 2677 2467 0 13:37 pts/2 00:00:00 grep --color auto=sshd"

Sshd is red

---

### Post by Iowan on 2014-01-25
Looks like the server is not running. This looks helpful:
[http://askubuntu.com/questions/103889/how-do-you-stop-restart-ssh](http://askubuntu.com/questions/103889/how-do-you-stop-restart-ssh)
I'm more familiar with the **sudo service ssh start** method...

---

### Post by joe53 on 2014-01-25
Tried 
Sudo service ssh start 
sudo /etc/init.d/ssh stop
sudo /etc/init.d/ssh start
Sudo start ssh. 

Start ssh returned 
Ssh start/pre-start, process 2922 

"ps -ef | grep sshd" returns same results as last time

---

### Post by joe53 on 2014-01-25
Yesterday I set up ssh on my system, I was able to connect to ssh on the system via localhost, via network from my Android phone, and via Internet from my Android phone. I shut down my computer for the night and today I am unable to connect via ssh at all, even on the system using
    ssh hostname@localhost:22
    i just receive a connection refused error. 


"ps -ef | grep sshd" returns 

"Hostname 2677 2467 0 13:37 pts/2 00:00:00 grep --color auto=sshd"

Suggesting that the service is not running. I Tried
Sudo service ssh start
sudo /etc/init.d/ssh stop
sudo /etc/init.d/ssh start
Sudo start ssh.

Start ssh returned
Ssh start/pre-start, process 2922

"ps -ef | grep sshd" returns same results as last time

Any idea what seems to be the issue?

---

### Post by Iowan on 2014-01-25
Threads merged. 

From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Do not cross post, or post the same thing in multiple locations.
You can use the "Report Post" (at the bottom-left of each post) to request a thread to be moved. :)

You can try the **ps -ef ** without the **| grep sshd** and look through the listing...
If the SSH daemon is running, there should be a line similar to:
 ```
root      2922     1  0  2013 ?        00:00:00 /usr/sbin/sshd
```
(I presume you didn't actually use the caps and/or period when you entered the lines).
The localhost access is only from the "local" machine - the server itself...

---

### Post by steeldriver on 2014-01-25
This is a bit left field but can you post the output of the command

```
ls -l /dev/null
```

---

### Post by joe53 on 2014-01-25
> **Iowan said:**
> Threads merged. 

From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):

You can use the "Report Post" (at the bottom-left of each post) to request a thread to be moved. :)

Sorry, didnt mean to break the rules, posting from my phone while at work.
> **Iowan said:**
> 
You can try the **ps -ef ** without the **| grep sshd** and look through the listing...
If the SSH daemon is running, there should be a line similar to:
  	Code:
 	root      2922     1  0  2013 ?        00:00:00 /usr/sbin/sshd 
(I presume you didn't actually use the caps and/or period when you entered the lines).
The localhost access is only from the "local" machine - the server itself...

Yes, this poped up with ps -ef. Also no i didnt use the caps and periods when i enterd the commands, and i was controling the server and using localhost on the machine only.
root      6573     1  0 16:57 ?        00:00:00 /usr/sbin/sshd -D

---

### Post by joe53 on 2014-01-25
ls -l /dev/null returns: crw-rw-rw- 1 root root 1, 3 Jan 25 09:44 /dev/null

---

### Post by joe53 on 2014-01-25
ok, umm. I can now connect via localhost. Im not sure what changed, but i still cannot connect via my wireless network or over the internet from elsewhere.

Also, my internal ip has drasticly changed from 192.168.0.20 to 172.16.42.106

---

