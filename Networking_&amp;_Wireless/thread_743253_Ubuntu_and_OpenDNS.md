---
title: "Ubuntu and OpenDNS"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by DenKain on 2008-04-02
I am using Ubuntu 7.10

I have been using OpenDNS on my home network for some time to filter out certain content and etc. I had set the DNS servers in the router so it will work for my entire network. My wife has gotten a little annoyed by this so I took the DNS settings off the router and let it default to my ISPs DNS servers. I opened "Network" and deleted my routers address in the DNS tab and then entered the two DNS addresses. I rebooted my laptop and when I go back to check on my local DNS settings they have reverted back to my router's IP. 

Any idea?

---

### Post by superprash2003 on 2008-04-02
yes, they will autorefresh and revert back.. if you want to setup the DNS permanently.. 
go to the terminal and type sudo gedit /etc/dhcp3/dhclient.conf
add the following line at the end

prepend domain-name-servers 208.67.222.222,208.67.220.220;

Thats it... now these will be your DNS servers always.

---

