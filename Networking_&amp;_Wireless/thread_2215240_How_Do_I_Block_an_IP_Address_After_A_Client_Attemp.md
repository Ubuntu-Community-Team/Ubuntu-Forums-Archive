---
title: "How Do I Block an IP Address After A Client Attempts to Connect To a Specific Port?"
date: 2014-04-05
forum: Networking &amp; Wireless
---

### Post by matt_p2 on 2014-04-05
Hello,
I am trying to block an IP address after a client attempts to connect to port 137.
I tried knockd with this config:
[COLOR=#333333][FONT=Helvetica][BlockAfter137]        sequence      = 137        seq_timeout = 1        command = iptables -I INPUT -s %IP% -j REJECT        tcpflags = syn

I tried debug mode, and when trying to telnet to that port from another client, I get:
[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica]Local IP: [/FONT][/COLOR][192.168.2.134]("http://192.168.1.134/")[COLOR=#333333][FONT=Helvetica]2014-03-05 12:00:27: tcp: [/FONT][/COLOR][192.168.2.129:54304]("http://192.168.1.128:54304/")[COLOR=#333333][FONT=Helvetica] -> [/FONT][/COLOR][192.168.2.134:137]("http://192.168.1.134:137/")[COLOR=#333333][FONT=Helvetica] 66 bytes2014-03-05 12:00:30: tcp: [/FONT][/COLOR][192.168.2.129:54304]("http://192.168.1.128:54304/")[COLOR=#333333][FONT=Helvetica] -> [/FONT][/COLOR][192.168.2.134:137]("http://192.168.1.134:137/")[COLOR=#333333][FONT=Helvetica] 66 bytesremoving successful knock attempt ([/FONT][/COLOR][192.168.2.12]("http://192.168.1.128/")9[COLOR=#333333][FONT=Helvetica])2014-03-05 12:00:36: tcp: [/FONT][/COLOR][192.168.2.129:54304]("http://192.168.1.128:54304/")[COLOR=#333333][FONT=Helvetica] -> [/FONT][/COLOR][192.168.2.134:137]("http://192.168.1.134:137/")[COLOR=#333333][FONT=Helvetica] 62 bytesremoving successful knock attempt ([/FONT][/COLOR][192.168.2.12]("http://192.168.1.128/")9[COLOR=#333333][FONT=Helvetica])

Any ideas?

Thanks for your time.[/FONT][/COLOR]

---

### Post by Lars Noodén on 2014-04-05
You could do it with iptables directly and not need any other tools.  There are a number of guides on port knocking, like this one:
[https://www.digitalocean.com/community/articles/how-to-configure-port-knocking-using-only-iptables-on-an-ubuntu-vps](https://www.digitalocean.com/community/articles/how-to-configure-port-knocking-using-only-iptables-on-an-ubuntu-vps)

The process could be modified heavily and greatly simplified to reject connections from the offending host once the wrong port is hit once.

---

### Post by matt_p2 on 2014-04-05
Thank you for the link. The tutorial seems to have the answer but unfortunately it is pretty complex. I'll try going through this and make it work but any additional help would be greatly appreciated.

---

### Post by ajgreeny on 2014-04-05
You can do it simply with ufw which should already be installed
```
sudo ufw deny from 207.46.232.182
``` or if you want to block the access only if it tries to use that port it will need a shell script, I think

---

### Post by matt_p2 on 2014-04-05
Thank you for your help.
What I am trying to do is only block once they attempt to connect to the port.

---

### Post by Lars Noodén on 2014-04-06
It could boil down to [two lines](http://manpages.ubuntu.com/manpages/trusty/en/man8/iptables-extensions.8.html).  Here is a guess:

```

iptables -A INPUT --match recent --name BLOCKED --rcheck --seconds 1200 -j DROP
iptables -A INPUT -p tcp -i eth0 --dport 137 --match recent --name BLOCKED --set -j REJECT

```

It's based on the example of port 139 in the manual page there but it's basically like one layer of the port knocking example.

---

### Post by Lars Noodén on 2014-04-07
Those lines would go before the check for established connections if you want to drop other active sessions:

```

iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

``` 

But probably, you'd want them after.

---

