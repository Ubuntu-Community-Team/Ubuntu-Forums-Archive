---
title: "Sending Messages Over a network to two Windows&amp;Ubuntu computers."
date: 2009-05-03
forum: New to Ubuntu
---

### Post by SilverSnakeEyes on 2009-05-03
I'm trying to set up a messaging system for a home network, and We've succesfully used Ip messenger on the two windows computers on our network, xip messenger on the three Ubuntu PC's, and the other two don't have it.

However, for the other two, I'm trying to make it so that I can send them messages without preinstalled software, I've tried the #smbclient -M command, but whenever I try to send messages to anyone but myself, it reports the NT_STATUS_BAD_NETWORK_NAME error.

The persons I'm trying to send to are Vanrit@VS-PC and OWNER-PC (thats what they show up as in network places), I've tried #smbcilent -M VS-PC and it doesn't work.

BTW, I found out that it needed a host, like for me I sent to Ubuntu instead of sek@ubuntu, even though it didn't work, it reported success.

---

### Post by Yashiro on 2009-05-03
If they're all using a gui then I'd just use Pidgin on all of the machines. Create a Bonjour account and you're all set. On windows this may require you to install the bonjour/mdnsresponder files from apple if the machines don't have itunes.

You have a uniform chat client and this works on Windows, Mac and Linux.

---

### Post by SilverSnakeEyes on 2009-05-03
I'm trying to do it without installing anything though, I'd known about pidgin, but that requires being installed, likewise with bonjour.

They don't necessarily need to be able to reply, I just want a popup on teh recieving machine.

---

### Post by SilverSnakeEyes on 2009-05-04
I also found out about the "write" and "wall" commands, but I'm not sure if that will work when sending to Windows, will it?

---

