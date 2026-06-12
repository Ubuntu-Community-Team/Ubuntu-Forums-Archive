---
title: "Getting email to work with 3ware 3DM2"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by AndyInNYC on 2010-12-16
I have a machine set up with a 3ware 9500S card.  I installed 3dm2 and it is running.

I installed sendmail on the machine, but I wouldn't know how to configure it if it bit me.

I'm trying to configure the 3dm2 section to send emails through one of my email accounts.  I just lost a drive, so I'm a little late getting this configured.

my email address would be:  [email]aaa@aaa.com[/email]
with a password of   b3b
the email server is smtp.comcast.net

When I put the obvious answers in the correct section I crash 3md2 - as, apparently, does everyone.  I saw a reference that I need the IP address of the server, not the name, but I have no idea how to get the ip address of comcast's outgoing email server.

Any help would be appreciated.

Regards,


Andrew

---

### Post by gilligan8 on 2011-11-29
I know it's a year late... but if you are still having issues or if anyone else has this problem...

You just have to ping your smtp server and it should at least resolve even if it doesn't reply.

---

### Post by AndyInNYC on 2011-11-30
comcast was able to supply the IP address, which is fortunately static.  By using the numeric IP address rather than the words (smtp.comcast.net, etc.) email is up and running.

Of course now I'm getting barraged by warnings about one of the drives in the array and I need to replace it (always good to know the email works, less good to know that it's telling you a piece of hardware wants a permanent vacation).

Andrew

---

### Post by gilligan8 on 2011-11-30
Either way it's better to know.

Glad it worked out.  Yeah, there is a DNS bug that seems to be lingering around... not sure why 3ware/lsi can't sort that out.  Very frustrating.

I got a crazy "unclean shutdown warning" the other day on a clients server.

I knew it was nothing but I called them to reassure them that I was still monitoring the server and make sure all was ok.  Just got to make sure they call me next time they need something. ;)

---

