---
title: "configure server ip"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by amup on 2008-10-22
I'm not sure where to post this.

I have installed Ubuntu server on my old laptop to play and learn.  I have it connecting to the internet via wireless ethernet card to my home router.

I would also like to use it to browse the internet.  So I am installing the desktop gui stuff.

I am following directions I found here:
[http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/](http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/)

It says I need to do this:

Change dhcp to static and add the lines shown below. Of course you need to use your IP address, netmask, and gateway instead of mine.

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1


First off, my connection is wlan0.  Second, I don't have a static ip address from my isp but I do from the router.  It is 192.168.2.4.  My router is 192.168.2.1.  How should I change the above to match my router and isp?  

Thanks!  I am having so much fun learning linux!

---

### Post by puppywhacker on 2008-10-22
If you already know your wireless card is wlan0, you are pretty much good to go. In your case the following 'stanza' should work in your interfaces file.

```
auto wlan0

iface wlan0 inet static
   address 192.168.2.4
   netmask 255.255.255.0
   network 192.168.2.0
   192.168.2.1
```

and I agree, linux is fun

---

### Post by amup on 2008-10-22
Thanks for your reply.  I am still waiting for desktop gui to finish installing.

In the meantime, I looked at my router's configuration page, I notice it has a WAN IP address, Default Gateway address, and a DNS address. 

So if I use 192.168.2.4 as the address which is the address of my laptop server, then is the server only accessible to my local network behind my router?  And if so, how would I go about making it accessible outside my router if I wanted to?  Would I change 'address' to the WAN IP address and network to the "DNS address" or vice versa?

```

auto wlan0

iface wlan0 inet static
   address 192.168.2.4
   netmask 255.255.255.0
   network 192.168.2.0
   192.168.2.1


```

---

### Post by amup on 2008-10-22
Wow, it certainly takes a long time on my old slug of a laptop to install the desktop stuff.  Finally it is done. 
 
All seems to work well except **I cant' access the internet with firefox?**  

I have not made any of the changes yet in the above posts.  I didn't think I would need to do that for accessing the internet as it downloaded the desktop stuff from the internet with aptitude.  So what do I need to do to fix firefox?

---

### Post by jimv on 2008-10-22
If you have the gui installed, you should use it to configure your network, rather than using the interfaces file.

---

### Post by Iowan on 2008-10-22
> **amup said:**
> 
```

auto wlan0

iface wlan0 inet static
   address 192.168.2.4
   netmask 255.255.255.0
   network 192.168.2.0
  [COLOR="Red"] 192.168.2.1[/COLOR]


``` What does this line do?  Is that supposed to be "gateway 192.168.2.1"?

Another potential source of problems is IPv6.  My link to disabling it is getting a li'l dated.

---

### Post by amup on 2008-10-22
Ok So I am in the gui network settings and it won't let me save anything. When I click Ok, it says:

"The configuration could not be saved You are not allowed to modify the system configuration".

So I can't disable romaing mode and select my router and set up WEP.

Is there a tutorial somewhere that would help with this?

Thanks!

---

### Post by amup on 2008-10-23
So I reboot, and even though I put the 4 lines to set up my wireless card in /etc/rc.local, it is not turned on.  

I go in to gui and it is not there for me to setup.  It is not clear to me what I need to do to set it up in gui.

---

### Post by amup on 2008-10-23
Well I went into terminal and tried to modprobe ndiswrapper again and got an error: " FATAL module ndiswrapper not found"

So I went through the reinstall steps. I did an iwlist scan and could see the nearby routers.  So instead of configuring it for my router and wep I went back into network in the gui.  I configured it there.  I deselected "roaming" and then setup my essid/key etc.  That seemed to work, it has a check.

But firefox still doesn't work.  

I go into network tools and I now see:

Loopback interface
wireless interface (wlan0)
wireless interface (wlan0:avahi)

There was no wlan0 before.  Anyway, now wlan0 interace information all says not available.  wlan0:avahi has all the information.  It is showing a weird Ip address though.  It doesn't match anything that I can see.

At this point, I am out of ideas.  I really know very little about linux so it is hard to troubleshoot.

---

### Post by Iowan on 2008-10-23
The avahi address (169.X.X.X) usually means the interface failed to get a DHCP address.

---

### Post by jimv on 2008-10-24
YOu know, it might be best to reinstall using the Desktop edition instead of the server.  The only difference is the kernel (and the serve doesn't come with anything installed).  The server uses to -server kernel and the desktop uses the -generic kernel.

You can still run all of the server apps like apache, mysql, dns, dhcp, etc with the Desktop edition.

---

