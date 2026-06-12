---
title: "Cannot (reliably) connect/browse to windows share"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by mkoonstra on 2008-08-30
I am trying to connect to a share on my Windows Vista PC by using Locations -> Connect to server. I then choose windows share and fill in the server and share name. After pressing OK it asks me for username and password, after doing so I get the overview of the shares content. But when I open a folder, it says it cannot open it and changes the icon to a text file.

Is there something I am doing wrong or is this a bug?

---

### Post by mkoonstra on 2008-08-31
Anyone?

I tried some more combinations, thinking the problem was vista. So I tried both a Ubuntu 7.04 Server with Samba as well as a Windows XP server with a share. The results were shocking:

The XP PC managed to connect to every server (Ubuntu samba and Vista)
Nautilus managed to connect to no server at all (Ubuntu samba, vista nor XP)

I think there is a serious bug here.

---

### Post by gregphil on 2008-08-31
I had a very similar problem under CentOS 5.2.  A friend suggested it was a gnome issue and I should try KDE.  Sure enough when I added KDE as a desktop manager option it would always find and display the other Windows or Samba "shares" on the local network but the gnome nautilus GUI app would hang forever looking for shares.  The underlying Linux operating system was the same for both desktop shells.  I never could get gnome to work right (unmodified standard centOS 5.2 distribution)

Interesting enough if changed the network hardware and connected (via a router) the private peer to peer subnet to a larger WAN network managed by a Windows domain server, then gnome would start "seeing" the local peer to peer shares right away.

In any case, KDE just worked better for peer to peer shares.

---

### Post by mkoonstra on 2008-09-01
Did not try KDE, but I did try with smbmount, which just works. I also tried gnome commander, which is also able to connect. Seems to me there is a bug in Gnome then.

---

### Post by mkoonstra on 2008-09-12
I have found that this issue is only present when winbind is installed. Winbind is used to map the hostname of windows/samba machines to ip addresses.

I hope there is a solution to this problem. I use DHCP and no DNS in my network, so I actualy depend on this feature.

---

### Post by gregphil on 2008-09-12
Been there done that.....

There is a serious bug in the new ubuntu 8.04 gnone authorization library (gvfs). This bug does not effect legacy command line tools or KDE (since they don't use the gnome library).  It does however effect many different Linux distributions, any that use the new gnome gvfs library.

The ubuntu 8.04.1 nautilus network file browser (and other gnone GUI apps) can not browse shared files from a Windows machine if authentication is required (i.e. the Windows shares are not enabled for anonymous or "guest")

See:  (and ignore the mis-leading bug titles)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

Good Luck.

---

