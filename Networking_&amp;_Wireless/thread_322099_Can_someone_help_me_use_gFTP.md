---
title: "Can someone help me use gFTP?"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by RobotChild on 2006-12-20
For the life of me I cannot figure out how to setup an FTP server, however I need to to transfer 10gbs of files to my Windows box.

Can anyone walk me through setting it up? (I have it installed and stuff)

I'll be using FileZilla on Windows.

(This will be on LAN)

---

### Post by RobotChild on 2006-12-20
Bump

---

### Post by RobotChild on 2006-12-20
Basically, all I need to know is what I would put under the host, and what port to type in.

---

### Post by samiux on 2006-12-20
> **RobotChild said:**
> For the life of me I cannot figure out how to setup an FTP server, however I need to to transfer 10gbs of files to my Windows box.

Can anyone walk me through setting it up? (I have it installed and stuff)

I'll be using FileZilla on Windows.

(This will be on LAN)

The first thing is setting up a FTP server at Linux box by using ProFTP or VsFTP or else.  The port is 21 in the FTP client (Windows) and the host is your server IP or the hostname (Linux) if you are at the LAN.  Disable the firewall at Linux box for easy handling.

e.g.
sudo apt-get install vsftpd

gFTP is a client indeed.

Hope this may help.

Samiux

---

