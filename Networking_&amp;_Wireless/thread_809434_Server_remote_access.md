---
title: "Server remote access"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by diasje on 2008-05-27
Hello, i mounted a new webserver for my work team, its a samll and very simple computer.

 

It has Ubuntu 7.10, Apache2, PHP5, MySql.

 

All the webpages and Databases are working fine.

 

I am behind a Proxy, that only allowa to connect to the server within the company network.

 

I use Putty to access this server from my workstation, and it works fine.

 

The problem is that  I'm going on vacations, and my team manager, asked if its possible for me to access it remotely from home, if  necessary.

 

I've been trying to install hamachi and vnc4server, but on hamachi, after its installed I cannot login, and i dont now how it works, with my logmein account; in My Computers page i cannot see the server.

 

The server has a internal network static IP.

 

I was thinking if hamachi is the same thing as the other logmein programs for windows, where I can access to my windows box at home, from work.

 

The other thing is that I have a newsletter program, that uses php mail, sendmail or smtp to deliver the news emails internally.

I have installed sendmail and exim4, but the program says that the e-mail was sent but none of my coworkers received it.

Is it possible to install a webserver, and use my gmail account?

---

### Post by SpaceTeddy on 2008-05-28
> **diasje said:**
> I am behind a Proxy, that only allowa to connect to the server within the company network.

can  you please draw a (simple) picture of this so i can undestand what is where and how it is connected ?
> **diasje said:**
> 
 The problem is that  I'm going on vacations, and my team manager, asked if its possible for me to access it remotely from home, if  necessary.

well, that's really gonna be a good vacation :(
> **diasje said:**
> 
I've been trying to install hamachi and vnc4server, but on hamachi, after its installed I cannot login, and i dont now how it works, with my logmein account; in My Computers page i cannot see the server.
i've never used hamachi, so i cannot help here, really. Maybe someone else has an idea ?
I only use openvpn Servers for that, but i guess that is a little overkill for you, to configure a full blown vpn environment.
> **diasje said:**
> 
The server has a internal network static IP.

this sounds like you might need to do a forwarding on your router which (should be) connected to the internet at all times. But Again, i need to see a picture of your layout to do a more... specific analysis :)
> **diasje said:**
> 
The other thing is that I have a newsletter program, that uses php mail, sendmail or smtp to deliver the news emails internally.

I have installed sendmail and exim4, but the program says that the e-mail was sent but none of my coworkers received it.
did this newsletter ever reach anyone yet, or is that what you want to do, but have not gotten it to work yet ?
In general, if you use an internal email-server, you will either need to configure a smarthost which you can relay the emails to, or you need to install a pop3/imap server aswell and then give everyone on the machine an "internal" email account. Most Email-Providers block email from an unknown source (and that for good reason)
> **diasje said:**
> Is it possible to install a webserver, and use my gmail account?
this question i do not understand ? what do you want to do here ?


Sorry i am not of more help (but hopefully will be in the future) :)

---

### Post by diasje on 2008-05-29
I work in a company, that has a proxy server, and we connect to the outsite network thru this proxy.

Our company has several teams, and me and my team have made a small server, to have our personal forum, databases etc. But as we have this proxy we cannot connect to this server from outside our network. The IT´s are not as flexible as we would like, so the will not help us and will not provide us one external IP to the server.

Vacations is vacations, but no one els now how to work with this server, and me and my team manager dont whant anyone els messing with the server.

Its only to work if needed.

I am using CCmail 1.0 as a php newsletter php script:

