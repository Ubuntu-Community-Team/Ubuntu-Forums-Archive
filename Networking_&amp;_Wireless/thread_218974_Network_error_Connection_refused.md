---
title: "Network error: Connection refused"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by cocotu on 2006-07-19
Hi guys, I'm here at work and I was connected to a LAMP server we have downstairs using putty. I went to lunch for 1 hour and left the connection on, and when I came back from lunch the connection was timed out. Now when I try to connect again I get: "Network error: Connection refused". Why is this happening to me???!! I'm very new to this SSH thing. I did a search in google and I got this: 

"This error means that the network connection PuTTY tried to make to your server was rejected by the server. Usually this happens because the server does not provide the service which PuTTY is trying to access. 

Check that you are connecting with the correct protocol (SSH, Telnet or Rlogin), and check that the port number is correct. If that fails, consult the administrator of your server."

I checked and I'm connecting with the correct protocol (SSH) and I check the port number which is the same I was using before. I did a restart: sudo /etc/init.d/ssh restart and nothing.
Please help me guys,

Thanks

---

