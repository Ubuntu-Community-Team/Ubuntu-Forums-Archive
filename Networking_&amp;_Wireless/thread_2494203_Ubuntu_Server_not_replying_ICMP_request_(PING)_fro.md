---
title: "Ubuntu Server not replying ICMP request (PING) from a particular networking segment"
date: 2024-01-08
forum: Networking &amp; Wireless
---

### Post by loloyoroot on 2024-01-08
[COLOR=#0C0D0E][FONT=-apple-system]Dear community,

I am having issue with a server that is not giving any reply back to ICMP package from a particular network,[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I can receive reply back if I ping from 192.168.42.0/24 networks[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293289&stc=1[/IMG][/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]But If I ping from 192.168.241.0/networks I cant receive any reply. 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293288&stc=1[/IMG][/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Thank you in advance for any advice,[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Jose G Diaz[/FONT][/COLOR]

[LIST]
[*]IP tables is disable
[*]It was working good but it seems it works stop working after a server restart
[*]We had restarted the server several times but no luck
[*]Ubuntu Version 22.04.1 LTS
[/LIST]

---

### Post by loloyoroot on 2024-01-08
[FONT=var(--theme-post-body-font-family]I just add a manual static route: 
sudo ip route add 192.168.241.0/24 via 192.168.42.185 

and it seems to be working now, but not sure why this happened and lost this route and also the default route is the 192.168.42.185 why is only working after I add that static rout.[/FONT]

---

### Post by SeijiSensei on 2024-01-08
Likely a routing problem. Is there a router between the two networks? Is it the gateway for the other network? 

Usually this problem happens when the ping packets arrive at their destination, but it has no route back to the originating host.

---

### Post by QIII on 2024-01-08
Moved to Networking & Wireless from Ubuntu, Linux and OS Chat.

The tagline for that chat sub-forum is > Hello, this sub-forum is for chat, not support &#8211; hence the name. If you need technical help, please post in an appropriate support sub-forum. 

Chat.  Not support.  Yours was a support request.

---

