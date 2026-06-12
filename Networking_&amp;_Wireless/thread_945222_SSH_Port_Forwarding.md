---
title: "SSH Port Forwarding"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by Sutur on 2008-10-12
Hi.
I've been having a lot of trouble over the last few days trying to get SSH working so I can access and operate my computer from work.
I've been looking at a lot of previous posts and learnt a great deal, but I'm stumpted at this point.
SSH client & server is installed.
The chosen port 1234 is listed in /etc/ssh/sshd_config:
```
Port 1234
```
Iptables has port 1234 allowed:```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1234
ACCEPT     udp  --  anywhere             anywhere            udp dpt:1234

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1234
ACCEPT     udp  --  anywhere             anywhere            udp dpt:1234

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
```

I have also followed a guide to set up port forwarding on my router, and I believe I have that set up correctly.

Now here's the problem.
```

sutur@muspell:~$ nmap -p 1234 localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-10-12 17:03 EST
Interesting ports on localhost (127.0.0.1):
PORT     STATE SERVICE
1234/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.084 seconds
```

```
sutur@muspell:~$ nmap -p 1234 210.80.x.x

Starting Nmap 4.53 ( http://insecure.org ) at 2008-10-12 17:03 EST
Interesting ports on adsl1-melb-171.static.spacelink.com.au (210.80.x.x):
PORT     STATE  SERVICE
1234/tcp closed unknown

Nmap done: 1 IP address (1 host up) scanned in 0.108 seconds
```

Localhost reports the port 1234 open, but my IP doesn't.
I'm sure the answer is staring me in the face, but after the 12th hour of trying to see it, I've given up and come here :-)

Thanks in advance!

---

### Post by Sutur on 2008-10-12
bump

---

### Post by kevdog on 2008-10-12
What you are testing are two different things.  Localhost refers to the computer that the ssh server is running upon.  Scanning via IP address is really referring to your router.  You need to make sure that for example the firewall on the router is either inactivated or is configured for your selected port.  You also need to make sure that your router is configured for port forwarding.

---

### Post by Sutur on 2008-10-12
On the router, I disabled the firewall completely, and port 1234 is being forwarded, what else could it be?

---

### Post by kevdog on 2008-10-12
If the router's firewall is turned off and the default firewall policy is accept (should be however you need to confirm this), then everything should work.

---

### Post by Sutur on 2008-10-12
Perhaps it's the router. It's got a lot of bad publicity over the years. 

D-Link DSL-G604T: ******* **junk**.

---

### Post by kevdog on 2008-10-12
Hmm, that would be strange if it was.  Can you set up any other service behind the router such as a ssh server on port 22 or ftp server on port 21?

---

### Post by Sutur on 2008-10-14
Nope. I can't even access the router's configuration panel from the Internet despite the function being enabled.

Do you reckon it's a dud?

---

### Post by dmizer on 2008-10-14
Are you testing from inside your network or outside your network?

Testing to your external ip (210.80.x.x) will not work from within your local network (when you have an ip of 192.168.x.x)

---

### Post by Sutur on 2008-10-15
Was testing it outside the network.

Gave up on it though, too much effort not enough reward.

Thank you all for the helpful suggestions :)

---

### Post by sab0tage on 2008-10-20
> **dmizer said:**
> Are you testing from inside your network or outside your network?

Testing to your external ip (210.80.x.x) will not work from within your local network (when you have an ip of 192.168.x.x)

Thanks for this information. I worked all day trying to access my server, thinking I was doing something wrong - turns out what you said was the answer. I logged into my webhost via ssh and then into my server, and it worked!

Is there a technical explanation as to why Testing to your external ip (210.80.x.x) from within your local network doesnt work?

---

### Post by kevdog on 2008-10-20
With some routers you can do this -- ie Linksys, with other you can not - ie DLink.  I have no idea of the explanation.

---

### Post by dmizer on 2008-10-20
> **kevdog said:**
> I have no idea of the explanation.

Many consumer end routers (including many Linksys routers) are not able to handle looping between internal and external networks. This is (at least in part) due to how the hardware firewall separates the internal network from the external network.

Here is a more detailed explanation with work around: [http://www.dyndns.com/support/kb/loopback_connections.html](http://www.dyndns.com/support/kb/loopback_connections.html)

Edit:
You may also look through your router settings page, as you may be able to enable loopback routing (sometimes it's simply not enabled by default as most people don't need it).

---

### Post by Sutur on 2009-04-28
Coming back to my original problem from ages ago.

Same issue as before, giving it a second shot.

nmap reveals localhost port 1234 is OPEN for SSH.
nmap reveals WAN IP port 22 is OPEN for SSH.
nmap reveals WAN IP port 1234 is CLOSED for SSH.

So by elimination, the culprit is the bridge between the router and the computer.

**In attempting to SSH via port 1234 to my WAN IP, my router is failing to bridge that connection to the computer with the SSH server on it.**

**[COLOR="DarkRed"]It's been over six months! How do I fix this?[/COLOR]**

---

### Post by Sutur on 2009-04-28
Bumping.

---

### Post by dmizer on 2009-04-28
Please post the output of:
```
sudo iptables -L
```

---

### Post by Sutur on 2009-04-29
> **dmizer said:**
> Please post the output of:
```
sudo iptables -L
```

I'm sorry I don't have the solution for everyone else's reference, but I did get it working.

I know in essence what I did was ensure that Xubuntu configured my IP address as static (NOT DHCP).
I then forwarded my chosen port (which I named 1234 in the forums for security purposes) in the router's configuration panel.
As a previous post mentioned, you cannot test whether the port is open from your own LAN, and this was the most vital piece of information in fixing the issue, since I may have had it working ages ago without knowing it.

[FONT="Arial Black"][COLOR="DarkRed"]SO!

If you've come here to fix a similar issue, make sure you heed the above, and use a web-based SSH client to test your settings...not on your own LAN :-)[/COLOR][/FONT]

Thanks to all ;-)

---

