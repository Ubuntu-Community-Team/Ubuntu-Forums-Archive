---
title: "How to set IP address?"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by logie on 2009-05-06
I am new to Linux.  I am running Ubuntu 8.10.
I have to configure a WAP, and I am told first to "configure the computer with a static IP address of 192.168.0.210". Can someone please tell me how to do this?

---

### Post by mick8985 on 2009-05-06
If you're running gnome you can do so in network manager, 

* right click on the network icon in the notification area > Edit Connections

* in Wired select "Auto eth0" or whatever device you want to set a static ip for.

*go to ipv4 settings, change from automatic (DHCP) to manual, and enter the information specific to your network.

---

### Post by kpkeerthi on 2009-05-06
If you are behind a router, just leave ubuntu settings as such and configure your router to serve your computer a static IP. There should be a setting somewhere in your router admin console where you can do it based on the MAC address of your computer.

---

### Post by logie on 2009-05-08
It worked - thanks!

Logie

---

### Post by choochoo22 on 2009-05-08
I have a similar problem requiring setting an IP address.  When I try to edit the connection, however, _most_ of the time Ubuntu greys out the "apply" button so I can't change the settings.  Inexplicably it did let me make the changes once or twice in live CD mode but this isn't permanent.  Is this a permissions problem of some kind?  How can I get past this to make the edit?

---

### Post by gandaran on 2009-05-08
> **choochoo22 said:**
> I have a similar problem requiring setting an IP address.  When I try to edit the connection, however, _most_ of the time Ubuntu greys out the "apply" button so I can't change the settings.  Inexplicably it did let me make the changes once or twice in live CD mode but this isn't permanent.  Is this a permissions problem of some kind?  How can I get past this to make the edit?
did you fill in all necessary  information? try posting a shot of the window with the grey button.

---

### Post by choochoo22 on 2009-05-08
I don't mean to be a smart a** but if I could post a shot of the dialog window with the greyed out button I wouldn't have a network problem to discuss.

Ubuntu let me re-name the network but if I change the settings from "DHCP auto" to "manual" so the IP can be set, the "apply" button disappears and does not return after the information is filled-in.  I'm not sure what to put in the "search domains" field but the time it worked I didn't fill this in and the "apply" button was never greyed out.

---

### Post by Pjotrovitz on 2009-05-08
The network manager checks the ip adresses to check that they are valid. Have you double checked that the adress doesnt contain invalid digits?

---

### Post by choochoo22 on 2009-05-08
The addresses look OK to me:

```
IP:      192.168.1.103
mask:    255.255.255.000
gateway: 192.168.1.1     (router IP)
DNS:     206.13.28.12
```

Also, I'm pretty sure that the time Ubuntu allowed the changes, the "apply" box never greyed out before, during, or after filling-in this information.

---

### Post by Pjotrovitz on 2009-05-08
Change 255.255.255.000 to 255.255.255.0

I know it should'nt matter, but it does for some reason..

---

### Post by choochoo22 on 2009-05-08
Well that certainly solved one problem thank you.  As soon as I entered 255.255.255.0 the "apply" button lit up!

Now the network is active and my local computers are accessable but DNS is not working.  IE: I can reach yahoo by entering 69.147.76.15 but not with yahoo.com.

206.13.28.12 is the DNS address provided by my ISP and is the same one used on this computer but it doesn't seem to work with firefox (it did once).  Do I need to do something more than type it in and apply?  Also, how do you enter multiple DNS addresses?  And what is the "Search Domains" field for?

---

### Post by Pjotrovitz on 2009-05-08
You can try using opendns.com to check if it is the server that's bad. They have adresses 208.67.222.222 and 208.67.220.220.

I've never used search domains, but I guess you can find out by googling it..

---

### Post by RetchingRabbit on 2009-05-08
> **choochoo22 said:**
> I don't mean to be a smart a** but if I could post a shot of the dialog window with the greyed out button I wouldn't have a network problem to discuss.



Nicely done! 

:P

---

### Post by choochoo22 on 2009-05-08
Nope, same problem with opendns, besides this vista computer is working OK with the regular servers.

---

### Post by AndyCooll on 2009-05-08
As mentioned by kpkeerthi above, you shouldn't really need to play with the network manager or anything else network related in Ubuntu itself to setup a static IP address, other than to supply your password for your home network. 

If you require a static IP address for your computer then you are better setting it on the _router_ if you have one, _not_ in Ubuntu. Assuming you have a router, by logging into it you can usually give the MAC address of your network card a static IP address. 

You can find the MAC address of your network card by typing into a terminal:
```
ifconfig
```
It's called "HWaddr" and if you have a laptop you will probably have two, one for your ethernet card, and one for your wireless card. Write this down.

Now login to your router and look for the relevent section (on mine it's under Services > Service Management). Enter your MAC address and the IP address you want it to pick up. And you're done.

This method works independent of OS!

:cool:

---

### Post by choochoo22 on 2009-05-08
> **AndyCooll said:**
> If you require a static IP address for your computer then you are better setting it on the _router_ if you have one, _not_ in Ubuntu. 

:cool:

I have had a static IP address set in my router for years and haven't touched it.  I also have static _private_ addresses for my local computers.  These have to be set individually on each computer and that is what I was initially having trouble with in Ubuntu.

That problem has been solved but DNS still does not seem to be working.

---

### Post by choochoo22 on 2009-05-08
The original IP problem was solved, thank you.  My current DNS problem is really off-topic for this thread, I think it would be best if I start a new thread.

---

### Post by wabbalee on 2009-05-08
just a suggestion: have you tried adding the dns entries on your router? I know I had to do that with a previous ISP to get acces to internet.

---

### Post by gandaran on 2009-05-09
> **RetchingRabbit said:**
> Nicely done! 

:P
if he can post on this forum without a network connection then he can also post a shot!

---

