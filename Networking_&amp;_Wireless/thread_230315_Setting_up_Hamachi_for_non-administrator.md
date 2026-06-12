---
title: "Setting up Hamachi for non-administrator"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by transistor on 2006-08-05
Hi, all. Dad is 75 and 3 hours away usually - opposite sides of Ireland. Hamachi / VNC is just what I need to steer him through the Ubuntu 6.06 GUI remotely. Setting up Hamachi has 'just about done my head in' though and I need a few pointers.

Status:
Hamachi and gHamachi installed for root user (me) on Ubuntu box. (What a job!)
I can persuade it all to start and can remote desktop by VNC from my Windows machine via the Hamachi vpn.

What I need:
I need Hamachi to start automatically and join my network every time Dad auto-logs in.

Problems:
1. I can't figure out how to start Hamachi from Dad's login.

2. Even on the admin login Hamachi doesn't restart automatically. I need it to start automatically for Dad on his login.

Can anyone give me some guidance on settin up what I need?

Many thanks.

---

### Post by transistor on 2006-08-27
In the end I had to write a bash script to start Hamachi and leave it on the desktop so he could start it manually. Unfortunately I could only get it to work as root user. I got home to find out that we couldn't talk anyway as one of our routers was blocking us and we would need to purchase a service from Hamachi to work around this.

By the way, I spent days installing Hamachi and trying to configure it. The Windows download and install took one or two minutes. Yes, I know ... 

Workaround
My main reason for trying Hamachi was that it solved the problem of changing IP address on Dad's ADSL connection. I found "ddclient" in the Synaptic Package Manager and this allows you to automatically update your dynamic DNS at DynDNS.org or any other similar service.

```
        dyndns.org
      /           \
     /             \
 Dad <-------------> Me 
```
The way it works is that you go to dyndns.org and register a domain name like "mydomain.dyndns.org". (Choose something that's likely to be unique.) Write this down along with your username and password.)
Now install ddclient (using Synaptic) on Dad's computer. Set it up with your dyndns.org information and it will send a message to DynDNS every time the IP address changes. 
On Dad's computer go to System > Preferences > Remote desktop and check all the boxes except maybe "Ask you for confirmation". Leaving this unchecked means you can administer the remote machine even if there is noone home. Enter a good secure password and hit Close.

On my computer I start VNC client and enter "mydomain.dyndns.org" in the Server field. When prompted enter your Remote Desktop password and you should be connected!

I hope this is of help to some.
I don't know what the security issues are with this setup. In my application it's not really an issue but it may be for some. Comments?
The other small problem I have is that I can't figure out how to get the ddclient GUI open again if I need to make any changes.

---

### Post by genekrupa on 2006-11-10
I got about as far as you got trying to set up hamachi to access my desktop from my laptop, before I gave up for the time being. 

Have you had a look at [www.portforward.com?](www.portforward.com?) They walk you through configuring your router for a variety of routers and applications

If your read german (or have a good translation tool), you might want to look at this for an alternative.

[http://freifunk.net/wiki/OpenVPNHowto](http://freifunk.net/wiki/OpenVPNHowto)

It would be nice to hear how you get along if you give it a shot.

---

