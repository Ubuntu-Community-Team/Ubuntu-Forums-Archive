---
title: "VPN to Dynamic IP, Updating DNS?"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by yfronto on 2008-09-18
I'm not having a lot of luck searching for any information on this, so any help would be greatly appreciated. Basically, here's what I'm looking for:

I manage my own DNS entries on a server in a co-lo office, I have a Cisco ASA at home, and a few mac/windows/linux machines in the house. The NS server at the co-lo is running Redhat(CentOS) 5 and my home computer is running Ubuntu 8.04. I can bring up a VPN connection to my house's external IP just fine, and then RDP/SSH/VNC/whatever to my machines at home, but the snag is the dynamic IP my ISP gives me (changes rarely, but often enough to be annoying).

Is there a tool that will allow one of the machines at home to query its current external IP (maybe once an hour or so), and then update the DNS info on the server in the co-lo? Then I could keep the TTL real short and always bring up a VPN to my house with a NS instead of the IP?

Thanks in advance.

---

