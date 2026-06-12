---
title: "Newb having trouble with Dapper Server"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by flyinggreg on 2007-11-19
Hi all

I installed Ubuntu 6.06 Server and followed: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

Everything has gone well and I have installed WebMin.  I am trying to setup a secure LAN, a public web server, and secure web server.  My setup looks like this:

INTERNET
|
|
|
ADSL ROUTER -------->(wireless)----->clients [Win2k and WinXP]
|
|(wired)
|
v
UBUNTU SERVER

I have setup my dynamic DNS resolution service.  I had a working web site a while ago when I had 6.06 desktop setup with Apache2 - so all these things should be ok.  FYI - I had to create dual boot - dual harddrive system for desktop because some Win software wasn't working under virtual machine...long story...since my desktop is supposed to be dual boot I lost my settings for Apache2, etc.  "Someone" was too smart to write configs to backup disk...DOH! :(

Here's the issue...I can only access my server from a client by only using the IP address of the server...webmin & apache2 default webpage in /var/www.  I cannot access it using "http://localhost" or "localhost" or using my website name.  I have setup the sites-enabled to show the default ServerAlias to be localhost, website, etc.  I know this is something simple I am missing - because I've had this working before!

So this Newb says thanks ahead of time for the responses!

---

