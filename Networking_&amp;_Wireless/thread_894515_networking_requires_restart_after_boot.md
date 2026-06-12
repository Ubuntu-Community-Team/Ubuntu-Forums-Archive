---
title: "networking requires restart after boot"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by rw_mott on 2008-08-19
Hi,
I have configured my wireless setting manually via NM. Whenever I boot/reboot my computer the connection doesn't work. If use the terminal to restart the networking interfaces it then all works fine.

I've since been trying to make a script to run on boot up that restarts the network interfaces to get round the problem but i can't get it to run because it requires sudo and a password.
Could anybody help either to get the script to run properly or to solve the problem with the connection in the first place?

thanks,

---

### Post by Iowan on 2008-08-19
Check the **/etc/network/interfaces** file to  verify an "auto" line for your wireless adapter. Add one if it doesn't have one.

---

