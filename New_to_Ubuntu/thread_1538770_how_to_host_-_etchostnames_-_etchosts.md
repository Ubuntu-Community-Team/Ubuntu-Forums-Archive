---
title: "how to host - /etc/hostnames - /etc/hosts"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by 007casper on 2010-07-25
What is the proper way?

I just want to add couple more domains to my hosts file properly.  And if my old settings are quirky, I would like to fix it, so domain resolves quickly. I have set it up way back by using howtoforge.com without really understanding fully.  Now, I have a little bit better understanding as far as file structure.

I read here [http://ubuntuforums.org/showthread.php?t=1520103](http://ubuntuforums.org/showthread.php?t=1520103), that it is not a bad idea to edit /etc/hosts and /etc/hostname at the same time - otherwise sudo complains.

I didnt see that on the manual page. Any ideas?

I have looked at the server guide manual on page 35, it states only set up for /etc/hosts
> 
127.0.0.1 localhost
127.0.1.1 ubuntu-server
10.0.0.11 server1 vpn server1.example.com
10.0.0.12 server2 mail server2.example.com
10.0.0.13 server3 www server3.example.com
10.0.0.14 server4 file server4.example.com
> 
*In the above example, notice that each of the servers have been given aliases in addition to their proper names and FQDN's. Server1 has been mapped to the name vpn, server2 is referred to as mail, server3 as www, and server4 as file.


when I used the howtoforge guide, I have set it up my /etc/hosts as...
> 
127.0.0.1	[www.mydomain.com](www.mydomain.com)	localhost.localdomain	localhost
68.180.206.184	[www.mydomain.com](www.mydomain.com)	www
206.190.60.37   sub.mydomain.com	sub

my aliases are on the sitting on the right hand side, and in the manual aliases are in the middle.  Does it matter?

In addition, I would like to add a new "domain3.com", lets say with IP address 66.235.120.101, and also need to fix 206.190.60.37 since I cant access it online, so my /etc/hosts would like this?
> 
/etc/hosts/
127.0.0.1	[www.mydomain.com](www.mydomain.com)	localhost.localdomain	localhost
127.0.0.1	[www.domain3.com](www.domain3.com)		localhost
127.0.0.1	sub.mydomain.com	localhost
68.180.206.184	[www.mydomain.com](www.mydomain.com)	www
206.190.60.37   sub.mydomain.com	sub
66.235.120.101  [www.domain3.com](www.domain3.com)         www

the reason why I added sub.mydomain.com to localhost is because as stated above, I cant access it on the web.  So, do I need to set it to localhost, and set it also on the router these two IPs  206.190.60.37, 66.235.120.101 to port 80 right? 

please advise thank you.

---

### Post by cariboo on 2010-07-26
You can edit /etc/hosts to your hearts content, but /etc/hostname is where the name of the computer you are using is located. Unless you plan on renaming your computer, just leave it alone.

---

