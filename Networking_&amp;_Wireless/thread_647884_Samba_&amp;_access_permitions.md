---
title: "Samba &amp; access permitions"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by marco202 on 2007-12-22
I'm sharing one folder in my home directory. When I put files or folders in it, other computers on the network can see it but can't access files untill i set permitions to newly added files/folders to 777. 

Is there a way to make files and folders from the shared folder always avaiable to other computers without the chod -R....?
Security is set to share.
 
Setting in smb.conf is : 
[share]
path = /home/smark/share
available = yes
browsable = yes
public = yes
writable = no

Can it maybe help to uncomment this line : ;   guest account = nobody with my user name?

---

### Post by gilf on 2007-12-22
I found that one of the problems I had was that you have to set up Samba users as well as folder shares.

A GUI program that made this easier for me is:

system-config-samba

I downloaded it through Synaptic.

Once installed it is accessed from the panel via System>Administration>Samba.

When it opens it shows your shared folders and devices with their location, names,  permissions, visibility and comments.

If you click on File>Preferences you can chose to see your server mode details or you can chose to see users listed in your system. You can add new users there.

When looking at the shares in the main view, if you click on one, you can edit the permissions and users.

This really cleared up a lot of my Samba problems with permissions, users and shares.

---

### Post by marco202 on 2007-12-23
I installed that package, but still have the same question. I don't use user mode for samba authentication, so when I add some new folder in share it still has permissions (ext3 permissions) that doesn't allow users outside of my user name's group to access them (default behaviour). 

In Samba Server Configuration, server settings, security tab, it says Guest account : No guest account. Is that OK?

---

### Post by gilf on 2007-12-23
This thread helped immensely in setting up samba in my own system.

You'll find information there about folder permissions as well:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by djfick on 2007-12-23
> **gilf said:**
> I found that one of the problems I had was that you have to set up Samba users as well as folder shares.

A GUI program that made this easier for me is:

system-config-samba

I downloaded it through Synaptic.

Once installed it is accessed from the panel via System>Administration>Samba.

When it opens it shows your shared folders and devices with their location, names,  permissions, visibility and comments.

If you click on File>Preferences you can chose to see your server mode details or you can chose to see users listed in your system. You can add new users there.

When looking at the shares in the main view, if you click on one, you can edit the permissions and users.

This really cleared up a lot of my Samba problems with permissions, users and shares.


Great help for me!  Thanks a bunch.  I'm afraid I might be getting the hang of this

---

### Post by marco202 on 2007-12-24
Enabling guest user and setting guest ok=yes on each share solved the problem. TNX!

---

