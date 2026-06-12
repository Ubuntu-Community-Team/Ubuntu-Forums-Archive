---
title: "VPN or Tunneling Help"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by grogger13 on 2008-02-23
I am not sure if vpn if what i want so im going to just  describe the solution im looking for.

I live in a dorm that blocks alot of networking stuff.  Torrents, Frostwire and even any irc chatting.  I have managed to set up an ssh tunnel with my computer at my house.  I can download things to that computer at home and then i have used sftp to transfer them to my computer but it takes twice the time becuase i have to download it twice.  Also my home computer is really old(runs ubuntu) and it only has 9GB and with my sisters music files and system files i only have about free on it.

I want some type of way to simly tunnel to my home network and download directly to my laptop in the dorm.

I think that vpn could do this but i'm not exactly sure.

---

### Post by hyperair on 2008-02-23
You could set up a proxy server at home, and then use SSH to tunnel the proxy data over. I'm not sure how to go about that though.

EDIT: Take a look at this: [http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

This article shows you how to set up a SOCKS proxy using SSH. You can then use that proxy for everything else. =)

---

### Post by grogger13 on 2008-02-23
i think my school still blocks me from using torrent programs.  I have configured the socks proxy and am connecting through mozilla with it but when i have azureus running with the socks proxy configured i get these messages in the terminal with the ssh tunneling.

[CODE] :~$ channel 5: open failed: administratively prohibited: open failed
channel 3: open failed: connect failed: Connection timed out
channel 3: open failed: connect failed: Connection timed out

:~$ channel 4: open failed: connect failed: Connection timed out [CODE]
 could someone confirm this.

---

### Post by hyperair on 2008-02-24
What port did you use?

---

### Post by grogger13 on 2008-02-24
i used ssh -D 7777 xxxxxxxxxxxx , so port 7777
I already had that port open on my router becuase i tried a tutorial for this.

I can't open ports on my router through ssh so i had to talk someone through it on the phone so i can't just open which ever port i want instantly.

I know my school blocks ports for torrenting but im not sure if there are some ports i can use.  Is there a way to figure out what ports they do and don't block.

---

### Post by grogger13 on 2008-02-24
Edit- Actually i just realized with my socks proxy through mozilla i can just access the router, so i can use what ever port i need.

---

### Post by hyperair on 2008-02-24
Just something worth noting: Everything is tunnelled through port 22. That's the only port you need to keep open on your router. For tunneling purposes. I"m not sure how torrenting via tunneling works though.

---

