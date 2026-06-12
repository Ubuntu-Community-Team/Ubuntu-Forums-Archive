---
title: "Apache index accessible from lan ip but not wan ip?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Apache0c on 2009-05-03
I'm sorry, I'm a linux noob. This should be a pretty simple task though. I have been searching and searching for about 2 weeks now and I can not figure this out. I am about to pull all my hair out. I'm literally having a nervous breakdown over this. I can not find a decent straightforward answer anywhere.

I have Apache v2.2 installed and running. 

I set the fixed lan ip for the server to 192.168.1.101 in the router's config.

I have my router configured to allow incoming connections on port 80 for my webserver machine.

I can access the index.html file in the var/www folder from any machine on my lan at [http://192.168.1.101](http://192.168.1.101)

But nothing is there when I point my browser to http://<my wan ip>

So it  must be something I need to change in the Apache2.conf file? 

Please help me. I know, I'm a pathetic noob and I am very sorry for taking your time with my ignorance. I'm running Linux Mint 5 LTS which is based on Ubuntu Hardy. Thank you very much for your help, it is greatly appreciated.

---

### Post by nandemonai on 2009-05-03
> **Apache0c said:**
> I'm sorry, I'm a linux noob. This should be a pretty simple task though. I have been searching and searching for about 2 weeks now and I can not figure this out. I am about to pull all my hair out. I'm literally having a nervous breakdown over this. I can not find a decent straightforward answer anywhere.

I have Apache v2.2 installed and running. 

I set the fixed lan ip for the server to 192.168.1.101 in the router's config.

I have my router configured to allow incoming connections on port 80 for my webserver machine.

I can access the index.html file in the var/www folder from any machine on my lan at [http://192.168.1.101](http://192.168.1.101)

But nothing is there when I point my browser to http://<my wan ip>

So it  must be something I need to change in the Apache2.conf file? 

Please help me. I know, I'm a pathetic noob and I am very sorry for taking your time with my ignorance. I'm running Linux Mint 5 LTS which is based on Ubuntu Hardy. Thank you very much for your help, it is greatly appreciated.

Routers will not forward requests from the internal LAN to a WAN address. Simple as that.

To test it's up from the outside use a site like: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) or get a friend on a different connection to test for you. :)

---

### Post by Apache0c on 2009-05-03
Thanks for your help! I appreciate it.

Ok, so I do also have a dyndns domain associated with my wan ip. And when I point my browser to http://<my dyndns domain> it still times out with no response. :(

What am I missing here? Thanks again.

---

### Post by nandemonai on 2009-05-03
> **Apache0c said:**
> Thanks for your help! I appreciate it.

Ok, so I do also have a dyndns domain associated with my wan ip. And when I point my browser to http://<my dyndns domain> it still times out with no response. :(

What am I missing here? Thanks again.

Same deal as above. The router will NOT forward requests from an internal IP to an external.

To get around this and access your server by the dyn name you need to edit your hosts file on the client NOT server. /etc/hosts

Put an entry in there that says:

xxx.xxx.xxx.xxx server.name.foo

Local IP - Domain name.

That will forward all requests to that domain to your internal IP for the server.

As I said above, the only way to test from the outside is with a 'Test my Firewall' type site or another connection. 

Hope that clears things up for you :)

---

### Post by alphacrucis2 on 2009-05-03
> **Apache0c said:**
> Thanks for your help! I appreciate it.

Ok, so I do also have a dyndns domain associated with my wan ip. And when I point my browser to http://<my dyndns domain> it still times out with no response. :(

What am I missing here? Thanks again.

The request has to come from the external (WAN) interface of the router for the port forwarding (DNAT) to work.

---

### Post by Apache0c on 2009-05-03
Ok, thanks a lot guys. You rule.

And it does work now, I had my friend test it. I knew it was something simple. It worked all along I was just too stupid to know what was going on. Thanks again.

---

### Post by Apache0c on 2009-05-04
I'm having another issue now that I was hoping you guys could help me tackle. I installed ddclient using the package manager and used one of the provided conf files on the dyndns website. But it doesnt seem to be working. I tested it by going in to my account on dyndns and changing the ip address for my webserver. Then I restarted my computer. I have the ddclient.conf file set for daemon=60. So I waited a while but it never updated. Is there something I left out? Thanks

---

### Post by Alterax on 2009-05-04
Just time, I'll wager. The update may have been sent, but sometimes it takes a bit for DNS entries to propagate.  Relax and take a break; sounds like you've learned a couple of things so you've earned one, in my opinion!

---

### Post by nandemonai on 2009-05-04
> **Apache0c said:**
> I'm having another issue now that I was hoping you guys could help me tackle. I installed ddclient using the package manager and used one of the provided conf files on the dyndns website. But it doesnt seem to be working. I tested it by going in to my account on dyndns and changing the ip address for my webserver. Then I restarted my computer. I have the ddclient.conf file set for daemon=60. So I waited a while but it never updated. Is there something I left out? Thanks

Likely just time as the above poster said. One thing to think about though is does your router support this function itself?

My last two have had support for dynamic DNS out of the box (Netcomm and and now a Billion), pick your DDNS provider, put in your details and anytime your WAN IP changes it auto updates :)

Worth a look at any rate.

---

### Post by Apache0c on 2009-05-04
Thanks guys. I did end up taking a break last night as I fell asleep at the keyboard, heh heh.

nandemonai, I'm not using the router's ip status to update. I'm using the code that pulls my ip from the dyndns checkip page. I figured that would be the easiest way to set it up and not have to worry about hardware compatibility. 

 I'm sure you're right, I'll give it more time. Hopefully it doesnt take too long though because I wouldnt want my site to be down because of the slow update. Thats why I changed "daemon=" in the code to 60 when it was set at 600 seconds.

Thanks again for all your help guys. I'll let you know if it does finally update.

P.S.

Just so you have a little background on the problem, I started to install ddclient manually, I set up the conf file and the cache directory. But then I couldnt find a tutorial that explained the pid file for the startup script so I went to the package manager and installed ddclient from there. That created the startup script and I also went back after that and checked my conf file and it was still there and so was my cache dir. I just cant help thinking I missed something though.

This is my conf file:

> # Basic configuration file for ddclient
#
# /etc/ddclient.conf

daemon=60
cache=/tmp/ddclient.cache
pid=/var/run/ddclient.pid
use=web, web=checkip.dyndns.com/, web-skip='IP Address'
login=<my username here>
password=<my password here>
protocol=dyndns2
server=members.dyndns.org
wildcard=YES
<my.domain.here>
custom=yes, example.comDo I need to change "cache="? Because the readme told me to make the cache dir here:

/var/cache/ddclient

Thanks for all your help guys!

---

### Post by Apache0c on 2009-05-04
Or should I start a new thread for ddclient questions?

---

