---
title: "Centralized user authentication &amp; server-side home directories"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by el3ktro on 2007-05-22
Hi,
I'm planning to test-install a small Ubuntu network of six client computers & one server, and I'm wondering how it is possible to have a centralized user authentication, with all users stored on the server (in /etc/passwd, within a database etc.) and server-side home directories. So when a user logs in on his computer, his username & password are checked on the server and then his home directory is mounted from the server via NFS or some other filesystem, preferably something with "offline" support so that when the network connection fails and comes back all files are synced to the server.

Is something like this possible and if yes - how? I'd appreciate any "starting point" where I could look to get a clue of how to set this up.

Thanks,
Tom

---

### Post by OneSeventeen on 2007-05-24
This is **Exactly** what I've been trying to figure out the past day or so.

I know it is possible, but have no idea how to do it.  I'm assuming if there were a package with a GUI to manage this sort of thing then more network administrators would be willing to give linux a chance for new networks and whatnot.

---

### Post by nunes on 2007-05-25
Hi,

this is exactly what i'm looking for right now.

Is there any solution for this?

I know it must involve NFS + LDAP but i have no idea how to do it.

Is there a package with a GUI that does this?

Cheers
Nunes

---

### Post by bmartin on 2007-05-25
I doubt there's a GUI to do this, but I have a set of instructions on how to set up NFS for this sort of thing. I've been interested in this endeavor myself, but since no one has posted instructions, I went searching on Google today. [Here's what I found]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS").

It's by no means a simply task; the instructions seem to assume you're using a Red Hat or Fedora or something of the sort. It appears to be a long and complicated process with a number of pitfalls; I've been using Linux for years and I wouldn't expect it to work perfectly the first time I tried.

---

### Post by jnorth on 2007-05-25
I knew I was not the only one...

I'm playing with an LDAP/Radius/MySQL authentication-only setup right now, I haven't even gotten started on figuring out how to set up NFS/cached home dirs yet.

As others mentioned, I've googled and not found any "easy" way to do it at this point, and I really don't want to set up AD.

Hoping someone finds something - I'll keep wading through .conf files until then :)

---

### Post by nunes on 2007-05-25
Hi bmartin,

thank you for your quick response.

The GUI isn't important actually. The important thing was to have a set of commands and instructions to make it work.

When this is configured, it doesn't matter if it has a GUI or not ;)

---

The guide you linked has instructions on setting up an NFS server (very complete btw).

What i was looking for was a way that the users could login in any desktop in the network and their home directory would be available (but only existed on the server). Meaning the home dir is linked to the user/pass you enter.

For this to work I think something like LDAP is necessary but i haven't tried it yet.

NFS + LDAP seems a bit hard to configure and i haven't found a guide that explains it all, only guides for each part.

Am i looking at this the wrong way?

Cheers
Nunes

---

### Post by MrFahrenheit on 2007-05-25
I don't have any links to guides, but try looking for NIS and Roaming Profiles.  It might get you the information you need

---

### Post by nunes on 2007-05-25
Hi,

I still haven't found any usefull guide but it seems NFS+LDAP is the way to go.

NIS is very insecure and Roaming Profiles, although interesting, is not what I'm looking for.

I'll search some more but it might come to merging a couple of guides.

Cheers
Nunes

---

### Post by OneSeventeen on 2007-06-09
I've heard this is possible using LDAPS (for added security) and NFS, then using Access Control Lists (ACL) to manage more advanced file permissions.

Out of curiosity, is it possible to administer a network without easily managable network authentication and advanced network storage?

Sounds like a great project to start working on, so as this post fleshes out with some methods and security tips, maybe we can start throwing together a simple interface to manage it?

---

