---
title: "[B][/B] What is DHCDBD...."
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by newbun on 2007-07-15
Hi there

And if the system log, says it's "missing", what does that mean for  Ubuntu 7.04 ???

The system 'freezes' at varying times, when online - whats happening

Please help.

---

### Post by spd106 on 2007-07-16
dhcdbd provides a dbus interface for the dhcp client. It is used be network manager to control ip address assignment among other things. If you are having trouble with it and you don't need roaming mode then try setting a static configuration or disable network manager completely and edit the /etc/network/interfaces file directly.

---

### Post by newbun on 2007-07-16
Thanks SPD106, I'll carry out your suggestions and let you know.  I'm having a screen freeze at the moment, and just wondered if this DHCDBD, has anything to do with it.  Just one more thing, which may or may not be related;  If I view a site thats predominately text, then I can browse for up to three hours and no problem.  When I view sites with high graphics output, then the 'freeze' happens in minutes.  

Is there any connection, with what you suggest???

I'm sending this from a windows m/c.

---

### Post by newbun on 2007-07-16
Just one more thing, what does disabling Network Mgr, actually do.  I know I'm new to Ubuntu, but it sounds as if it SHOULD be connected - doesn't it?

I'm connecting via an ethernet connetion through a wireless router.  Works fine on the Windows mc.

---

### Post by spd106 on 2007-07-16
It's very unlikely that the root of this problem is related to dhcdbd, which usual manifests itself as failing to get an IP address or perhaps connection drop outs in a severe case.

It sounds more like an issue with your graphics card driver or perhaps some other video related bug.

---

### Post by newbun on 2007-07-17
I think you MAY be onto something SPD106 !!  I noted an earlier thread, where a poster had the same connection through an ethernet cable to a router, where 'WIRED NETWORK CONNECTION' came up after about a minute - but 'SERVER NOT FOUND' resulted, when trying to connect to the net.

My problem is, that when I first installed UBUNTU 7.04 and hooked up the cable ....I HAD a connection - checked a few news sites, browsed THIS site (which sometimes gave me the screen freeze).  But then  I HAD a connection.  

Now, I haven't changed ANYTHING since then, so I don't understand why it's suddenly stopped working.

If - as you say - I have a graphics card problem which is causing all these problems, what do you suggest I do? Do I do the obvious, and replace it?   But before we go down THAT road, could you tell me what COULD suddenly go wrong with a card??

I'm sending this through a Windows system through the SAME router - only wirelessly.

I'm intrigued!!

---

### Post by spd106 on 2007-07-17
You said before that browsing mostly text based websites was not a problem, but multimedia websites (with flash?) caused slow downs. Do you get any CPU usage spikes during this? I like to use the system monitor panel applet to monitor cpu, network and disk utilisation, though a terminal app like *top* would work equally well.

I good test would be to download a large file or run the update manager if you haven't already. If you don't get any slow downs or drop outs after a say half an hour or so, then it's unlikely that the connection is the problem.

It would be useful to know a bit more about your PC, is it a laptop? Which graphics card (and driver), CPU and network card does it have?

Server Not Found could be related to DNS problems, though if you can browse the web at all this suggests that any problem would be intermittent at worst.

---

