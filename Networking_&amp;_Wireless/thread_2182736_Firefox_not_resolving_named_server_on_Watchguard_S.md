---
title: "Firefox not resolving named server on Watchguard SSL VPN"
date: 2013-10-22
forum: Networking &amp; Wireless
---

### Post by SilkyPantsDan on 2013-10-22
Hi all,

My apologies if this has come up, or if it's something simple/outside of Ubuntu. 

I'm trying to move away from my Windows development setup and have found replacements for almost everything, but I require to connect to a Watchguard SSL VPN for work. I'm currently testing everything in a live USB build of 13.10 with persistence, and can connect to the VPN fine. My problem is when I try to access a named server via the browser (I've tried both Firefox and Chrome), they both cannot resolve the name to the site, returning that the server cannot be found.

After searching I first thought it might have something to do with the dnsmasq change from back in 12.04 - but after following the guides to turn it off, while I do see the VPN nameservers show up in /etc/resolv.conf after connection I get the same result of it not connecting. I had also read to check that I could get a result from the nslookup tool, which turns out the right result. Unfortunately I can't use the IP address of the server as IT have set something up that it needs to be referenced by it's name to show the correct site.

I'm not sure if it might be part of it, but I have found that I cannot ping the server by name, but I can by IP address. Would this be something on my side of the VPN? Or could this be a setting that isn't required for the Windows/Mac client of Watchguard but is needed for a Linux OpenVPN connection?

Thanks for the help, and once I can get this one issue resolved I can easily transition over :)

Dan

EDIT: Please ignore my profile name, I stuffed up my registration and cannot change it until 9 more posts :(

EDIT #2:
On a crazy whim I tried connecting to the server by dropping the domain. To give an example of this, the server I'm trying to reach is devportal.company-name.local and the domain is company-name.local. The server also has an administration setup that is accessed by it's IP address instead.

 If I try to load up the full name I get a 'Server cannot be found' error, but if I drop the domain I get the same page as if I had entered the IP address instead. I can't answer how the server has been set up, I've just been given the addresses to connect to.

---

### Post by SilkyPantsDan on 2013-10-24
Update:

More searching, I found someone had a [similar problem]("http://askubuntu.com/questions/124646/cannot-resolve-custom-domains-when-vpn-is-up") to mine and have edited my /etc/nsswitch.conf hosts line from

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

to
hosts:          files mdns4_minimal dns mdns4 [NOTFOUND=return]

and now I can ping the server by name, but I still cannot open it via Firefox or Chrome. IS there a way I can see how the browsers are resolving the names? Could they be reappending the domain to the sites address?

---

### Post by SilkyPantsDan on 2013-10-27
More searching and I came across [this article](http://blog.403labs.com/post/22325731425/vpn-dns-resolving-woes-in-ubuntu-12-04) which explains the exact problem I have been having. After following the bottom portion and reconfiguring the avahi daemon I am now able to resolve the local hosts on my VPN. 

Just to repeat the steps here:

> The real solution is to [follow the recommendations from the Avahi project]("http://avahi.org/wiki/AvahiAndUnicastDotLocal"), which is what is causing the .local domains to resolve.
  Here is a walk-through of the steps to fix this problem:
  
[LIST=1]
[*]Open up a terminal and edit the following file:
  sudo nano  /etc/avahi/avahi-daemon.conf
[*]Change the following line:
  #domain-name=local  to
  domain-name=.alocal
[*]Save the file and exit: Hit Ctrl + o then Ctrl + x

[*]Restart AVAHI:
  sudo service avahi-daemon restart
[/LIST]
You should now be able to resolve .local hosts provided by your VPN&#8217;s DNS server.



---

