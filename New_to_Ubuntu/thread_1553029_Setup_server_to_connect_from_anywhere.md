---
title: "Setup server to connect from anywhere??"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by dragonpimpsta on 2010-08-14
My ubuntu server is setup as dhcp and i can connect to it from my laptop running ubuntu, so i've been putting files on it, and organizing them. (btw i prefixed this as kubuntu because i installed kubuntu graphical interface)

I should setup static though right? Once i leave for school and my server is here in this different city will i still be able to connect to it? I was looking at guides for setting up static ip, and the ip I would use is 192.168.0.103 which is how my linksys router had it setup. That only works inside of my house though right? I want to be able to connect to it from school (a different city) so how should I do that?

I'd also like to be able to connect to it from windows xp as well if possible 

I'm a complete ip noob. lol. Thanks for any help in advance

---

### Post by stlsaint on 2010-08-14
For starters you should install [openssh]("https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html") and use key authentication instead of username and password. Then you need to setup [port forwarding ]("http://en.wikipedia.org/wiki/Port_forwarding")through your router and forward port 22 (or whichever you choose to use, 22 is default) to ip that you set for router! IE: port 22 is forwarded to 192.168.0.103. Now let me explain, that address 192.168.0.103 is whats called a private ipaddress. You have a public ip address that the rest of the world sees. So if you go to your router status you should see your public ip which will be something completely different from your private. 
SO.....
private = 192.168.0.103
public = 65.345.87.32 (or whatever yours is)

Once you have ssh and port forwarding setup you will be able to reach your server from anywhere in the world by using the ssh command:

```
ssh <username>@<public-ip>
```
or like this
```
 ssh stlsaint@65.345.87.32
```

NOTE: I suggest key authentication if you only intend on connecting from say your laptop that you travel with. If you want to connect from ANY computer you use then you will use username/password which is highly LESS secure than key authentication!! ;)

---

### Post by earthpigg on 2010-08-14
hi,

> I was looking at guides for setting up static ip, and the ip I would use is 192.168.0.103 which is how my linksys router had it setup. That only works inside of my house though right? I want to be able to connect to it from school (a different city) so how should I do that?

only your ISP can give you a static IP address, but there are other workarounds.

[dyndns]("http://www.dyndns.com/") is what i use. they provide a $0.00 service that allows you to connect to your server even if the IP changes on you. a daemon (ddclient) is installed on the server that notifies dyndns every x minutes of it's current IP address. then, when you want to talk to your server, you use [email]name@dyndnsdomain.com[/email] or something similar in place of an IP address.

---

### Post by anewguy on 2010-08-14
+1 on dyndns.  You can't just assume your IP address from your ISP will always be the same - power outages, resets by the ISP, etc., will likely result in a different IP address.  You also just can't say "hey - I'm www.hereiam.com" either as these names are controlled. 

So, either use dyndns (you get a name as described above) and connect to your server externally for free, or have your ISP set you up.  They would first need to give you an assigned IP address to keep it static.  If you want your server known by some URL instead of IP address, you'll also need to get a domain name.  Chances are at that point you need to talk to your ISP about a business account as they normally won't let you have your own server without it.  Remember that once you open your server up to external connections you will have to take security on your server very seriously.

---

### Post by S.R on 2010-08-14
> **stlsaint said:**
> ]NOTE: I suggest key authentication if you only intend on connecting from say your laptop that you travel with. If you want to connect from ANY computer you use then you will use username/password which is highly LESS secure than key authentication!! ;)

I am going to set up my own server and had not thought of using a key but now that you bought it up ... can you save your keys to a USB stick to use from another computer or in my case just to keep them more secure?

Sorry for venturing a little off topic.

---

### Post by dragonpimpsta on 2010-08-14
@stlsaint 
If I set my router up to portforward to 0.103 will that mess up other internet connections on the router? This isn't a very serious server so if my public ip changes and i have to reconfigure it later on it wont be a big deal. What will be a big deal is if my dad or visitors can't use the internet off that router anymore off their seperate PCs lol.

@earthpig
I think i'll just stay with dhcp for now for simplicity. Then if it does become a problem i'll try dyndyn. Thanks!

@anewguy
It's just going to be my personal file server that I wont give many other people access to. I won't need a domain (even though i did install LAMP on it)

Thank you all for your help :D

---

### Post by stlsaint on 2010-08-14
> **S.R said:**
> I am going to set up my own server and had not thought of using a key but now that you bought it up ... can you save your keys to a USB stick to use from another computer or in my case just to keep them more secure?

Sorry for venturing a little off topic.

Yes you can. I save my entire .ssh directory and just copy it over to new systems when needed same ssh settings allowed.

---

