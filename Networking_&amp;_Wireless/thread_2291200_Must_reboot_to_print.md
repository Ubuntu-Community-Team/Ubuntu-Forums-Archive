---
title: "Must reboot to print"
date: 2015-08-18
forum: Networking &amp; Wireless
---

### Post by rogersma on 2015-08-18
Recently I bought an HP Envy 4504 all-in-one for my home office.  I've been really pleased with it -- very easy setup with our smart phones (1 iPhone, 1 Android) and my desktop running Ubuntu 14.04.  Scanning and printing have worked very well, but printing doesn't work when my desktop is already up and running.

Normally I don't power up the printer until I need it -- every few days.  I've discovered that if my desktop is already on, the printer appears in the printer System Settings and in Envision or acroread, but print jobs (even the System Settings test page) get stuck in the queue.  If I reboot the desktop, then printing works again.  I don't have this problem with the smart phones, so at the moment, I e-mail documents to myself and use my iPhone to send them to the printer.  This is cool, but I'd love to learn how to make it work correctly on my desktop.

I assume something needs to be restarted or prodded.  I've tried restarting the cups daemon, but the commands I've found on the internet don't work for me.  If I use
```
sudo service cups restart
```
I get the message:

```
stop: Unknown job: cups
start: Unknown job: cups

```

I'm sure the solution must be simple, but I've had a helluva time trying to find information on this specific issue online.  I appreciate any ideas from the more experienced sysadmins here -- many thanks in advance.

---

