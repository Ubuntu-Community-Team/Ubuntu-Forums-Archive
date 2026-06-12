---
title: "Make user-specific hosts file"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by gkaragoulis on 2008-08-16
Hi everyone, here's my problem:

I have my office environment setup almost entirely in ubuntu, and I setup a 'homes-server' so that I have a centralized home directory so wherever I login I have the same settings and such.  The only thing is each computer on the domain has its own /etc/hosts file, so changes to those files are not persistent across all domain computers that I login to.  Ideally I would like to add a host to that file and be able to use that host-name-alias on all my domain computers.  So my question is this:

Is there a way to setup a hosts file that resides in my /home directory so that I can take it with me wherever my domain account goes?  I am guessing it has to do with symbolic links, but I can't figure out how to link /etc/hosts to my /home/hosts file without creating a definite dependency on my home directory being there, in-case the network is down. Any ideas?

---

### Post by bab1 on 2008-08-16
I would use a DNS server and leave the /etc/hosts files alone.  My DNS is handled by my router. You might be able to use your "homes-server" for DNS. What exactly are you using for homes?  My /etc/hosts files only have the localhost and the hostname of the computer in them.

---

### Post by gkaragoulis on 2008-08-18
The problem with relying a DNS server is what happens if it goes down and I need to resolve IP addresses.  I like to have the big servers written in the hosts file so that doesn't happen.  Currently my DNS server is a virtual machine, so while I'm restarting the host machine I have no name resolution.

---

### Post by jimv on 2008-08-18
If you don't want to use DNS because your server goes down, you need to rethink the way you have things set up.  DNS is the way to go.  If you're worried about your DNS server going down, create a secondary DNS server on another machine...there's little overhead required, so there's no reason not to.

Besides, if your hosts file resides on another machine, how do you propose to connect to that machine when DNS is down without adding that machine to all the hosts files on all your other machines?

---

### Post by bab1 on 2008-08-18
I'm in agreement with jimv.  

The reliability of a DNS server is about the same as expecting an /etc/hosts file to load properly every time you boot up.   Both are about 99.999% reliable.  

I wouldn't worry about failure, that is guaranteed to happen to your network someday when you least expect it.  More to the point is functionality and ease of administration.

One last point, unless you have an entire domain that you are maintaining virtually, why would you have a DNS server running virtually?  In other words,  why do you have a critical server that can't be seen by the network 100% of the time?

---

### Post by gkaragoulis on 2008-08-19
Ya I think a secondary DNS server would be the way to go.  Is it pretty easy to set one up in Ubuntu?  Is there software I should know about?

---

