---
title: "Remote connect from Macbook Pro to Ubuntu?"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by bgreenaway on 2008-05-20
I used to connect remotely from my Apple Macbook Pro Mac OS X 10.4 Tiger at home to my office desktop running Windows XP by using the VPN connection. Worked great. I have now migrated my office desktop from XP to Ubuntu 7.10 Gutsy. The VPN connection from home will now not connect.

What alternative can I use to connect to my Ubuntu office desktop and how? VNC? SSH? Any help gratefully received.

---

### Post by wadelewis4 on 2008-05-20
This is a completely non-technical way to do it:

Get a free account & install LogMeIn for Mac [HERE]("https://secure.logmein.com/products/free/mac/Default.asp?lang=en").

After you install that on your mac, you can remotely control it through Firefox easily.

---

### Post by wadelewis4 on 2008-05-20
Actually, disregard that last post - I misread which OS you were trying to control. Just use VNCviewer (TIGHT VNC).

---

### Post by anystupidname on 2008-05-20
SSH and VNC would be fine.

-Make sure port 22 is forwarded to office box on routers at work
-On the mac do something like "ssh bgreen@workwanip -D 1234"
-Set VNC client to use "localhost:1234" as socks server
-Then tell VNC client to connect to localhost

should work...

You could easily substitute ssh with VPN if work has a router that mac can vpn to. Otherwise, you're looking at (in my opinion) a more difficult freeswan vpn setup.

P.S. I forgot that hamachi now has *nix and mac clients, you should check into that.

---

### Post by bgreenaway on 2008-05-22
> **anystupidname said:**
> SSH and VNC would be fine.

-Make sure port 22 is forwarded to office box on routers at work
-On the mac do something like "ssh bgreen@workwanip -D 1234"
-Set VNC client to use "localhost:1234" as socks server
-Then tell VNC client to connect to localhost

should work...

You could easily substitute ssh with VPN if work has a router that mac can vpn to. Otherwise, you're looking at (in my opinion) a more difficult freeswan vpn setup.

P.S. I forgot that hamachi now has *nix and mac clients, you should check into that.

Thanks for the info and some follow-up questions:

I use ISA Server 2004 as the firewall on my Windows 2003 server. Should I open port 22 in the ISA config and are there any other ports as well? Would the *workwanip* be the external IP address or the internal IP address (192.xxx.xxx.xxx) of the workstation I am trying to connect to??

---

