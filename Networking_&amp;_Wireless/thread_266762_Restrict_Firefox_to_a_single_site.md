---
title: "Restrict Firefox to a single site"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by swaaye on 2006-09-27
Is it possible to restrict Firefox to one site? I want to use a machine as a kiosk for employees and customers, but I don't want to allow browsing the entire web...

---

### Post by madmetal on 2006-09-27
i am not an expert but i think that squid you can helpp you with this..
:-k  (waiting for more experienced answers..):-k

---

### Post by wenzlicker on 2006-09-27
It really has nothing to do with firefox, but with your router configurations. You could set up you router (provided that you have this option in your router), to block all but a specific domain.

I'm not a networking expert, so I can't give you a lot of information, but I've seen this done in computer labs to block WoW, myspace, facebook, etc.

---

### Post by fstab on 2006-09-28
I recommend setting up a firewall on the kiosk using iptables.  Configure it  to drop packets packets on port 80 by default, but accept packets on port 80 whose IP address matches the single site.

---

### Post by sbergman27 on 2006-09-28
> **swaaye said:**
> Is it possible to restrict Firefox to one site? I want to use a machine as a kiosk for employees and customers, but I don't want to allow browsing the entire web...

For a kiosk, you may want to look into Epiphany and its lockdown settings:

Applications->System Tools->Configuration Editor->Apps->Epiphany->Lockdown

---

### Post by swaaye on 2006-09-28
I'm not seeing the Lockdown app for Epiphany you mention. I installed Epiphany from the repositories.

edit: nm. I had to get "pessulus". This looks like it will do the job quite adequately. Thanks.

---

