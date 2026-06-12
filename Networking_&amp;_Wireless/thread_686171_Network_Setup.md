---
title: "Network Setup"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by tbrooke on 2008-02-02
I have a a Ubuntu desktop I'm using as a server and a laptop running Ubuntu, I can not get them to see each other on a network.I can use VNC and NFS file works when I put in IP addresses. I think it is something to do with the domain names. I have been putting in the IP address to get a connection but I can not use any names and I want to do a remote login which I can't do.I have tried both static and fixed IP and roaming enabled and disabled. 

My server is caled Ubuntu and I put in Brooke as a domain name. My laptop called laptop and I put in Brooke as a domain name but it disappears if I save i and look at it. With VNC and ping Ican connect with the IP address and Ubuntu,local I can only ping the laptop with the IP address I think my problem is I can't get both computers in the same domain 

Any ideas - I have been working on this for several  days

Tom

---

### Post by metallicatony on 2008-02-03
Hi tbrooke,
  From your post i can understand that you want to avoid using IP while connecting between your computers and you prefer using HOSTNAMES of the respective computers.
If so please edit your /etc/hosts file. Insert the remote machine's IP and HOSTNAME there.
After saving it, try pinging to that remote computer with the hostname. You can find that it gets mapped to its IP correctly.

PS: From your post, i understood that you just want to refer your remote systems with a name and you dont want something like DNS setup. Pardon me, if im wrong.

Thanks!

---

