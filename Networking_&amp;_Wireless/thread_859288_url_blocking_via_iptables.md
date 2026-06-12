---
title: "url blocking via iptables"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by Mr.Jkate on 2008-07-14
I just executed following commands on my command prompts.
iptables -I INPUT 1 -p tcp --dport 80 -m string --string "linuxhq.com" --algo kmp -j DROP
iptables -I INPUT 1 -p tcp --dport 80 -m string --string "vmware-server.com" --algo kmp -j DROP

Then I executed following command. 
root@test-desktop:/home/test# iptables -L
Chain INPUT (policy ACCEPT)
target prot opt source destination 
DROP tcp -- anywhere anywhere tcp dpt:www STRING match "vmware-server.com" ALGO name kmp TO 65535
DROP tcp -- anywhere anywhere tcp dpt:www STRING match "linuxhq.com" ALGO name kmp TO 65535

Chain FORWARD (policy ACCEPT)
target prot opt source destination 

Chain OUTPUT (policy ACCEPT)
target prot opt source destination 
root@test-desktop:/home/test# 

When I tried to access linuxhq.com via browser, I could access the site. 
Any body has any idea by adding rules to iptable did not worked ?

---

### Post by deufrai on 2008-07-22
You try to block requests that go *out* of your network, so don't you think those rules should rather be added to the OUTPUT chain ?

---

### Post by kung fu buntu on 2008-08-18
I am also searching for a solution to my problem (block URLs matching an expression with reverse lookup) and haven't found the perfect solution so far :(

Anyway, as for your question, google led me to:
iptables -I OUTPUT -p tcp --dport 80 -m string --string "linuxhq.com" --algo kmp -j DROP
iptables -I OUTPUT -p tcp --dport 80 -m string --string "vmware-server.com" --algo kmp -j DROP

I don't know if it works on not.

What I would like to know is if it's possible to automatically do ip blocking on those URLs.
The above rule will block linuxhq.com, but what if I ping/dig it and then use the ip address instead? There goes the master plan... :(
Is it possible to automatically do reverse lookup blocking with iptables?

Another problem with this is that it works at a domain level, that is, it doesn't support specific sites in a domain.

EDIT: after using the string module I don't have a very good impression of it... it doesn't work very well :(  At least for URL blocking (not all the domain)... sometimes it works, sometimes it doesn't :(

---

### Post by SpaceTeddy on 2008-08-19
isn't that what transparent proxies are for ? i have never setup something like this, but usually you would block there... using iptables for this seems wrong - as iptables should only work ipbased and does not care about hostnames... 

just an idea - maybe this is garbage...

---

### Post by azrazr on 2010-09-27
Check the firewall status.
if your firewall is on the your rules can't affect!

---

### Post by SeijiSensei on 2010-09-27
> **SpaceTeddy said:**
> isn't that what transparent proxies are for ? i have never setup something like this, but usually you would block there... using iptables for this seems wrong - as iptables should only work ipbased and does not care about hostnames... 

just an idea - maybe this is garbage...

No, not at all.  I have exactly this setup running at a couple of clients' sites.  Here's how it works:

First, I install [Squid]("http://www.squid-cache.org/") on the firewall to proxy HTTP requests.  Next, I add a rule to iptables like this:

```

iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 -s 10.0.0.0/8 --destination-port 80

```

replacing 10.0.0.0/8 with your own network's address.

This rule intercepts outbound requests to port 80 and pushes them into Squid though its default port 3128.

In Squid, you can permit or enable access to remote resouces by a wide range of characteristics beyond simple IP and hostname matching like mimetypes and file extensions.  You'll also get a log of every machine's HTTP request history.  You can also install the [Squid Analysis Report Generator]("http://sarg.sourceforge.net/sarg.php") to produce summaries of these logs.

One important use for this approach is blocking access to executable programs out on the Web.  Usually we only let admins download .exe's, .cab's, and similar files, but we do permit general access to places like windowsupdate.com and the antivirus provider's site to enable the workstations to stay current.

The beauty of this is that is a "transparent" proxy.  You could accomplish the same thing by installing Squid, then configuring all the browsers to use it.  It's obviously much simpler to manage this on the firewall.

---

### Post by ipernar on 2010-09-27
I have another question... I use

iptables -A OUTPUT -d 146.82.205.211  -j DROP

and it blocks particular IP, but how do I block whole range
146.82.205.0 -- 146.82.205.500

Is there simple way to do that? thanks in advance

---

### Post by tienhien on 2010-11-23
To block whole range, you need an iprange module.
iptables -A OUTPUT -m iprange --dst-range  146.82.205.0-146.82.205.500 -j DROP

---

