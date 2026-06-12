---
title: "SSH Outside Network"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Frank_F on 2008-12-22
Hello,

I had this working in Feisty Fawn, but since I loaded 8.10 I am only able to ssh via Putty from inside my network...when I connect from work it simply times-out...not sure if there was some /etc/ssh files in need to change....x11 ?

Thanks

---

### Post by SlidingHorn on 2008-12-22
you can run ssh from the command line

```
ssh 12.345.678.90 -l username
```

---

### Post by Frank_F on 2008-12-22
yes...I just tried the command.

---

### Post by DGortze380 on 2008-12-22
> **Frank_F said:**
> Hello,

I had this working in Feisty Fawn, but since I loaded 8.10 I am only able to ssh via Putty from inside my network...when I connect from work it simply times-out...not sure if there was some /etc/ssh files in need to change....x11 ?

Thanks

do you have a static ip? dyndns?

are you using a router/firewall/ids/ips???

Some common things to check.. firewall rules allowing ssh, port forwarding to correct machine at border, ip address/domain

---

### Post by Frank_F on 2008-12-22
Hellor
 I am using a router( DLINK) I have the port 22 forward...i have allowed the firewall to communicate with tcp-ssh.

Is there anything in need to change in /etc/shh ?

---

### Post by Nepherte on 2008-12-22
Perhaps you still have to set /etc/hosts.allow to allow connections other than lan for the ssh daemon?

---

### Post by Frank_F on 2008-12-22
Hello

No success, I have set the hosts.allow to sshd: ALL.

Any other suggestions ?


Thanks

---

### Post by IamReck on 2008-12-22
Maybe your work place is not allowing SSH connections.

---

### Post by IamReck on 2008-12-22
What error message are you getting exactly?

---

### Post by Frank_F on 2008-12-22
Hello

No real error message...when I ping my machine (ubuntu 8.1) internally via a xp laptop, no problem (i can even ssh via Putty), however when I ping the same address from the laptop outside my network I receive a timeout.

Thanks

---

### Post by Iowan on 2008-12-22
Did the IP address or port-forwarding change?  SSH shouldn't affect **ping**.

---

### Post by DGortze380 on 2008-12-22
> **Frank_F said:**
> Hello
...however when I ping the same address from the laptop outside my network...

Thanks

Well that there's your problem...

When you ssh within your network at home, I'm sure you are using one of the following addresses:

192.168.x.x
172.16.x.x
10.x.x.x

These are private reserved addresses. They are not valid on the internet, and 90%% of your packets are getting drop at their first hop.

Go to [http://www.whatsmyip.org/](http://www.whatsmyip.org/) (or similar) and use that valid external address to ssh to your router which will forward to your reserved internal address.

NOTE: Unless you pay for a static address from your ISP, this IP will likely change at random. Use a service like dynamic dns to overcome this, or pay for a static address from your ISP. [http://www.dyndns.org/](http://www.dyndns.org/)

---

