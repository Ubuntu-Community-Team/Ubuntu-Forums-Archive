---
title: "Unable to connect to NAS"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by bjsisko on 2011-01-06
Hello,
I have installed Ubuntu 10.10 and experience the following problem situation: I have two different NAS systems on my local network. I can connect to system A without problems from my Ubuntu machine, however connecting to NAS B fails consistently.

What am I doing? I use Nautilus File-Connect to server and enter
service: Windows share
server: hostname of NAS
share: name of share
all other fields kept blank
and click "connect"

I receive an additional dialogue asking for username, domain and password which I am providing.

In case of NAS A, the connect / mount works and I see the files on the share within Nautilus

In case of NAS B, I get the dialogue for username, domain and password again and again, but no specific error message at all.

I verified that I am using the correct username, domain, password (I am able to connect to the NAS from a windows machine using those credentials). 

One difference between the two NAS systems is that NAS A is supporting SMB2 while NAS B is not supporting SMB2 but just version 1.

So I have two questions:
1) How can I see what really is failing? Is there a log (where)? Can I change log / trace levels ...?
2) Can I configure Ubuntu to just use SMB version 1 to test whether thi sis the problem? How?

---

