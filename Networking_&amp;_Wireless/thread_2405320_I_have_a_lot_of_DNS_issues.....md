---
title: "I have a lot of DNS issues...."
date: 2018-11-04
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2018-11-04
First of all I'm currently on AT&T DSL.  It's the worst internet on the planet and on a good day I get about 5Mbps down.  It got to where the connection was so bad that DNS wasn't resolving properly, using AT&T's DNS servers.  

I also have a DHCP controller and a DNS server in house.  I researched DNS servers and set my network up with three DNS servers.  Mine, which is 10.0.0.153; Level6's, which is 4.2.2.1; and Google's, which is 8.8.8.8....In that order.  That's how my DHCP server is setup.  I've been running it that way for about a year.  At first everything sped up.  Now, on a daily basis, at certain times I can expect google to load after about 30 seconds.  Ubuntu updates timeout, everything acts like my ping is out the roof.  As I'm writing this, speed tests won't even start until I refresh a few times.  I try to ping various domain names and it takes up to 10 seconds for them to resolve.  Speedtest.net is taking about 5 minutes to load.  When it does finally load, it acts like nothing is wrong.  The ping time is 21ms downspeed is 5.8Mbps and upspeed is 0.39.  I also don't have any problems streaming youtube videos, just loading them.  This is what leads me to believe it's a DNS issue.  

What in the world have I done wrong?....if anything.  Should my internal DNS server be the first DNS on the list?

---

### Post by TheFu on 2018-11-04
Call AT&T and have them roll a truck unless you are paying for 5 Mbps down / 400 Kbps up.  The contract matters. Hold them to it.

If you use IP addresses directly and everything works fine, then it is a DNS issue.  Otherwise, it is a connection issue.  Do you have chipmunks, rats, squirrels, gophers and buried phone lines?

---

### Post by pepsifx357 on 2018-11-05
Big LOL on that one.  I don't want to have to tell the story of how it took AT&T 2 years to come replace my 50 year old, ground spliced cable...or how they've run out of "ports" and won't give my neighbors internet.  I'm literally on my own here.  I've actually built a 100' tower next to my house and I'm weeks away from getting a DIRECT connection to a data center and starting my own ISP.  I just want to make sure I haven't done anything stupid, like set the DNS wrong.  Which has to be the problem because I can ping IPs all day.

What's weird is that I can ping youtube.com and get an instant resolve, but pinging google.com hangs there for a minute.  Even my internal DNS is taking too long to resolve in house host names.  I'm using ClearOS as a DNS server.

---

### Post by pepsifx357 on 2018-11-05
```
master@unms:~$ time host google.com
;; connection timed out; no servers could be reached

real	0m14.746s
user	0m0.000s
sys	0m0.016s
master@unms:~$ time host youtube.com
;; connection timed out; no servers could be reached

real	0m14.018s
user	0m0.008s
sys	0m0.000s
master@unms:~$ time host unms
unms has address 10.0.0.250
Host unms not found: 3(NXDOMAIN)

real	0m8.274s
user	0m0.008s
sys	0m0.000s
master@unms:~$ time host ubuntu.com
;; connection timed out; no servers could be reached

real	0m14.018s
user	0m0.004s
sys	0m0.004s

```

---

### Post by TheFu on 2018-11-05
If you can ping IPs, can you ping the DNS servers?  Those are the IPs that matter.
 
AT&T does run out of "ports" in some service areas.  They aren't making that up.  ISPs aren't regulated, so your friend is SOL, but if there are phone line issues that connect to the same DSLAM, perhaps the entire setup there will be upgraded which would not have old DSL. They'd put in newer tech which deals with bad copper much better. And port density is much higher now than in 1990s when the plain DSL was put in.

About a year ago, they came through the nearby main road and put in fibre all along it.  Then Comcast started advertising faster speeds.  Here it was 250/25 Mbps for $499/month + $800 installation.  Last spring, AT&T came through the neighborhood an dug up the yard for fibre (they'd done it for ADSLv2+ in 2007).  Now AT&T is offering 300Mbps down / 5 Mbps up for $40/month.  I have a business connection with a /29 static IPs.  It is less about bandwidth and more about running 20-30 services for clients for $10 /month in power on some 5-8 yr old PCs.  I'll always prefer hosting in my computer closet for cost management, but a $5/month VPS would easily become a forwarding and caching server to a symmetric 1000 Mbps connection for $100/month, if AT&T will offer that service.  Comcast has increase the speed here a few times the last 2 yrs.  AT&T says that the advertised price is the real price, unlike Comcast with all their junk fees added.

If I could get someone else as a provider for 100Mbps and higher speeds, for a reasonable price, I would, but that isn't how internet works here.

We used to have natural gas provided by 1 company, then about 15 yrs ago they deregulated the business and split the consumer side off.  The same infrastructure company manages the pipes, but I never have to deal with them. That former company isn't allowed to sell to consumers anymore. There are 100+ Gas Companies here now and they all compete.  Switching for a better price or better service is trivial, since the physical connections aren't touched.  I'd like to see this for residential internet.  Basically, the last mile is a shared resource and 50+ ISPs would have access paying rent to the huge companies which would be prevented from competing.

I've got some phone calls to make today.

---

### Post by pepsifx357 on 2018-11-05
Like I said, I can ping IPs all day.  8.8.8.8 and 4.2.2.1 ping just fine.

---

### Post by TheFu on 2018-11-05
Sorry. I try to help about 10 people posting here daily.

That would leave the possibility that outside DNS is being blocked for some reason. [https://arstechnica.com/information-technology/2018/05/att-is-blocking-cloudflares-privacy-focused-dns-calls-it-an-accident/](https://arstechnica.com/information-technology/2018/05/att-is-blocking-cloudflares-privacy-focused-dns-calls-it-an-accident/)  I had an ISP do that - realized it within a day and contacted them.  They fixed it immediately.  I know AT&T's network didn't like the 1.x.x.x/8 subnet when that DNS became available.  I'm not up on my IPv4 netblocks, but I could see a huge company with locations worldwide setting up part of their internal networks using public address ranges or addresses previously listed a bogons.  

I know nothing about any ISP blocking of 8.8.8.8 or 8.8.4.4 and have no idea what 4.2.2.1 is.  Maybe use a DNS performance testing tool that will find the fastest public DNS for your connection?

There are forums frequented by different ISP reps here: [www.dslreports.com](www.dslreports.com) .  Maybe they can help?

---

### Post by pepsifx357 on 2018-11-05
Thanks, I'll dig further into it.

---

### Post by pepsifx357 on 2018-11-06
I can comfirm 100% that AT&T is blocking any DNS server but their own.  Once again it's AT&T's fault.  I'm going to quit doubting myself from now on.  Thanks for the help everyone.

---

