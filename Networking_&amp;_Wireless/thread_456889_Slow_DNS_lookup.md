---
title: "Slow DNS lookup"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by likwid on 2007-05-28
Hi

I'm having problems with browsing internet and constantly having to waiting for web browser to look up/receive addresses.

The routers Linksys WRT54GL with DDWRT firmware. Another networked box works fine. I have tried static and dhcp ip.

I had already disabled ipv6 and I tried using opendns on the router and the local machine (/etc/resolv.conf).

It's odd because when i first boot up everything's fine, but after a few minutes i am constantly waiting for firefox to look up addresses, which takes usually around 9-10 seconds each. It's not firefox as i've tried konqueror. As i mentioned, there's a windows installation on the same pc and it works perfectly.

---

### Post by mkor on 2007-05-28
I have similar problem with my D-Link adsl router. In my case the DNS works or not, randomly, but more often does not work. For me, the only solution was to use static IP on my laptop and put my provider's DNS addresses into /etc/resolv.conf. Are you saying it does not help in your case? I've been thinking of buying the same router you have... well, I'll have to think twice.

One more thing - before I changed to static address, I tried just setting DNS servers in resolv.conf, but the DHCP client used to overwrite my entries each time the network was up - that's why I use the static address now.

---

### Post by likwid on 2007-05-28
Thanks for answer.

I have a static ip and have also tried defining dns servers as you describe.

I'm certain the problem doesn't lie with the router, which is very good, but with my installation of ubuntu. I have another ubuntu pc, same version, static ip, which works absolutely fine.

It's a really frustrating problem as i'm in the middle of a huge project for uni. If anyone can help i'd be very, very grateful.

---

### Post by kerry_s on 2007-05-28
Try changing your router/wireless beacon interval to something shorter. You might want to also start cacheing the dns's for faster browsing-> [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

---

### Post by likwid on 2007-05-28
Thanks for advice.

The local cache doesn't work either, which is really strange but perhaps will be likely to help diagnose what's wrong. 

After the initial caching of addresses i experienced some very quick browsing for 3-4 minutes before the same behaviour persists as before. Initially all is well but after a few minutes firefox's status bar informs me that it's 'looking up' whatever address i'm navigating to. This pause usually lasts 9-10 seconds, which ends up wasting a lot of time.

Oh, i checked that resolv.conf hasn't been overwritten. I'm on a static ip so it shouldn't and it hadn't.

Also worth pointing out that if i switch network configuration, be that changing my static ip or selecting dhcp, then i have the usual few minutes of fast browsing before the problem rears its head again.

Further, on this same pc i have a windows installation on another partition which gets used occasionally. Don't know if this might be significant but..

---

### Post by likwid on 2007-05-28
Some research indicates this might be a problem with udp port 53 being blocked? 

I'm not sure why if this were to happen it wouldn't be consistent, ie. why i get these few minutes of favour when logging in or reconfiguring local ip address. I don't have any firewall gui installed and i assume that this means the ports are open outbound. My router has a firewall but nothing is blocked outbound.

Anyone any ideas? :(

---

### Post by likwid on 2007-05-28
Anyone any ideas before i try reinstallation which i really, really don't have time for.

---

### Post by kerry_s on 2007-05-28
My guess is it's your router, linksys have always been touchy, which is why i hate that brand, i would try resetting your router to stock then setting it up so you know exactly whats set.

---

### Post by likwid on 2007-05-28
Hey again.

I don't think it can be the router given that another ubuntu machine works ok, as well as windows installations, and the fact that local caching of addresses doesn't help. Also my understanding is that the DDWRT firmware is pretty solid.

---

### Post by likwid on 2007-05-28
Is there an alternative to Network manager, or can i reinstall it/restore default settings?

---

### Post by bmartin on 2007-05-28
Are you using a wireless connection? If so, what wireless chipset are you using? I had a similar problem with a Broadcom 4318 chipset using the bcm43xx firmware.

---

### Post by likwid on 2007-05-28
Thanks for advice. 

I'm not using wireless but will try another network adapter tomorrow. :)

---

### Post by likwid on 2007-05-31
Well, i reinstalled ubuntu and now everything is fine and dandy. :/

---