[http://www.cicoandcico.com/ccmail-10/](http://www.cicoandcico.com/ccmail-10/)

And i have been messing with the script and the server for hours, and nothing came out from it, nobody received any e-mails.



I have asked about hamachi becouse i have read so mutch about it, but i cannot understand it.

For 3 or 4 days i have been looking for something.

I cannot mess with the router, i am only a simple worker that has a real messed mind :lolflag:

Now about the mail server and gmail.

I have a gmail account, and is it possible to configure a webserver or script to send e-mails (or newsletters) from the my smtp.gmail.com account?

Thanks for your help.

---

### Post by SpaceTeddy on 2008-05-29
> **diasje said:**
> I work in a company, that has a proxy server, and we connect to the outsite network thru this proxy.

Our company has several teams, and me and my team have made a small server, to have our personal forum, databases etc. But as we have this proxy we cannot connect to this server from outside our network. The IT´s are not as flexible as we would like, so the will not help us and will not provide us one external IP to the server.

i don't like IT's guys who think they are not in a service business... but that does not solve your problem.
> **diasje said:**
> 

Its only to work if needed.

right. This is going to be a little... tricky. If you are using a proxy for http connections, i am guessing that you cannot open SSL-encrypted sites either. Which means you are pretty much blocked off from the internet and have no way of a direct connection (let alone an INCOMING connection). If your setup is like i would do it to totally block of a network, i'd say that hamachi does not work because it simply gets blocked at a firewall somewhere. 

The easy answer to this is - convince your IT guys.

The hard (possibly very long) way is go around them. In that case i must warn you that you will probably get into a fight with the IT guys if they find out, and that you will need to understand a lot if you are to evade their security. Also, this might not be a good idea at all.

But, neverless, here is (about the only thing i can think of) the way of evading about any firewall there is. 
There are two things you need for that:
1.) you need a relay somehwere on the internet that is freely accessable. Let that be your home computer, some root-server or a machine somewhere else. The important thing is, it MUST be able to have connection inbound to it. Without that, you're not going anywhere.
2.) The second is a requirement on your Site - you MUST be able to open encrpyted websites. so, if you can load sites like gmail.com from your internal network, and the bar in your browser goes either Yellow or green or whatever it colour it should have for an encrypted connection, you're good to go.

The basic idea is to forge a https (http over SSL) connection via the standard https port (443) which does NOT hold infomration about any website, but really is a VPN connection which will allow inbound connections through the firewall and proxy without them noticing. Again, i must mention that you can get yourself into trouble for doing this.

So, in plain english - you hijack a connection that is meant for websites and open a ssh-connection overlayed on that. 

I can explain on how to do that, but i would like to know first if you really want to do that, and if you have the outside relay that is needed (the relay CAN BE your own computer laptop if need be).

> **diasje said:**
> And i have been messing with the script and the server for hours, and nothing came out from it, nobody received any e-mails.

Now about the mail server and gmail.

I have a gmail account, and is it possible to configure a webserver or script to send e-mails (or newsletters) from the my smtp.gmail.com account?

yes, that is (of course) possible, but i'd say it doesn't work because a direct smtp connection is simply not allowed by your companies firewall. So your server can't even reach smtp.gmail.com.

there is a simple way to test this (if you have connectivity) - just telnet into the smtp you want to access. smtp servers always run on port 25 - to a 
```
telnet smtp.gmail.com 25
```
should give you an output like this:
> Trying 209.85.135.111...
Connected to gmail-smtp.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP s10sm983195muh.10
*quit*
221 2.0.0 mx.google.com closing connection s10sm983195muh.10
Connection closed by foreign host.

The italic writing is what i typed to close the connection. If you do NOT get this kind of output (for exapline, the connection is timing out) then your work is blocking connections on port 25. There is not way (apart from the realy, but this is then going REAL ugly) for you to send external emails. You will need to use an internal email account from your work and send it via that. 
Can't you ask your it guys to have another email account for the machine and then just use that account to send the email ? that way is easier... really :)

i hope i made some sense... ;)

---

### Post by diasje on 2008-05-29
Thanks very mutch.

The problem here, is that they think that they are the law, a few months ago we could open youtube and now we cant, because they thing we work better without youtube, but, i found a way :guitar:
to open youtube.

I have just pinged the youtube.com, and opened the website by the IP, and that works fine. They bloked only the domain name and not the IP, so we rule.

I will confess, i am an IT too, i am part of a team of customer service for one of the biggest computer company of the world.

And they now that we now mutch more then they do, so they block everything becouse they are afraid.

I have only been providing support for laptops, desktops, monitors, printers, AIO´s, etc. And i have only worked with Windows XP, and Vista.

But a few months ago i found out that Ubuntu is simpler that i was thinking about, and i give it a try, and now on my home i have 2 laptops with Xubuntu ans Ubuntu, ans 2 desktops, one is a small samba server and the other one (the oldest) is the test one.

Until 1 month ago, on my work e had on my workstation a xamp server with all our things, but its not as good as having a dedicated server.

So i picked up a old test computer that we have, opened it, cleaned it, and upgraded it, as far as we could.

It only as 96MB ram with a PII very slow, but for only 10 to 20 people use it so its quite good. And it works fine too.

I have read what you said, and if you explain how to do it, i will schedule a meeting with my team and our team leader and will explain them whats going on, and if they will agree with it.

About the SMTP server its not a must, so i will doo it later or do it in a external free webserver or something.

