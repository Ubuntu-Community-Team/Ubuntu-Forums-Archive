---
title: "How hard would it be for an absolute beginer to use Ubuntu to run a wordpress blog?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by w.g.hanna on 2008-12-13
I want to get my fiance a web site for christmas with her own web address.  What I'd like to do is use a wordpress blog template.  One option is to purchase web hosting - something I know little about.  

Another option would be to run the website off of my computer, or use an old computer (maybe running xubuntu or another lightweight linux).  problem is:  i don't know anything about anything.  How hard would it be to learn, and where can i find a step by step for numbskulls?  Is this something I could get up a running with a solid day of focus?  Is this something I can do without advanced command line use or text documents?  Or am I just better off shelling out the cash and using somebody else's interface?

If the latter is the case, can anyone recomend a good web host for a beginer to set up a wordpress blog on?

---

### Post by Titan8990 on 2008-12-13
You will likely encounter issues with your ISP over them. Contact them and ask them what their policy is on web servers.


> Is this something I can do without advanced command line use or text documents? 


Where is the fun in that?

IMO config files will always be easier than bloated GUIs.

---

### Post by binbash on 2008-12-13
I suggest buying a webhosting.If not, you will install LAMP (apache,php,mysql - you can search for howtos if you dont know anything) then you will go to wordress , download and install it.There is no one single howto.Install apache first and be sure it is working, then you can google wordpress installation etc if you have problems.

---

### Post by Kareeser on 2008-12-13
With no prior experience with Ubuntu, it took me a couple days of false starts and learning to get going.

However, if you want, we can guide you through it. The entire process should not take longer than an hour... if you're lucky... (relaying messages over a forum ain't the easiest)

Again, your ISP must be okay with servers, of you may get into a spot of trouble...

---

### Post by mikjp on 2008-12-13
> **w.g.hanna said:**
> problem is:  i don't know anything about anything.  How hard would it be to learn, and where can i find a step by step for numbskulls?  

It's not difficult, but it is probably cheaper and easier to use some webhotel. I pay 15 &#8364; / year for my site (not the one in signature :) ), including the domain name & webhotel.

---

### Post by capn_hector on 2008-12-13
how hard to get up and running, if you have a good problem solving ability and a willingness to run into a wall several times before you find the door (google will help you find the door)  then its not that hard to get a lamp server up and running (see above post) now as far as which hosting service is the best for a wordpress site is the same as the debate between the 9mm and 45acp  just look around the web if you decide you dont want to run your own server (which is exposed to the nastyweb and hackers which means hardening the server) and see what the different hosting services offer.

---

### Post by aysiu on 2008-12-13
Wordpress has links to a bunch of hosts that have easy installation and update maintenance for Wordpress:
[http://wordpress.org/hosting/](http://wordpress.org/hosting/)

---

### Post by billgoldberg on 2008-12-13
> **w.g.hanna said:**
> I want to get my fiance a web site for christmas with her own web address.  What I'd like to do is use a wordpress blog template.  One option is to purchase web hosting - something I know little about.  

Another option would be to run the website off of my computer, or use an old computer (maybe running xubuntu or another lightweight linux).  problem is:  i don't know anything about anything.  How hard would it be to learn, and where can i find a step by step for numbskulls?  Is this something I could get up a running with a solid day of focus?  Is this something I can do without advanced command line use or text documents?  Or am I just better off shelling out the cash and using somebody else's interface?

If the latter is the case, can anyone recomend a good web host for a beginer to set up a wordpress blog on?

One.com has web hosting for around 2-3 euro a months. I use it, the service isn't great but the website hasn't been down since I use them.

--

Running a website on your own box shouldn't be that hard.

You should have a static ip (most people have a dynamic one). But I believe there are workarounds if you have a dynamic one.

Then buy a domein name (lets say htt://yourownblog.com). These go for around 20 euro a year.

Then set up your lamp server and download and install wordpress.

The install instructions are on wordpress.org.

Setting it up is pretty easy.

--

That being said I wouldn't never host my own website. 

It's just that much easier to pay for the hosting.

---

### Post by greg@localhost on 2008-12-13
Although it's trivial to host your own site in your garage or whatever - it really isn't worth the hassle these days with web hosting being so cheap.

Remember that you will need to pay for the extra electricity, you will need to ensure that you have a cool room and that you have a reliable machine to run it on (after all you'll want to eave it on 24/7).

Also consider the noise and the bandwidth overhead.

Anyhow, here's a [guide to setting up Apache 2]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html")

If you want to set up the server yourself, then get yourself a VPS or dedicated server. Most hosts will let you choose the OS that you would like to run. You can then configure it via an SSH connection.

---

### Post by chrisod on 2008-12-13
You can do the blog at Wordpress.com for free. I would start there. If you want your own domain name buy it fromm any of a million places for about $10 a year and point it to your Wordpress.com blog. If she really gets into blogging then maybe you can move it to her own domain on your own hosting account. As somebody said above, it's not particularly hard to host it on your own box, but there is a lot of upkeep with security and software updates etc. Given the abundance of free blog hosting available and cheap hosting if you want more control, the only reason to do it yourself is for the learning experience. If you just want to get a blog up with minimal hassle outsource.

---

### Post by Kellemora on 2008-12-13
Hi WGH

I'm not saying this to be nasty, just factual!

We tried using the WordPress Blogging program, as well as their web site.
Every single time we finally found work arounds for all the bugs, they would update something and we would be back to square one all over again.
We lost hundreds of manhours every time they changed something, and eventually just gave up trying, because we knew they would mess it up again in less than a week.

Your best bet is to set up a REAL web page and then add a blogging feature to it, you can still use the Wordpress program for this, but omit their pages when doing so, just use the fields as they never change those.

Or as an alternative, you might want to consider a low cost alternative such as [SquareSpace]("http://www.squarespace.com/") which can give you your own domain name too.
I have not used them, but a club I belong to moved from Wordpress to SquareSpace and 100% of their problems instantly ceased.  Have no idea what they charge, but it can't be much!

TTUL
Gary

---

