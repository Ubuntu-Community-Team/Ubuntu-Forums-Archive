---
title: "Ubuntu v.22 to W10 RDP"
date: 2022-08-18
forum: Networking &amp; Wireless
---

### Post by glex711 on 2022-08-18
How to RDP Ubuntu from w10 tried already tutorials what could be wrong anyone?

Sample tutorial links

[https://www.makeuseof.com/tag/how-to-establish-simple-remote-desktop-access-between-ubuntu-and-windows/](https://www.makeuseof.com/tag/how-to-establish-simple-remote-desktop-access-between-ubuntu-and-windows/)
[https://linuxhint.com/enable-remote-desktop-ubuntu-access-from-windows/#:~:text=First%2C%20search%20for%20the%20Remote,LTS%20computer%2C%20and%20click%20Connect](https://linuxhint.com/enable-remote-desktop-ubuntu-access-from-windows/#:~:text=First%2C%20search%20for%20the%20Remote,LTS%20computer%2C%20and%20click%20Connect).

Anyone can assist with me about these problems?

---

### Post by TheFu on 2022-08-18
RDP is the issue.  MSFT has created a number of security enhancements with every release, so the Gnome team tries to guess what will be the current for most users, within limits.  The trick for you is to figure out what your Win10 RDP security settings are and try pick the correct ones for a client.  

Saying "it doesn't work, help" doesn't tell us enough to attempt to help.  We need exact versions of and which software you're using and what the log files say, specifically any errors on both the client and the server.

Can you confirm that you want an Ubuntu client to RDP into a Win10 server?

I have no idea what "v.22" means. Please be exact.

---

