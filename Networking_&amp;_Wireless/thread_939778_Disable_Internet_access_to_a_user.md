---
title: "Disable Internet access to a user"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by santhoshsd on 2008-10-06
How do I disable internet access to a user and how do I re-enable it .. later on ?

---

### Post by nixscripter on 2008-10-06
Define "internet access." Do you mean blocking all outgoing traffic? What about incoming traffic? Are you just trying to make the kids stop surfing the 'net and do their homework? ;-)

In general, you can control network traffic in all sorts of ways with iptables. If you describe the problem in more detail you are trying to solve, I'll see if I can come up with a script.

---

### Post by santhoshsd on 2008-10-07
I want to disable both incoming and outgoing traffic on my system?

---

### Post by nixscripter on 2008-10-07
But where does the one user come in?

The thing is that a lot of processes for everyone use the internet in ways most users aren't aware of, so you can't cut off everything without seriously reducing usability of the system, even for "local" functions.

That is why I am asking about the goal. In other words, what are you trying to accomplish **by** "cutting off internet for one user"?

---

### Post by santhoshsd on 2008-10-07
the user should not be able to attach any files from the system to his mail or copy code via his mail.

so I want to disable internet access for the user.
T
his is one of the steps I am trying to do to make the files on the system 
a little more secure than it is now, so that no body can copy them, they can only read, write and execute ... but the users should not be able to copy anything.

---

### Post by nixscripter on 2008-10-07
The only way to do that is to have the e-mail server which the user sends mail through remove attachments. If you don't have control of it, then you can set up your own internal server which forwards everything to the "real" server, except attachments.

Check out **postfix**, an SMTP server which can run on Ubuntu.

Info on setup is here: [http://pccicla.blogspot.com/2007/02/ubuntu-smtp-server.html](http://pccicla.blogspot.com/2007/02/ubuntu-smtp-server.html)

And full documentation is here: [http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

Hope this helps.

---

