---
title: "firewall for small business network?"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by elj4176 on 2006-08-30
I have a small network of ~35 or so users. Mostly XP but some MAC's too and one lonely Ubuntu box for some proxy and DansGuardian.

I would like to take make a linux firewall for our network and get rid of our current hardware Xincom firewall/router. I am basically looking for advice/opinions on some of the options.
I have looked at: Smoothwall Express, IPcop, mOnOwall and I see Guarddog is listed in the Ubuntu repositories.
Are any of these 'business-class' firewalls? We will be moving our email server in house as well as our Web site within the next year so security and uptime are factors.

Thanks!

---

### Post by encompass on 2006-08-30
For a network of your size you may want to have tweaked controling... have you concidered just learning the iptable settings?  If you have experience with firewalls it may be the best way.
Commerical grade me back to the console in my opinion.  It gives you the best control with the least performance loss.  Especially if you running it as a mail server too.
Currently for my network of 3 I use firestarter.  But you may want more control.  Most if not all the softwareout there to run your linux firewall are just using iptables anyway in the backend.

---

### Post by elj4176 on 2006-08-31
I don't have a ton of experience with firewalls or iptables for that matter but I will look into it a bit more. Firestarter and Guarddog are gui's for iptables IIRC.
Our consultants are pushing us towards a hardware firewall called Watchguard for ~$1700. We would rather not spend that much at this point in time so the old pc and linux idea looks good - if it can hold up to our needs.
thanks for the reply!

---

### Post by doobit on 2006-08-31
> **elj4176 said:**
> I have a small network of ~35 or so users. Mostly XP but some MAC's too and one lonely Ubuntu box for some proxy and DansGuardian.

I would like to take make a linux firewall for our network and get rid of our current hardware Xincom firewall/router. I am basically looking for advice/opinions on some of the options.
I have looked at: Smoothwall Express, IPcop, mOnOwall and I see Guarddog is listed in the Ubuntu repositories.
Are any of these 'business-class' firewalls? We will be moving our email server in house as well as our Web site within the next year so security and uptime are factors.

Thanks!

Smoothwall, and m0n0wall are both standalone firewall/gateways that would probably work very well for your application. Smoothwall is very easy to setup. You can use practically any old computer and put two NICs in it to get it going. Once you've set it up you can administer remotely so you don't even need a permanent video monitor.

---

### Post by jefrat72 on 2006-08-31
I use IPCop for <= 20 users.  It is really easy to setup and maintain, I've found it to be very stable and some really cool add-ons.  I had it on a Dell GXa 333 with 384mb of ram.  I do url filtering now so I "upgraded" it to a GX1 866 with 512mb.  No problems whatsoever with performance.  I think the best thing is if there ever was a crash with the firewall box I have another Gxa 333 I could load and reinstall the config very quickly.

I've also use Shorewall, which is a little harder to put together but I find very flexible and again very stable.

---

### Post by rigor on 2006-08-31
without ipcop distribution,  is there a gui to admin the firewall via http?

---

### Post by jsage on 2006-08-31
elj,

> Our consultants are pushing us towards a hardware firewall called Watchguard for ~$1700. We would rather not spend that much at this point in time

Just to set your mind at ease, the Watchguards are a very good firewall for a very competitive price.  And they're even linux-based (used to be BSD).  I run several of them here.

That said, if the money's not in the budget, then perhaps a dedicated distro is the answer.  Look for a good web-based admin console and the ability to archive your rules and export your logs.

But I would pay close attention to the hardware - you don't want a box that is going to fail or that will fall flat on it's face due to traffic.  Perhaps a nice 1U Dell, HP or IBM rack-mount box.

And at minimum you'll need three ethernet adapters - one for the internet connection, one for your internal users, and one for a "DMZ" for your email and web servers.  Whatever firewall distro you pick needs to be able to route between the three adapters as appropriate.

have fun,
john

---

### Post by jefrat72 on 2006-08-31
> **rigor said:**
> without ipcop distribution,  is there a gui to admin the firewall via http?

I assume you mean "with"?  If so yes, you can connect to it command line, behind the firewall http and remotely http.  You can VPN in as well.

IPCop.org

---

### Post by Uluen on 2006-09-01
Maybe you could have a look at [Endian]("http://www.endian.it/en/community/about/")?
It's more secure default (most outbound traffic disabled which is a good thing), you open only the ports needed unlike Smoothwall et al.

---

### Post by jsutton on 2007-10-25
Avoid WATCHGUARD like the plague.
I couldn't be less happy than with this crappy WatchGuard SOHO6 router.  Only expensive paid support.  They quickly end-of-life gear too to force upgrades, no device updates ever again (even though they have plenty of issues).

They are overwhelmed by BITTORRENT use and die in the known overflow issues.  Support says its not their software, just Bittorrent's fault.  No fix offered or available.

GAMING is problematic too for some reason.  Son uses XBOX360 Live and has to reboot the WATCHGUARD every third game or so.   I'm spent hours on the lightly used Community forums trying to find answers.  People respond but they are not Watchguard tech people so their answers rarely fix things.

Avoid WATCHGUARD, and spread the word, too.

---

### Post by handy on 2007-10-26
Here is a superb how-to on IP tables:

***_[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables)_***

---

