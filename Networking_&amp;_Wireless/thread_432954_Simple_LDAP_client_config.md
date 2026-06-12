---
title: "Simple LDAP client config"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by kalariwarrior on 2007-05-04
Let's say that you have some Ubuntu/Debian clients with LDAP as your backend and that you want to "join them to a domain" and "map their network drive" just like in Windows so that 

1. Users can login to Ubuntu by entering their network username and password just like they would by hitting Ctrl+Alt+Del on Windows 
and 
2. User's sharespace will mount automatically at login just like they would under Windows

Here's how to do just that (of course if you already setup LDAP this may be a little basic but you never know):

[http://www.debuntu.org/ldap-server-and-linux-ldap-clients-p2](http://www.debuntu.org/ldap-server-and-linux-ldap-clients-p2)

SUPER IMPORTANT ADDITION: You need to edit libnss-ldap.conf and set the bind_policy to soft BEFORE you reboot or the comp will lock up on you!

If you have the user's home directory path in LDAP (which you should for convenience...), add this to nsswitch.conf:

automount: ldap

Then edit /etc/fstab and have it mount a /home or whatever you call your share directory.

Example: you have an LDAP field named homeDirectory: /home//username
LDAP will automount this to the /home directory from fstab on the local comp.

Make sure your /home directory or whatever you call it is being shared out from the server (type exportfs to see what's being offered).

Also check the permissions on your server to make sure that users can't browse anything but their folder.

I found that putting an icon to the user's sharespace on their desktop makes them incredibly happy. ZOMG! IT'S JUST LIKE WINDOWS!!!

---

### Post by HornedBeast on 2008-01-28
Im having an issue where sometimes the session data from a user isn't saved, and when they try to logout the client system just hangs.

Also, stuff like changing the volume from the speaker icon in the desktop isnt authorised and the user doesn't have permissions. Im fairly certain LDAP is working correctly, I beleive it to be a problem with the Client Machine. How do I set it so that all the users on my LDAP server (that seem to be able to login ok via GDM and SSH) have the same access that a normal user on a regular Ubuntu Desktop has?

---

