---
title: "dyndns"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by dacool25 on 2007-07-25
Hi everyone,

I was just wondering how the site dyndns.com works, and if it is at all possible to do it using your own server?

I suppose that i would have to have another dns server at another location in order to do it right?  And then from there it would automatically update the ip address in the zone file?

Atleast that is my understanding of it.  Does anyone know of such a script, or could you please correct me if my understanding of how it works is wrong.

Thanks! :)

---

### Post by kidders on 2007-07-27
Hi there,

dyndns.com is a service for people who don't have a static IP, and don't want to run their own public DNS service (which is a non-trivial undertaking). It works by setting your DNS records' TTL to be very short, so other services/software don't cache name resolutions for very long, and accepting updates to DNS information using a pre-defined protocol.

If you have administrative access to a DNS service, you could certainly implement such a system for yourself. In fact, you could probably improve on it slightly, given that your personal ddns service wouldn't have millions & millions of other customers to worry about.

Just one word of caution: As you may know, DNS has its own mechanism for performing record updates ... *don't be tempted to try to use it remotely*. Instead, I would suggest a public interface that perhaps uses SSH or HTTPS ... ie something commonplace, but encrypted.

---

### Post by dacool25 on 2007-07-27
Alright so if i were to put in my own dns server, how would i have it automatically update my ns record ip address, without me doing it manually every time?

---

### Post by kidders on 2007-07-27
That's entirely up to you, really. My best suggestions (as I mentioned) would be to transmit update requests over HTTPS (plus maybe a little perl script), or SSH. I'm not sure which I prefer. The specifics would depend on how your DNS service is run, and what would be most convenient for you client-side ... which is hard for *me* to guess about. If your service supports DNS updates, then you could arrange to have nsupdate (or similar) called on the primary nameserver. You may find you need to alter the frequency of updates to your secondary name servers, so people don't get fed outdated information.

If DNS updates *aren't* supported, then you'd probably have to resort to modifying all your nameservers' underlying databases manually & restarting them. In the case of Bind at least, it'd be fairly trivial (ie they're just flat text files), but you'd still have to find a way to get it to inform its secondary servers of the change, so they could replicate it.

---

### Post by dmizer on 2007-07-30
> **dacool25 said:**
> Alright so if i were to put in my own dns server, how would i have it automatically update my ns record ip address, without me doing it manually every time?
just install ddclient:
```
sudo aptitude install ddclient
```
it will update for you.

you'll have to sign up for an account with dyndns so you have your domain.  then install ddclient.  when ddclient installs, it will walk you through an install menu.  everything is self explanatory except "use device".  if your server has a direct connection (no router) to the internet, then put your wan adapter in this spot.  if you have a router, leave that spot empty.

edit the /etc/ddclient.conf file as sudo, and add this line to the end of the file:
```
daemon=600
```
then your server will automatically check your wan ip address every 600 seconds and update if necessary.  you don't want to do this too often, or dyndns gets upset and locks your account.

---

### Post by kidders on 2007-07-30
> **dmizer said:**
> you'll have to sign up for an account with dyndnsThis seems to be exactly what the o/p *doesn't* want to do. :confused:

---

### Post by dmizer on 2007-07-30
so you're right.

well, unfortunately you can't do this with your own server unless your dns server is acredited and registered (read: $$$$$$$$).

only way i can think of to have this happen without using a dynamic domain service like dyndns, is to have a static ip from your provider, and purchase a registered domain.

---

### Post by csaga on 2007-09-03
I signed up for a free [COLOR="Red"]dyndns [/COLOR]account and everyting working fine, but how can i update my [COLOR="Red"]dyndns[/COLOR] acount automatically, when start Ubuntu?
Thanks for answers!

---

### Post by wieman01 on 2007-09-03
> **csaga said:**
> I signed up for a free [COLOR="Red"]dyndns [/COLOR]account and everyting working fine, but how can i update my [COLOR="Red"]dyndns[/COLOR] acount automatically, when start Ubuntu?
Thanks for answers!
See above. There is a tool mentioned in the thread. In addition to this some routers support the use of DynDNS. At least mine does (Linksys DD-WRT).

---

### Post by csaga on 2007-09-04
I install the **ddclient** program but when start and configuring i dont understand this:
*Interface used for dynamic DNS service*?
Thanks for help!

---

### Post by wieman01 on 2007-09-04
That would be your network interface e.g. eth0, eth1, wlan0. Find out about your interface using "ifconfig".

Manual: [http://ddclient.wiki.sourceforge.net/Usage]("http://ddclient.wiki.sourceforge.net/Usage")

---

### Post by csaga on 2007-09-04
I try with **eth0** but also have a **ppp0**? Before i proceed below:
Start the terminal and paste this code:
**sudo sh /etc/ppp/ip-up.d/dyndns_update.sh** and when pinging my domain and connect to my PC is working fine. Now, with ddclient when i try to ping nothing happens!
Thanks for help!

---

