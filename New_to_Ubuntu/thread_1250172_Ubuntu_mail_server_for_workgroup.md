---
title: "Ubuntu mail server for workgroup"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by Daniel Nelson on 2009-08-26
Hi

I'm trying to set up an Ubuntu mail server to replace my aging Windows mail server running Workgoup Mail. 

Things I need:

1. I need to collect mail from various pop3 boxes and keep them in their own separate boxes on the local server for the different machines mail clients to collect.

2. It needs to act like a normal pop3 server for all the different platforms

3. I need to be able to keep track of the incoming and outgoing e-mail. (Business backup of sorts)

4. It should be easy to disable an account so that the sales people can connect directly to the original pop3 server when abroad.

I don't need this server to be accessed via the net, my isp won't give me a static IP in any case and the steal our lines at least once a year (South Africa, what can I say).

I have the server configure to use samba and connect to local net as well as the web with no problem.

From reading up it looks possible to use [Postfix]("https://help.ubuntu.com/community/Postfix") and [Dovecot]("https://help.ubuntu.com/community/Dovecot") to accomplish what I need. It looks like a mind bender to set up and hence the question, is there no easier way of doing this?

If no and you know of a nice simple guide to get this up and running please post it.

Thanks

Daniel

---

### Post by alexlafreniere on 2009-08-26
Try these two guides:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

[http://ubuntuforums.org/showthread.php?t=40047](http://ubuntuforums.org/showthread.php?t=40047)

---

