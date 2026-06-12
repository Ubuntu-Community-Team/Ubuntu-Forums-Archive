---
title: "ssh from Internet not working"
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by prshah on 2008-08-20
Hello,

I've setup OpenSSH server on my desktop, and configured it with a non standard (non-22) port.

I can successfully ssh into it from the local network, with both wired and wireless clients.

However, when I try to ssh into it from the Internet, the connection times out.

I'm using the correct IP address (verified by two methods).

I'm using the correct (non-standard) port. (For nit-pickers, I've also tried various low and high port numbers, including 22).

I've NAT forwarded the correct port everytime in the router; my desktop ip address matches the router's NAT "forward to" ip address.

I've made the necessary firewall adjustments for the port using firestarter.

A ping to the (WAN) IP address of my desktop (router, actually) returns a reply. (0% loss, count of 5)

sshd is running fine.

"ssh -vvv" doesn't give anything helpful. Just "connection timed out", among other guff.

A recap: I can successfully ssh within the local network, but cannot access the box from the outside (via Internet).

a) Any suggestions?

b) How do I check if my desktop is listening at the assigned port, from the Internet? (ie, how to I check from the Internet if the specific port at the specific ip address is open/accessible?)

---

### Post by finer recliner on 2008-08-20
what computer outside the router's subnet are you using? if you are at work, they may be filtering your internet activity. can you try to ssh from a different computer (like a friend's computer)?

---

### Post by prshah on 2008-08-20
> **finer recliner said:**
> what computer outside the router's subnet are you using? if you are at work, they may be filtering your internet activity. can you try to ssh from a different computer (like a friend's computer)?

Err.. I don't understand your first question.

As for the second, I'm more likely to filter than be filtered ;) But I've tried from multiple sources (Various offices, Internet cafes, neighbors), no luck.

---

### Post by finer recliner on 2008-08-20
> **prshah said:**
> Err.. I don't understand your first question.


sorry for the poor wording. that first question actually tied to the second one. i just wanted to know if you were trying to SSH from your office and if you had tried connecting from multiple computers.

you seem to have already thought of most of the typical problems.

how about posting your config files (like sshd). maybe someone can spot an oversight.

---

### Post by cpetercarter on 2008-08-20
Sounds like a firewall problem, either the firewall on your computer, or any firewall built in to your modem/router.

---

### Post by Joeb454 on 2008-08-20
Have you forwarded your port from the router to your ssh-server pc?

---

