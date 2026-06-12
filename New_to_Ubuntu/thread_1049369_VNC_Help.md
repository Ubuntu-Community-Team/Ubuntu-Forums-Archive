---
title: "VNC Help"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-01-24
How do I setup VNC to connect my laptop to my desktop. My laptop is using Windows (I'll change it eventually) and my desktop runs Ubuntu. What do I have to download and install so I can remotely control either one. I also heard that are some security issues with using vnc, so what should I do to make sure that my computer isn't vulnerable? I'd also like to be able to save files I created on my laptop to my desktop. Would I need more software to do that, or can VNC do that too? 

Thanks for all your help.

---

### Post by Cypher on 2009-01-24
You can install the VNC server on your laptop and then using VNCViewer in Ubuntu you can access your laptop while on the local network. The security issues arise in that VNC transmits everything in clear-text. So any passwords you enter can be intercepted if you use it over VNC directly.

The secure way of using VNC over the Internet is through a SSH tunnel. A google search will yield countless pages dealing with this setup.

VNC is *JUST* for viewing your remote desktop from your local desktop. No files are transferred back and forth in that session. To be able to share files between your two machines, you'd use the traditional schemes of FTP, SFTP, SCP and so on..

---

### Post by Sup3r3g0 on 2009-01-24
Oh I see. What about a VPN connection?

---

### Post by Cypher on 2009-01-24
A VPN connection would also work and be secure. But know that the VNC connection might be slow because it's going over the VPN..

---

### Post by Sup3r3g0 on 2009-01-24
So what would give me the best combination of security and speed? 

I really appreciate all the help. It's one of the reasons I switched to Ubuntu, the support.

---

### Post by Cypher on 2009-01-24
A lot of people run VNC over SSH and the overhead is less than through a VPN connection and you might find it to be usably so. But anytime you leave the confines of a local network and to the Internet, you're going to take a hit in performance.

The only way to really know how much of a hit is to set things up and try it out..

---

### Post by Sup3r3g0 on 2009-01-24
> **Cypher said:**
> A lot of people run VNC over SSH and the overhead is less than through a VPN connection and you might find it to be usably so. But anytime you leave the confines of a local network and to the Internet, you're going to take a hit in performance.

The only way to really know how much of a hit is to set things up and try it out..

Thanks. Do you know where I can find a specific walkthrough for running a vnc over ssh?

---

### Post by diablo75 on 2009-01-24
> **Sup3r3g0 said:**
> Thanks. Do you know where I can find a specific walkthrough for running a vnc over ssh?

I'm looking for one myself so just tagging along here...

---

### Post by Cypher on 2009-01-24
The terms "Ubuntu VNC ssh tunnel" will yield a plethora of Google results for ya...

For starters, check these two out:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/RemoteAccess#How_to_Run_a_Windows_machine_from_Ubuntu_securely_using_VNC](http://ubuntuguide.org/wiki/Ubuntu:Feisty/RemoteAccess#How_to_Run_a_Windows_machine_from_Ubuntu_securely_using_VNC)
[https://help.ubuntu.com/community/VNC#Guide%20to%20example%20scenarios](https://help.ubuntu.com/community/VNC#Guide%20to%20example%20scenarios)

---

### Post by Sup3r3g0 on 2009-01-24
Thanks for your help

---

