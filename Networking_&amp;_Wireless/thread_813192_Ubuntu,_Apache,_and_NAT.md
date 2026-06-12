---
title: "Ubuntu, Apache, and NAT"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by derdud on 2008-05-30
I have Ubuntu 8.04 running on a server with Apache2. This machine is behind a firewall. I made a DHCP reservation for it on our domain controller, so it will always pull 10.56.232.150. Then, through the firewall (which handles our NAT), I set up a NAT entry for this machine and gave it an IP of (for the sake of example) 1.2.3.4. 

From inside our network, Apache works great. The content I put on the page loads fine. This content is not accessible from outside the network, however. I'm not very familiar with Apache, but is there a change that I need to make to Apache's configuration in order for it to work both inside and outside of our network?

---

### Post by superprash2003 on 2008-05-31
dont you have to enter the same 10.x.x.x ip for the NAT-DMZ

---

### Post by derdud on 2008-05-31
I'm not sure actually. I basically followed the same procedure I've always used to open machines to the Internet so I'm not sure why it's not working right. That's why I assumed that maybe I missed something that I was supposed to set or configure on Apache or Ubuntu.

---

### Post by derdud on 2008-06-03
Any ideas?

---

### Post by rickyjones on 2008-06-03
> **derdud said:**
> Any ideas?

What kind of firewall?
What port(s) did you configure your NAT entry for?
Did you follow the exact procedure for other internet services that you host?
Is this site supposed to be public? If so, can you post the IP and see what our results are?
Can you telnet to IP:80 from outside the network?
What error message do external users receive?

Please answer the above questions as it will give us a better idea as to what the problem is. IE, connection, DNS, etc...?

Thanks,
Richard

---

