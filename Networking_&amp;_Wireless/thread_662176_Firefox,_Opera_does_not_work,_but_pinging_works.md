---
title: "Firefox, Opera does not work, but pinging works"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by domer on 2008-01-08
I recently changed my ISP and now I cannot connect to the internet using Firefox or Opera and Gaim Internet Messenger does not work either. I am using Ubuntu Dapper on this machine. Everything works fine using Windows. 

***This is the weird part***

When I open terminal and type "**ping [www.yahoo.com](www.yahoo.com)**" or any other server, I get 0% data loss and Weather Report works too. I have tried releasing/renewing my ip address using the following commands, 

**sudo dhclient -r** (for release) 
**sudo dhclient **(for renew)

but still cannot view any webpage or use Gaim (not that I can't live without gaim). 

ssh does not work either. 

Weird, huh? 

Can anybody please help. 

Thank you.

---

### Post by guren on 2008-01-08
> **domer said:**
> I recently changed my ISP and now I cannot connect to the internet using Firefox or Opera and Gaim Internet Messenger does not work either. I am using Ubuntu Dapper on this machine. Everything works fine using Windows. 

***This is the weird part***

When I open terminal and type "**ping [www.yahoo.com](www.yahoo.com)**" or any other server, I get 0% data loss and Weather Report works too. I have tried releasing/renewing my ip address using the following commands, 

**sudo dhclient -r** (for release) 
**sudo dhclient **(for renew)

but still cannot view any webpage or use Gaim (not that I can't live without gaim). 

ssh does not work either. 

Weird, huh? 

Can anybody please help. 

Thank you.

do you have proxies? i'm guessing that your proxy was not enabled for your environment's proxy settings and your terminal was set to the right proxy with HTTP_PROXY. Or maybe it could be the other way around, your proxy was set **wrongly** in your environment's proxy settings and was not set in the terminal, therefore leaving your new ISP proxy-less which makes it work.

---

### Post by domer on 2008-01-08
Hi,

Thanks for your reply. In Firefox, I went Advanced --> Settings (for Connections) and it has "Direct connection to the Internet" set. 

It's a radio button, so everything else is grayed out.

---

### Post by guren on 2008-01-08
Hi you may also have to do that not only in firefox.
If you're using Gnome, there is Gnome Network Proxy Settings under System -> Preferences -> Network proxy

---

### Post by domer on 2008-01-08
This is how the Network Proxy Settings look like (please see attachment).

And when I typed "ping www.google.com" i got the following

chatterjee@maverick:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (64.233.167.147) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=1 ttl=244 time=24.9 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=2 ttl=244 time=24.9 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=3 ttl=244 time=26.5 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=4 ttl=244 time=25.1 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=5 ttl=244 time=24.7 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=6 ttl=244 time=24.7 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=7 ttl=244 time=24.9 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=8 ttl=244 time=24.5 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=9 ttl=244 time=24.5 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=10 ttl=244 time=24.4 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=11 ttl=244 time=24.7 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=12 ttl=244 time=24.7 ms
64 bytes from [www.google.com](www.google.com) (64.233.167.147): icmp_seq=13 ttl=244 time=24.6 ms
--- [www.l.google.com](www.l.google.com) ping statistics ---
13 packets transmitted, 13 received, 0% packet loss, time 12009ms
rtt min/avg/max/mdev = 24.463/24.895/26.557/0.560 ms

---

### Post by sonofusion82 on 2008-01-09
how about trying wget?
for me, i would get something like:

[FONT="Courier New"]$ wget [http://www.google.com/](http://www.google.com/)
--21:57:10--  [http://www.google.com/](http://www.google.com/)
           => `index.html.1'
Resolving [www.google.com](www.google.com)... 64.233.189.104, 64.233.189.99
Connecting to www.google.com|64.233.189.104|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.google.com.my/](http://www.google.com.my/) [following]
--21:57:10--  [http://www.google.com.my/](http://www.google.com.my/)
           => `index.html.1'
Resolving [www.google.com.my](www.google.com.my)... 64.233.189.104, 64.233.189.99
Reusing existing connection to [www.google.com:80](www.google.com:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 5,341         --.--K/s

21:57:10 (70.77 KB/s) - `index.html.1' saved [5341][/FONT]

also, perhaps you can try to check/compare the proxy settings in Windows too.

---

### Post by domer on 2008-01-11
Hi, 
Sorry for the delay is responding. I tried **wget [www.google.com](www.google.com)** and i get no response. pinging still works with 0% packet loss.

---

### Post by guren on 2008-01-11
what about other sites? can you try ping and wget

---

### Post by domer on 2008-01-12
Same situation :(
 
ping works, wget does not. I ran the live cds of Feisty Fawn and Dapper, internet works fine in both cases. 

I know this will be a loser's way out, but since I do not have much information on my partition, i would do a fresh install.

---

### Post by StooJ on 2008-01-13
> **domer said:**
> 
I know this will be a loser's way out, but since I do not have much information on my partition, i would do a fresh install.

Pity. I have a friend in a similar situation and would have been keen to see some more ideas :(

---

### Post by edm1 on 2008-01-13
Sounds like a DNS resolution problem. Try connecting to [64.233.167.147]("http://64.233.167.147/").

---

### Post by sqrt2 on 2008-01-13
Since ping can resolve the hostname, I don't think it's DNS.

It'd be interesting to know what firefox and wget actually say when you try to fetch a resource from the web. All we know is that ICMP works, but HTTP doesn't.

Since connectivity is protocol specific, the problem could also be some strange packet filter rule. What does "sudo iptables -vnL" say?

---

### Post by domer on 2008-01-13
Sorry to disrupt the flow of information exchange here, but I had to reinstall Ubuntu (got Feisty this time) as I needed my system to be up and running immediately.

---

### Post by petrisyv on 2008-01-16
Help is still appreciated for I have exactly the same problem. I can ping any ip or domain name (both lan & internet), but can't connect in any way. I've tried everything, http, ftp, ssh, irc, you name it. I can also ping the computer having the problem, but connecting to it still results in timeout. I will post what "sudo iptables -vnL" says as soon as I can find an usb memory or some other way to copy the output to a machine with a working connection (I'm too lazy to copy all the lines by hand). I was doing a lot of things while the problem occured, one of them was configuring vpn and I think that was what messed up with something important. Is there any way to reset all the networking, firewall, etc. settings?

---

### Post by webceo on 2008-05-04
I too have a very similar problem. 

Check this :
[http://ubuntuforums.org/showthread.php?t=590934](http://ubuntuforums.org/showthread.php?t=590934)

Can anyone please help

---

