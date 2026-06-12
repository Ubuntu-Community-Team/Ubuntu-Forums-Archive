---
title: "VPN and security question"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by vapore0n on 2007-11-19
I'm going to install Ubuntu on my parents computer this weekend.
I want to be able to connect remotely to that computer so that I can apply updates and maintenance.

I would need to open a port on their router and computer and leave it open, and install a VPN client on both sides. I would log in with my own account, not root.

Could leaving a port open cause a problem with hackers/port bangers?
How can I do all this securely?

Also, their computer might have the "auto-login" setting enabled. The account will be restricted and still have a password, different from the root one of course.
Any possible risk with that?

---

### Post by vapore0n on 2007-11-20
bump

---

### Post by wieman01 on 2007-11-20
I don't see any security risks entailed by opening a port. Just make sure that you have all (Ubuntu) security patches installed and set a secure (at least 10 characters in length, special characters, etc.) password.

Opening a port only entails a risk if the service using that port is faulty. So using an up-to-date VPN server/client will do.

---