Ask waht you have to ask, and... sorry for my poor english.

---

### Post by SpaceTeddy on 2008-05-29
mhm - you did not answer the two most important question... so i'll repeat them in short.

1.) do you have a computer at home that can run the relay ? or was the part about your computers at home the answer to that ?. If so, i'd assume that your computers at home have a permanent link to the internet (connected 24/7)... that would suffice :)

2.) is it possible to load https websites ? without that it is not possible to tunnel the connection - at all. Since the "normal" web pages run through a proxy, the proxies will pick up on the encrypted payload of the connection and refuse it. The only way of getting this to work is by forging an SSL connection which looks like an https request. but since the connection is encrypted, the proxies cannot decide what is really carried - and what way.
So can you access https websites ?

And now, here is what i am thinking of:
You install the openvpn executable on your home pc and on the server at work. Then you generate a static key which you put on both computers so they can identify each other (this is essential - if this is NOT time, anyone could spoof your dns name and have instant connection to the internal server. This WILL bypass any security the IT-guys of your company have put in).
Once both computers have the key, your home computers needs either a static ip, or a static dns name. I'd think that the dns name is easier. I usually use no-ip.org, but any service will use. Sign up there, download the linux client, register a dns name, and then configure the client to the hostname. Once you are sure that your dns name is set properly, you can configure the server at work to connect to that name, or rather, to the openvpn process which is running on that machine. 
Since this is now an outbound connection your IT department should not be able to pick it up anymore as it looks no different to any other encrypted https request. Once the connection is between the two is established, you can tell your computer at home to utilize the openvpn connection to to a backwards connection to the server. 

The config files for the openvpn process are pretty much straight forward, the key generation is (fairly) simple. 
If you want to read more about that, here is a description on [[COLOR="Blue"]static ptp links[/COLOR]]("http://openvpn.net/index.php/documentation/miscellaneous/static-key-mini-howto.html") between openvpn processes, and here is a [[COLOR="Blue"]tutorial[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127") on how to do peer links with it (the tut is more than you want to do - but nevermind that :) )

so, are there any questions left from your side ?

---

### Post by aaa11 on 2008-05-29
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]
Wholesale Bape,BBC,Evisu Hoodies. Lacoste ,Polo T-
shirts.Evisu,Redmonkey,True religion Jeans. Nike ,Jardon shoes.
site :   [www.clothes-sneaker-wholesale.com](www.clothes-sneaker-wholesale.com)    (paypal accept)
msn :   [email]hhf770816@live.cn[/email]

---

### Post by diasje on 2008-06-02
Sorry, yes i have a computer do to the relay (i dont now what that is, but...)

My connection at home is 24/7 12MB at the end of this month i will have a 24/7 24MB connection.

At home and work, i can connect to https websites.

I will study this very carefully.

[IMG]http://diasje.890m.com/img/ubuntu2.png[/IMG]

---

### Post by SpaceTeddy on 2008-06-03
that connection is more than sufficient. Should work flawlessly. Here are the steps that you will need to accomplish in order to get this working.

1.) install openvpn on both computers
sample command for ubuntu:
```
sudo apt-get install openvpn
```

2.) generate the key on on server and securly copy it to the other (usb-stick, ssh connection or something like that - NEVER USE EMAIL !)
sample command for generating the key:
```
sudo openvpn --genkey --secret /etc/openvpn/static.key
```
remember the filename "static.key" you will need it in the config file !

3.) port forward tcp 443 on your home network from your router to your machine running the openvpn.
This i cannot help you with, as i don't know what kind of hardware you are running.

4.) get yourself a hostname from no-ip.org or dyndns.org
go to [no-ip.com]("no-ip.com") and sign up for a free account. 
 - log into that account
 - on the side, choose add
 - create a hostname you desire
 - download the client for no-ip *on your home computer* with this command
```
wget http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz
```
unpack the client
```
tar xvf noip-duc-linux.tar.gz
```
now, the next steps are probably not a good idea, but that is how i do it. quick and dirty, without packaging or anything. if you are unsure about this, try to find yourself a packaged version of the no-ip client or a different tutorial :)
copy the no-ip executable to /sbin with this command
```
sudo cp noip-2.1.7/binaries/noip2-Linux* /sbin
```
next, make sure that the /usr/local/etc directory exists. If it does not, create a symlink to /etc in /usr/local (or so i do it)
lastly, run the appropriate command (eiter 32bit or 64bit) for your machine to configure the no-ip client
for 32-bit:
```
noip2-Linux-32bit -C
```
for 64-bit:
```
noip2-Linux-64bit -C
```
that should ask you some questions. In that process it should ask you for your newly setup hostname. once that is done, the last thing to do is run the client by simply calling it without the -C flag.
If you want it to come up after boot, i suggest you take a peek at the start/stop scripts supplied in the archive, or you edit your /etc/rc.local accordingly

