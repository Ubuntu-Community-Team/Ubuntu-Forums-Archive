---
title: "Port in Use"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by maulakai on 2008-02-29
Hello,

I've been trying to configure my ssh to listen on port 80.  It works fine on my home network, but gives errors when I try to access it at work over the internet. 

 Examination of the auth.log shows

error: Bind to port 80 failed, Address already in use.

I've disabled the apache server, but 

nmap 127.0.0.1 

says that port 80 is open for http service

Know of a way I can manage these ports and services so that ssh can use it without a conflict?

---

### Post by Mr. C. on 2008-02-29
If the command:

```
netstat -an --tcp
```

shows port 80 in use... its in use, and you have not successfully shutdown apache.  Does ps -elf show apache running?  How did you shut apache down?  Disabling the service makes it not run at bootup.  You have to still run the /etc/init.d script with the stop option.

---

### Post by maulakai on 2008-03-01
ok so ps-elf shows apache not running.  /etc/init.d/apache2 stop confirms that it isn't running

netstat -an --tcp shows port 80 in use

when i /etc/init.d/ssh stop

the port is no longer listed

starting the service again shows it listed again, so its definately ssh using that port, but

tail /var/log/auth.log  shows

Mar  1 00:30:49 threshold sshd[9262]: Received signal 15; terminating.
Mar  1 00:31:26 threshold sshd[12638]: Server listening on :: port 80.
Mar  1 00:31:26 threshold sshd[12638]: error: Bind to port 80 on 0.0.0.0 failed: Address already in use.
Mar  1 00:31:41 threshold sshd[12649]: Bad protocol version 

Again the ssh service works from a machine on the intranet, but will throw the error  "server unexpectedly closed connection" when i try to access it over the internet, using putty

---

### Post by Mr. C. on 2008-03-01
Uncomment the 

```
[COLOR="Silver"]#ListenAddress ::[/COLOR]
[COLOR="Black"]#ListenAddress 0.0.0.0[/COLOR]

```
in /etc/ssh/sshd_config and restart the server.

[edit: pasted wrong entry; ignore gray entry]

---

### Post by maulakai on 2008-03-01
Yay!  and not Yay!

Uncommenting the line you suggested does indeed solve the error that was showing up in the log file.

Unfortunately, I still can't connect to the server remotely.

First off, what exactly did uncommenting that line do?

And secondly, any thoughts on why I'm having these connection problems?  The port is definately open and forwarded correctly.  I've even tried multiple clients, all of which give a similar error.  It's not timing out, the connection is being closed.

---

### Post by Mr. C. on 2008-03-01
I misspoke and gave you bunk.

The ListenAddress 0.0.0.0 is an IPv4 address. The other one (ListenAddress :: ) is IPv6.

Set ListenAddress 0.0.0.0 (which disables listening to IPv6) to avoid the errors in the auth.log.  Listen only on this address if your router has trouble with IPv6.

I'm able to connect just fine this way.

---

### Post by maulakai on 2008-03-01
Well I've made the change, although it's had no effect that I can tell.

I suppose the "nmap 127.0.0.1" identifies port 80 as being open and http service because port 80 is usually running a webserver, and not because it knows something I don't.

I've grep'd every config file on my hard drive that mentions port 80, but nothing seems to let this baby run on port 80

I do have my router configured with other services that run just fine, which is why I'm inclined to think the problem is somewhere in ubuntu or ssh

---

### Post by Mr. C. on 2008-03-01
Don't use nmap to inform you about the state of your system ports.  Use netstat locally.  nmap is fine for various types of probing, but it is interpreting for you, hence the http confusion.

Does your router have a port 80 webserver for the management interface (many do)?  If so, it explains why you can't access remotely.  If not....

So your netstat should show a line that looks like:
```

tcp  0  0.0.0.0:80      0.0.0.0:*    LISTEN
```

Run tcpdump, listening for any communication on port 80 (src or dst) on the SSH server machine.  Attempt a remote connection.  If you see no packets, its your router doing the blocking.

---

### Post by ghostdog74 on 2008-03-01
> **maulakai said:**
> ok so ps-elf shows apache not running.  /etc/init.d/apache2 stop confirms that it isn't running

netstat -an --tcp shows port 80 in use

when i /etc/init.d/ssh stop

the port is no longer listed

starting the service again shows it listed again, so its definately ssh using that port, but

tail /var/log/auth.log  shows

Mar  1 00:30:49 threshold sshd[9262]: Received signal 15; terminating.
Mar  1 00:31:26 threshold sshd[12638]: Server listening on :: port 80.
Mar  1 00:31:26 threshold sshd[12638]: error: Bind to port 80 on 0.0.0.0 failed: Address already in use.
Mar  1 00:31:41 threshold sshd[12649]: Bad protocol version 

Again the ssh service works from a machine on the intranet, but will throw the error  "server unexpectedly closed connection" when i try to access it over the internet, using putty

use lsof -i tcp:80 to see what application is still using it. Also, when using putty , make sure you enter the port number as 80 and not 22.

---

### Post by maulakai on 2008-03-01
wow mrc, you really know your stuff.  Thanks for your help, by the way.

I do have the line about listening on port 80 in my netstat output.  

Doing the tcpdump has caused me some problems.  i'm new to the command and cant seems to make heads or tails of it ... i'll keep playing around with it

---

### Post by Mr. C. on 2008-03-01
```
sudo tcpdump -i eth0 port 22 -s 1514
```

Change eth0 if it is not your interface - ifconfig -a will tell you.

---

### Post by maulakai on 2008-03-01
Thanks guys!

I've been able to sort out the problem, mainly due to your sharing with me the following commands:

tcpdump

lsof

To be honest, I was a complete nub.  My dyndns didn't update and I had subsequently been using out of date ip addresses to try to connect.   That makes it impossible to say at what point the actual problem was solved.

Thanks again for your help, those commands are clutch!

---

### Post by Mr. C. on 2008-03-01
And now you have new tools to use for the next time.

---

