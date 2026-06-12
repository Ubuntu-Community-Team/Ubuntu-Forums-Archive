---
title: "Does a Corkscrew guide exist"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by AnimalMother on 2006-11-26
Is there a definitive corkscrew guide out there?  The reason I ask is I have been unsuccessful using it. I have read the man page and the corkscrew home page (now blocked by company firewall/proxy). I have tunneled on http before to get to my home desktop through a Microsoft proxy using HttpTunnel4VNC [http://www.online-marketwatch.com/HttpTunnel4vnc/](http://www.online-marketwatch.com/HttpTunnel4vnc/).  This worked very well, but I really just want to ssh a terminal to my home computer.  The corkscrew home page says that it probably will not work through a Microsoft proxy, but since it is http that corkscrew is tunneling with I figured that NTLMAPS [http://ntlmaps.sourceforge.net/](http://ntlmaps.sourceforge.net/) might be able to do the NTLM authentication for corkscrew. 

Now if there is somebody who has actually used corkscrew (or is willing to try), could you please post what your “Proxycommand” entry (without security info, just substitute word or numbers that make sense) is in your ssh_config file, and what you typed on the ssh command line entry to get it to work?  

The way I have been doing it is for my Proxycommand entry:
```

Proxycommand corkscrew Proxy.ToBe.Tunneled  ProxyPort   h% p%

```

On the command line:
```

ssh  AnimalMother@Home.Computer.IPaddress

```
Now this is all with out trying to use NTLMAPS to authenticate yet.  I just want to know if the entries about look right for how to use corkscrew.

If I can make sure I have that part right I will try and authenticate with NTLMAPS after words.

Thanks to all who answer call!

---

