---
title: "Remote Login with Directory"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by TorchlightJay on 2008-04-12
Hello,

So let's say that I have a server running some kind of directory (LDAP, Active Directory, eDirectory, etc.) and everyone has an account on the server. Normally on a network you can log into the server and access your user account via your client computer. Now this works when you are on the network .

Let's say you were at a hotel and still wanted to access you account on LDAP or Active Directory or whatever. Normally people say to use VPN or PPTP but I want to actually have that same level access that you would have if you were on the actual network. Any ideas on how to pull this off?

I am looking for both Linux AND Windows solutions. Thanks in advance.

---

### Post by ginge6000 on 2008-04-12
Would you be using a laptop?  If so you can set it up so that it stores the user data locally (see this [https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)) and once logged in, VPN into the network to access your files

---

### Post by TorchlightJay on 2008-04-12
Ya, I am using a notebook. I understand that once logged in locally, I can VPN to my network but I would rather be able to log into the network in the first place rather than login to my local machine then VPN/PPTP. 

I want to have not just myself but my employees logging into the network from company notebooks. I'd feel better if they were 100% logged in when they connect to my server and the directory with accounts and not just be connected to a VPN. Is this possible?Thanks.

---

### Post by koenn on 2008-04-12
from Windows (on the laptop) you can do this by checking "use dialup" on the log-in dialog box. This will prompt for  "which dial-up connection do you want to use ?" and you can select your pptp connection. Obviously, you need to have a pptp connection configured in advance. The result is a domain log-on as if you were on the LAN. 

I'm not to sure about how you could handle this on Linux. There may be something similar to the Wondows solution, or you'd have to look into ways to set up tunnels (eg openvpn) before a user is logged on. Openvpn is mainly abouit network / rouring, and certificates, so I suppose it's possible, but I don't know of any implementations.

---

### Post by ginge6000 on 2008-04-13
Could you not make your LDAP server available from the internet (forward the relevant port on your router) and then set the VPN to connect automatically at logon?

---

### Post by TorchlightJay on 2008-04-14
Cool, thanks everyone. One quick question, what if you are on a wireless device? How do you auto-dial-up at login if you are using wireless whether it be Windows or Linux?

---

