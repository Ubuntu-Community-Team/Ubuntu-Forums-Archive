---
title: "File sharing with a XP machine"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by WildOscar on 2008-06-21
I never had this trouble until now. In my previous install of 7.04 file sharing with a XP / Mac was a breeze didn't have to do a whole lot of configuration.

Finally, Hardy made it down right impossible (for me). I just dun know how to work around it. I hope people can give a easy step-by-step to get this workin.

My set-up:

Laptop -Running on XP (Office)
Desktop -Running on UBUNTU Hardy Heron (Home)

My Goal:

Is to connect to my shared folder in my home machine from my office so i could share my folders.

My connection is 2mbps/DSL. I can configure the firewall and port forwarding and also have already setup no-ip on the ubuntu machine and its running. Am able to ping my dekstop from the office.

How do i share that folder. Must i install nautilis or something??

---

### Post by tornado89 on 2008-06-21
Make Sure That The Samba Package Is Installed Correctly
And That The Samba Service Is Running..

Then U Can Share Your Folders Using Nautilus....

---

### Post by WildOscar on 2008-06-21
> **tornado89 said:**
> Make Sure That The Samba Package Is Installed Correctly
And That The Samba Service Is Running..

Then U Can Share Your Folders Using Nautilus....
Thanks! but have found a work around using a web post i found.

Link:[http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/](http://jngalloway.wordpress.com/2008/06/08/easy-file-sharing-in-ubuntu-no-editing-text-files/)

but still... is this a bug or a security feature! are there any better work around for this? so it could be done from gnome and not start nautilus every time i want to share something?

---

### Post by jetsam on 2008-06-21
> I can configure the firewall and port forwarding

GAK!  Do not use Samba to share files over the Wild Wild Web!  

The underlying protocols are insecure and not securable.

You need an ssh server on the Ubuntu side and winscp on the Windows side (easy setup), or an ftp server (less easy), or a vpn (doable, but not really easy at all.)

---

### Post by tornado89 on 2008-06-21
Yeah..
You Can Run An FTP Server On Your Linux Machine
Setup A User And Password....
And Access It From Your Windows PC Using Any FTP Client

---

