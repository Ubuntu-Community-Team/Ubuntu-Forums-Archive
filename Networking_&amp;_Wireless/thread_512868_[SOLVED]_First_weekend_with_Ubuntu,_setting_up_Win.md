---
title: "[SOLVED] First weekend with Ubuntu, setting up Windows Shares"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by mikeliketrike on 2007-07-29
I can't see my desktop (running Ubuntu with a wired connection) on my laptop (with Win XP and a wireless connection) and I don't know why.  I can see both computers from within Ubuntu, but in Win XP, the laptop can only see itself.

Here's what I know:
 - Samba's installed
 - I've shared the folders on the desktop that need to be by right clicking on them and selecting to share, but I can't edit the read/write permissions because I don't log in as 'root'
 - I'd really like to rename the shared folders, but I don't know how to
 - I tried setting up the permissions for the folders by typing 'chmod 777 //share', but I'm not sure that it did anything
 - The drive that contains the shared folders is mounted

I've read through Samba tutorials and How To's in this forum regarding networking, but everything I've tried doesn't seem to work.

---

### Post by jimrz on 2007-07-29
> **mikeliketrike said:**
> I can't see my desktop (running Ubuntu with a wired connection) on my laptop (with Win XP and a wireless connection) and I don't know why.  I can see both computers from within Ubuntu, but in Win XP, the laptop can only see itself.

Here's what I know:
 - Samba's installed
 - I've shared the folders on the desktop that need to be by right clicking on them and selecting to share, but I can't edit the read/write permissions because I don't log in as 'root'
 - I'd really like to rename the shared folders, but I don't know how to
 - I tried setting up the permissions for the folders by typing 'chmod 777 //share', but I'm not sure that it did anything
 - The drive that contains the shared folders is mounted

I've read through Samba tutorials and How To's in this forum regarding networking, but everything I've tried doesn't seem to work.

try this
```
sudo chmod -R a+rwx /<full path to shared folder>
```
from the terminal for each folder you want to share

---

