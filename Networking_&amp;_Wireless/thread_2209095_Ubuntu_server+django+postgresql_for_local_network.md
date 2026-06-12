---
title: "Ubuntu server+django+postgresql for local network"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by eakDev on 2014-03-03
hi everyone, here is the scenario:

GOAL: setup a LAN server that can host an internal website for the departments connected on a local area network

SPECIFICS: web framework: Django, server: SQL (postgresql)

PROBLEM: How do I setup a server to host the website and be available to the network?

IDEAS ON MY MIND: (for commenting)
1. Install Ubuntu Server on one computer and install the website there? would this be sufficient?
2. Use a NAS server (can I host the website on a NAS server? how?)

NOTES:
- it would have been easier to just host the website online but they don't have a reliable ISP due to the location of the municipality (yeah trust me we still have a lot of places with no internet).

Help would be grate!!!

---

### Post by SeijiSensei on 2014-03-04
I don't know about Django, but setting up a web server with Postgresql is not hard.

Install a copy of the [server edition]("http://cdimage.ubuntu.com/ubuntu-server/precise/daily/current/") which comes with the Apache web server.  You'll have to install PG separately:

```
sudo apt-get install postgresql-server
```

By default, the server uses the directory /var/www as the "DocumentRoot" in Apache.  Put your website there, give the machine a name on your network, and it should work fine.

Django is written in Python so you might need a couple of additional packages like python3-postgresql and libapache2-mod-python.  You'll need to read the Django documentation to know what is required.

---

