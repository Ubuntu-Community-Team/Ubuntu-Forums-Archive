---
title: "Backup software for Ubuntu Server"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by cbelote on 2009-10-14
I have a Dell Poweredge server that is running the latest version of Ubuntu Server (w/ Ubuntu Desktop installed) in my home that I'd like to use to backup several windows vista computers on my LAN. I don't care for any of the "cloud" backup solutions out there (spideroak, mozy, etc). Id like a prety powerful software suite that would allow me the option of encrypting the local backup store; a web interface; advanced scheduling based on either time or file modification. 

Anything out there like this? What would you recommend? Thanks!

---

### Post by Girya on 2009-10-14
My vote is for backuppc. It has everything you want except for encryption (it might have it, I never bothered to look). It has a couple of  features that made it ideal for me: Data pooling to save on disk space and the ability to backup clients with no client side software. My set up is on a LVM disk which has saved me when I filled up a disk and needed more storage. 

[http://backuppc.sourceforge.net/info.html]("http://backuppc.sourceforge.net/info.html")

---

### Post by cbelote on 2009-10-14
I like the configurability of backuppc and especially like the data pooling feature! Thanks :) I've searched their wiki though and can't find any options for encrypting the store. This is a must have feature for my situation: this machine will also act as a webserver. Even though I have all my folder permissions set correctly and the backup store will reside on a completely different raid array I'd still like the insurance ;)

---

