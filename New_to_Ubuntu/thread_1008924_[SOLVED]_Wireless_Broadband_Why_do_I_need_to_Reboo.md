---
title: "[SOLVED] Wireless Broadband: Why do I need to Reboot if Signal Lost?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Andavane on 2008-12-12
I am posting from an internet cafe.
From time to time the signal is lost; we tell the cafe owner who "does something", and after that the signal is fine.

Am using a Sony Vaio Laptop VGN-S3HP (13.3 inch screen).

Last year in the same place on the same machine, whilst running Windows XP,
when the same thing happened, the owner would "do something" and I'd get the signal back straight away without the need for rebooting.

When this happens here & also in UK (on Hardy), I need to reboot.
Is there something I can do so that when the signal is lost I get it back straight away without the need to reboot?

Regards,

John

---

### Post by lisati on 2008-12-12
It sometimes takes *ubuntu a little while to realise that the signal is back. You could try clicking on the networking icon on your panel and trying to re-establish the connection from there.

---

### Post by Andavane on 2008-12-12
> **lisati said:**
> It sometimes takes *ubuntu a little while to realise that the signal is back. You could try clicking on the networking icon on your panel and trying to re-establish the connection from there.
Thank you.
When it happened, the Cafe Owner suggested I click on the netowrking symbol:

properties/network name (ESSID): (cafe name) was there, but signal not received.
Owner tells me that he went to his equipment, and saw my signal which was then accepted by him. Still I needed to reboot to receive the signal.

If this happens again,  have thought of manually entering the static IP address. Does this sounds sensible? We will try anyway.

Regards

John

---

### Post by plucky on 2008-12-12
Have you tried restarting networking?

From a terminal

```
sudo /etc/init.d/networking restart
```


Good Luck

---

### Post by Andavane on 2008-12-13
> **plucky said:**
> Have you tried restarting networking?

From a terminal

```
sudo /etc/init.d/networking restart
```


Good Luck
Yes, typing in that command worked a treat.
Cheers!
John

---

