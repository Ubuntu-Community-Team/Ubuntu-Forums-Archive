---
title: "The Certificate Authority failed to verify the temporary nginx configuration changes"
date: 2022-06-16
forum: Networking &amp; Wireless
---

### Post by chat-4432 on 2022-06-16
when i run 
[FONT=Consolas]sudo certbot --nginx -d example.com -d [www.example.com]("http://www.example.com")
[/FONT][https://www.nginx.com/blog/using-free-ssltls-certificates-from-lets-encrypt-with-nginx/](https://www.nginx.com/blog/using-free-ssltls-certificates-from-lets-encrypt-with-nginx/)[FONT=Consolas]
**_example = my domain_**
[/FONT]it shows 
```

Challenge failed for domain [FONT=Consolas]example[/FONT].com
Challenge failed for domain [www.example]("http://www.example.com/").com


Certbot failed to authenticate some domains (authenticator: nginx). The Certificate Authority reported these problems:


Domain: [FONT=Consolas]example[/FONT].com
  Type:   unauthorized
  Detail: 202.28.1.60: Invalid response from [http://](http://)[FONT=Consolas]example[/FONT].com/.well-known/acme-challenge/PXHGYf9fXIKIcMwDD6aBnuX-ersYFT2H0mWUVKg5fZI: 404


  Domain: [FONT=Consolas]www.example[/FONT].com
  Type:   unauthorized
  Detail: 202.28.1.60: Invalid response from [http://](http://)[FONT=Consolas]www.example[/FONT].com/.well-known/acme-challenge/MIflLdJyy0etblJfRvUQqG21uAVlUmbZ0dLr-HD6-Gg: 404




Hint: The Certificate Authority failed to verify the temporary nginx configuration changes made by Certbot. Ensure the listed domains point to this nginx server and that it is accessible from the internet.

Cleaning up challenges
Some challenges have failed.
Ask for help or search for solutions at [https://community.letsencrypt.org](https://community.letsencrypt.org). See the logfile /var/log/letsencrypt/letsencrypt.log or re-run Certbot with -v for more details.

```
what should i do ??

---

### Post by TheFu on 2022-06-16
You can't have keys for example.com.  That domain is taken.  You need to use a domain that you've bought and registered in DNS or LE won't issue certs.


8% of men are colorblind, so perhaps highlighting using bold/underline would be helpful?

---

### Post by chat-4432 on 2022-06-17
i registerd no-ip >> manage DNS record >>> [COLOR=#696C6D][FONT=&amp]Port 80 Redirect >>> 8080[/FONT][/COLOR]
& try again it shows
**_example = my domain_**
Certbot failed to authenticate some domains (authenticator: nginx). The Certificate Authority reported these problems:
  Domain: example.ddns.net
  Type:   connection
  Detail: 34.199.8.144: Fetching [http://localhost:8080/.well-known/acme-challenge/eUzRFW9KRvdeFlGDxlH7l6yCSnDY_Ftp4L_OuSDxtrk:](http://localhost:8080/.well-known/acme-challenge/eUzRFW9KRvdeFlGDxlH7l6yCSnDY_Ftp4L_OuSDxtrk:)**_Invalid port in redirect target. Only ports 80 and 443 are supported, not 8080_**


  Domain: [www.example.ddns.net]("http://www.example.ddns.net")
  Type:   dns
  Detail: DNS problem: NXDOMAIN looking up A for [www.example.ddns.net]("http://www.example.ddns.net") - check that a DNS record exists for this domain; DNS problem: NXDOMAIN looking up AAAA for [www.example.ddns.net]("http://www.srimuang.ddns.net") - check that a DNS record exists for this domain


Hint: The Certificate Authority failed to verify the temporary nginx configuration changes made by Certbot. Ensure the listed domains point to this nginx server and that it is accessible from the internet.


Some challenges have failed.
Ask for help or search for solutions at [https://community.letsencrypt.org](https://community.letsencrypt.org). See the logfile /var/log/letsencrypt/letsencrypt.log or re-run Certbot with -v for more details.

---

### Post by chat-4432 on 2022-06-17
when i manage DNS record >>> [COLOR=#696C6D][FONT=&amp]DNS Hostname (A) localhost
it shows
[/FONT][/COLOR]**_example = my domain_**
Certbot failed to authenticate some domains (authenticator: nginx). The Certificate Authority reported these problems:
  Domain: example.ddns.net
  Type:   dns
  Detail: no valid A records found for example.ddns.net; no valid AAAA records found for example.ddns.net


  Domain: [www.example.ddns.net]("http://www.example.ddns.net")
  Type:   dns
  Detail: DNS problem: NXDOMAIN looking up A for [www.example.ddns.net]("http://www.example.ddns.net") - check that a DNS record exists for this domain; DNS problem: NXDOMAIN looking up AAAA for [www.example.ddns.net]("http://www.example.ddns.net") - check that a DNS record exists for this domain


Hint: The Certificate Authority failed to verify the temporary nginx configuration changes made by Certbot. Ensure the listed domains point to this nginx server and that it is accessible from the internet.


Some challenges have failed.
Ask for help or search for solutions at [https://community.letsencrypt.org](https://community.letsencrypt.org). See the logfile /var/log/letsencrypt/letsencrypt.log or re-run Certbot with -v for more details.
what should i do ??

---

### Post by chat-4432 on 2022-06-17
[B]_example = my domain_
[/B]when i config[B] 
Port 80 Redirect [/B][https://www.noip.com/support/knowledgebase/how-to-configure-your-no-ip-hostname/](https://www.noip.com/support/knowledgebase/how-to-configure-your-no-ip-hostname/)
it show [www.localhost:8080]("http://www.example.ddns.net:8080") on my site
do you to how to change [www.localhost:8080]("http://www.example.ddns.net:8080/") to [www.example.ddns.net]("http://www.example.ddns.net") ?
when i config 
[B]DNS Host (A) 
it show [/B][www.example.ddns.net]("http://www.example.ddns.net/"):8080

---

### Post by TheFu on 2022-06-17
Let's Encrypt is picky about who they give domains.
The web server must be on the internet if you plan to use the web-cert challenge-response issuing method.  There are other ways to prove you own the domain. Some friends use the DNS method. I do not.
The web server must have proper DNS records that bridge the domainname to the IP address.
The web server must be reachable by at least 3-5 Let's Encrypt random servers from around the world.  I actually have to disable my firewalls to renew certs, because we block entire regions of the internet after been attacked so often from those regions. With the firewall blocking, the 1 server would work, but the others would not and the certs would not be issued/renewed.

I use nginx, but don't use certbot.  For LE management, I switched to acme.sh years ago.  Just found it more intuitive and it worked easily. I started out with certbot and was able to get certs issued - lots of clear how-to guides exist. But when it was time to renew, it didn't work.

I've owned about 20 domains for over 20 yrs. How the Registrar --> DNS --> Website works isn't hard, but each part must be correct.
In general, the DNS needs to point at static IPs and as the error message says, ports 80/tcp and 443/tcp are required.  What really sucks is that even for renewals, port 80/tcp must be reached, still.  AAAA records are for IPv6.  I don't support IPv6 and don't have any DNS records to support it.  If that has recently become mandatory to use LE, I'll fight that battle in a few days. It wasn't last time we renewed.

Every 77-85 days, I run a script to renew all the certs. Takes about 90 seconds for all of them.

You are putting a web server on the public internet.  It needs a public IP. It needs a public Domainname. It needs a public DNS with multiple records.  There are how-to guides for each of those. Specific providers for each will have slightly different methods to have a working setup.  If you clearly post the exact domain, we can look at the registrar and DNS and try to ping the IP to see what's wrong.  Often, the way web server appear over the internet and from inside the LAN are very different.

I have a few webservers that are for internal use only, but those have LE certs to make stupid browsers happy.  For 90 seconds, during renewal, I run a webserver that appears to be those internal websites - just long enough to get the certs.  acme.sh has a standalone webserver capability for exactly this need.

---

### Post by chat-4432 on 2022-06-19
> **TheFu said:**
> 

I've owned about 20 domains for over 20 yrs. How the Registrar --> DNS --> Website works isn't hard, but each part must be correct.
In general, the DNS needs to point at static IPs and as the error message says, ports 80/tcp and 443/tcp are required.  What really sucks is that even for renewals, port 80/tcp must be reached, still.  AAAA records are for IPv6.  I don't support IPv6 and don't have any DNS records to support it.  If that has recently become mandatory to use LE, I'll fight that battle in a few days. It wasn't last time we renewed.

Every 77-85 days, I run a script to renew all the certs. Takes about 90 seconds for all of them.


can you give me a guide to use acme.sh

---

### Post by chat-4432 on 2022-06-19
> **TheFu said:**
> 

You are putting a web server on the public internet.  It needs a public IP. It needs a public Domainname. It needs a public DNS with multiple records.  There are how-to guides for each of those. Specific providers for each will have slightly different methods to have a working setup.  If you clearly post the exact domain, we can look at the registrar and DNS and try to ping the IP to see what's wrong.  Often, the way web server appear over the internet and from inside the LAN are very different.



do i need to buy router to do this ??

---

### Post by TheFu on 2022-06-19
acme.sh has documents on the project team's website. I think that's a gitlab or github page. They were pretty self-explanatory to me.

My renewal script that sits on the reverse proxy server looks like this:

```

# disable the huge blocklist
sudo ipset flush countryblock

cd  ~/.acme.sh
ACME_SETUP="--keylength 4096 --nginx --renew --force"

# ################[ Static Websites ]################
sudo ./acme.sh $ACME_SETUP  -d domain1.domainxyz1234.com 
sudo ./acme.sh $ACME_SETUP  -d domain99.domainxyz1234.com 
```

That's for websites that can have their certs updated while still online.  For websites/webapps that cannot be updated while ngnix is running, 

```
sudo service nginx stop
sudo ./acme.sh $ACME_SETUP -d splat.domainxyz1234.com   --standalone
sudo ./acme.sh $ACME_SETUP -d www.domainxyz1234.com   --standalone

sudo service nginx start  
```

Then I reboot the system to ensure the ipset rules are brought back in. Since it is a virtual machine, the reboot only takes a few seconds.  I suppose I could restart the ipset service instead, but it hasn't been an issue and being down for 2 minutes, once every 3 months usually on a Sunday morning just isn't that important.

I don't have notes on requesting a cert that I know works.  Haven't done that in a few years.  Sure, I have the commands that used to work, but ... I wouldn't want to send someone incorrect code.  However, there were 2 steps.  Get the cert, then deploy the cert.  

I setup some directories under  /etc/nginx/ssl/$DOMAIN/ for each cert to be held. That's where certs get deployed into.  The nginx config for each domain needs to point to the certs in those locations (/etc/nginx/ssl/$DOMAIN/ ) too. It isn't automated or I don't remember it being automated.   Each of those directories has 3 files:
```
$ ls -l  /etc/nginx/ssl/nc.domainxyz1234.com/
total 16
-rw-r--r-- 1 root root 1834 cert.pem
-rw-r--r-- 1 root root 5585 fullchain.pem
-rw------- 1 root root 1679 key.pem  
```

Hope this helps.

---

### Post by chat-4432 on 2022-06-19
I can't issue
when i run
 [COLOR=#24292F][FONT=ui-monospace]acme.sh --issue -d example.com -w /home/wwwroot/example.com
[/FONT][/COLOR]it show
mkdir: cannot create directory &#8216;/home/wwwroot&#8217;:_** Permission denied**_
/home/username/.acme.sh/acme.sh: line 4867: /home/wwwroot/example.com/.well-known/acme-challenge/hs2ecFqwfCIKskIgMwcN2-vJBNihGCUhN_HIO6Ii-u4: **_No_** such file or directory
[Sun Jun 19 15:07:10 UTC 2022] **_example.com:Can not write token to file : /home/wwwroot/example.com/.well-known/acme-challenge/hs2ecFqwfCIKskIgMwcN2-vJBNihGCUhN_HIO6Ii-u4_**
[Sun Jun 19 15:07:10 UTC 2022] Please add '--debug' or '--log' to check more details.
[Sun Jun 19 15:07:10 UTC 2022] See: [https://github.com/acmesh-official/acme.sh/wiki/How-to-debug-acme.sh](https://github.com/acmesh-official/acme.sh/wiki/How-to-debug-acme.sh)
when i
[COLOR=#24292F][FONT=ui-monospace]sudo acme.sh --issue -d example.com -w /home/wwwroot/example.com[/FONT][/COLOR]
it show 
sudo: acme.sh: command not found
what should i do ??

---

### Post by TheFu on 2022-06-19
> **TheFu said:**
>  
You are putting a web server on the public internet.  It needs a public IP. It needs a public Domainname. It needs a public DNS with multiple records.  There are how-to guides for each of those. Specific providers for each will have slightly different methods to have a working setup.  If you clearly post the exact domain, we can look at the registrar and DNS and try to ping the IP to see what's wrong.  Often, the way web server appear over the internet and from inside the LAN are very different.

Please provide the requested information.  Feels like you are missing some very important details based on later questions that are trivial to verify. Until those details are verified as correcd, it won't work, you cannot make it work.

---

