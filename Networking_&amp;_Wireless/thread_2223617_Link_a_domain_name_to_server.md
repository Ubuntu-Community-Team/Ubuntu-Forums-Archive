---
title: "Link a domain name to server"
date: 2014-05-12
forum: Networking &amp; Wireless
---

### Post by Philb1961 on 2014-05-12
I am in need of some help. After installing the Ubuntu Server addition along with webmin and virtualmin I cannot link a domain name to the server to start hosting a web site. I am based in Queensland Australia. If there is an expert out there willing to help over the phone I am more than happy to call them or they could call me.

Thanks in advance

---

### Post by Lars Noodén on 2014-05-12
Can you see your web server using the ip number directly?  If so then you need to log into your registrar's web interface and use it to point your DNS entry to it.  Which registrar are you using?

---

### Post by spynappels on 2014-05-12
Can you give some additional detail?

Is your server directly connected to the Internet with a public IP, or is it in a LAN behind a router?

Is the website set up as a name-based virtualhost or just vanilla Ubuntu Server default on the server's IP?

If the server is on a LAN, can you see the site if you enter the server's IP in your browser, as Lars said? If it is directly connected to the Internet with a Public IP, can you see your site if you enter your Public IP into the browser?

Also, check your domain registrar as Lars said, and make sure you have an alias for [www.yourdomain.com](www.yourdomain.com) pointing to yourdomain.com. Without this, you'll get the website when you go to yourdomain.com but not when you go to [www.yourdomain.com](www.yourdomain.com)

---

### Post by Philb1961 on 2014-05-12
I have the server set up behind a router, I have a static ip with my internet connection. The domain is registered with crazydomains
I can login to webmin but cannot see the domain using just the domain name. I would be happy to give someone the login details if they would be willing to help.

---

### Post by Philb1961 on 2014-05-12
i have set the names servers to ns1.mydomain.com and ns2.mydomain.com and then at the registrar point it to these zones

---

### Post by Lars Noodén on 2014-05-12
Can you get your static ip number from DNS if you look it up?

```

host *mysite.example.com*

```

