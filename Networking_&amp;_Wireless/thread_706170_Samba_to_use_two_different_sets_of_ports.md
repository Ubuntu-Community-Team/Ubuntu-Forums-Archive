---
title: "Samba to use two different sets of ports?"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by eku on 2008-02-24
I have Ubuntu working as a network drive at my parent's home. They have two Windows machines, which both have network drive for backuping things.
Ubuntu is running samba.

I don't live at my parent's place and I have Vista. I want to access my parent's Ubuntu the way I would access it as I would be at my parent's house.

Problem is, ISP is blocking all ports smaller than 1024. So, in order to access my parent's Ubuntu by samba, I should have to make Samba also use some ports higher than 1024.

My Vista is behind a wlan router. It could be used change the ports back to "defaults", so my Vista (or any other computer on this network) would be able to access it easily.

Now, how I make my parent's Ubuntu to use two different sets of ports? One set to be used at LAN, and other to be used at WAN?
Or is this impossible?

L

---

### Post by ryanhaigh on 2008-02-24
Looking at the man page for smbd (the samba daemon) it appears as though you can specify mutliple ports in your /etc/samba/smb.conf file. I have never done this so I can't give you exactly what you need.

I don't know if samba would be the best way to allow what you are trying to do here, having samba shares accessible on the net just seems like a bad idea to me for security reasons. I would recommend installing an ssh server on the ubuntu machine and using something like WinSCP to access your parents ubuntu system via ssh/sftp. There are instructions on how to setup an ssh server and do file sharing using this more secure protocol here 
[https://help.ubuntu.com/community/SSHHowto#head-1aa0ea24fdf28c7516f58131897fa15691d8e58d](https://help.ubuntu.com/community/SSHHowto#head-1aa0ea24fdf28c7516f58131897fa15691d8e58d)

If you still want to have the share available over the net this page may be useful:
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/cfgsmarts.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/cfgsmarts.html)
It says something about specifying ports by smb ports = portnumberhere but doesn't really mention multiple ports. I assume you have thought about it but just incase: if your parents also have a router do the port forwarding on that aswell as yours to allow the change without modifying samba.

---

