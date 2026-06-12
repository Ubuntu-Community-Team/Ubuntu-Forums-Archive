---
title: "LTSP login with Feisty"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by calvarymanagua on 2007-05-23
I have been using K12LTSP for my LTSP server.  I decided to change over to Ubuntu to give it a try.  Unfortunately, I am having some problems.

1) I cannot get the resolution that I desire.  When the login screen comes up it is at 800x600.  When I log in, I do not have the option to change it to 1024x768.  In k12LTSP, I had the same problem and changed the lts.conf file to say XSERVER=cirrus.  This solved the problem.  However, in Ubuntu it does not seem to work?  Any ideas why - is there something else I have to change

2) When I change the language of a user on the server - it does not change the language on the client.  I have to manually change the language on every boot up.  Is there a way to set up default languages for the clients?

3) every once in awhile I will get a problem with nfs-premount.  I have no idea why this would happen and it is not consistant.

If anyone has an ideas thanks
Brian

---

