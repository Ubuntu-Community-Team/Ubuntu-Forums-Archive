---
title: "NFS mounted remote home directories"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by kesomir on 2008-03-01
My setup:

Ubuntu 7.10 clients and server

Home directories mounted from a remote NFS server using automount (previously using fstab nfs mount).

There are other shared directories also mounted over nfs using automount.

Problem:

A vast amount of network traffic after login which makes client stations unusable (applications wont load, logout panel takes 5 mins to appear after clicking exit etc)

Spikes of traffic slow applications down.

Disabling the home autofs mount (and leaving others up) removes the problem,(so I know that the home dirs are the issue) but then we lose 'roaming profiles'.

-----

Is there a way to detect what process is causing the network traffic? (As a note - I have removed tracker from the system.)

Is there a way to automount each users .mozilla .gnome2, desktop and documents only?

Is there any reason people can think of why this happens?

I know theres a blueprint for a system similar to what AD does - downloads the users profile to the local machine, and synchronises on logout, but as I understand it isn't implemented yet.

All suggestions welcome.

---

### Post by Eiríkr on 2008-03-02
Don't know much about analyzing network traffic aside from what I've heard about ethereal, but I did find [thread=516565]this thread[/thread] about LDAP and profiles in Ubuntu.  It mentions that the Samba-based profile sync option doesn't work when profiles get larger than a certain size, and recommends using rsync at logon/logoff.  There's plenty more and links to other resources too.

HTH,

Eiríkr

---

