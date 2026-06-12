---
title: "[SOLVED] USB dialup POP3 IMAP"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by peterroots on 2007-11-24
Hi can anyone help tell me where to look on my machine for possible solutions to my problem?
I run Kubuntu 7.04
I have a home dialup connection via a usb Huawei dial up wirless terminal (like everyone else kppp does not work but wvdial does)
I can surf the internet!
At work I can connect via ethernet or wireless to the network and get internet where i can surf and collect my mail from google using either pop3 or disconnected IMAP in kmail
What I would really like to do is collect my mail at home!  unfortunately kmail jsut tells me 'transmission compete no new messages'.
I can send my mail though, using smtp both at home and work with kmail.
If I grit my teeth and use Windows with outlook express I can see my mail with IMAP (not tried with POP3) using the dial up home connection so it would not seem to be TTCL (my ISP) so I assume the problem is somewhere in my dial up system on my computer.
The problem is I have no idea where to start looking for clues as to the problem
HELP

---

### Post by peterroots on 2007-11-24
Would you believe it?!
Last week I discovered that KnetworkManager screws up ethernet port aliases so 40 mins after posting the above question I thought 'I wonder what happens if I shut down KnetworkManager?'
I get hundreds of emails, that's what!!
so
Now my question no is -
A) why include KPPP in kubuntu when it does not work and just raises false hopes?
B) why include a network manager that messes up network connections?

My second question is - how do I flag this as SOLVED?
Thanks
Just found out how to mark as solved - I had never looked at the thread tools before!

---

### Post by frogface on 2008-02-18
That's fantastic! Your fix has worked for me!

---

### Post by Bukunut on 2008-04-21
Peterroots

I was searching for a thread as I was having the same problem with using the USB Option Icon 225 modem, I couldn't fathom out why my mail accounts were not being downloaded yet local mail was.

Wonderful! Stop Knetworkmanager and yes, email starts downloading as it should!

Best wishes - Bukunut.

PS> I have filed a bug with launchpad on this matter. [https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/220248](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/220248)

---

### Post by peterroots on 2008-06-27
Rather a long way down the line and now on kubuntu Hardy but I have now got a different usb modem working with knetworkmanager and fixed the mail download problem slightly more elegantly

[http://ubuntuforums.org/showthread.php?p=5275078#post5275078](http://ubuntuforums.org/showthread.php?p=5275078#post5275078)

---

