---
title: "Question about LAMP"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Kannibal28 on 2009-04-04
I installed LAMP last night, and I was wondering:

I already have a hosted Domain Name through GoDaddy, but I wanted to nix the actual hosting with GoDaddy and use the Domain Name for my new LAMP machine.  How would I go about doing this? 

Any help is greatly appreciated.

---

### Post by halitech on 2009-04-04
you need to setup the DNS to point to your system. Do you have a static IP address? Does your ISP allow you to host a domain/server on your current internet connection?

---

### Post by kellemes on 2009-04-04
> **Kannibal28 said:**
> I installed LAMP last night, and I was wondering:

I already have a hosted Domain Name through GoDaddy, but I wanted to nix the actual hosting with GoDaddy and use the Domain Name for my new LAMP machine.  How would I go about doing this? 

Any help is greatly appreciated.

My domain-name host gives me the option to redirect this domain-name to my server through **there DNS**. From there configuration-screen I can choose this option: Redirect Through DNS
Now I only need to fill in the actual domain-name and the external ip address of my server. Works fine..

I guess you need to check GoDaddy's options.

---

### Post by Kareeser on 2009-04-04
You'll need to downgrade your hosting plan to just a domain name.

After that, you'll have to use a DNS service (either the one provided free by GoDaddy, or another service like everyDNS) to point the domain name to your IP address.

---

### Post by Kannibal28 on 2009-04-04
As far as I know, my IP is not static.  Also, I don't know about my ISP, I've never attempted this before.  If it makes a difference, I use Cox Communications.  

Is it 100% necessary to have a static IP if I don't plan on turning the PC off?  Just a question.  If it is necessary, how would I go about getting a static IP?

I know, there's alot I don't know.  But I appreciate your help.

---

### Post by halitech on 2009-04-04
Static IPs make life easier in that most DHCP servers will refresh the IP every 72 hours (some more often some less) and you may or may not get the same IP everytime.

As far as if you are allowed: [http://www.cox.com/policy/#Acceptable_Use_Policy](http://www.cox.com/policy/#Acceptable_Use_Policy)

6. Servers. You may not operate, or allow others to operate, servers of any type or any other device, equipment, and/or software providing server-like functionality in connection with the Service, unless expressly authorized by Cox.

---

### Post by kellemes on 2009-04-04
> **halitech said:**
> Static IPs make life easier in that most DHCP servers will refresh the IP every 72 hours (some more often some less) and you may or may not get the same IP everytime.

As far as if you are allowed: [http://www.cox.com/policy/#Acceptable_Use_Policy](http://www.cox.com/policy/#Acceptable_Use_Policy)

6. Servers. You may not operate, or allow others to operate, servers of any type or any other device, equipment, and/or software providing server-like functionality in connection with the Service, unless expressly authorized by Cox.

Find another host would be my advise. I hate restrictions like that.
Or ask them if you're permitted to run your own server, or else..

---

### Post by halitech on 2009-04-04
> **kellemes said:**
> Find another host would be my advise. I hate restrictions like that.
Or ask them if you're permitted to run your own server, or else..

most ISPs (at least that I've dealt with) don't allow running a server without having a commercial package and some even block incoming connections on port 80 as most offer a hosting package of some sort and they don't want to lose the revenue they get off hosting.

Doesn't mean you can't do it, just not legally...

---

### Post by Kannibal28 on 2009-04-04
Thanks guys.

I contacted them to see if I could get permission, all I got was a bunch of phone numbers with no clear direction.  Tried 3 out of 5 of the ORIGINAL numbers so far, every person I have spoken with gives me a new number.  

Not that I would ever consider doing anything illegal, but what would be my alternative if I couldn't manage to get the permission?

---

### Post by halitech on 2009-04-04
> **Kannibal28 said:**
> Thanks guys.

I contacted them to see if I could get permission, all I got was a bunch of phone numbers with no clear direction.  Tried 3 out of 5 of the ORIGINAL numbers so far, every person I have spoken with gives me a new number.  

Not that I would ever consider doing anything illegal, but what would be my alternative if I couldn't manage to get the permission?

on a saturday you'd have better luck getting President Obama on the phone then getting an answer out of a phone monkey. Give them a call on Monday when the business office is open.

if you can't get permission (either from lack of contact or a no from someone) then you have no option on hosting the site yourself. Now, if you want to play around with running a server but can't get permission to host your own, you could look into Private Virtual Servers. 

[http://en.wikipedia.org/wiki/Virtual_private_server](http://en.wikipedia.org/wiki/Virtual_private_server)

---

