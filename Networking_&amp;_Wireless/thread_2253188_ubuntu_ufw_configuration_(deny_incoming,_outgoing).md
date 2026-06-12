---
title: "ubuntu ufw configuration (deny incoming, outgoing) whitelist http, https"
date: 2014-11-17
forum: Networking &amp; Wireless
---

### Post by seabird22 on 2014-11-17
Need help configuring ufw: The log below shows the current status. What I am trying to accomplish is, to deny incoming and outgoing and whitelist http. Is that possible? I have read the ufw wiki but I was not able to find what I need. My knowledge of tcp ip is very limited right now. Google Chrome is the browser I use, but this is not working with firefox either.

One more thing. I deleted ufw.log. How do I get it back? 

thanks for all of the help.

```
Status: activeLogging: on (low)
Default: deny (incoming), deny (outgoing), disabled (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
80/tcp                     ALLOW IN    Anywhere
80/udp                     ALLOW IN    Anywhere
80/tcp (v6)                ALLOW IN    Anywhere (v6)
80/udp (v6)                ALLOW IN    Anywhere (v6)


80/tcp                     ALLOW OUT   Anywhere
80/udp                     ALLOW OUT   Anywhere
80/tcp (v6)                ALLOW OUT   Anywhere (v6)
80/udp (v6)                ALLOW OUT   Anywhere (v6)


mbsb@reNET:~$ sudo ufw default allow outgoing
Default outgoing policy changed to 'allow'
(be sure to update your rules accordingly)
```

---

### Post by ajgreeny on 2014-11-18
From a quick look somewhere around line 49 or 50 of **man ufw** it looks as if ```
ufw allow in http
```should do what you want.

Try ```
sudo ufw --dry-run allow in http
```which will not actually do anything with the dry-run option, but will report back the changes that would be made, to see if it does do this. I have no software firewall on my machine, so can not test it myself.

---

### Post by Lars Noodén on 2014-11-18
Do you want to allow http in or to reach external http sites yourself?  What about https?

If you  are blocking everything and then white listing a  few services, then you will also need to whitelist DNS which would be port 53 (domain) for TCP and UDP.  And ICMP would be needed as well.  For ICMP, you might have to resort to going around UFW:

[http://www.kelvinism.com/2010/09/enable-icmp-through-ufw_461.html](http://www.kelvinism.com/2010/09/enable-icmp-through-ufw_461.html)

Then regardless of how incoming connections are blocked, outgoing connections should probably be blocked with reject so that you don't have to wait for a timeout.

---

### Post by seabird22 on 2014-11-18
> **ajgreeny said:**
> From a quick look somewhere around line 49 or 50 of **man ufw** it looks as if ```
ufw allow in http
```should do what you want.Try ```
sudo ufw --dry-run allow in http
```which will not actually do anything with the dry-run option, but will report back the changes that would be made, to see if it does do this. I have no software firewall on my machine, so can not test it myself.I did see that in the wiki (allow www) and 'allowed'  it, but apparently, there is more needed. thanks for your help!

---

### Post by seabird22 on 2014-11-18
These are the changes I made but still not working. Please see below. Not sure if my DNS entries are correct as they are set only for outbound. Got ping working with before.rules change

```


Default: deny (incoming), reject (outgoing), disabled (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
80/tcp                     ALLOW IN    Anywhere
443                        ALLOW IN    Anywhere
80/tcp (v6)                ALLOW IN    Anywhere (v6)
443 (v6)                   ALLOW IN    Anywhere (v6)


53/tcp                     ALLOW OUT   Anywhere
53/udp                     ALLOW OUT   Anywhere
53/tcp (v6)                ALLOW OUT   Anywhere (v6)
53/udp (v6)                ALLOW OUT   Anywhere (v6)


```


also added in /etc/ufw/before.rules and ping is working.

```


# allow outbound icmp
-A ufw-before-output -p icmp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
-A ufw-before-output -p icmp -m state --state ESTABLISHED,RELATED -j ACCEPT


```

thanks again.

---

### Post by seabird22 on 2014-11-19
I figured out how, ( block ALL incoming, outgoing; whitelist http, https) and here is how I did it. 

```


Default: deny (incoming), deny (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
80                         ALLOW IN    Anywhere
443                        ALLOW IN    Anywhere
8080                       ALLOW IN    Anywhere
80 (v6)                    ALLOW IN    Anywhere (v6)
443 (v6)                   ALLOW IN    Anywhere (v6)
8080 (v6)                  ALLOW IN    Anywhere (v6)

53                         ALLOW OUT   Anywhere
80                         ALLOW OUT   Anywhere
443                        ALLOW OUT   Anywhere
8080                       ALLOW OUT   Anywhere
53 (v6)                    ALLOW OUT   Anywhere (v6)
80 (v6)                    ALLOW OUT   Anywhere (v6)
443 (v6)                   ALLOW OUT   Anywhere (v6)
8080 (v6)                  ALLOW OUT   Anywhere (v6)

```

and you have to add this to /etc/ufw/before.rules

```


# allow outbound icmp
-A ufw-before-output -p icmp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
-A ufw-before-output -p icmp -m state --state ESTABLISHED,RELATED -j ACCEPT

```

thank-you for your help.

***UPDATE*** 

It is not necessary to add the above two lines to /etc/ufw/before.rules to retain ICMP and to get http and https to work.

---

