---
title: "Remote desktop"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by dmsn on 2006-10-24
Yoo
I trying to remote my linux machine from windows xp with remote desktop (terminal services) over RDP.
But i cant connect, how do i start the remote server in ubuntu linux?
Must i run vnc? I want more rdesktop over 3389.

---

### Post by dmizer on 2006-10-24
system > preferences > remote desktop.

---

### Post by dmsn on 2006-10-24
When i do that vino-server starts on port 5900.
I said i want RDP port 3389.
So i can connect with rdesktop from windows computers.

---

### Post by zek725 on 2006-11-15
How about in Xubuntu -> XP?

---

### Post by dannyboy79 on 2006-11-15
for xubuntu, install vnc-viewer I believe. then install vnc server on winbloz and that should do it. good luck

---

### Post by musicinmybrain on 2006-12-16
> **dannyboy79 said:**
> for xubuntu, install vnc-viewer I believe. then install vnc server on winbloz and that should do it. good luck

Or try something like grdesktop and use RDP.

To answer the original question, it has not historically been possible to run an RDP server on Linux. There are some projects to create such a server, but none are mature. Is there any particular reason you want to use RDP instead of VNC?

---

### Post by dermotti on 2006-12-16
You also might wanna look into running FreeNX. I find it much faster than VNC or RDP.

[http://www.nomachine.com](http://www.nomachine.com)

---

### Post by dannyboy79 on 2006-12-18
> **dermotti said:**
> You also might wanna look into running FreeNX. I find it much faster than VNC or RDP.

[http://www.nomachine.com](http://www.nomachine.com)

i take back my original post about vncviewer. I now use nxserver, nxclient, nxnode and it's awesome. it's the same website the previous poster posted. [www.nomachine.com](www.nomachine.com). i am not sure if it's free forever though, I thought I read anopther user post that he had a message displaying that he needed to install a license after his 30 days were up. I am getting close being near the 30 day mark. the reason that nxserver is so cool is because it tunnels thru ssh so everything is encrypted. it's pretty fast also!!! i have used it in windows and within xubuntu to use my ubuntu server thru my xubuntu laptop. it's awesome!!! the one thing I can't get working is have a custom passphrase key with the nxserver cause it only authenticates using a password, so because of that I have had to allow my ssh server to accept password authentification along with public/private key authentification, so what happens is if someone tries to break into my system, they don't need the key cause the second form of authentification is password but they'd have to know my username first and then figure out my 14 character password which has a combination of puncuation, numbers, and letters and according to a brute force website I read, it would take approximately 56 years to break my password and that's using a cracker that tries like 50 passwords a second I think so I am pretty certain that they can't get in and as a back up I am only allowing certain ip addresses thru iptables so I don't think any hacker's getting into my box. he he

---

