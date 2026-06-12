---
title: "Domain setup and config. for personal mail server"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by BlakeM on 2009-01-30
Hi all,

What I would really like is to have a personalised email address (e.g. [email]exmaple@example.com[/email]) and make it work with my own mailserver. I'm following this tutorial:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

I know it's a very good tutorial, but it doesn't really explain concepts to noobies so well. I've been Googling around to find answers but I've spent hours and haven't got very far. Also, it's focused on setting up a mail server and doesn't explain how to get your own domain or how to configure it.

I'm looking for a good place to find info about getting started with domains and what I do with the domain after I've registered it. A few things that I don't get:

[LIST=1]
[*]When I go to register my chosen domain, do I supply my static IP to the registrar so they can forward traffic directed to this domain to my IP? Or is this something that I have to set up myself?
[*]I've seen examples like this: name.example.com. From what I understand, "example" is the domain and "com" is the domain level (or something), so what's "name" represent?
[*]I read in another post it was recommended to read up on MX, PRT, A, etc records...where does one set these up?
[/LIST]

Sorry for the nooby questions.

---

### Post by hyper_ch on 2009-01-30
there are multiple things you need to consider:

- what registrar do you want to use?
- you have a static ip address?
- what nameservers do you want to use? Do you want to run your own nameserver(s)?
- what MTA?
- what IMAP/POP server?
...
...
...

---

### Post by theozzlives on 2009-01-30
I use [bluerazor.com]("http://www.bluerazor.com"). They are reasonable. Yes, you have your domain go to your static IP. I have 100 mail addresses that I can forward (got the cheap package) to my other email addresses. For example [email]ozzie@theozzmicrosystems.com[/email] goes to [email]ozzmicrosystems@coxinet.net[/email]. I don't have postfix setup just Apache2 PHP5 and MySQL.

---

### Post by BlakeM on 2009-01-30
> **hyper_ch said:**
> there are multiple things you need to consider:

- what registrar do you want to use?
- you have a static ip address?
- what nameservers do you want to use? Do you want to run your own nameserver(s)?
- what MTA?
- what IMAP/POP server?


Choosing a registrar doesn't really bother me. I'll look for something cheap, reliable and provides decent services, but that's a (relatively) small decision to make.

Yes, I'm fairly certain my ISP provided my with a static IP address. It certainly doesn't change.

Just for confirmation: A nameserver is a server that runs software to map a human recognizable name to an external IP address. As I understand it, the DNS nameservers for my IP address would probably be controlled by my ISP, is that right?

Also, if I choose to run my own DNS nameservers, what are the benefits of doing that? Does it mean you don't have to go through your ISP when you want to attach a domain to your IP address? Is BIND the software that I would need to install on (preferably) two servers to map a domain to my IP?

For the MTA and POP/IMAP server, I'll just keep following that guide.

---

### Post by BlakeM on 2009-01-30
> **theozzlives said:**
> I use [bluerazor.com]("http://www.bluerazor.com"). They are reasonable. Yes, you have your domain go to your static IP. I have 100 mail addresses that I can forward (got the cheap package) to my other email addresses. For example [email]ozzie@theozzmicrosystems.com[/email] goes to [email]ozzmicrosystems@coxinet.net[/email]. I don't have postfix setup just Apache2 PHP5 and MySQL.

So if I purchase a domain from a registrar, their servers are responsible for handling the mapping of the human recognizable address to my IP?

---

### Post by BlakeM on 2009-01-30
Okay, for anyone interested I found a good tutorial/explanation about dns name servers and how to setup your own: 

[http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml](http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml)

---

