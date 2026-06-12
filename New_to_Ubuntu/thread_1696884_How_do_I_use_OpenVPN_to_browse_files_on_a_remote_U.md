---
title: "How do I use OpenVPN to browse files on a remote Ubuntu server?"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by ck234 on 2011-02-28
Hello.
         Apologies if this seems like the most simple question.  I am new to OpenVPN and Ubuntu.

I am hoping to browse my music collection at home from my office computer.  I wanted to set up a secure connection, but have the folders on the remote server appear to be on the same network as the office computer.  After looking at various solutions, like Firefly media server, I settled on setting up a bridged VPN connection.

I followed the instructions provided on ubuntu.com and OpenVPN.net and set up a bridged OpenVPN server.  I can set up a tunnel from a remote ubuntu (eeebuntu) laptop behind NAT to an Ubuntu (lucid) machine running OpenVPN server, also behind a NAT.

My question is - now I can set up the tunnel, how exactly do I browse resources on the remote server?  Is there a GUI for it?  Does Nautilus provide some tools to browse folders on the remote network?

Thanks for your replys in advance, and keep up the good work.

---

### Post by lmarmisa on 2011-02-28
Welcome to the forums.

Consider to use Samba to share the music folders on the remote server and to use a Samba client (Nautilus supports this feature) on the office computer. 

This link can help you:

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by ck234 on 2011-05-03
Imarmisa,
   Thanks for your reply.  I finally succeded in browsing a Samba share over the internet using OpenVPN.  The bit that was confusing me was which IP address to use to connect to the remote Samba server, and what program to use to do it.  For anyone else who is a total novice like me, this is what I did:


[LIST=1]
[*]Make sure the OpenVPN server is up and running on the remote Ubuntu machine (start it via SSH)
[*]Fire up the openVPN client on the local client machine (Windows GUI)
[*]Open up Windows Explorer and type in the IP of the remote OpenVPN server (as specified in the OpenVPN server.conf file on the server, followed by the sharename.  So in my case I typed \\10.x.x.x\sharename.
[/LIST]

---

