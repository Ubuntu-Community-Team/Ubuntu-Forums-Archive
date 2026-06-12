---
title: "Going nuts over webserver"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by SeanCly10 on 2007-02-23
Greetings all,

I want to preface by saying that making this post is my last resort. I'm not one who normally asks for help, always been a fiddle-with-it-until-it-works kinda fellow, but this thing has got me feeling badly out of my element.

I've worked with computers for about 17 years. I know protocol and procedure for troubleshooting and problem solving, and I'm no stranger to these machines by far. My issue is, though, that that entire time has been spent on Windows machines. I know them fairly well, at least up to XP, and so when there's a problem with one, I usually have at least a basic idea what's wrong, and how to fix it.

With the advent of Vista, and all the assorted garbage that Microsoft has put into it, I am in no way willing to stick with an OS that will do it's best to screw me for nothing more than being a customer. So, I decided to take a leap out of my little box and try out Ubuntu. Thus far, I've enjoyed it a lot. The customizability (is that a word?) appeals to my tinkering nature, and I've never been scared of a command line. I enjoy seeing all the things that can be done with it, and the price tag isn't at all bad either.

Problem is, when a serious issue comes up, I have no frame of reference whatsoever in which to even fathom a fix, much less attempt one. Given time, I might be able to hammer one out, but with a new baby and a full-time job, scads of time to devote to chasing a fix just isn't there.

All that pointlessness said, now I come to my issue. What I've been trying to do is to set up a simple web server, using Apache2, so that my folks in another state can see pics of our son. Networking has never been my forte, but I figured that some searching would find me my answers, and it did find me a few. But now I've run into a wall I can't find a way around. Despite everything I've tried, my folks back home can't get to the server, and nothing I've tried has done any good.

Here's what I've done so far. To start with, I'm running Ubuntu Ultimate Edition, which is Edgy Eft, and came with Apache2 preinstalled and at least partly configured, best I can tell. My PC sits behind a Linksys WRT54G wireless router (although I'm using the wired connection) on a hi-speed cable modem. I know that I'll need to use port forwarding on port 80 to allow access through, and I'm thinking that I'll need a server-side static IP to forward the port to.

I say that Apache is at least partly set up right because I can access my web page by pointing my browser at the internal IP address, but trying to do that from outside the router gets me nothing. 

My question: can someone recommend me a howto, from start to finish, on the way to set up Apache and configure the router and connection to allow outside access to it?

Thanks for any help, y'all.

---

### Post by RandomJoe on 2007-02-24
What sort of Internet connection do you have?  If it is a standard residential connection, most block port 80 (and a host of other well-known ones) in an attempt to cut down on spam/worms/etc.  (Or so they say...)

If this is the case, you will need to run your web server on a different port.  Try some random high-numbered port - 8080 is commonly used for proxies and such and is easy to remember.  Or, preferably, sign up for a "home office" account (if available) that gives you fixed IPs as well as permission to run servers.  That costs more, of course...

Other than that, it's a pretty simple problem and it sounds like you should have everything accounted for.

---

### Post by Banthaman on 2007-02-24
you probably need to forward port 443 for apache to work right. Test it by opening your browser and entering your routers external IP/folder_you_want and see if it opens anything. buy default it will have a "apache is working" page all you need to do for a alblum is 

