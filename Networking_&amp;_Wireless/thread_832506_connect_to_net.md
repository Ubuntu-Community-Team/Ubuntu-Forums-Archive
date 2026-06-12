---
title: "connect to net"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by Montalo on 2008-06-17
i am using a VPC to run ubuntu


how to i connect the vpc to the intrent, using my current connection

---

### Post by Montalo on 2008-06-18
any one??

---

### Post by uidb4056 on 2008-06-18
What you mean by 'VPC' ?, if it's virtual machine what application are you using to run it?

---

### Post by Montalo on 2008-06-18
> **uidb4056 said:**
> What you mean by 'VPC' ?, if it's virtual machine what application are you using to run it?
i am using microsofts virtual pc software to run

---

### Post by uidb4056 on 2008-06-18
I've not used it but you will have to configure the virtual machine to use his virtual network card with NAT or Bridging to the network of your host PC. Can you post the result of running in Ubuntu Terminal the command *ifconfig*  also open a DOS window in your host PC and post the result of *ipconfig /all* , this info can help to guide you a bit more.

---

