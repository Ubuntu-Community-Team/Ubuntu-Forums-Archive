---
title: "Ubuntu drive mapped as network drive in Vista?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by enim on 2009-04-27
I have an old box I want to try and use as a server for my music in my house.  It barely runs with Windows, so I was thinking about throwing Jaunty on it.  I havent been in the linux scene for a few years.

What I ultimately want to do is have the hard drive in the Jaunty box mapped from my Vista laptop as a network drive.  Is this possible?

Cliffnotes: Computer with Ubuntu, big HD.  Want to use laptop to access big HD over wireless-wired network.  Possible?

---

### Post by Ocxic on 2009-04-27
Yes, from a terminal "sudo apt-get install samba" (samba is the windows filesharing protocol)
then download webmin from webmin.org and install, this will allow you to manage the samba server.

To access it after install type "https://127.0.0.1:10000" in a web browser on your server, or "https://server.ip.here:10000" from a remote machine.

---

