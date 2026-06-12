---
title: "Nginx -  Certbot  The domain is not able to work"
date: 2024-04-30
forum: Networking &amp; Wireless
---

### Post by fernandovch on 2024-04-30
Hi
I have an ubuntu server with nginx installed and certbot, I'm trying to access my domain from the browser but the connection gets canceled.
I'm new at configuring ubuntu server, I followed a lot al tutorials and I end up with the same result, the https request is not able to resolve. 

The curl -v [https://www.domain.com](https://www.domain.com)
is trying to resolve but it's failing after a while. 

the curl -v [http://www.domain.com](http://www.domain.com)

```

ufw status
Status: active


To                         Action      From
--                         ------      ----
Apache                     ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
22                         ALLOW       Anywhere
Nginx Full                 ALLOW       Anywhere
OpenSSH                    ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
443/tcp                    ALLOW       Anywhere
443                        ALLOW       Anywhere
Apache (v6)                ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)
22 (v6)                    ALLOW       Anywhere (v6)
Nginx Full (v6)            ALLOW       Anywhere (v6)
OpenSSH (v6)               ALLOW       Anywhere (v6)
80/tcp (v6)                ALLOW       Anywhere (v6)
443/tcp (v6)               ALLOW       Anywhere (v6)
443 (v6)                   ALLOW       Anywhere (v6)



netstat -tulpn --verbose
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      225379/nginx: maste
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      684/sshd: /usr/sbin
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      225379/nginx: maste
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      550/systemd-resolve
tcp6       0      0 :::80                   :::*                    LISTEN      225379/nginx: maste
tcp6       0      0 :::22                   :::*                    LISTEN      684/sshd: /usr/sbin
tcp6       0      0 :::443                  :::*                    LISTEN      225379/nginx: maste
tcp6       0      0 :::3000                 :::*                    LISTEN      32635/next-server (
udp        0      0 127.0.0.53:53           0.0.0.0:*                           550/systemd-resolve
udp        0      0 10.0.0.4:68             0.0.0.0:*                           547/systemd-network
udp        0      0 127.0.0.1:323           0.0.0.0:*                           603/chronyd
udp6       0      0 ::1:323                 :::*                                603/chronyd

```

---

### Post by TheFu on 2024-04-30
Certbot is a PITA.  

I switched to **acme.sh** [https://github.com/acmesh-official/acme.sh](https://github.com/acmesh-official/acme.sh) perhaps 4 yrs ago and never looked back.  The only times I've had issues with getting certs renewed was when I had firewall rules blocking access to parts of the world from which attacks originated.  Now, I manually flush the firewall rules on the cert box just prior to renewal.  Takes about 90 seconds for all the certs to be renewed, then I re-enable all the firewall rules.  For internal websites and will never be accessible over the internet, but we still want LE certs for, I stop nginx and run a acme.sh in stand-alone mode to get the certs.

I think there's something that people don't like about the acme.sh project. Don't remember what that was.  Just know that certbot only worked for me to create certs, but never to renew.

I would run a renewal to test everything for you, but our certs don't expire until late June. We renew every 77 days.  A few times, when the renewals were problematic, we needed the extra days to figure out problems.

The renewal command I use looks like this:
```

# Some settings.
ACME_SETUP="--server letsencrypt --home $HOME/.acme.sh --nginx --renew --force"
KEYLENGTH="--keylength 4096"

~/.acme.sh$ sudo ./acme.sh $ACME_SETUP -d blog.jdpfu.com    --standalone $KEYLENGTH
```
for all the proxied domains.  I use nginx as a reverse proxy and load balancer.   I have to stop nginx before running that command for each domain.  I used to have a number of domains inside the same cert, but found that was being abused by people trying to access non-public domains, so I switched to 1 domain per cert.

For static websites hosted on the nginx reverse proxy system, renewals are easier.
```
~/.acme.sh$ sudo ./acme.sh $ACME_SETUP  -d lpi.jdpfu.com $KEYLENGTH
```

They warn about using sudo, but since my certs are stored under /etc/ it isn't exactly possible for any other user to update them. In short, sudo is required for my specific setup.

I don't think the keylength option was honored last time I looked. Haven't really researched why not. I'm not doing ecommerce and don't really worry about privacy of the connections beyond what TLS v1.3 already provides.  I specifically disable all earlier cipher versions.

Anyway, hope this is helpful in some way.  Probably not, but at least you got a reply.

---

### Post by TheFu on 2024-04-30
If you cannot ping your own domain, that has nothing at all to do with certbot. That's a network or DNS problem.

---

### Post by fernandovch on 2024-05-01
Hi, 
from my local machine I cannot get a result when I ping the public IP from my VM. 
One thing is that from my local machine I'm able to get a first response from my VM and the nginx, I mean that I can see that is redirecting from [http://www.domain.com](http://www.domain.com) to  [https://www.domain.com](https://www.domain.com).
If inside of my ubuntu VM y run   

curl -v [http://www.domain.com](http://www.domain.com) I get the `301 Moved Permanently`, this is expected based on my ngix config file. 

But if I run  curl -v [https://www.domain.com](https://www.domain.com)  Im getting a time out. 

The idea is to reach the nextjs app that its running in  [http://127.0.0.1:3000](http://127.0.0.1:3000), I know it's running because I curl -v [http://127.0.0.1:3000](http://127.0.0.1:3000)  and I'm getting the landpage of my app. 

This is the config file of ngix.


```

server {
    server_name domain.com [www.domain.com;](www.domain.com;)


    # Next.js specific configuration
    location / {
        proxy_pass [http://127.0.0.1:3000;](http://127.0.0.1:3000;) # Assuming Next.js is running on port 3000
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
     }


    listen [::]:443 ssl ipv6only=on; # managed by Certbot
    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/domain.com/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/domain.com/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot




}


server {
    if ($host = [www.domain.com](www.domain.com)) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


    if ($host = domain.com) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


    listen 80 default_server;
    listen [::]:80 default_server;
    server_name domain.com [www.domain.com;](www.domain.com;)
    return 404; # managed by Certbot
}
```

---

### Post by fernandovch on 2024-05-01
Update:

I added in the hosts file the 
127.0.0.1  [www.domain.com](www.domain.com)
127.0.0.1 domain.com

and now I can do a curl -v [https://www.domain.com](https://www.domain.com) and get the web app. 
This from the inside of the ubuntu VM.

Still, no luck from my local machine using the web browser.

---

### Post by fernandovch on 2024-05-01
> **TheFu said:**
> If you cannot ping your own domain, that has nothing at all to do with certbot. That's a network or DNS problem.

I finally solved the issue, as you mention, there was a DNS problem, the final fix was to add a inbound rule allowing port 443. 
And the other thing was adding the domain into the hosts file. 


Thanks for you help.

---

### Post by TheFu on 2024-05-01
> **fernandovch said:**
> Update:

I added in the hosts file the 
127.0.0.1  [www.domain.com](www.domain.com)
127.0.0.1 domain.com

and now I can do a curl -v [https://www.domain.com](https://www.domain.com) and get the web app. 
This from the inside of the ubuntu VM.

Still, no luck from my local machine using the web browser.

Some web browsers only work with remote DNS, so until you setup a public DNS service, something like no-ip.com, those browsers won't work.  Google Chrome is famous for this and defauilts in firefox used to point to their DNSSEC service unless you setup a LAN DNS.  /etc/hosts are ignored.  Most Android devices ignore /etc/hosts, BTW, so you'll want/need to setup a LAN DNS anyway.  

And you really shouldn't use 128.0.0.1/8. Any of those are "localhost" and useless for any other computer.  You should be using the real LAN IP.

---

