---
title: "Odd Home Network Problem"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by Doji Grovesai on 2007-11-23
I have 2 computers: a Dell Inspiron 600m laptop running Fiesty, and a Dell Dimension desktop running the same.  The desktop is a "headless" machine.

My network runs through a Linksys wireless router/gateway.  The laptop connects wirelessly, and the desktop is wired in.

The problem:
My desktop cannot connect to the internet.  This isn't a terribly big deal, except that it makes updating software a little problematic.  Using the laptop, I can vnc into the desktop machine.  It works just fine.  I can ping the desktop as well.  But for whatever reason, I cannot make the desktop connect to the internet.  I cannot update the software via repositories, nor even connect to google.

I've never come across this sort of problem before, so all help is appreciated.

---

### Post by jflaker on 2007-11-23
do you have WEP or WPA on your access point?

---

### Post by caricc on 2007-11-23
If you are using wpa for your router security, then try and get a copy wicd for your network manager. You may need to d/l it with your laptop to get it on you pc. This is the only network manager I am currently using. I have not had any problem with my home network on the pc or my laptop connecting.

---

### Post by wirelessmonkey on 2007-11-23
This has nothing to do with your wireless security. If you can ping your laptop from your desktop and vice versa, I'd guess that you have misconfigured DNS on your desktop machine.

---

### Post by Doji Grovesai on 2007-11-24
> **wirelessmonkey said:**
> This has nothing to do with your wireless security. If you can ping your laptop from your desktop and vice versa, I'd guess that you have misconfigured DNS on your desktop machine.

I figured that might be the case, so I used network manager to alter the hardware configuration.  I took all the settings for everything (subnet mask, gateway address, DNS, etc.) from what was given on my linksys router.

It still doesn't work, and I'm not sure where else I could get the correct settings from.  The router seemed the logical choice to me.  Any ideas of where else I could go?

---