### Post by stlsaint on 2010-08-14
> @stlsaint 
If I set my router up to portforward to 0.103 will that mess up other internet connections on the router? This isn't a very serious server so if my public ip changes and i have to reconfigure it later on it wont be a big deal. What will be a big deal is if my dad or visitors can't use the internet off that router anymore off their seperate PCs lol.


No it will NOT affect any other user unless they too wish to setup port forwarding through the same port to another ip address. Then its just a simple fix of changing ports that ssh runs through. I have multiple ports going to multiple ip's! :D
If you just have other users surfing the net then no it wont hurt their connection!

---

### Post by stlsaint on 2010-08-14
Earthpig brings up a good point though. I host a site from home via godaddy so when my ip changes its a big deal for me. For you leaving for school you will have to have someone else who has access to the router to inform you when your ip changes as you wont be able to access the router unless you setup remote management! (which i really DONT suggest you do!)
So if your public ip changes without you knowing than running that ssh command i gave earlier wont work until you enter the correct ip!

---

### Post by dragonpimpsta on 2010-08-14
When i try to connect to that ip i get connection refused by server. I think this particular type of port forward up wrong :( When i enter my public ip into my browser it takes me to my router config page lol.

@stlsaint
How often do would my ISP change my public IP address? 

Daily?Weekly? Monthly? Yearly?

---

### Post by dragonpimpsta on 2010-08-14
> **dragonpimpsta said:**
> When i try to connect to that ip i get connection refused by server. I think this particular type of port forward up wrong :( When i enter my public ip into my browser it takes me to my router config page lol.

@stlsaint
How often do would my ISP change my public IP address? 

Daily?Weekly? Monthly? Yearly?

I KINDA Got it working... it at least asks me for my password now, but then it says "End of stream" and doesnt actually connect

---

### Post by roger_1960 on 2010-08-14
Hi

If all you need is access to files on your server, the simple way is to use dropbox - [www.dropbox.com](www.dropbox.com) which will allow access to your synchronised files from anywhere.

---

### Post by dragonpimpsta on 2010-08-14
I GOT IT WORKING!!!!! ;DD
I'm going to try dyndns next.
I will also try that dropbox out because it sounds simple.



Is there a way to add my server as a drive letter in XP? or will i have to install an ftp type program?

---

### Post by JKyleOKC on 2010-08-14
> **dragonpimpsta said:**
> How often do would my ISP change my public IP address? 

Daily?Weekly? Monthly? Yearly?Depends in part on how often you reboot. Each reboot may quite likely get a different IP address. The ISP can also change it at any time, though. The usual interval is daily.

Some years ago I was on DHCP from AT&T (then Southwestern Bell) and kept the same IP for months on end. They later switched from DHCP to PPPoE and now users may get a new IP at each login, no reboot required.

Using dyndns or one of its competitors is the best way to go. You install their client program on your server, and it will keep them informed of your current IP so that you can address it by name rather than by IP. The down side of this whole idea, though, is that **anyone** can get into your server unless you keep it locked down tightly. I've just gone through a 10-day reformat-and-reinstall nightmare because someone got into my system (due entirely to my own carelessness and violation of basic security principles) and had the opportunity to take total control of it, by grabbing my ssh key files!

---

### Post by dragonpimpsta on 2010-08-15
Connecting through my public ip worked on my home connection, but when i tried it at someone else house later today it didnt work. The connection timed out. Is there another router setting I should change or what? My dyndns account even works for connecting to the server while im at home already connecting through my router. It just doesnt work anywhere else for some reason.

---

### Post by JKyleOKC on 2010-08-15
The reason that security experts advise using a router even if you have only one machine behind it is that by their design, routers won't accept incoming traffic unless it's in response to outgoing traffic already sent. That prevents anyone, including yourself, from initiating a connection from outside. You want to keep this feature as intact as possible to prevent unwanted intrusion.

The port forwarding feature that stlsaint mentioned back in post #2 of this thread is how you "poke a hole" in the automatic protection to allow connection from outside through a single specific port. The exact commands for doing this will vary from one make of router to another, but the magic words to look for are "port forwarding."

Even using ssh to create your secure "tunnel" through the router can be risky. I'm still trying to recover from an intrusion that happened more than two weeks ago because a combination of events made my "secure" system insecure. I've had to reformat every machine on my local network, reinstall everything, and lost more than a week's worth of messages and reference material -- and the system still isn't back to full normal operation. Don't take any shortcuts with this, or you could find that your machine has become a "mule" for a child porn ring, or the newest member of a botnet pumping out spam at the rate of thousands of messages an hour!

---

### Post by dragonpimpsta on 2010-08-15
sounds scary. i'll research security and try a different port.

---