You can get even more information with [dig](http://manpages.ubuntu.com/manpages/trusty/en/man1/dig.1.html)

```

dig *mysite.example.com*

```

---

### Post by Philb1961 on 2014-05-12
sorry Lars, I ran the comand but dont understand what the results mean

---

### Post by spynappels on 2014-05-12
Do you want to post the output in code tags?

---

### Post by Philb1961 on 2014-05-12
if i type my static ip into the address bar I get my netgear d600 router login

---

### Post by Philb1961 on 2014-05-12
; <<>> DiG 9.8.1-P1 <<>> qldscuba.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14067
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;qldscuba.com.                  IN      A

;; AUTHORITY SECTION:
qldscuba.com.           38400   IN      SOA     ns1.qldscuba.com. master.qldscuba.com. 1399802487 10800 3600 604800 38400

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon May 12 23:11:53 2014
;; MSG SIZE  rcvd: 77

---

### Post by spynappels on 2014-05-12
Does your server have an internal static IP? If so, what do you see if you put that IP into a browser? That's assuming your browser is on a machine in the same LAN of course.

---

### Post by Philb1961 on 2014-05-12
did that make any sense?

---

### Post by Philb1961 on 2014-05-12
if i type in the servers internal ip I get the domain home page or the index page

---

### Post by Philb1961 on 2014-05-12
when i type the server internal ip into the address bar I do get the domains home/index page

---

### Post by spynappels on 2014-05-12
Ok, that means it's not a server issue.

It could either be a port forwarding issue or a DNS issue, or possibly a combination.

You said when you put your Public IP into the browser, you get the Router's Config page, I guess this is from inside the LAN? Do you have the means to test it from outside the LAN? It seems that your router does not support LAN passthrough, so using the external IP from inside the LAN will never work.

I'm also having some issues resolving your domain, it seems to time out, so when you confirm whether or not you can reach the site by using your public IP from outside the LAN, we can then move to troubleshooting the DNS.

---

### Post by Philb1961 on 2014-05-12
I just took a look in the router configuration and have enable port forwarding and now when I type the static ip I do get the domain index page up

---

### Post by spynappels on 2014-05-12
Ok, that is good.

I suspect that the problem is with the DNS settings, as I cannot resolve qldscuba.com at all, on any DNS server.

If your registrar is crazydomains, have you changed the nameservers in the domain control panel?

You should not need to change anything there, you should just put your static IP in the DNS Service section and leave the Name Server Details as default.

---

### Post by spynappels on 2014-05-12
Just to confirm the required settings you'd need as a minimum:

A record for qldscuba.com  >  your public IP
CNAME record for [www.qldscuba.com](www.qldscuba.com)  > qldscuba.com

The last step is optional but will make sure that someone entering [www.qldscuba.com](www.qldscuba.com) in their browser will get the page.

---

### Post by Philb1961 on 2014-05-12
OK so now from my phone, if it type my external ip I get the web page up but not if I type qldscuba.com.
I will login to crazy domains and check things out there.

would you mind checking it also ip is 60.240.253.76

---

### Post by spynappels on 2014-05-12
Other than the images not showing, I can see the site ok from the IP address. It's definitely an issue with the DNS setup you're using.

We're getting there.

---

### Post by Philb1961 on 2014-05-12
[TABLE="class: table alignMiddle dnsTable aRecords"]
[TR]
[TD]ns1.qldscuba.com[/TD]
 [TD]&#8250;[/TD]
 [TD] Remove 60.240.253.76 [/TD]
 [/TR]
[TR]
 [TD]ns2.qldscuba.com[/TD]
 [TD]&#8250;[/TD]
 [TD] Remove 60.240.253.76 [/TD]
 [/TR]
[TR]
 [TD]www.qldscuba.com[/TD]
 [TD]&#8250;[/TD]
 [TD] Remove 60.240.253.76 [/TD]
 [/TR]
[TR]
 [TD]https.qldscuba.com[/TD]
 [TD]&#8250;[/TD]
 [TD] Remove 60.240.253.76
[/TD]
[/TR]
[/TABLE]

---

### Post by Philb1961 on 2014-05-12
above is a copy of what I set up at crazydomains

---

### Post by spynappels on 2014-05-12
Ok, those entries are incorrect.

Remove all those entries and create 2 new ones:

First, create an 'A record' (quotes to show this is it's name) for qldscuba.com and point that to 60.240.253.76

Second, create a 'CNAME record' for [www.qldscuba.com](www.qldscuba.com) and point it to qldscuba.com

Give this some time to propagate through the DNS network and try again.

---

### Post by Bashing-om on 2014-05-12
Philb1961 -> spynappels;

Looking good !
IP 60.240.253.76 ->
> 
Welcome to Abyss Commercial Diving


Pat on the back
[INDENT][INDENT][INDENT]ya do GooD work
[/INDENT][/INDENT][/INDENT]

---

### Post by Philb1961 on 2014-05-12
Thanks for your help last night.
Unfortunatley we are still not working so if you feel like it at some stage, let me know?

---

### Post by lisati on 2014-05-12
I'm not familiar with the way crazydomains is set up, but qldscuba.com seems to have its NS entries pointing to qldscub nameservers. Is this correct?

When I was running my own server a year or two back, using a different domain registrar, I found it a lot easier to leave the default NS entries provided by my registrar well alone.

---

### Post by spynappels on 2014-05-13
Did you try what I said in post #23? Could you please show what your crazydomains Control Panel has now? I agree with Lisati, the default settings should have been left.

Crazydomains.co.uk uses the following nameservers by default:
```
ns1.dnspackage.com
ns2.dnspackage.com
```

---

### Post by Philb1961 on 2014-05-13
The names servers at crazydomains were a parked nameserver so I had to change them.
The last time I used Ubuntu which was a few years ago, I had someone set it up for me and they set up the nameservers inside Ubuntu.
This time I am trying to do it all myself so I have a better understanding and hopefully a little more knowledge.
This is a great place to learn and I really appreciate all the help.
Sadly, its still not working.

---

### Post by Philb1961 on 2014-05-13
[h=3]Active Records[/h] [TABLE="class: table alignMiddle dnsTable aRecords"]
  [TR="class: withoutSorting"]
 [TH="width: 49%"]Domain[/TH]
 [TH="width: 2%"] [/TH]
 [TH="width: 49%"]IP Address[/TH]
 [/TR]
 [TR]
 [TD]www.qldscuba.com[/TD]
 [TD]&#8250;[/TD]
 [TD]60.240.253.76 
[/TD]
 [/TR]
[TR]
 [TD]qldscuba.com[/TD]
 [TD]&#8250;
[/TD]
 [TD] 60.240.253.76 
[/TD]
 [/TR]
[TR]
 [TD]qldscuba.com[/TD]
 [TD]&#8250;[/TD]
 [TD] 60.240.253.76 
[/TD]
 [/TR]
[TR]
 [TD]ns1.qldscuba.com[/TD]
 [TD]&#8250;[/TD]
 [TD] 60.240.253.76 
[/TD]
 [/TR]
[TR]
 [TD]ns2.qldscuba.com[/TD]
 [TD]&#8250;[/TD]
 [TD] 60.240.253.76 
[/TD]
 [/TR]
 [/TABLE]
  [&#8249; Back]("https://manage.crazydomains.com.au/members/domains/details/?id=16996331")

---

### Post by Lars Noodén on 2014-05-13
The last two lines are the problem.  ns1.qldscuba.com and ns2.qldscuba.com should be pointing to two of crazydomains' machines.  Can you find the way to restore the default on just those two, leaving [www.qldscuba.com](www.qldscuba.com) and qldscuba.com still pointing to your site?

---

### Post by Philb1961 on 2014-05-13
Will give it a go Lars

---

### Post by spynappels on 2014-05-13
Hmm, I'm not sure about that.

With all due respect, I think it might be best to walk first, and run later.

When you use a registrar for a domain name, it is usual to use the registrar's DNS servers too for the A, CNAME and MX records for the domain you've registered. While it is possible to run your own DNS servers, this is adding a layer of complexity as you'll need to tell the DNS network they're there, and you would only have one running on the box in any event leaving you no redundancy.

I'm not saying for you to not run your own DNS servers, but as qldscuba appears to be a commercial site, why not get it up and published now using CrazyDomain's DNS infrastructure and experiment with another (hobby) domain to get your own DNS infrastructure set up.

---

### Post by Philb1961 on 2014-05-13
[TABLE]
  [TR]
 [TD]Name Server 1:[/TD]
 [TD="width: 10"] [/TD]
 [TD]ns1.parkme.com.au[/TD]
[/TR]
 [TR]
 [TD]Name Server 2:[/TD]
 [TD="width: 10"] [/TD]
 [TD]ns2.parkme.com.au

[/TD]
[/TR]
[/TABLE]
These were the original nameservers

---

### Post by spynappels on 2014-05-13
Crazydomains in the UK use the two nameservers I noted above in post #27, not sure if crazydomains in Australia does the same.

Edit: Nevermind, you got the Aus ones.

---

### Post by Philb1961 on 2014-05-13
The problem is I have the nameserver names but ni ip addresses to go with them.

---

### Post by Philb1961 on 2014-05-13
ns1.secureparkme.com  203.170.87.13
ns2.secureparkme.com  203.170.87.13

will these nameservers work as they are the generic ones from crazydomains?

---

### Post by spynappels on 2014-05-13
Could you post a screenshot of the domain control page, suitably anonymised? On my crazydomains control panel, the nameservers used for the domain are in a separate section to the DNS records for this domain. I'll see if I can get a screenshot from mine, but in the meantime can you share yours?

---

### Post by spynappels on 2014-05-13
[ATTACH=CONFIG]253113[/ATTACH]

If you look at the screenshot attached, you will see that the first section is the Name Server Details. These are the name servers which look after the DNS records for the domain in question. You only need to enter the secureparkme nameservers here, with no IP addresses.

The DNS Service section of the control page is where you create the records which will be hosted in the DNS servers you entered above, and this is where you create the A and CNAME records and point them to your Public IP address.

If the Australian crazydomains Control Panel is different, then I'm afraid I won't be able to be of much more help, as I don't know what they are looking for in what fields.

---

### Post by Philb1961 on 2014-05-13
The Australian lay out is exactly the same.
Didnt know how to take a screen shot but have attached what it looks like as a note pad document

---

### Post by spynappels on 2014-05-13
Ok, then change it to look like my screenshot with only the 2 nameservers in the Name Server Details and a single A record and a single CNAME record in the DNS Service Section. You will not have an MX record or a subdomain in your Control PAnel, but otherwise it should look the same except with your nameservers, domain and IPs

---

### Post by Philb1961 on 2014-05-14
I have now restored the original nameservers so will give it a few hours to see what happens.
Thanks for all your help and keep your fingers crossed for me.

---

### Post by Lars Noodén on 2014-05-14
Great.  Make sure that the A record points to the right IP address, too.  Then we should know within an hour or so.

---

### Post by Philb1961 on 2014-05-14
This is what I have now

---

### Post by Lars Noodén on 2014-05-14
DNS looks good from here too!  Compare the following with your older dig output:

```

$ dig www.qldscuba.com

; <<>> DiG 9.9.5-3-Ubuntu <<>> www.qldscuba.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26262
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 2, ADDITIONAL: 5

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;www.qldscuba.com.		IN	A

;; ANSWER SECTION:
www.qldscuba.com.	1800	IN	CNAME	qldscuba.com.
qldscuba.com.		1800	IN	A	60.240.253.76

;; AUTHORITY SECTION:
qldscuba.com.		172799	IN	NS	ns2.dnspackage.com.
qldscuba.com.		172799	IN	NS	ns1.dnspackage.com.

;; ADDITIONAL SECTION:
ns1.dnspackage.com.	172799	IN	A	27.124.125.5
ns1.dnspackage.com.	172799	IN	AAAA	2a00:fd80:aaaa:ffff::cccc:1
ns2.dnspackage.com.	172799	IN	A	27.124.125.6
ns2.dnspackage.com.	172799	IN	AAAA	2a00:fd80:aaaa:ffff::cccc:2

;; Query time: 307 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Wed May 14 13:47:58 EEST 2014
;; MSG SIZE  rcvd: 210

$ host www.qldscuba.com
www.qldscuba.com is an alias for qldscuba.com.
qldscuba.com has address 60.240.253.76

```

---

### Post by spynappels on 2014-05-14
It is resolving for me too, but I'm not able to connect using a browser, but I can't connect to the site using the IP directly either.

I think the DNS issues are resolved for now, have a look at your port forwarding etc again now, this worked before so should not be a big deal.

You're definitely getting there.

---

### Post by Philb1961 on 2014-05-14
OK will login to the router again and take another look

---

### Post by Philb1961 on 2014-05-14
nothing changed on the router side

---

### Post by Philb1961 on 2014-05-14
would you mind checking [www.qldscuba.com](www.qldscuba.com) from your end Lars? Tell me what you see.

---

### Post by Bashing-om on 2014-05-15
Philb1961; Hey,

I may not be able to help much, but, I can help this much;
the url fails to load:
> 

Oops! Google Chrome could not connect to [www.qldscuba.com](www.qldscuba.com)

Did you mean: [www.scuba.com](www.scuba.com)


[INDENT][INDENT]every little bit helps
[/INDENT][/INDENT]

---

### Post by Philb1961 on 2014-05-15
would you mind checking [www.qldscuba.com](www.qldscuba.com) from your end Lars? Tell me what you see.

---

### Post by Lars Noodén on 2014-05-15
The DNS entry looks good but the web server times out.  Have you gone through the usual checklist?  Can you access the web page via the same LAN?  Can you access it via the ip address (60.240.253.76) directly?  I get nothing today and yesterday, though it was working the other day.

---

### Post by lisati on 2014-05-15
> **Lars Noodén said:**
> The DNS entry looks good but the web server times out.  Have you gone through the usual checklist?  Can you access the web page via the same LAN?  Can you access it via the ip address (60.240.253.76) directly?  I get nothing today and yesterday, though it was working the other day.

Likewise from my end: all I'm getting is firefox telling me "Connecting", spinning its wheels, and eventually telling me "Problem loading page"

Is the port forwarding on your router set to direct website access (port 80) to a suitable IP address on your local network?

---

### Post by Philb1961 on 2014-05-15
I can access it directly via my lan connection but not from my phone once i disconect from the wifi. Not sure what has changed Lars from the other day when you accessed it with the ip address.
Any suggestions?

---

### Post by Philb1961 on 2014-05-15
This is my router settings

---

### Post by Lars Noodén on 2014-05-15
Does your web server still have the internal address listed there in the router menu?  It could be that you are still getting a dynamic address from the router and need to set it to be static there also.

---

### Post by Philb1961 on 2014-05-15
more router settings

---

### Post by Lars Noodén on 2014-05-15
I'm not able to ping 60.240.253.76 from two different places.  Can you check with an outside service to verify your ip number and that ports 80 and 443 are open?

[http://canyouseeme.org/](http://canyouseeme.org/)

---

### Post by Philb1961 on 2014-05-15
failed on both ports, it says they timed out

---

### Post by Lars Noodén on 2014-05-15
Did that site report the right IP number at least?  What kind of arrangement do you have with your ISP regarding a static IP address?

---

### Post by Philb1961 on 2014-05-15
static ip with isp was to run a home based server

---

### Post by Philb1961 on 2014-05-15
[COLOR=red]**Error:**[/COLOR] I could **not** see your service on **60.240.253.76** on port (**80**)
Reason: Connection timed out
                             Your IP:                      
                       Port to Check:

---

### Post by Lars Noodén on 2014-05-15
In #54 the screen shot shows LAN ip number is 192.168.0.200 and you can still access the web site from another machine on the same LAN using the internal (LAN) ip number.  So that part should be good.

DNS works, in regards to looking up the domain name and resolving it to the external ip number, 60.240.253.76.  So that part is good.  

Your screen shot in #56 shows NAT enabled and that the external ip is 60.240.253.76.  Can you access the web site from another machine on the same LAN using the external ip number?

---

### Post by Philb1961 on 2014-05-15
When I use 192.168.0.200 or 60.240.253.76 qldscuba.com from my laptop on the same lAN I can see the qldscuba home page.
I am going to change to an older router that used to work for Ubuntu and see if the issue is my new router.
Will let you know how I go.

---

### Post by Philb1961 on 2014-05-16
Changed the router to no avail. Then decided to call my ISP to see if everything was OK at their end. I was put on hold for five mins and so after for mins I checked the site and all was working fine. The tech came back on and said it was all fine. Asked what he did and he said nothing at all.  Strange that hey. lol Now for putting up the correcy website as the one there now is one I built for a friend a couple of weeks back.
Let me know if its working from your end please guys?

---

### Post by Philb1961 on 2014-05-16
Will start a new post with my next question soon. Hope you guys dont get P--sed of with me as I have a few to ask.

---

### Post by Lars Noodén on 2014-05-16
Yep. Now that the middle is also connected, the site comes up fine with the site for "Abyss Commercial Diving"  Very cool.

---

### Post by spynappels on 2014-05-16
Yep, all good now.

Glad you got there in the end! And at least it's fun learning, right?

---

### Post by Philb1961 on 2014-05-16
Thanks to you guys its all good now

The next thing I want to look at is Virtualmin
Have a number of domain names to work with so want to set it up as a virtual server to host a few sites.
Any ideas what I need to do?

---

### Post by spynappels on 2014-05-16
Never used Virtualmin, but have a look for namebased virtualhosts in the wiki. That's the default way of doing it AFAIK.

---

### Post by Lars Noodén on 2014-05-16
Apache2 can handle multiple virtual hosts.  You'll need to set up separate directories for each new site's DocumentRoot and then make a configuration file for that virtual host (aka vhost).  Then find a guide for namebased virtual hosts as spynappels points out.  

One thing with 2.2, which is what you have I think, is that on Ubuntu the default DocumentRoot for the default virtual host is /var/www.  If you are going to host several sites on that machine, it might be good to move that.  For example you could have

/var/www/qldscuba.com/
/var/www/tasscuba.com/
/var/www/nswscuba.com/

and so on.

The only thing that matters is that the directory name on the server matches what is in the vhost's DocumentRoot.

---

### Post by Philb1961 on 2014-05-16
I did enjoy the learning side of getting this working so thanks again for all your help.
Cheers.

---

