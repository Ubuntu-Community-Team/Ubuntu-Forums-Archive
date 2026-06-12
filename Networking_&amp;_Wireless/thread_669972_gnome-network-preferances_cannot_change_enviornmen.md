---
title: "gnome-network-preferances cannot change enviornment variables?"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by mooglinux on 2008-01-16
I installed dansguardian with tiny proxy a little while ago and have since removed them. Now i cannot connect to download from the repositiries whether it be through synaptic, add/remove programs, or apt-get. After a lot of poking around and reading up on things, i have learned that my http_proxy enviornment variable is goofy, and needs to be changed back or removed. however, i am stumped how to do this. gnome-network-preferances gives me this error when i open it:
```
The application "gnome-network-preferences" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.
```
clicking 'details' tells me this:
[COD Can't overwrite existing read-only value: Value for `/system/proxy/mode' set in a read-only source at the front of your configuration path[/CODE]

/etc/enviornment
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
```

sample error message when trying to fetch the repo indexes:
```
http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
```

so the http_proxy variable is set to connect to localhost at port 8080 but i cannot figure out how to fix this. i need to be able to use gnome-network-preferances as we will be setting up a proxy server soon and i need an easy way to connect to it, without setting enviornment variables if possible (at least using a gui anyways)

---

### Post by mooglinux on 2008-01-17
also, it tries to connect via port 8080 to localhost. any suggestions anywhere?

---

### Post by mooglinux on 2008-01-21
... anyone at all?

right now i cannot get anyhthing from the repositories, and that leaves my computer a bit crippled, as there is software i need to install and many updates

---

