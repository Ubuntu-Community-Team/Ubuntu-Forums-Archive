---
title: "Problem opening HTTPS websites: gnutls_handshake() failed"
date: 2018-10-09
forum: Networking &amp; Wireless
---

### Post by rmam2 on 2018-10-09
I'm using Ubuntu 16.04 and I've noticed that sometimes some web pages  simply don't load and the browser fails silently, ending up showing an  empty page.  I've also noticed that when I use curl to open one of these  web pages, the output returns the message "gnutls_handshake() failed: Error in the pull function."

Apparently this problem is also behind some pip issues I've been having lately.

Does anyone know what's behind this problem and, more importantly, how to fix this?

---

### Post by TheFu on 2018-10-09
Welcome to the forums.

I have a troubleshooting idea.

Create a new userid.
Login using that userid and try using a few different browsers.  
If it works perfectly, then you know it impacts only 1 userid and the issue is in that other users environment and settings.
If it fails in the same way, then you know it is a system-wide problem, probably created by modifying the system settings somehow.

And as always, do the system log files have anything interesting related to this or other problems inside them?

---

### Post by rmam2 on 2018-10-09
Hi @TheFlu

Thanks for the idea.  However, I've experienced the gnutls_handshake() fail while trying to access sites that don't require a user ID.  For instance, trying to open a tutorial page from Vagrant triggered the handshake fail I've posted in the previous email.

---

### Post by TheFu on 2018-10-09
I think you missed my point.  It isn't about **any** remote userid. Or I could have misunderstood.

---

### Post by rmam2 on 2018-10-10
@TheFlu in that case I really didn't understood your suggestion.  Sorry about that.  In that case what do you mean by "create a new userid" ?  Are you suggesting I create a new user account on Ubuntu to check if gnutls_handshake() still fails?

---

### Post by TheFu on 2018-10-10
> **rmam2 said:**
> @TheFlu in that case I really didn't understood your suggestion.  Sorry about that.  In that case what do you mean by "create a new userid" ?  Are you suggesting I create a new user account on Ubuntu to check if gnutls_handshake() still fails?

yes.

---