1. cheap and dirty - creat a folder in the var/www/your_alblum_here 
2. put a site index page in there with thumnails
3. have a lamp server (apache-php-mysql) server setup and run a dynamic web alblum(harder to setup but nice in the longrun I'm using phpBB2 with the alblum addon but you can find your own method)

---

### Post by koenn on 2007-02-24
> I say that Apache is at least partly set up right because I can access my web page by pointing my browser at the internal IP address, but trying to do that from outside the router gets me nothing.
This indicates that you have Apache up and running. The problem is probably with your networking, not with your apache configuration. 

I do understand correctly that you can get a web pache to show on a PC other than the web server, but only from the LAN, nor from outside, right ? 


> I know that I'll need to use port forwarding on port 80 to allow access through, and I'm thinking that I'll need a server-side static IP to forward the port to. This is probably the answer to your problem, and i suppose you have not implemented it yet. 
Here's a quick and dirty howto:

A- set up port forwarding.
1/ find out the ip address of your web server. Let's assume its something like 192.168.0.1
2/ find out the IP address that is visible from the internet. You'd find this in the config of your router (as "WAN IP", "external IP" or something similar. You can also visit a web site that displays visitor's IP addresses, such as [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
let's assume you find your external ip address is 85.81.83.223

3/ from any PC on your local network, you should be able to find the index page of your web server by browsing to [http://192.168.0.1/](http://192.168.0.1/) but that address is useless for external visitors : they'd have yo use [http://85.81.83.223/](http://85.81.83.223/) . This is actually the (external) address of your router, so you have to tell your router to
forward incoming trafic on 85.81.83.223 [or: external interface]: tcp port 80 to 192.168.0.1 : tcp port 80. You probably find this in the router's config screen under NAT /  port forwarding.
people browsing to [http://85.81.83.223/](http://85.81.83.223/) will then end up at [http://192.168.0.1/](http://192.168.0.1/) .and see your web pages there

B- DNS ?
people don't like to use IP addresses, and the address might change aif you're using an ordinary home internbet account. You can work around this by registering an account at a dynamic DNS service (eg. [http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/) )  that will bind a hostname to your public IP address (and track changes to the public IP address) so people can browse to something like [http://myserver.ddns.net](http://myserver.ddns.net) in stead of [http://85.81.83.223/](http://85.81.83.223/)

C- security
port forwarding allows direct access from the internet to your webserver (LAN) and should be regarded as a risk. You might want to enable some firewalling on the router and use Apache's config to limit access.


> If it is a standard residential connection, most block port 80 (and a host of other well-known ones) in an attempt to cut down on spam/worms/etc. (Or so they say...) If this is the case (and my assumption that port forwarding is the sollution is correct), you'd have to forward a different port, say 8080. there's two ways :
a. forward incoming trafic on 85.81.83.223 : tcp port 8080 to 192.168.0.1 : tcp port 80. 
b. forward incoming trafic on 85.81.83.223 : tcp port 8080 to 192.168.0.1 : tcp port 8080. - in this case you need to configure Apache to be listening on port 8080

in both cases, your visitors would need to browse to http:// 85.81.83.223:8080/ or [http://myserver.ddns.net:8080](http://myserver.ddns.net:8080)


> 
you probably need to forward port 443 for apache to work right This is irrelevant unless you want to use http**s**.in stead of http. When you use https, you'd also have to configure user authentication.

---

### Post by SeanCly10 on 2007-02-24
SUCCESS!!!

It worked! Well, at least mostly. Entering the DynDNS name that I registered only sent my test to the DynDNS homepage, but plugging in the IP itself worked flawlessly. Wondrous!

Now, questions answered...

> I do understand correctly that you can get a web pache to show on a PC other than the web server, but only from the LAN, nor from outside, right ?

Just so. I've got a wireless laptop on the LAN that could get to the index page fine, but no one outside could.

> What sort of Internet connection do you have?

Standard home connection, right. If I find that I have the dedication to host a honest-to-God website, then I might go on with the home business connection, but for now what I've got seems to be doing me fine.

Thanks to all for everything!

---

### Post by dmizer on 2007-02-25
okay ... i've been at this one a while now, and i've set up more than several dedicated web servers with ubuntu.  so here's a list of things to look for.

1) i suggest basing your dedicated web server on dapper rather than edgy.  it's more stable and things are not as likely to break when an update comes down the pipe.

2) install a lamp server.  if you're comfortable with the cli, then i suggest that you not even bother with a graphical interface.  then to manage your server, you can install webmin via this howto: [http://www.ubuntuforums.org/showthread.php?t=195093](http://www.ubuntuforums.org/showthread.php?t=195093)

3) you'll want to install phpmyadmin (to manage your database), apache2, mysql, and php5.  look here: [http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page) for howto install all of these.

4) to have a nice looking, and secure, frontend to host out your photos use gallery2: [http://gallery.menalto.com/](http://gallery.menalto.com/)

with this set up, you'll be able to park your server in a dark closet without a monitor and never have to look at it.  and, you will be able to administrate it from any computer on your local network (windows or linux).

---

### Post by koenn on 2007-02-25
> **SeanCly10 said:**
> SUCCESS!!!
It worked! 

:) 

> 
Well, at least mostly. Entering the DynDNS name that I registered only sent my test to the DynDNS homepage, but plugging in the IP itself worked flawlessly. Wondrous!
It's possible this problem disappears in a few days when the binding between your external IP and your DDNS domain name has propagated to more DNS servers on the internet. 
Otherwise, you'd need to look whether the problem only exists when browsing from your LAN ( then you may have to tweak DNS on your LAN  a bit ) - or whether it also exists for external clients (then maybe you'd have to look at your DDNS account / setup a bit)

---

