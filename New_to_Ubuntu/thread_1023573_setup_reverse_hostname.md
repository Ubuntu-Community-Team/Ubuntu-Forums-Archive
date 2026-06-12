---
title: "setup reverse hostname"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by adza on 2008-12-28
Hi There, sometimes when i'm sending emails from my server setup (sun ultra 60 running 6.06 lts), i get the response 'Client host rejected, cannot find your reverse hostname'. How do i set this up? I have checked the settings in /etc/hosts and /etc/network/interfaces and they both resolve to the correct ip address. When i run ```
hostname
``` i simply get the hostname (ie, example), however when i run ```
hostname -f
``` i get example.server1.com. ?? Shouldn't these two commands produce the same output and if so, how can i set this up to work correctly?

---

### Post by adza on 2008-12-29
***bump*** can someone please help me with this one?

---

### Post by hyper_ch on 2008-12-29
I guess you did not set a reverse hostname in your dns.

---

### Post by scorp123 on 2008-12-29
> **hyper_ch said:**
> I guess you did not set a reverse hostname in your dns. +1

reverse hostnames are a matter of DNS .... so playing around with with the "hostname" command won't help.

@OP: Do you have a DNS server? Or do you use some router which then takes over this kind of functionality?

With my Linksys WRT54G router (running DD-WRT) at home I get the reverse hostname functionality on my LAN by assigning static DHCP leases to my machines. So maybe you could try this on your router too? (if you have one, that is .... )
.
.
.
.

---

### Post by adza on 2008-12-29
I have a static ip address setup on my router.. how do i set this up in the DNS? The router is the DNS server on the network as well...

---

### Post by hyper_ch on 2008-12-30
[http://www.letmegooglethatforyou.com/?q=reverse+dns+bind](http://www.letmegooglethatforyou.com/?q=reverse+dns+bind)

---

### Post by scorp123 on 2008-12-30
> **hyper_ch said:**
> [http://www.letmegooglethatforyou.com/?q=reverse+dns+bind](http://www.letmegooglethatforyou.com/?q=reverse+dns+bind) Didn't know that one :)

---

### Post by Bachstelze on 2008-12-30
Wrong.

On a home connection, you can't set the reverse DNS records yourself using your own nameserver. The reverse DNS record for your IP address is on your ISP's nameservers, so you need to ask them if they allow modification of the reverse DNS. If they don't, you're toast.

---

### Post by scorp123 on 2008-12-30
> **HymnToLife said:**
> Wrong. OP wrote this: > ... "i get example.server1.com. ?? ..." This suggests a misconfiguration on OP's own server.

> **HymnToLife said:**
>  On a home connection, you can't set the reverse DNS records yourself using your own nameserver.  You can on the inside. Which leads me back to what I wrote above: the error message above does not originate from an ISP but from OP's own server which doesn't seem to work with the incorrect default settings.

> **HymnToLife said:**
>  The reverse DNS record for your IP address is on your ISP's nameservers  While this is definitely true I am not sure it explains the behaviour we see. OP is trying to send a mail using his own server and I was under the impression that the error message OP reported e.g. > "Client host rejected, cannot find your reverse hostname" ... originates from OP's own server, not from their ISP.

Because from an ISP's point of view ... what's the difference? What I mean: Even if you have DSL (as opposed to a fixed line with a fixed IP) you most likely have a reverse hostname. If I check that on my connection I get something like ... ```
123.123.123.12.in-addr.arpa	name = 123-123.123-123.customer.someprovider.here.in.ch.
``` ... In other words: I do have a reverse hostname from my ISP. So from the ISP's point of view: What's the difference between me sending an e-mail from my client PC using Thunderbird directly to my ISP's MTA or sending my e-mail first to my internal server, and than having my internal server forward the e-mail to my ISP's MTA .... There is none!!  From my ISP's point of view both e-mails would originate from my external IP address, no matter what my internal setup looks like. 

So we definitely should not be getting the error message OP reported here, IMHO.

What we have here IMHO looks like a misconfigured MTA (and probably DNS too?) on OP's part, inside their own network.

---

### Post by Bachstelze on 2008-12-30
> **scorp123 said:**
> OP is trying to send a mail using his own server and I was under the impression that the error message OP reported e.g.  ... originates from OP's own server, not from their ISP.

Perhaps the OP should give us that information, then: to whom is he trying to send mail, and where does the error message appear. Otherwise, we'll just be making assumptions, and that's not good.

Also, perhaps someone in charge of a whole domain with internal mail- and nameservers shouldn't be posting in ABT, but that's just my view...

---

### Post by scorp123 on 2008-12-30
> **HymnToLife said:**
> Otherwise, we'll just be making assumptions, and that's not good. Absolutely.

---

### Post by adza on 2009-01-01
thanks for all this help :) I am running an internal mailserver indeed, this error message is being generated from this server...

---

### Post by vmikalinis on 2009-01-06
I just ran into the same problem, called my T1 provider (XO) and they told me that they have a web interface into which I can go and set the reverse IP.  They said that it must be done through them as they own the IP.  I'll add more info once they get me set up, they said possibly a day or two.

---

