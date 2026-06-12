---
title: "vnc issue"
date: 2019-10-31
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2019-10-31
I have an issue with one of our library computers running xubuntu 18.04. I can access the admin account (librarian) via vnc when that account is logged in but I can't connect to the non admin account (darcy) when that account is logged in. I have uninstalled and reinstalled all of the vnc software. I need to log in the the user account to do live remote help. When I try to access the user account it says failed to connect to server. The admin account connects perfectly. The ufw ihas the correct ports open. On that particular computer desktop sharing is not listing as an option in setting manager-session and startup-application autostart and I can't see how to add it. I do have everything set up correctly in dconf editor. Is there anything else to try?

---

### Post by Skaperen on 2019-10-31
is your vnc setup using any security layer like ssh, ssl, or tls?  vnc might think it can't connect if it's really getting an access permission error from a security layer.  can you establish a text-only session to that user with ssh (just to verify)? are both computers running the same xubuntu 18.04?

---

