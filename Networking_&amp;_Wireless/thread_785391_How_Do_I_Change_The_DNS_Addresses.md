---
title: "How Do I Change The DNS Addresses?"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by matey3 on 2008-05-07
Hello All:

*This post may belong to the "Absolute Beginners" forum but since it is related to Networking I posted it here. sorry.....*

Our ISP has changed their DNS IP Addresses and gave us 3 new ones.
They sent the info saying I need to go to our "Servers" and under /etc/ edit the resolve.conf file.(add the line like : nameserver 192.168.1.3 etc.) 

My question is 
1- how do I know which "Server"? (is the DNS)?

I did an ipconfig /all on a Windows machine and got the DNS Address but then I found our DHCP (different machine than the DNS) also has the old DNS IP address in that RESOLVE.CONF file?? (and I have another 20 machines/servers here)??!!

So at this point I am not really sure 

2- How one machine plays the role of DNS and another machine plays the role of a its backup etc.?so.

3-How do you set roles for the Servers (i.e DHCP or DNS etc.?)


Thanks very much for any replies.
Regards;

---

### Post by Monicker on 2008-05-07
Check /etc/resolv.conf on the machines to see which DNS server they are using.  If the machine are getting their ip address via DHCP, then that information is usually passed along when the machine is given an ip address to use.  You should change the configuration of your dhcp server so that it gives out the proper dns servers for the clients to use.


The role of a server simply depends on which services are installed and configured on it.

---

### Post by jtrindle on 2008-05-07
I'm a little confused on your network architecture..

Do you have a machine which gives out IP addresses to your local network?  Do you have a machine which performs DNS for other machines on your local network?  

In my home setup, I have a router that gives out DHCP to my local machines.  *that* device needs to know the new DNS server addresses  so that it can include them in the response to DHCP requests from the local machines.

That would do for Windows DHCP clients.  I haven't quite got Ubuntu to get the nameservers along with the IP and Gateway info from my router, so I have to include all three of my ISP-supplied nameservers in the /etc/resolv.conf file

My resolv.conf:

search hr.cox.net
nameserver 68.105.28.12
nameserver 68.105.29.12
nameserver 68.105.28.11


You'd have to update the resolv.conf of each machine which has either static IP configuration, or whose DHCP client doesn't request all the information properly, like mine.

If you have a Linux box actually performing DNS functionality, you need to go to the /etc/bind directory (assuming its Debian/Ubuntu) and look in named.conf.options for the lines to change.

---

### Post by matey3 on 2008-05-07
Thanks very much Monicker for the reply.

I think I got it now...

Thanks a lot jtrindle;

heh You are absolutely right about confusing network. I dont know who set it up but its a mess. we have so many class A type private IP networks with class A type subnets all mixed up that most ppl cannot even print.
I asked why they had set it up like that and all i heard was for security reasons..
any ways I think I know how to do this change now thanks a lot..

oh..
BTW 
1-Do I have to reboot the server before the changes take effect? Or can I run a file or something else??

Thanks again!
very fast responses! I appreciate it :)

---

### Post by Monicker on 2008-05-07
Changes to /etc/resolv.conf take effect immediately.

If you make any changes to a dhcp or server, you should restart the service.

For dhcp server
```
sudo /etc/init.d/dhcpd restart
```

For dns server
```
sudo /etc/init.d/named restart
```

I'm not 100% positive on those services names, but you should be able to tell by looking at what is in /etc/init.d

---

### Post by jtrindle on 2008-05-07
> **matey3 said:**
> T


1-Do I have to reboot the server before the changes take effect? Or can I run a file or something else??

Thanks again!
very fast responses! I appreciate it :)

If you are just changing resolv.conf, you don't have to reboot or restart any services.  If you are changing the files in /etc/bind you have to do a /etc/init.d/bind9 restart

---

