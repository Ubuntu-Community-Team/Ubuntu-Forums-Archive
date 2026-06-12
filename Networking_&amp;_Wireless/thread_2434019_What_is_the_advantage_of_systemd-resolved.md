---
title: "What is the advantage of systemd-resolved"
date: 2019-12-29
forum: Networking &amp; Wireless
---

### Post by holiday on 2019-12-29
After discovering that systemd-resolved was inserting my ISP's DNS servers into my DNS search list, I did this :

- disabled systemd-resolved
- deleted the /etc/resolv.conf link
- recreated resolv.conf as a static /etc/resolv.conf  listing only the DNS servers I want (Cloudfare)

I have had no problems with this approach -- for more than a year now.


But I wonder : what features of systemd-resolved  am I missing with this configuration.

---

### Post by TheFu on 2019-12-29
Well, clearly it is the attention to backwards compatibility and that everything "just works" without any admin or user needing to touch anything.

**NOT!**

When systemd-resolv broke here, I removed it and put in a DNS-over-https solution. That was a few years ago.  Haven't had any issues since.  DHCP is only used for portable devices.  Non-portable devices have static IPs, static network settings, some addition routes, additional firewall rules to limit network hopping and a few Linux bridges needed by some different virtual machines.  Since systemd started taking on more and more stuff, they seem to get picked up and made default much too soon, before features are complete.  I suppose for trivial configs, things might just work. That hasn't been the experience here, which has lead to our scepticism around anything that project touches.  resolvconf attempted to fix issues our sites never had.  Systemd-resolv seems to be trying to fix resolvconf issues ... that we never had.  All the changes in networking stuff the last few years have been problematic for us.  We didn't deploy 18.04 due to netplan issues.  Probably 80% self-inflicted.  Initially, the bridge support in netplan wasn't there.  The lack of post-up and pre-up capabilities has been an issue too.

Startup/shutdown/restart of services seems to be handled very well now.  I'm still running into surprises around the systemd-mount stuff.

I definitely do appreciate their picking up crufty, unmaintained code and doing some good new stuff.  Pulse audio has been stable now for about 2 yrs. The same leader of systemd did pulse audio, if you didn't know it. 

This same issue runs throughout anything systemd touches, IME.  For example, systemd has taken over mounting file systems in the fstab, but decided those last 2 numbers in an fstab record should be binary - 0 or non-0.  This fundamentally changed existing behavior without telling anyone.

Also, **sudo touch /forcefsck** was too complicated to get the root file system to run an fsck next boot.  The systemd guys decided to do something else, which is fine, but why not support the old method too?

Sorry for the rant. Just seems some extremely important core subsystems are being replaced by half-working solutions well before they are feature or production ready.  Eventually, things will get there, but in the meantime, there is pain.

Don't get me started about snapd.

---

### Post by Tadaen_Sylvermane on 2019-12-29
> After discovering that systemd-resolved was inserting my ISP's DNS servers into my DNS search list, I did this :

It only uses what the dhcp server gives it. Fix that and your problem is solved. Dont get on that waste of time anti systemd bus. It isnt the problem.

---

### Post by holiday on 2019-12-29
> **Tadaen_Sylvermane said:**
> It only uses what the dhcp server gives it. Fix that and your problem is solved. Dont get on that waste of time anti systemd bus. It isnt the problem.

I don't have a problem with systemd. I generally like it. 

In fact I don't have a problem at all. I have a question:

What am I missing by not using systemd-resolved? That doesn't trouble me;it interests me.

Looking for more here than a simple "Don't worry; be happy" response.

---

### Post by CatKiller on 2019-12-29
> **holiday said:**
> What am I missing by not using systemd-resolved? That doesn't trouble me;it interests me.

Automatic DNS caching and automatic DNS encryption, mostly. There's a bit more information [here](https://www.ctrl.blog/entry/systemd-resolved.html), [here](https://www.freedesktop.org/software/systemd/man/systemd-resolved.service.html), and [here](https://www.phoronix.com/scan.php?page=news_item&px=systemd-229-Released). Or you can check the man pages.

---

### Post by holiday on 2019-12-30
> **CatKiller said:**
> Automatic DNS caching and automatic DNS encryption, mostly. There's a bit more information [here](https://www.ctrl.blog/entry/systemd-resolved.html), [here](https://www.freedesktop.org/software/systemd/man/systemd-resolved.service.html), and [here](https://www.phoronix.com/scan.php?page=news_item&px=systemd-229-Released). Or you can check the man pages.

So if I'm reading correctly I can replace resolved with my own bind9 server for caching and dnssec. Okay I've done that.

Am I missing something there?

---

### Post by CatKiller on 2019-12-30
> **holiday said:**
> Am I missing something there?

No, I don't think so. You've just had to do three steps rather than none. It's not some explosive and revolutionary change, it's just consolidating things so that they're easier to automate and standardise.

---

