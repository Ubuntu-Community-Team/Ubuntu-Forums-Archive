---
title: "Block Specific rss feeds??"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by andytof47 on 2007-03-29
Hi ,

I have run into a little trouble here, basically I have Dansguardian running and it's doing a wonderful job of blocking unwanted Pron amongst other content......


Anyways I have just discovered rss video feeds and now there are advertised channels that include very suggestive titles and pictures.....


If it were just standard html and websites the thumbnail and source would be blocked but this isn't so with RSS



Can anyone help ---- E.G do I need to configure dansguardian???

---

### Post by andytof47 on 2007-03-29
Bump - I have installed wireshark and am monitoring where the traffic comes from but is this the most effective way of blocking it????

any help appreciated :popcorn:

---

### Post by andytof47 on 2007-03-29
bump - this is a forum people and i'm desperate:)  I can't let this one slide

---

### Post by Mr. C. on 2007-03-29
You said "specific", but I'm reading that you want to block video feeds in general.

Look at : [http://urlblacklist.com/](http://urlblacklist.com/)

MrC

---

### Post by andytof47 on 2007-03-29
well actually it is specific i.p's from within Democracy T.V. player

O.k Wireshark is running and I have some captures so knock urself out and check it out..:)

I have added the domain 8.3.209.205 to my 

bannedsitelist

my blacklist is also updated to include that domain and also 

media.revver.com is also included

I really don't understand why even though the traffic is going through my proxy and Dansguardian it still isn't blocking the traffic... anyhelp is appreciated as well as any explanation

I already have url blacklist installed

so again any help / info / perhaps even a a book on kung fu or tai chi to help me understand the way of the tiger :)  Mr.C appreciate ur help

it's not all video feeds - if that were so i would just update my bannedmimtype or bannedextensionlist just specific feeds

---

### Post by Mr. C. on 2007-03-29
I laughed out load when I read the kung fu/tai chi comments! 


If you look at and select frame 8 of your capture, and expand the Hypertext layer, and the sub-layer HEAD, you will see the HOST is media.revver.com, and the partial URI is a /qt/206658.mov.

Let's look at the addresses records for that host:

```
$ dig A media.revver.com

; <<>> DiG 9.3.4 <<>> A media.revver.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 479
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 2, ADDITIONAL: 2

;; QUESTION SECTION:
;media.revver.com.              IN      A

;; ANSWER SECTION:
[COLOR="Red"]media.revver.com.       282     IN      A       8.3.209.227
media.revver.com.       282     IN      A       8.3.209.228
media.revver.com.       282     IN      A       8.3.209.225[/COLOR]

;; AUTHORITY SECTION:
revver.com.             85729   IN      NS      ns3.revver.com.
revver.com.             85729   IN      NS      ns1.revver.com.

;; ADDITIONAL SECTION:
ns1.revver.com.         85731   IN      A       80.68.80.167
ns3.revver.com.         2931    IN      A       8.3.209.60

;; Query time: 2 msec
;; SERVER: 192.168.3.200#53(192.168.3.200)
;; WHEN: Thu Mar 29 16:49:54 2007
;; MSG SIZE  rcvd: 150
```

Aha!  They are DNS load-balancing (round-robin style) amongst three IPs.  I think you can now see why your single IP block is not working.

Thanks for the good laugh!
MrC

---

### Post by andytof47 on 2007-03-29
Hey glad you liked the humor :)

I really found that info helpful.

I'm still trying to understand how you got that information - I know the answer is right in front of my face......

I tried a standard whois for media.revver.com but it says there are no records what am i doing wrong???

Also I entered the three different addresses into the bannedsitelist file but the feed still comes through hmmmmmmmmm............

However I know that it isn't a big problem because other feeds are now being blocked even inside democracy so that good..... it's just a matter of blocking the right addresses 


Thanks for all your help - qualllllllllittttyyyyyy information mate

---

### Post by andytof47 on 2007-03-29
Ahhhhhh

dig A media.revver.com

of course it waaaaaaaaaaaas right in front of me



'awesome another tool to add to my box of goodies - i'm a newb but i'm learning


thanks again


is there a reason why after i did dig A media.rervver.com the second time it only spat one ip back?????

just curious

---

### Post by Mr. C. on 2007-03-29
It's always easier to find what you're looking for, when you've seen it a thousand times.  There can be so much data, its overwhelming.

