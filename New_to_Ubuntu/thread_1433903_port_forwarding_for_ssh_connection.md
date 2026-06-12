---
title: "port forwarding for ssh connection"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by gottijr on 2010-03-19
The home network is connected trough a switch SmartAX MT882

  I want to install a home server ubuntu there.

  I'm not sure how to set this switch port forwarding rules for connecting through ssh(in my linksys router is diff much more easy and i can put ssh protocol)

  this smartax MT882 doesn't have protoc ssh (options for protocol : TCP, UDP, ICMP, ALL

  please advice

 P.S. not sure if relevant, internet connection is adsl, somewhere in europe, 2mb

---

### Post by mikewhatever on 2010-03-21
Just fill in the fields. The port number for ssh is 22 TCP by default, enter another one if you changed it.

---

### Post by gottijr on 2010-03-23
it doesn't work

  i get some errors.

---

### Post by bodhi.zazen on 2010-03-23
> **gottijr said:**
> it doesn't work

  i get some errors.

What errors ?

How did you set up port forwarding ?

---

### Post by gottijr on 2010-03-23
I managed to fix it

  i was supposed to set it from : BASIC -> NAS -> Virtual Server

  the filter stuff i guess is something else.

  but thanks for your reply.

---

