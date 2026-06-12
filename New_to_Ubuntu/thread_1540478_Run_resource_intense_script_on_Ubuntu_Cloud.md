---
title: "Run resource intense script on Ubuntu Cloud?"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by harleyk on 2010-07-27
I have a bioinformatics script that would take 1 week to run on my laptop. I'd like to ssh into a big server, upload my files and script, and have the server run my script. Is this something I could do with Ubuntu Cloud? I've read a lot about Amazon EC2 service, but I think it may be more than I need.

Suggestions?

Thank you.

---

### Post by marshmallow1304 on 2010-07-27
AFAIK, there is no "Ubuntu Cloud" per se.  The term is used to refer to a way of setting up a networked cloud using Ubuntu machines.  EC2 might be exactly what you need.  It looks like you can get a high-CPU instance for $0.17/hr or even lower if you use the Spot Instances.

---

