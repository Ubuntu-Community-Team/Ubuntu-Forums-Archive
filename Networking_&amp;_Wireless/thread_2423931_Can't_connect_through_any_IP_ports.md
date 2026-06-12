---
title: "Can't connect through any IP ports"
date: 2019-07-31
forum: Networking &amp; Wireless
---

### Post by molipha2 on 2019-07-31
Hi,

I've got this very strange problem. I have 3 computers: 10.0.0.1, 2 & 3. 

10.0.0.1 cannot connect to 10.0.0.2 through port 5984
10.0.0.1 can connect to 10.0.0.3 through port 5984

10.0.0.2 can connect to 10.0.0.1 through port 5984
10.0.0.2 can connect to 10.0.0.3 through port 5984

10.0.0.3 can connect to 10.0.0.1 through port 5984
10.0.0.3 cannot connect to 10.0.0.2 through port 5984

So the problem seems to be with 10.0.0.2 blocking port connections, however, everyone can ping each other no problem. (In the title I say all ports because I couldn't get 2 & 3 to talk to each other using sshfs and I tried various ports to no avail.)

If anyone can provide some hints how to troubleshoot the situation I'd be grateful.

---

### Post by uRock on 2019-07-31
Hello and welcome to the forums.

Are all three systems running ubuntu or another flavor of Linux? Have you edited their firewalls?

---

### Post by TheFu on 2019-07-31
Why would you believe that 5984 should be available?  Perhaps that is an important detail for the problem statement?



Perhaps?

---

### Post by molipha2 on 2019-08-01
Hi uRock. All three on lubuntu 18.04. There are no firewalls.

---

### Post by molipha2 on 2019-08-01
> **TheFu said:**
> Why would you believe that 5984 should be available?  Perhaps that is an important detail for the problem statement?



Perhaps?

Hi [COLOR=#000000]TheFu, 

Yes, it should be available.[/COLOR]

---

### Post by TheFu on 2019-08-01
> **molipha2 said:**
> Hi [COLOR=#000000]TheFu, 

Yes, it should be available.[/COLOR]

Why?  Prove it.  It isn't like that port is standard for any protocol.  Or did you solve the problem?

We can't read your mind.  Please do assume we magically know what you mean.

---

### Post by molipha2 on 2019-08-01
Hi TheFu. 

>>>[COLOR=#000000]Why? Prove it. It isn't like that port is standard for any protocol. Or did you solve the problem?
I've used that same port for years for this application as have countless other individuals and institutions since it is the default port for couchdb. Plus, it works fine on 10.0.0.1 & 3. Just not on 2 when connecting with other computers. It actually works fine as a localhost port. Besides, I tried many different ports trying to get 2 & 3 to connect using sshfs to no avail. The problem remains. Many thanks for your response.[/COLOR]

---

### Post by TheFu on 2019-08-01
So ... how should anyone know you are using couchdb?  There wasn't any mention of that until post #7.
Specific ports have default services where people expect to see them. If you don't name the daemon that is listening on the port, nobody can help.  

I certainly wouldn't have replied at all for any couchdb issue, since I've barely heard the name before.

Nobody here can read your mind.  Good luck. I'm out.

---

### Post by uRock on 2019-08-01
Install and open GUFW. Enable it, then look at Report. This will show you the active ports. Create a rule allowing that port. Are you doing this for a Udemy course?

---

### Post by molipha2 on 2019-08-01
Hi uRock. Thanks for the tip, I'll give it a try. Like I said, the weird thing is the port is active since localhost can use it. I just can't communicate to 2 from other machines on any port. 

>>> [COLOR=#000000]Are you doing this for a Udemy course?[/COLOR]
No, this is an internal app I've developed over the course of many years that uses couchdb as storage.[COLOR=#000000]
[/COLOR]

---

### Post by The Cog on 2019-08-01
Installing a firewall won't help - it'll just complicate things.
If you want to see what ports are listening, use:
```
sudo ss -lntp
```
but the output is ugly - looks better if you do
```
sudo ss -lntp | cat
```

Once you know the port is open, you can try to see if it's blocked by a firewall by trying to connect form elsewhere:
```
nc -vz 10.0.0.2 5984
```
Connection Refused means the firewall let the request through (unless the firewall is using REJECT instead of DROP, which is unusual). Timeout means the server didn't respond, which usually means a firewall dropped the request.

---

### Post by molipha2 on 2019-08-01
Hi uRock. Thanks. Was worth a try but no success.

---

### Post by molipha2 on 2019-08-01
As I recall, this was working fine at one point. However I had to downgrade from 19.04 to 18.04 and since then the issue arose. However, since I wiped out the existing data on the hard drive in doing the downgrade, I don't think it can be a case of a lingering setting causing problems.

---

### Post by molipha2 on 2019-08-01
Hi Woof. Thanks for the help. 

Running ss on 10.0.0.2 shows it listening on 127.0.0.1:5984 which would be the local couchdb instance. Otherwise, no mention of the port which I assume shows everything as normal. 

Running [COLOR=#000000][FONT=&quot]nc -vz 10.0.0.2 5984[/FONT][/COLOR] on 10.0.0.3, returns "nc: connect to 10.0.0.2 port 5984 (tcp) failed: Connection refused".

---

### Post by uRock on 2019-08-01
> **The Cog said:**
> Installing a firewall won't help - it'll just complicate things.
<snip>

It wasn't a matter of installing a firewall. It was to have a GUI to show open ports. Besides, it's "uncomplicated" lol.

---

### Post by The Cog on 2019-08-01
> **molipha2 said:**
> Hi Woof. Thanks for the help. 

Running ss on 10.0.0.2 shows it **[COLOR="#FF0000"]listening on 127.0.0.1:5984[/COLOR]** which would be the local couchdb instance. Otherwise, no mention of the port which I assume shows everything as normal. 

Running [COLOR=#000000][FONT=&quot]nc -vz 10.0.0.2 5984[/FONT][/COLOR] on 10.0.0.3, returns "nc: connect to 10.0.0.2 port 5984 (tcp) failed: Connection refused".
It's only listening on its loopback address, which is unreachable from outside the machine. It's not listening on 10.0.0.2 (or 0.0.0.0 which means all addresses). So the connection is being refused because there's no application listening on that address.

This is almost certainly a configuration setting in couchdb. I think it's a security thing - it defaults to a setting where it's not accessible from outside before the admin has had a chance to configure it properly.

[COLOR="#555"]@uRock: The firewall GUI won't tell you whether the PC is listening on a port or not, it will only tell you whether or not firewall is blocking access to that port. And if it's blocking access then you can't even test from outside whether the OS accepting or rejecting connections. In the same vein of course, ss (or netstat) will only tell you if an application is listening or not (port open or closed). It will not tell you if a firewall is interfering with its communications.
[/COLOR]
EDIT:
Correction to @uRock paragraph above: The gufw GUI does indeed show you which ports are actually listening. Press the report button to see the list. The list changes as listening applications are started and stopped. My apologies to uRock and thanks for educating me. I still think it's a complicated way of finding out which ports are listening though.

---

### Post by molipha2 on 2019-08-01
Hi Cog. 

Yes, you are absolutely right. Thanks so much. I really appreciate your assistance. This is now resolved.

---

