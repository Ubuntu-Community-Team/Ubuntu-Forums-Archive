---
title: "Home Networking Help"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by Landara on 2008-08-12
So I finally have Ubuntu working more or less here, but the one problem I have is accessing my laptop on the network.  I can see it, but there's nothing there at all when I click it.  Its running 32b Vista, Im running 64bit Ubuntu. I read a bit here but all of this happens to be about wireless and internet, I am not wireless here(though my laptop is of course) but I am wired to the hub.  And my Internet works fine.  Any information would be helpful :)

---

### Post by jonathanmotes on 2008-08-12
You have to install Samba to access Windows machines from Ubuntu. Have you done that?

If not, use Synaptic Package Manager to do install it first.

---

### Post by Iowan on 2008-08-12
My Gutsy came with Samba-client pre-installed - Server must be installed, though (to share files with Windows machine).  To quote **superprash2003** in [this]("http://ubuntuforums.org/showthread.php?t=870330") thread:> **superprash2003 said:**
> to access windows shares from ubuntu go to terminal and type nautilus smb://x.x.x.x whre x.x.x.x is the ip of the windows machine..
about the samba issue.. go to the terminal and type sudo gedit /etc/samba/smbusers and post output here.. also try uncommenting the line guest account = nobody

---

