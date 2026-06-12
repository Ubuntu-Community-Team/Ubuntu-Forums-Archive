---
title: "Modifying Network Parameters"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by TANGUN on 2007-12-25
Finally a few minutes to start a new project. I'm currently working on writing a guide for those who want to start their own webserver. But, since I'm new to Ubuntu and I've gotten lazy (read: Windows user) and don't remember many of the CLI commands, I'll need some help. I'm trying to learn a couple of things so I'm starting at the server lever and will continue to build upwards until I'm running a few websites.

I currently have 6.10 server running on an old PC (PIII-500, 512MB RAM, 20GB HD). Apache2, PHP5 MySQL5 are all up and running and I can access test pages by typing in the IP of the server and the filename. Good! 

First I'd like to take care of the unsightly numbers and would rather have a domain name for the server. To get a domain name I can use a free service such as DYNDNS and I'd get a 'test.uts.dyndns.org' name for the server. [uts is the name of my server] That wouldn't be too bad and may be the route I want to take. 

**QUESTION #1**: Is there another way to replace the IP with a domain name only for my home computers? Can I force the computers in my home to recognize 'www.testdomain1.com' and pull up the default page on my server? If not, I will register with DYNDNS. I am also unsure if this will make the server visible to the rest of the internet.* 

If I do register with DYNDNS, my next step will be to set up three* different sites on the server.

*The purpose of the three sites is:
#1: Single static page visible to home network and internet.
#2: Dynamic site always visible to home and visible to internet when desired (similar to a server on/off switch).
#3: Dynamic site visible to home only.

Thanks for your help.

---

### Post by mightyteegar on 2007-12-26
> QUESTION #1: Is there another way to replace the IP with a domain name only for my home computers?

Yes, there are two ways to do this.  

**STATIC MAPPINGS**

1a. (Linux) Edit /etc/hosts on every machine in your home network and add a static name/IP mapping.  You don't even need to use a fully-qualified domain name; just a hostname will do fine for testing.  For example, if you want to call your host "webby" and it sits at IP address 192.168.0.2 on your LAN:

```
192.168.0.2 webby
```

1b.  (Windows XP)  Edit C:\WINDOWS\System32\DRIVERS\ETC\hosts exactly the same way.

**LOCAL DNS**

2.  Install and configure BIND on one of your Linux machines to provide DNS to your home network.  However, my feeling is that this would be overkill for your needs.

> If not, I will register with DYNDNS. I am also unsure if this will make the server visible to the rest of the internet.* 

That depends.  It will make your public IP address reachable from the Internet using a domain name, but if you have a router or firewall on your home network, you would need to configure routing and/or punch a hole in your firewall for people to get to your webserver from the outside.  

> If I do register with DYNDNS, my next step will be to set up three* different sites on the server.

*The purpose of the three sites is:
#1: Single static page visible to home network and internet.
#2: Dynamic site always visible to home and visible to internet when desired (similar to a server on/off switch).
#3: Dynamic site visible to home only.

Easily accomplished via a number of different methods.  You could:

1.  Configure the three sites to allow or deny traffic based on source IP addresses.  Do this by editing /etc/apache2/sites-available/name-of-site.conf for each site: 
```

Order allow,deny
Allow from <your local subnet here; ex: 192.168.0.0/24>
Allow from all (or) Deny from all # if you want to block traffic from the Internet

```
Disabling site 2 to the world would be as easy as changing "Allow from all" to "Deny from all" and restarting Apache.  I recommend this way.
2.  Configure three different sites running on three different ports, and only open sites 1 and 2 to the Internet.  To "turn off" site 2 to the Internet, just close the port.  Pretty easy to set up, but cumbersome and not as efficient as method 1.
3.  Use PHP or whatever scripting or programming language you're using to allow or block access based on source IP.  Not recommended in this case unless you can't use either of the other two methods for whatever reason.  

Personally, I'd recommend getting a DynDNS domain name.  All that does is map your IP to a domain name to the rest of the world, and you could use it for any service you want -- web, FTP, ssh, whatever.

---

