---
title: "Apache &amp; FIOS ?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by garyed on 2009-02-11
I've had my Apache server working fine before I switched to Verizon FIOS. I just realized it only works within the computers on my router & not from the web. Researching the web it seems that Verizon blocks port 80 but Verizon wouldn't confirm or deny it, they just wanted me to pay a minimum of $89.00 for phone tech support with no guarantee so I opted not.
My router is a Westell 9100 EM just in case anyone is familiar with it.
I read something about DNS redirection where someone got it working but they were using Apache with Windows so it didn't really help me.
Any ideas appreciated.

---

### Post by punx45 on 2009-02-11
I seem to recall this being an issue when I had verizon DSL as well, so im not surprised.   im not sure if i ever found a solution for this.   Other than inelegant alternate ports.   DNS redirection depends on if you have a registered domain and who its with, probably.   you could always set apache to run on nother arbitrary high port, but you would have to include it in the url.

---

### Post by garyed on 2009-02-11
> **punx45 said:**
> I seem to recall this being an issue when I had verizon DSL as well, so im not surprised.   im not sure if i ever found a solution for this.   Other than inelegant alternate ports.   DNS redirection depends on if you have a registered domain and who its with, probably.   you could always set apache to run on nother arbitrary high port, but you would have to include it in the url.

That's a good idea & I think that's how the other guy got his working.
My first problem is I can't figure out how to configure the router correctly & I haven't found any help yet.

---

### Post by punx45 on 2009-02-11
that router config is kinda confusing, but its verizon, so im not surprised.   their cell phone software was terrible too.   looks like you have a bunch of ports forwarded to your server.   what you need to do is change the apache configuration where it specifies what port it listens on.   if you cant figure that out on your own, i cant remember off the top of my head but ill look at my stuff and figure it out and get back to you.


update:   I assume you are using apache2.   
in /etc/apache2/ports.conf   you can add a line for every port you want apache to listen on.   you can list as many as you want.   

just add another line for each
```

Listen 8080
Listen 8081
Listen 21355

```

dont forget to restart apache after you make changes:
```

sudo /etc/init.d/apache2 restart

```


if you are using apache 1, this is set in httpd.conf somewhere


also be prepared to accept the fact that verizon may be blocking all incoming requests and getting a server public may be impossible.   i seem to recall never getting anything externally accessible on verizon dsl.

---

### Post by usererror on 2009-02-11
Who was your old provider?  If everything was working just fine until you switched and all your equipment is the same, I'm betting they are blocking Port 80.

My ISP blocks port 80 as well, so I am forced to run it all through port 8080, its annoying but it works.  I don't want to pay extra $$$

---

### Post by garyed on 2009-02-11
Thanks for all the help, that did the trick.
I added 8080 to the ports.conf file & port forwarded it also on the modem & it works. The only thing is that I have to add ":8080" to the ip address to log on but that's not much of a problem since I'm not hosting my own website.

---

### Post by punx45 on 2009-02-12
yeah, that is the only downside to that workaround.   it may be possible, if you have a domain name registered, to have requests to your domain on port 80 to forward to 8080, that way it would be transparent in the url, and more user friendly.   this would totally depend on how you implemented a domain name, if you even have.

---

