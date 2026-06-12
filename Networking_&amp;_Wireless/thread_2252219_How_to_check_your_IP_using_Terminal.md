---
title: "How to check your IP using Terminal?"
date: 2014-11-10
forum: Networking &amp; Wireless
---

### Post by flaymond on 2014-11-10
How to check your ip using terminal? I'm also confused and don't understand what are the difference between Telnet, Ethernet, SSD, and Internet.

---

### Post by JKristant on 2014-11-10
put this command in your terminal :
ifconfig

for more detail
ifconfig --help

For more information : [Linux Tutorials]("http://www.maskris.com/search/label/linux")

---

### Post by Lars Noodén on 2014-11-10
What are you trying to do?  What is the ip for?

> **JKristant said:**
> put this command in your terminal :
ifconfig

for more detail
ifconfig --help

Yes, this will get your LAN ip address.  Usually you will use eth0 for a wired connection (Ethernet) or wlan0 for wireless (wi-fi)

```

ifconfig eth0
ifconfig wlan0

```

But if you are behind some router using NAT then your external address will be something else and the easiest way to find it is to use some external service that reports back to you where you are connecting from.  The built-in web browser [wget](http://manpages.ubuntu.com/manpages/trusty/en/man1/wget.1.html) can be used to fetch that info.  You can use an external service like [http://icanhazip.com/](http://icanhazip.com/) to find your external IP number, if you are using NAT:

```

wget -q -O - http://icanhazip.com/

```

That tells wget to fetch the URL [http://icanhazip.com/](http://icanhazip.com/) and write it out (-O) to the terminal display (-) aka *stdout* without displaying any connection information (-q).  Wget is included in all versions of Ubuntu, so you won't have to install anything to use it.

---

### Post by sudodus on 2014-11-10
Thanks for this tip Lars :KS

---

### Post by pfeiffep on 2014-11-10
> **InterProg said:**
> [SIZE=1]How to check your ip using terminal?[/SIZE] I'm also confused and don't understand what are the difference between Telnet, Ethernet, SSD, and Internet.[INDENT][Telnet]("http://pcsupport.about.com/od/termstz/g/telnet.htm") - Command Line Interface (CLI) program used to communicate 
[Ethernet]("http://www.pcmag.com/encyclopedia/term/42781/ethernet") - a standard for connecting computers together enabling communication
[SSD]("http://www.pcmag.com/article2/0,2817,2404258,00.asp") - Solid State Drive as opposed to a spinning hard drive
[Internet]("http://en.wikipedia.org/wiki/Internet") - millions (billions?) of computers connected using ethernet[/INDENT]

---

### Post by flaymond on 2014-11-13
err...hey..it worked...but i don't see using the terminal i got the right IP, i just check at several websites (Ip tracker/tracer) and found out that my IP in terminal and in the website is totally different. Why its different? Am I doing something wrong?

im using:
 
ifconfig wlan0 



I got different IP :(

---

### Post by Bucky Ball on 2014-11-13
Good news. Please mark the thread as solved. See the second link in my signature. Thanks.

---

### Post by sudodus on 2014-11-13
> **InterProg said:**
> err...hey..it worked...but i don't see using the terminal i got the right IP, i just check at several websites (Ip tracker/tracer) and found out that my IP in terminal and in the website is totally different. Why its different? Am I doing something wrong?

im using:
 
ifconfig wlan0 



I got different IP :(

ifconfig finds the IP of the computer in the local network (behind the  router). The other address is what is seen from the outside (by the  internet, that is by the websites that you visit).

---

### Post by Lars Noodén on 2014-11-13
> **sudodus said:**
> ifconfig finds the IP of the computer in the local network (behind the  router). The other address is what is seen from the outside (by the  internet, that is by the websites that you visit).

@InterProg, you can also lookup info about NAT (network address translation) aka masquerading to find out more about the method being used.  Basically you have a Local Area Network (LAN) with it's [own address space](https://tools.ietf.org/html/rfc1918) that the router seamlessly connects to the Internet.  This allows you to build out your LAN without needing to get public IPs for each new device.  It's not a firewall, it is penetrable on its own, though many firewalls do also offer NAT.  

If you have [traceroute](http://linux.die.net/man/8/traceroute) available, you can watch your connection pass through various networks.  It is in its own package and not in the default installation, so you'll have to add it.

```

traceroute ubuntuforums.org
traceroute -n ubuntuforums.org

```

Off the router, through the ISP, off the backbone, to the second ISP, to the serverroom -- nothing but 'net.

---

### Post by flaymond on 2014-11-13
ty Sudo for that info, and ty Lars...you give me some knowledge to jump in and discover more about Computer Techs...:D

---

