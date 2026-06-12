---
title: "Deluge 1.1.6 - Ubuntu 9.04 - &quot;No incoming connections&quot;"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by brrant on 2009-07-01
Hi,

I'm using Deluge 1.1.6 on Ubuntu 9.04.

I've forwarded several ports in my router, using 7777 currently, And Deluge still says "No incoming connections."

I'm using a Linksys BEFSX41 router.

I don't think the, "No incoming connections" problem has anything to do with my router, because when I bypass the router completely, I still receive the same error.

I'm using a Qwest (Actiontec GT701-WG) wireless DSL modem.)

Any help?

Regards,
John

---

### Post by TeoBigusGeekus on 2009-07-01
Do you get decent speeds with it?
From what I remember from the period I used Deluge, it shows that the ports are closed whereas in fact they're open.

---

### Post by lovinglinux on 2009-07-01
The alert on Deluge status bar just means there are no incoming connections, this could be due to a closed port or because nobody is requesting connections to you (which is not usual).

To test if the port is really open, start deluge, then go to [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm) and scan the port forwarded to Deluge. If you receive a report that the port is Stealth or Closed, then it's definitely closed. It should give you a report that the port is open.

---

### Post by brrant on 2009-07-07
I tried going to the web site listed and it gives the following information. Apparently all of my ports are "Stealthed". Can anyone tell me where to go from here? ( I XXXXX'ed out the port number intentionaly.

[COLOR=green]"Stealthed"[/COLOR] (by a firewall) -Means that your computer is invisible to others on the Internet and protected by a firewall or other similiar software;
"Closed" (non-stealthed) - means that this port is closed, but your computer is visible to others on the Internet that can be potentially dangerous;
[COLOR=red]"Open"[/COLOR] - Means that this port is ready to establish (or has already established) a connection with remote address. It also means that your computer is vulnerable to attacks and could have been already hacked or infected by a trojan/backdoor;
              Port:         [IMG]http://www.pcflank.com/img/wpxl.gif[/IMG]         Status                     Service                     Description            XXXXX           [COLOR=green]stealthed[/COLOR]             n/a             n/a [IMG]http://www.pcflank.com/img/wpxl.gif[/IMG] [IMG]http://www.pcflank.com/img/wpxl.gif[/IMG]   **Recommendation:**

All the ports we have scanned are Stealthed (by a firewall). So just continue following the fundamental security measures and regularly update your security software.

---

### Post by lovinglinux on 2009-07-07
> **brrant said:**
> I tried going to the web site listed and it gives the following information. Apparently all of my ports are "Stealthed". Can anyone tell me where to go from here?

Visit [http://portforward.com](http://portforward.com) for instructions on how to open the port.

---

### Post by brrant on 2009-07-07
After reading another thread, I already used that guide to forward port 7777. Attached is a screenshot displaying that.

Hopefully you can see what I'm missing. Thanks for replying. :)

---

### Post by lovinglinux on 2009-07-07
> **brrant said:**
> After reading another thread, I already used that guide to forward port 7777. Attached is a screenshot displaying that.

Hopefully you can see what I'm missing. Thanks for replying. :)

Instead of "Both" I use only TCP. As far as know you only need UDP if you use DHT. But that's correct.

---

### Post by brrant on 2009-07-07
Hmm... I tried switching it to just TCP, but that didn't have any impact.

Earlier, someone asked what kind of speed I've been getting. It's typically in the 40 to 60 KiB range. I've limited my upload bandwidth to 30 to prevent my dsl connection from getting choked. On this machine when I had windows installed previously, and on other machines in the house currently using windows, I can consistently hit speeds of 630 to 680 KiB, so I know it's Ubuntu that's having the issues.

Also, whenever I have Deluge open (or Transmission, I've been trying both with the same results) web browsing is nearly non-functional. About 30% of the time when I open a new web browser, Firefox defaults to the local web page, failing to make an internet connection at all. Other times it typically takes 30 to 120 seconds to load simple web pages. Closing the torrent clients eliminates this problem.

Is there a firewall delivered and activated by default in 9.04? I haven't found one, if so.

Best regards

---

### Post by lovinglinux on 2009-07-07
> **brrant said:**
> Is there a firewall delivered and activated by default in 9.04? I haven't found one, if so.

Ubuntu comes with iptables and ufw, but there isn't any rules by default.

---

### Post by brrant on 2009-07-08
Bump?

Anyone else have any suggestions, or should I move this to another forum?

Getting a torrent client to work correctly, shouldn't be impossible. All of my ports are "stealthed" and I'm receiving no external connections. My download speed is about 10 percent of practical capacity on average.

Regards

---

### Post by lovinglinux on 2009-07-08
> **brrant said:**
> Bump?

Anyone else have any suggestions, or should I move this to another forum?

Getting a torrent client to work correctly, shouldn't be impossible. All of my ports are "stealthed" and I'm receiving no external connections. My download speed is about 10 percent of practical capacity on average.

Regards

I checked your screenshot again and realized that you might be forwarding the port to the router IP. For example, in my local network address range, the IP ending with 1 is the router. Check your network settings by running the following command:

```
ifconfig $1 | grep "inet addr"
```

Your internal IP is the first value on the output.

If you are using DHCP to assign IP's automatically on your local network, then the first computer connected to the router will get the first available IP. So you might want to consider configuring the network manually with the Network Manager, instead of using DHCP, to assign a fixed IP to your machine.

---

### Post by brrant on 2009-07-08
I receive the following output when executing that command:[INDENT]```
$ ifconfig $1 | grep "inet addr"
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet addr:127.0.0.1  Mask:255.0.0.0
``` [/INDENT]I tried forwarding my port to "192.168.1.100", it was directed to "192.168.1.1". I'm not sure if those are actually different ports, but the change had no effect.

Could you provide more information on how to set a static IP? Looking under >System>Preferences>Network Connections, on the IPv4 Settings tab, I see "Method: Automatic (DHCP)", but I'm not familiar with how to do this correctly. If I change "Method" to "Manual" I am able to enter an Address, but I don't know what that should be. Would I also have to populate the "DNS Servers:" field below or make other changes?

---

### Post by lovinglinux on 2009-07-08
> **brrant said:**
> I receive the following output when executing that command:[INDENT]```
$ ifconfig $1 | grep "inet addr"
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet addr:127.0.0.1  Mask:255.0.0.0
``` [/INDENT]I tried forwarding my port to "192.168.1.100", it was directed to "192.168.1.1". I'm not sure if those are actually different ports, but the change had no effect.

Could you provide more information on how to set a static IP? Looking under >System>Preferences>Network Connections, on the IPv4 Settings tab, I see "Method: Automatic (DHCP)", but I'm not familiar with how to do this correctly. If I change "Method" to "Manual" I am able to enter an Address, but I don't know what that should be. Would I also have to populate the "DNS Servers:" field below or make other changes?

Weird. Before setting up the static IP tell me what is the address that you use to configure your router?

---

### Post by j.biddy on 2009-07-11
> **lovinglinux said:**
> Weird. Before setting up the static IP tell me what is the address that you use to configure your router?

I'm betting 192.168.0.1.

I'm having a similar problem. All ports properly forwarded and still getting the _/!\_ when testing the active port.

---

### Post by cariboo on 2009-07-11
I'm using Deluge 1.1.9 on Karminc, and I get the same message, of no incoming connections, even though I can see it is downloading. Eventually the message goes away. I haven't set up port forwarding, and use the default setup. Speeds range from glacially slow to well over 300Kbps.

---

### Post by brrant on 2009-07-14
To access my router I use 192.168.1.1.

Sorry, for the slow response, I was gone for a few days.

Cariboo907, as for the message going away eventually. I hope you don't mean to imply that the problem goes away or doesn't exist. If you go in and test your connection from within Deluge, you'll see it's still not reaching the outside world. 

Thanks

---

### Post by ekjsim on 2011-01-06
I get this this status as well, but downloads will hit max if there are enough seeders. Can anyone tell me what this status actually mean?

---