Your capture showed a series of frames, each one a conversation between two hosts.  I looked for the conversations with the host you indicated.  This is where knowing the Ethernet and TCP/IP layers comes into play.

The URL is part of the payload of the TCP connection to the remote host.  I simply looked for HTTP messages in the Info section of Wireshark.  I saw a HEAD request for a .mov file, and then inspected the HTTP dialog, which shows the host and URI.

Whois won't show you what you want.  It will show some registrar information, and other stuff, not useful to you for this task.

You need to use nslookup or dig to examine the DNS records for a hostname.  I requested all the A records for the hostname specified in the URI request; there were 3 of them.  So you need to block all 3.

If additional feeds are coming through, you need to examine those in like fashion, and block those to earn your green belt!  There may be many sites to block.  (This is what makes blacklists so attractive to many.)

Hope this helps a little more,
MrC

---

### Post by Mr. C. on 2007-03-29
> **andytof47 said:**
> 
is there a reason why after i did dig A media.rervver.com the second time it only spat one ip back?????

just curious

Are you using your router as a nameserver  (check /etc/resolv.conf for nameserver lines) ?

MrC

---

### Post by andytof47 on 2007-03-29
yeah I am,

but not too worried about that now - is there any reason why traffic is still coming through from this site now that I have blocked in every way I thought I could?




again it's driving me nuts


thanks MrC

---

### Post by Mr. C. on 2007-03-29
Ok, so your router's DNS server is not providing all the answers it should.  Cheap, commodity routers have poor DNS implementations.  Use your ISPs instead, or setup your own.

Of course there is a reason why some traffic is coming through; but we need raw data to discover why.  Have you verified that these IPs are being blocked ? 

MrC

---

### Post by andytof47 on 2007-03-29
> Have you verified that these IPs are being blocked 

hmmm The data is still coming through so I can verify that it's not blocked :) 

but seriously I thought that the litmus test was traffic blocked or not blocked - and this is done either through ur blacklists, bannedsitelist or as I am contemplating even via iptables  (althought we both know that I shouldn't be trying this approach hehe wink wink nudge nudge ay ay - I think we both know what i'm refering to here - isn't that right "sensai" :) )

cheers again

---

### Post by Mr. C. on 2007-03-29
Using iptables to block larges lists of IP addresses is too large a hammer, and all traffic pays the price in terms of performance.  Consider that each packet must be matched against entire chains, and only then can it be forwarded.

It is better to block at the application level when possible, so that only such applications are penalized, and other traffic performance is unaffected.

I'm not sure I understand - are you saying traffic from the blocked IPs is not being blocked, or that similar traffic from other sources is coming through.  The former will require figuring out why you blacklist is not being effective, the later will require more tcp dumps, which is probably a good idea in either case.

MrC

---

### Post by andytof47 on 2007-03-29
yeas it is definitely blocking the files now


however I still receive porno thumnails - More anaysis is need to work this out but I am absolutely sure I will knock this on the head


Many many thanks MrC:)

---

### Post by Mr. C. on 2007-03-29
You're welcome.  Post more captures if you need more help.

Cheers,
MrC

---

### Post by andytof47 on 2007-03-29
I just checked the website that the feeds are coming from and loaded the page in my browser - I think the reason I am getting the thumb nails is because it is a

https - site and DG doesn't filter SSL

so although I want to get rid of these thumbnails ------ Alas I fear i am stoooofed? is that correct thinking

---

### Post by Mr. C. on 2007-03-29
HTTP or HTTPS still must resolve to an IP address; just block the appropriate IPs.  The IP cannot be hidden.  If thumbnails are being passed encrypted, block the site entirely, not allowing any connection to be made there.

MrC

---

### Post by andytof47 on 2007-03-29
> HTTP or HTTPS still must resolve to an IP address;

Once again words from a true master of the art of HTTP

Thanks (bows humbly - whilst never making eye contact as a sign of true humility. bows again maintaing the downward gaze as not to offend. Bows one final time as he exits the dojo and falls down the stairs just outside of the entrance breaking every bone in his upper torso ever yet maintaining NO eye contact :) )



Many Many Many thanks - You have just averted a tragfedy yup sir - In my panic of proxy sites and perhaps porno that uses https my head was spinning however the old 

trace them back to an IP address trick never fails:)

---

### Post by Mr. C. on 2007-03-29
I now call you Master!

---

