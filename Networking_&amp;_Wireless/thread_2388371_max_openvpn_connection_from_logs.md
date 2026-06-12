---
title: "max openvpn connection from logs?"
date: 2018-04-01
forum: Networking &amp; Wireless
---

### Post by jj4 on 2018-04-01
Is there a way I can find the max number of connections per day or total to my openvpn server?
not sure how to grep the logs for that...

---

### Post by #&amp;thj^% on 2018-04-01
Here is good place for various stats for server's: [https://www.blackmoreops.com/2014/09/25/find-number-of-unique-ips-active-connections-to-web-server/](https://www.blackmoreops.com/2014/09/25/find-number-of-unique-ips-active-connections-to-web-server/) 
I set a friends up with the below.
Show all active connections to Web server &#8211; sorted and unique

Now the output contains only foreign IP addresses. We now need to sort them, and then pipe it to uniq command so that we are left with unique foreign IP in a sorted manner. I also want uniq command to count the number of connections per IP.
```

netstat -antu | grep :80 | grep -v LISTEN | awk '{print $5}' | cut -d: -f1 | sort | uniq -c
```

"uniq -c" will count total number of connections per IP.
Hope this is useful.

---

### Post by jj4 on 2018-04-01
this is current connections I thinkÉ I need connections over a number of days

---

### Post by #&amp;thj^% on 2018-04-01
Picky Picky  :p Well I would add a counter then.

---

### Post by jj4 on 2018-04-01
Just realised, the above is for a webserver on port 80 also.
I meant I was trying to grep through the logs to see who had connected, on which day and the total number per day.
I need to grep the log and group by the day (stripping off the times), and then count the users.

---

### Post by SeijiSensei on 2018-04-02
You could use an iptables logging rule that monitors the port(s) in use.

Suppose you're using port 1194. Then

```
/sbin/iptables -I INPUT -p tcp --dport 1194 -j LOG --log-prefix vpn_tcp
/sbin/iptables -I INPUT -p udp --dport 1194 -j LOG --log-prefix vpn_udp

```

---

### Post by jj4 on 2018-04-02
I think all the data is in /var/log/openvpn.log already, just need to grep it somehow.
The iptables rule above will pick up every single port request on 1194 won't it?

---

### Post by slickymaster on 2018-04-02
Thread moved to **Networking & Wireless** for a better fit

---

### Post by #&amp;thj^% on 2018-04-02
What you need is very complex (Meaning not a easy to do), so just offering some ideas to help.
And if all else fails you could simply ask for help here: [https://forums.openvpn.net/viewtopic.php?t=20742](https://forums.openvpn.net/viewtopic.php?t=20742)
All the below is just for idea's, in hopes you can figure out what you need. ;)
"If" you are using the network manager plugin (network-manager-openvpn), look into /var/log/syslog

This should give you the last logs of openvpn:  (I know this is not what is ideal for your needs)

```
grep VPN /var/log/syslog
```

Connection details are to be found in "/etc/openvpn/"

By default, in most distros, OpenVPN log output goes to the syslog, which is usually again in /var/log/syslog

Maybe Important informtion.
**_However, your config files can set the logfile location explicitly, e.g.:_**

```
log-append /var/log/openvpn.log
```

This works for both OpenVPN clients and servers. OpenVPN config files are usually located in /etc/openvpn and usually named *.conf. server.conf is canonical; client config filenames are usually like <client name/>.conf.

I know just a plain answer would be better, but this is the best I can offer.

Good Luck, and maybe update this thread if you find a suitable solution. I know I would be very interested.:)
Regards

---

### Post by SeijiSensei on 2018-04-03
> By default, in most distros, OpenVPN log output goes to the syslog, which is usually again in /var/log/syslog.

iptables uses the "kern" syslog "[facility]("https://wiki.gentoo.org/wiki/Rsyslog#Facility")." By default this goes to syslog, but you can direct this output to a separate file by editing rsyslog.conf.

> **jj4 said:**
> I think all the data is in /var/log/openvpn.log already, just need to grep it somehow.
The iptables rule above will pick up every single port request on 1194 won't it?

Yes, but you can use the "state" parameters to log only initial requests:

```

/sbin/iptables -I INPUT -p tcp --dport 1194 -m state --state NEW -j LOG --log-prefix vpn_tcp
/sbin/iptables -I INPUT -p udp --dport 1194 -m state --state NEW -j LOG --log-prefix vpn_udp

```

I don't use this in practice, so I can't vouch for the accuracy of those commands, but I believe they are correct.

---

