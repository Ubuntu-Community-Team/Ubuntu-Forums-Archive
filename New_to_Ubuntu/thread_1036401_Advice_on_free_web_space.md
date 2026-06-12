---
title: "Advice on free web space"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Lakeside5 on 2009-01-10
I know I`ve asked this somewhere before, sometime, but ended up getting a little confused.. so I`ll try again.  I am looking for free web space, if that is possible.  Not web hosting, just the space because I am planning to use Hardy Heron server ltd 8.10 to practice and learn web serving. I have looked for free web space, but find places selling web hosting, along with the space. 
I am already using 8.04 server, and hosting a practice page. I have some free space from my local ISP account, which I was going to use to host my Joomla practice site, but then discovered that I can only host a simple HTML page with it. So I am wondering if there is actually free space out there that would support:  MySql database, Apache web serving, Joomla CMS etc.  And then, I am trying to figure out how a domain name would figure into all of this.  I actually had a free domain name registered,  but I used it with paid web hosting through Rochen, for a few months.  Is it possible to get all I want (free domain name plus free web space that supports what I need to host a site like Joomla)? thanks for any advice.

---

### Post by perlluver on 2009-01-10
Check out [http://www.freehostia.com](http://www.freehostia.com), they have MYSql, Apache Server's, Php, and loads of other features.

---

### Post by osquid on 2009-01-10
I used [www.000webhost.com]("www.000webhost.com") for a few months before upgrading to a paid host in May of 2007. Full cPanel admin and a subdomain. PHP, MySQL, no ads, etc.

Pretty nice for a free host.

---

### Post by Lakeside5 on 2009-01-10
Thanks very much for the quick replies and advice osquid and perlluver. I checked them both out and decided to get a free domain name from webhost.com. They both have great free webhosting packages, but I only want the space, I want to host it myself, and realized I still would need a domain name for that. I had one before from no ip, but now when I try to use the free domain service from there, I must be doing it wrong or something, it keeps trying to charge me! So now I have a free domain name, (even though it looks silly, the domain is silly, and my domain is actually a sub domain after it, oh well somewhere to start).  I`m still at square one though because I only wanted SPACE and all I find is free hosting that INCLUDES space (albeit, with great services like php, apache, php etc.) I want to be my own server but I need space.  Can I use their space, but just my own webserver, how do I do that. confused

---

### Post by Lakeside5 on 2009-01-11
Well, I have a nice account set up at 000webhosting, but I only wanted the web space, so I asked my question there, and got a response:  `Wait, huh? If its hosted off your server, than its hosted off your server, but if its hosted here, then its hosted here, theres not a way to use the web space, but host it off your server. If I'm reading what your trying to do right, its not possible.` So maybe it isn`t but I am still wondering because:  My ISP provider (account for my internet connection) provides some free web space, which I am using to host a web page with a Ubuntu server in my computer. The problem is that it does not support php, or MySql etc- in short, I cannot put a Joomla web site up there with it.  Is there ANY place, do you think, that would provide that type of free web space? If not, I will stop asking this silly question lol. thanks again.

---

### Post by lazyart on 2009-01-11
Methinks you're a little tongue-tied with terminology.

It sounds like you want your own web address which is run by your Ubuntu server... correct?

---

### Post by ithanium on 2009-01-11
I used this for my websites and worked ok.
[http://ej.am/](http://ej.am/) you need to make 10 posts on their forums and after this you will get your free hosting :D

---

### Post by Paddy Landau on 2009-01-11
Lakeside5, I'm getting confused reading what you're asking.

The computer that hosts the website is the same computer that provides the space.

"Host" is a metaphor; just as a hotel might host a guest, you can't have the hotel host the guest while the guest stays at a different inn. That wouldn't make sense.

In the same way, if you want to host the website on your own computer, then your own computer becomes the host, holding the website. It would become a server, serving pages to anyone on the Internet who would ask for it. Your own computer would need:


[LIST]
[*]The space to hold the website (normally not a lot at all, especially if you're just playing around, e.g. with Joomla).
[*]The programs to provide the service (i.e. to be a server), which would include Apache, PHP, MySQL, and whatever else you needed.
[*]A suitable firewall where you could guard against hackers while allowing genuine requests through.
[*]A domain name is optional, because people would only need to know your IP address. Obviously, a domain name makes it easier ([www.mynicepage.com]("http://www.mynicepage.com") is easier to remember than 73.123.6.434). I don't know anyone that would give you a free domain name, but they cost under $10 per year on GoDaddy, so it's no big deal.
[*]Broadband big enough to handle however many requests you might get.
[*]A computer powerful enough to handle however many requests you might get.
[/LIST]

That's why most people go with a professional host, because the host worries about all that stuff. You just have to worry about putting the pages on.

The advantage of hosting on your own computer is that you have total control. The disadvantages are that you need to administrate all the programs and firewall, and keep your computer on all the time for people to be able to access your webpages.

Web hosts are jolly cheap these days, although I understand that for just experimentation you wouldn't want to pay even that. You've been given a couple of great ideas; it's your decision how you want to proceed!

Good luck.

---

### Post by Lakeside5 on 2009-01-11
Hi lazyart.  Yes, I think that`s correct.  Ithanium- I will check that out too. Thanks Paddy, for explaining it so well, and I had thought it was something like that. I guess where my confusion came from, was that my ISP provides some free space without the hosting (as part of my internet account), so I had thought I could get the same thing from somewhere else- only, from somewhere that would allow the use of php, MySql etc. I have my own server, that I am actually using right now to host a page using my isp`s space, but it can`t host Joomla, only a small, html type thing. I am planning to get paid hosting down the road for my (hopefully :) ) future Joomla website clients.  I just wanted to be able to host one example website of what I can make them, for now, and it wouldn`t get much traffic or actually be used that much. I hear that it is possible to get web space for my purpose, but it would cost money, maybe I will got that way. thanks again for all your help everyone.):P

---

### Post by ugm6hr on 2009-01-11
> **Lakeside5 said:**
> `Wait, huh? If its hosted off your server, than its hosted off your server, but if its hosted here, then its hosted here, theres not a way to use the web space, but host it off your server. If I'm reading what your trying to do right, its not possible.`

This isn't possible.

You do not need any webspace, since you want to host the site locally.

When you "buy" a host - you pay for:
1. "webspace" = the volume of files that are stored on their server
2. "bandwidth" = the amount of accessing / downloading from their server that people visiting your website use

If you want to use your own server, you would have to have:
1. HD space for your webpages etc.
2. Enough bandwidth from your ISP to cater for any visitors to your site

As mentioned, a domain name / fixed IP is up to you.

---

### Post by Lakeside5 on 2009-01-11
Well I really hope you are right, ugm6hr :)  I am going to try something then. I am already hosting, locally (just for development purposes as I work on it, within my computer) a joomla website I made. I will try uploading it with the Hardy Heron server I have on here, that is already hosting a simple html page `out there`.  My isp provider has already said that this can`t be done, as they don`t support anything that `complicated` (they are referring to the php, and MySql etc.)  See, I am still getting confused, as I had thought as you did, that the `space` that`s being used, is actually in my own computer as I am being the web server, and I have apache, php, mysql on here in the hardy heron server.  But I will try and see what happens. thanks again.

---

### Post by ugm6hr on 2009-01-11
In fact, this has nothing to do with your ISP.  You do not need any extra help from them.

The only thing they will be concerned about is your bandwidth use, which, assuming your website is not going to be too busy, should not be a problem.

---

### Post by Lakeside5 on 2009-01-11
Thanks again.  I am indeed the queen of confusion lol. I am uploading Joomla as I type this (crosses fingers). Also I think where I was confused is, I wanted a domain name, but to get a free one, you  either have to get free (which I did) web hosting, or paid. The alternative, which I think I will do, is to actually pay for a yearly domain name of my own- it is pretty cheap as was pointed out. thanks.

---

### Post by ugm6hr on 2009-01-11
If you are not fussy - you can use uni.cc: [http://www.uni.cc/site/home.php](http://www.uni.cc/site/home.php)

If you have a fixed IP, you can forward to it.  Else, no-ip should allow that function (I have never used it).

---

### Post by Lakeside5 on 2009-01-11
Thanks, it looks good but it seems to be closed to registration for 2008, so it should be open soon, for 2009? lool thanks again.

---

### Post by Lakeside5 on 2009-01-12
Ok everyone, I have a dynamic dns. I signed up at DynDNS and got one, something like `BassWebs.selfip.com`. And I also have a domain name which I got from ooowebhost.com. But they are not the same thing (just checking, I am really bad at this lol). The domain name, BassWebs.net84.net is the domain, and Basswebs.selfip.com is not, but I would put that in my router, where it asks for host or something, to redirect my ip so it doesn`t keep changing? Hard to believe but I`m still confused, please forgive me. thanks

---

### Post by lazyart on 2009-01-12
:)  You're getting closer.

You can simply use the address you've gotten from DynDNS.  You'll need to run an application that will update your IP address when it inevitably changes.  Some routers can do this for you and I think you've found that already.

You would put in the address you've gotten from DynDNS into your router and probably your account information and it should keep you synced up.

From there you forward port 80 to your server that is hosting the page.  Then ask someone to check out your site to see if it works.

Eventually you might want to purchase your own domain name... and they are terribly cheap.  Mine was totally an impluse buy, but I've got it for three years and will hang onto it afterwards.

Good luck!

---

### Post by Lakeside5 on 2009-01-12
Thanks! I confess, I did do this briefly (until all the  windows viruses crashed my computer ;( ) using WAMP, somehow, my biggest confusion was where and how to enter the info from the DynDNS site into the router, so I might ask again with screenshots, when I start doing it :) So the free domain name I got from 000webhosts can`t be used then? I want to actually get a paid domain name, but have to wait until I can put money in my paypal, and then that takes a few days to get in there, I don`t have a credit card lol.
But at least I am on the right track. thanks guys.

---

