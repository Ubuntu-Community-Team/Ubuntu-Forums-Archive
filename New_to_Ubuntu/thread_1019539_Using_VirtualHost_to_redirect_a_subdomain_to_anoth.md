---
title: "Using VirtualHost to redirect a subdomain to another server"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by gcwebdev on 2008-12-23
At my new job I've inherited two servers, each with a ton of redirects and hacks that I've not had time to sort through. I've created a new virtual server to start fresh and migrate sites there as I improve them.

I'm a web designer not a sysadmin, but from Apache docs I've figured out a bit. my new box is Ubuntu and I think my old boxes are centos. I'm hoping to get some clarification on VirtualHost documentation ([http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)).

If I want to send a subdomain on server1 to server3 this should work, right?

```
<VirtualHost *>
ServerName subdomain.server1.org
ServerAlias www.subdomain.server1.org
      Redirect permanent / http://server3.org/sites-enabled/subdomain
<VirtualHost>
```

Here's what I'm not sure of:
[LIST]
[*]ServerName = domain name of server receiving the request?
[*]ServerAlias = possible alternative requests for ServerName?
[*]Redirect = path requested + intended redirect?
[*]Does it matter if the intended redirected server name is an ip?
[*]If a redirect points the receiving domain name from server2 to server1, will the above redirect still work to server3?
[*]Is there anything that needs to be done on server3 to receive this redirect?
[/LIST]

Let me know if this should be placed somewhere else; I consider myself a newb but who knows. :)

---

### Post by wizard10000 on 2008-12-23
You do it like this -

<VirtualHost *:*>
ProxyPreserveHost On
ProxyPass / [http://192.168.111.2/](http://192.168.111.2/)
ProxyPassReverse / [http://192.168.111.2/](http://192.168.111.2/)
ServerName hostname.example.com
</VirtualHost>

[http://httpd.apache.org/docs/2.2/vhosts/examples.html](http://httpd.apache.org/docs/2.2/vhosts/examples.html)

Read the section on "Using Virtual_host and mod_proxy together"

Good luck -

---

### Post by gcwebdev on 2008-12-23
Thanks, wizard10000. Using this method, is there no longer a need for ServerAlias and Redirect? Otherwise I'd just combine all directives.

---

### Post by hyper_ch on 2008-12-23
is there a reason why you don't do this at DNS level?

---

### Post by wizard10000 on 2008-12-23
> **hyper_ch said:**
> is there a reason why you don't do this at DNS level?

Only reason I can think of is if you don't manage your own DNS servers  ;)

---

### Post by wizard10000 on 2008-12-23
> **gcwebdev said:**
> Thanks, wizard10000. Using this method, is there no longer a need for ServerAlias and Redirect? Otherwise I'd just combine all directives.

Not sure - maybe someone else knows?

---

### Post by hyper_ch on 2008-12-23
if he does not manage it himself then he could surely ask the one who manages it....

---

### Post by gcwebdev on 2008-12-23
hyper_ch, would that be easier? I'm pretty new to anything server level, guess I was following the pattern of the previous administrator. Do you have documentation I can read or a keyword I can look up?

wizard10000, I tried based on the example shown and my server failed to restart because of ProxyPreserveHost. When I commented out just that line it loaded ok. Is that advisable?

I'm currently managing the box. There are some colleagues I go to for occasional assistance but, yeah, holiday. :/

---

### Post by wizard10000 on 2008-12-23
> **gcwebdev said:**
> wizard10000, I tried based on the example shown and my server failed to restart because of ProxyPreserveHost. When I commented out just that line it loaded ok. Is that advisable?

You can leave it off.

ProxyPreserveHost Directive
Description:	Use incoming Host HTTP request header for proxy request
Syntax:	ProxyPreserveHost On|Off
Default:	ProxyPreserveHost Off
Context:	server config, virtual host
Status:	Extension
Module:	mod_proxy
Compatibility:	Available in Apache 2.0.31 and later.

When enabled, this option will pass the Host: line from the incoming request to the proxied host, instead of the hostname specified in the proxypass line.

This option should normally be turned Off. It is mostly useful in special configurations like proxied mass name-based virtual hosting, where the original Host header needs to be evaluated by the backend server.

---

### Post by hyper_ch on 2008-12-23
gcwebdev:

basically you need to make an entry on the zonefile for the domain like:


sub.domain.com.  IN ADDR  IPAddress

or

sub.domain.com.  IN ADDR  [www.otherdomain.com](www.otherdomain.com).

I think it's simpler but it all depends on how you manage the DNS for your domain.

---

