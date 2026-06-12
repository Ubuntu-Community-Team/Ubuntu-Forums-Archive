---
title: "getting unique ip for pc on internet"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by shashi123 on 2007-04-10
This is not actually related to ubuntu os directly 

but i would be really glad if anyone can help me with this query

i have a windows server it runs a proxy 

and my ubuntu client surfs the internet from behind this proxy 

whenever i see my ubuntu ip from internet it shows the same ip as that of my windows  pc. But i want to have a unique ip for this pc on internet 

is there any software in ubuntu which will give it a unique ip when on internet dosent matter even if it changes everytime i reboot the pc

thanx in advance

---

### Post by rajko on 2007-04-10
It is not actualy question of software.
It depends on your ISP. Usualy they give one IP per connection.

You need to use NAT port forwarding if you need to se your other pc from outside.

rajko

---

### Post by dbott67 on 2007-04-10
Whenever you share a single internet connection (whether you use a Windows Connection Sharing or a home router like a D-Link or Linksys NAT device) all computers will appear to emanate from a single IP address.

For example, at work I have 150 PCs at 4 different locations, however, to access the internet they all must pass through the firewall.  The firewall uses Network Address Translation to convert the internal IP address (192.168.x.y) to the real external IP address (provided by my ISP).  However, if I go to a website to check my IP address from any of my computers they all report the same IP address --- the one provided by my ISP.

The only way around this is to contact your ISP and request a 2nd IP address.

If you can explain what you are trying to do, there are many solutions available if you want to be able to access multiple PCs that share a single connection.  At home, I have 5 computers (running various OSes: Windows XP, Vista, Ubuntu & OSX) connected to a D-Link router and can access all of them remotely using port-forwarding techniques and programs like SSH, VNC, NoMachine & pcAnywhere.

-Dave

---

### Post by shashi123 on 2007-04-10
thanx for ur reply 

but is there any way i can access this perticuler pc without the ip by giving a path from server ip to this perticular ubuntu pc ip (the internal ip) 

actually i am testing a website for that purpose i have hosted this site on this pc and for testing purpose so i might need this facility for at the most 1 week 
and the isp might not provide me this facility for such a short period and even if they do the process might take 1 week 


now if i do [http://localhost/index.php](http://localhost/index.php) from this ubuntu pc 

then i am  able to see this site from the same machine

and i am also able to see this site from all machines in network when i do 

[http://192.x.x.x/index.php](http://192.x.x.x/index.php)  but my webdesigner wants to see this from his office 

how can he do it


plz help me for this

---

### Post by dbott67 on 2007-04-10
You need to setup a port-forwarding rule on your proxy server.  Are you running Windows Internet Connection Sharing?  If so, try this document:

[Windows ICS Port Forwarding]("http://forum.portforward.com/YaBB.cgi?board=Knowledge;action=display;num=1134525903")

- Assume your Ubuntu computer is 192.168.1.100
- Assume your Windows ICS internal IP is 192.168.1.1
- Assume your Windows ICS external address (assigned by your ISP) is aaa.bbb.ccc.ddd

The example in the link above is referring to a game, but you will want to forward port 80 from your Windows computer to your Ubuntu computer.  Then your friend will point his browser to your public ISP IP address ([http://aaa.bbb.ccc.ddd/index.php]("http://aaa.bbb.ccc.ddd/")) and the request should be passed onto your Ubuntu computer (192.168.1.100).


-Dave

---

### Post by shashi123 on 2007-04-10
actually i am using ccproxy

there is a facility to map port 

what could be the setting for this 

as per ur saying i would have done ICS but I am not much of a geek in these things

can u suggest me setting with ccproxy 

thanx  for ur help

awaiting ur reply

---

### Post by dbott67 on 2007-04-10
> **shashi123 said:**
> actually i am using ccproxy

there is a facility to map port 

what could be the setting for this 



According to the FAQ on their site:
> 
**How to use CC Proxy port map?**
               Please go to "**Options**" dialog box, click a "**E**"                  button near the "**Port Map**" and you will find out how                  to set port mapping.



-Dave

---

### Post by shashi123 on 2007-04-11
after doing the port map i got this msg

as invalid user

my internal host pc ip is 172.16.97.11 

in cc proxy 

i put this as dest host - 172.16.97.11
dest port - 80
port type - tcp 
local port - 80

now when i say [http://203.109.77.206/index.php](http://203.109.77.206/index.php) 

it says "203.109.77.206 is external user, blocked"  where  203.109.77.206 is the ip given to me by isp 

and 172.16.97.11 is the ip of ubuntu pc where the site is hosted 

i have also tried to add internal ip of windows machine  172.16.97.54 but still the same error

what should i do now

---

### Post by dbott67 on 2007-04-11
A few things to consider:

1. Are you trying to connect from outside of your network?
2. You may need to post a question in the ccProxy forums
3. Certain ISPs may prevent you from hosting web/mail/ftp servers and block the required ports.  

I would suggest that you make sure that ccProxy is properly configured first (or try a different Internet Connection Sharing product, such as a D-Link or Linksys router, or just use Windows ICS).

-Dave

---

### Post by shashi123 on 2007-04-11
i think ur suggestion has worked out

i added my isp ip in ccproxy setting and 

and now when i do [http://203.109.77.206/index.php](http://203.109.77.206/index.php) it shows the homepage but with out the images and if i try to click some link then the address becomes 
[http://localhost/the-other-link](http://localhost/the-other-link) and i am not able to see that link and it shows invalid user

but when i try and change localhost to 203.109.77.206 
ie changing  [http://localhost/the-other-link](http://localhost/the-other-link) 

to 

[http://203.109.77.206/the-other-link](http://203.109.77.206/the-other-link) 

the link on the webpaage is visible

what could be the problem

but thanx anyway without ur help i would not have even able to get the home page

thanx a million times

---

