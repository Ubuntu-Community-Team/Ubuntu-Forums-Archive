---
title: "&quot;sudo ufw app list&quot; missing applications that exist in &quot;sudo ufw status&quot;"
date: 2017-01-25
forum: Networking &amp; Wireless
---

### Post by willcoq on 2017-01-25
**UPDATE: I resolved this. No need to assist me. Thanks.**

**How I solved it:**
I was actually having this problem on two machines (and a third didn't use the Nginx source, so it didn't have the problem).

One one machine, I solved it with the following:
sudo apt purge nginx
sudo apt purge ufw
sudo apt install ufw
sudo apt install nginx

Then I manually added the Nginx roles as shown below:
```
alpha@sparky:/etc/ufw/applications.d$ sudo nano /etc/ufw/applications.d/nginx-http
alpha@sparky:/etc/ufw/applications.d$ sudo nano /etc/ufw/applications.d/nginx-https
alpha@sparky:/etc/ufw/applications.d$ sudo ufw allow 'Nginx HTTP'
Rule added
Rule added (v6)
alpha@sparky:/etc/ufw/applications.d$ sudo ufw allow 'Nginx HTTPS'
Rule added
Rule added (v6)
alpha@sparky:/etc/ufw/applications.d$ sudo ufw app list
Available applications:
  Nginx HTTP
  Nginx HTTPS
  OpenSSH
alpha@sparky:/etc/ufw/applications.d$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
Nginx HTTP                 ALLOW       Anywhere
Nginx HTTPS                ALLOW       Anywhere
OpenSSH (v6)               ALLOW       Anywhere (v6)
Nginx HTTP (v6)            ALLOW       Anywhere (v6)
Nginx HTTPS (v6)           ALLOW       Anywhere (v6)

alpha@sparky:/etc/ufw/applications.d$
```

The nano commands contained this content:
[Nginx HTTP]
title=Web Server (HTTP)
description=for serving web
ports=80/tcp

and

sudo nano /etc/ufw/applications.d/nginx-https
[Nginx HTTPS]
title=Web Server (HTTPS)
description=for serving web
ports=443/tcp

On the other machine, I did a "sudo ufw reset" followed by the above commands. 

**The original post:**
Background:
On a fresh install of Ubuntu Server 16.04.1, I did the following:
```
sudo apt update
sudo apt full-upgrade
sudo apt install nginx
sudo ufw app list
sudo ufw status
```

In steps 4 and 5, I saw the same applications. Everything was fine.

On a different fresh install of Ubuntu Server 16.04.1, I did the following:
```
sudo apt update
sudo apt full-upgrade
sudo nano /etc/apt/sources.list
```

I then added the following lines:
```
deb http://nginx.org/packages/ubuntu/ xenial nginx
deb-src http://nginx.org/packages/ubuntu/ xenial nginx
```

And then proceeded with:
```
sudo apt update
sudo apt install nginx
sudo ufw app list
sudo ufw status
```

At first, both commands ONLY showed OpenSSH. Nginx wasn't listed at all. I then did a lot of "cat"-ing to look at various files, but I never changed any files or changed ufw at all. When I went back later to run those to commands, "sudo ufw status" was not showing Nginx! But it was only showing HTTP and HTTPS. Full wasn't there. And "sudo ufw app list" still doesn't show Nginx.

So then I did the following:
```
sudo nano /etc/ufw/applications.d/nginx-full

```

And added this to the file:
```
[Nginx Full]
title=Web Server (HTTP and HTTPS)
description=for serving web
ports=80,443/tcp

```

After saving that file, Nginx Full showed up on "sudo ufw status" but still not under "sudo ufw app list". I then deleted that file, disabled ufw, rebooted the entire machine, enabled ufw, and "sudo ufw status" is STILL showing Nginx Full, despite the fact that I deleted it. "sudo ufw app list" as usual only shows "OpenSSH". And if I do "ls /etc/ufw/applications.d", the only file is "openssh-server."

Obviously, this has only happened to me after adding the new source as instructed by the official Nginx insructions here: [https://www.nginx.com/resources/wiki/start/topics/tutorials/install/](https://www.nginx.com/resources/wiki/start/topics/tutorials/install/)

How do I fix ufw? I have tried fully uninstalling and reinstalling both ufw and nginx.

Additional information that may help:
```
alpha@sparky:/lib/ufw$ sudo cat /etc/ufw/user.rules
*filter
:ufw-user-input - [0:0]
:ufw-user-output - [0:0]
:ufw-user-forward - [0:0]
:ufw-before-logging-input - [0:0]
:ufw-before-logging-output - [0:0]
:ufw-before-logging-forward - [0:0]
:ufw-user-logging-input - [0:0]
:ufw-user-logging-output - [0:0]
:ufw-user-logging-forward - [0:0]
:ufw-after-logging-input - [0:0]
:ufw-after-logging-output - [0:0]
:ufw-after-logging-forward - [0:0]
:ufw-logging-deny - [0:0]
:ufw-logging-allow - [0:0]
:ufw-user-limit - [0:0]
:ufw-user-limit-accept - [0:0]
### RULES ###

### tuple ### allow tcp 80 0.0.0.0/0 any 0.0.0.0/0 Nginx%20HTTP - in
-A ufw-user-input -p tcp --dport 80 -j ACCEPT -m comment --comment 'dapp_Nginx%20HTTP'

### tuple ### allow tcp 443 0.0.0.0/0 any 0.0.0.0/0 Nginx%20HTTPS - in
-A ufw-user-input -p tcp --dport 443 -j ACCEPT -m comment --comment 'dapp_Nginx%20HTTPS'

### tuple ### allow tcp 22 0.0.0.0/0 any 0.0.0.0/0 OpenSSH - in
-A ufw-user-input -p tcp --dport 22 -j ACCEPT -m comment --comment 'dapp_OpenSSH'

### tuple ### allow tcp 80,443 0.0.0.0/0 any 0.0.0.0/0 Nginx%20Full - in
-A ufw-user-input -p tcp -m multiport --dports 80,443 -j ACCEPT -m comment --comment 'dapp_Nginx%20Full'

### END RULES ###

### LOGGING ###
-A ufw-after-logging-input -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-A ufw-after-logging-forward -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-I ufw-logging-deny -m conntrack --ctstate INVALID -j RETURN -m limit --limit 3/min --limit-burst 10
-A ufw-logging-deny -j LOG --log-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-A ufw-logging-allow -j LOG --log-prefix "[UFW ALLOW] " -m limit --limit 3/min --limit-burst 10
### END LOGGING ###

### RATE LIMITING ###
-A ufw-user-limit -m limit --limit 3/minute -j LOG --log-prefix "[UFW LIMIT BLOCK] "
-A ufw-user-limit -j REJECT
-A ufw-user-limit-accept -j ACCEPT
### END RATE LIMITING ###
COMMIT
```

**RESOLVED. SEE TOP OF POST.**

---

