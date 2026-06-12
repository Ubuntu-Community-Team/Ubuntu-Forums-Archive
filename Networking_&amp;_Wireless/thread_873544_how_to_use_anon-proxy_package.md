---
title: "how to use anon-proxy package"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by NotSoInnocent on 2008-07-29
Hi  :)

I used the synaptic package manager to install the anon-proxy (version 00.05.38+20080123-1) package. According to the description it should install the JAP client. 

I can start the program from the terminal using: 
sudo /etc/init.d/anon-proxy start

and I get the following output:

 * Starting anon-proxy mix 


However, when I change the proxy settings in my firefox to localhost:4001
I receive this error:


Proxy Server Refused Connection
Firefox is configured to use a proxy server that is refusing connections.
The browser is configured to use a proxy server, but the proxy refused a connection.

    * Is the browser's proxy configuration correct? Check the settings and try again.
    * Does the proxy service allow connections from this network?
    * Still having trouble? Consult your network administrator or Internet provider for assistance.


Also, I don't see the port 4001 when I run a port scan on localhost.I don't know if this is a firewall problem, but I tried to change my AP settings to the minimum security possible, but nothing changed. 
I also have some other open ports, namely 631, 8118, and 9050.

I think the JAP also has a user interface, but I don't know how to get it. I can't install the package manually from the JAP website, because it is blocked here. :(

Please help. Thank you.

---

### Post by NotSoInnocent on 2008-07-29
I tried using tor privoxy too, but I received a forwarding error. Any suggestions??

---

### Post by knedlyk on 2008-08-25
After some workaround I finally started anon-proxy on 8.04 hardy. Here is my advices.
First of all try to start anon-proxy server:
```
sudo /etc/init.d/anon-proxy restart
```
Next make sure it is running:
```
ps xuaw | grep mix
```
You should see something like 
```
105      10880  0.0  0.3  21704  2404 ?        Ss   01:19   0:01 /usr/sbin/mix -a -d -j -r /var/run/anon-proxy/mix.pid -n mix.inf.tu-dresden.de:443 -p 4001
```
If not, do the following: 
```
sudo nano /etc/init.d/anon-proxy
```
and add these two lines below the line "PIDFILE=/var/run/anon-proxy/mix.pid":
```
mkdir /var/run/anon-proxy
chown anon-proxy:nogroup /var/run/anon-proxy
```

That's actually all. Then restart anon-proxy and it must work. I discovered that daemon doesn't create /var/run/anon-proxy directory with the process pid file and finally doesn't start.
Hope it will help.

---

### Post by mkrahmeh on 2008-09-09
i think changing the port number in the firefox settings is not enough..
dont we need to change the HTTP proxy too, to be through jap client..??

---

### Post by airtonix on 2008-10-09
Jap has a backdoor created to satisfy a german court of law.

Tor's strength is that it truly does obfuscate the point of origin....for a time and only against assailants who do not persist with profiling methods.

There is however a simple way to extend this timeframe of "anon-saftey". 

It seems that unless you are encrypting the traffic from you to your target (meaning the entire trip from your machine, through the tor network, and out the other end to your target)...profiling methods can and will indentify you from data captured over a period of time.

More info here: 
[http://www.outpostfirewall.com/forum/showthread.php?t=16458](http://www.outpostfirewall.com/forum/showthread.php?t=16458)

---

