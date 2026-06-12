---
title: "Access PC through IP - Tried Everything"
date: 2014-08-18
forum: Networking &amp; Wireless
---

### Post by FaBioW114 on 2014-08-18
Hi, I'm trying to access a page in my computer from the 'outer world' though my ip address.

I have installed apache2 and on my router I did a port forward procedure.

When I test on canyousseme.org, it gives me this:
Success: I can see your service on (my ip) on port (8080)
Your ISP is not blocking port 8080

localhost:8080 a "It works!" page is displayed.

Also, I have a simple index.html file under /var/www/

But when I type my ip in the browser, I get an error page.

Does anybody have any idea what else I could do?

Thanks in advance,

---

### Post by Lars Noodén on 2014-08-18
Try accessing it from the LAN address from a different computer on the same LAN.  Odds are that is still blocked.  Did you open up port 8080 in UFW?

```

sudo ufw allow 8080

```

---

### Post by FaBioW114 on 2014-08-18
Hello Lars, thanks for the reply.

I haven't executed this command before, but it's done now. I'm getting the same result, although it seems it's taking more time to load the error page.

When I enter the local ip on other computer, the "Apache2 Ubuntu Default Page" appears. Any other guess?

---

### Post by steeldriver on 2014-08-18
Are you trying to access via the **public **IP from **inside **the LAN? not all routers support that (NAT "loopback" or "hairpinning")

---

### Post by FaBioW114 on 2014-08-18
Hi steeldriver,

I asked a friend who is outside the lan to access my page, but he also got an error page.

---

### Post by steeldriver on 2014-08-18
What version of Ubuntu are you running? The default apache2 DocumentRoot changed from /var/www to /var/www/html for 14.04 I think - you may need to move your index file there

---

### Post by lisati on 2014-08-18
> **FaBioW114 said:**
> I asked a friend who is outside the lan to access my page, but he also got an error page.
Did your friend put in **:8080** at the end of the url?

---

### Post by ian-weisser on 2014-08-18
The easy way to troubleshoot.
Do this, in order, to rule out common causes one by one:

Test the server.
If, on the *same** machine*, [http://localhost:8080](http://localhost:8080) works, then the web server is operating properly.

Test the server's firewall and the LAN IP address.
If, on *a different machine on the same LAN*, http://<LAN IP Address>:8080 works, then the server's firewall is configured properly and the server really does have the same IP that you expect.
If not, then your server's firewall is blocking access or your server is at a different IP address.

Test the router's firewall and port forwarding.
If, on *a machine out on the internet*, http://<domain name>:8080 works, then the router is configured properly.
If not, log into your router. Check that the firewall is not blocking 8080, and that 8080 is forwarded to the correct LAN IP address.

---

### Post by FaBioW114 on 2014-08-18
lisati and ian, my friend now accessed my ip through :8080 and got the "It works!" page.

And.... me too! I didn't configure anything beside the "sudo ufw allow 8080" command, which didn't work right after I executed it...

Is this some kind of delay matter?

Either way, thanks guys!

---

