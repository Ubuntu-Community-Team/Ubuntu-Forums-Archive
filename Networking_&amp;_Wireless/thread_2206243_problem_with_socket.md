---
title: "problem with socket"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by chuchi on 2014-02-18
Hi everyone!
 

 I am working with EC2 Amazon and I have a socket server in PHP listening on port 5006.
 

 The problem is that socket clients can not connect, the error message is:
 

 ```

Could not connect: [51] Network is unreachable

```

 I have open the port in the EC2 management console.  
 

 Also, the IP that the server connects to is the internal IP &#8220;172.31.5.211&#8221;, not the public IP.  
 

 Could you help me please??
 

 Thank you very much!!

---

### Post by chuchi on 2014-02-18
I solved the problem disabling the firewall with this command
 

 ```

 /etc/init.d/iptables stop
 
```
 

 Is it good to disable the Firewall??
 

 Thank you very much

---

### Post by ian-weisser on 2014-02-18
Since your firewall faces the internet, then disabling it may be rather unwise.
You should instead tell your firewall to allow inbound connections on port 5006.

I think you should be aware of exactly what services are listening on which ports on any internet-facing machine. This will help you keep your firewall rules tidy, and will help you trim unused services. I use the command **sudo netstat -tulpn** for that purpose.

---