5.) write the config file for the openvpn clients. They are mostly the same, they just different in a few lines.
there are the following things to looks out for:
 - the work computer should ONLY use the remote command and should connect to your no-ip/dyndns name
 - the home computer should ONLY use the float and local option. It should NOT try to connect to the work computer, but passivly wait for a connection
 - both processes should use TCP instead of UDP and should use port 443 instead of the standard 1194

here is a sample config for the work computer
```
dev tun
_proto tcp_
**remote example.no-ip.org**
*ifconfig 10.17.0.1 10.17.0.2*
*secret /etc/openvpn/static.key*
daemon
ping-restart 60
ping 20
tun-mtu 1500
fragment 1500
mssfix
_rport 443_

persist-key
persist-tun

user nobody
group nogroup

status /var/log/openvpn-status.log
log-append  /var/log/openvpn.log

```

And here is a sample config for your computer at home:
```
dev tun
_proto tcp_
**local 192.168.5.5**
*ifconfig 10.17.0.2 10.17.0.1*
*secret /etc/openvpn/static.key*
daemon
ping-restart 60
ping 20
tun-mtu 1500
fragment 1500
mssfix
_lport 443_

persist-key
persist-tun

user nobody
group nogroup

status /var/log/openvpn-status.log
log-append  /var/log/openvpn.log
```

The **bold** lines need to be modifed by you. They need to match your setup. one *must* hold the no-ip name, one *must* hold the local ip-address of the machine running the process. It might be possible that you also need to add the "float" option to one or both config files

The *italic* lines are your configuration. You can change that, but you can also leave it. Note that the ifconfig statement is swapped. The first if always the local IP, the second the remote ip. These will be the IP's of the computers once they are connected to each other. 
Also they key is marked. I chose the same path as in my generation example, so you can leave it like that if you did not change anything. But you might need to fix that

The _underlined_ options are for pure interesst only. They make sure you are using a port 443 connection. Also, i am not sure if it is possible to only specifiy rport or lport alone - it might be that you need to specify both (i have not tested this setup - i am writing this of the top of my head)

6.) test the connection (see if it comes up) from work. You possibly (if it does not come up) need someone at your house to type in some commands/change configs if you have no remote access to your home machine from work. 
you can start the openvpn with the following command:
```
sudo /etc/init.d/openvpn start
```

if anything fails, check the logs for error messages :)

i hope everything worked fine. If you get here, you should be able to access the server at work from your home machine via the ip 10.17.0.1.

Ok, that was a very long post. i hope it helps (somewhat)

---

### Post by diasje on 2008-06-04
Wow... [IMG]http://ubuntuforums.org/images/smilies/star.png[/IMG][IMG]http://ubuntuforums.org/images/smilies/star.png[/IMG][IMG]http://ubuntuforums.org/images/smilies/star.png[/IMG][IMG]http://ubuntuforums.org/images/smilies/star.png[/IMG][IMG]http://ubuntuforums.org/images/smilies/star.png[/IMG]

---

### Post by diasje on 2008-06-04
> 3.) port forward tcp 443 on your home network from your router to your machine running the openvpn.
This i cannot help you with, as i don't know what kind of hardware you are running.

I use a Router, but i dont have any active firewall, couse i had some probs.

So i will not need to port forward.

I am using a Speed Touch ST546v6.

I am goint to have some fun doing this.

For now i am not going to do this in my actual work server, i will do this in a ubutu tester pc.

---

### Post by SpaceTeddy on 2008-06-04
the firewall is not a problem (usually) - the NAT is. Which basically means that your internal IP-addresses are not visible from the internet. That is what you need port forwarding for.

So if you have more that one computer running, you will need port-forwardig, regarless of your firewall configuration :)

cheers

[EDIT]
while re-reading my steps, i found a little hickup. It might be that your openvpn does not start right away because if insufficient rights for log files (nobody is not allowed to write to /var/log) so you might need to create the files and chown them to nobody before the openvpn starts properly... 
Just saw it, thought i mention it.

---

