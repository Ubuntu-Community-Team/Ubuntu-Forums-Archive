---
title: "Find ip address."
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Hygaphunkik on 2010-02-01
OK not sure this is in the right place but here goes.

I am in the process of building a server, so far I have setup samba file sharing and that is working quite nicely. Made sure that my server has a static ip on the home network, but I am now trying to think about accessing some of these files from elsewhere in the world. To that end I wish to set it up as an ftp server, which means I need to know how to address the ip of the computer on my network from outside of that network. How is this done?

So the question to sum up is, how do I address a pc on my local network from a pc that is not on my local network?

Perhaps [ftp://routerip/networkip/folder](ftp://routerip/networkip/folder) ? or am I barking up the wrong tree here?

---

### Post by pirateghost on 2010-02-01
you need to go into your router configuration page and forward the ports required for the service (FTP in this case) to forward to your server.

then the other user would use [ftp://yourpublicipaddress/](ftp://yourpublicipaddress/)

better still would be to get a dynamic dns name from dyndns.com and give them a 'web address' so to speak.
[ftp://hygaphunkik.dyndns.org](ftp://hygaphunkik.dyndns.org)

---

### Post by manoriax on 2010-02-01
There are, of course, web services which let you find out your current IP address. Demanding on the place you're living and the ISP you use, it is possible that your IP address changes in a fix period of time (e.g. every 24 hours).

Here is one service that lets you find our your IP: [http://www.myipaddress.com/show-my-ip-address/](http://www.myipaddress.com/show-my-ip-address/)

Though, if you intent to make your server accessible from an external network (like the internet) you will have to unlock the associated ports in your router/firewall I guess.

In case your ISP changes your IP address after a time, you could use a service like this one [http://www.dyndns.com/](http://www.dyndns.com/) to forward your IP address to a "static domain".

---

### Post by nhasian on 2010-02-01
pretty close.  it would just be [ftp://wanIP/folder](ftp://wanIP/folder) or sftp would be more secure.

wanIP is the public IP address your ISP gives you as opposed to the lan private address on your network (192.x.x.x or 10.x.x.x)

You'll need to configure your router to forward port 21 for ftp, or port 22 for ssh/sftp.  port 5900 is also useful to forward if you want to remote desktop into the machine.

[COLOR="DarkGreen"]TIP[/COLOR] You should make sure the target computer always has the same IP address or the port forwards you set up in the router will point to the wrong computer.  On some routers you can tell the DHCP server to always assign a particular IP address to a computer's hardware mac address.  If your router does not have this function than you will need to set a static ip address for the computer instead of relying on DHCP.

> **Hygaphunkik said:**
> Perhaps [ftp://routerip/networkip/folder](ftp://routerip/networkip/folder) ? or am I barking up the wrong tree here?

---

