---
title: "pptp over ssh limits once logged in"
date: 2014-09-17
forum: Networking &amp; Wireless
---

### Post by tuxulin on 2014-09-17
hi
i have an ubuntu 12.04 server. i  have setup pptp tunneling over ssh which is working fine.
but i want to give other users access to the server so they too can tunnel their web data.

is there a way to allow remote users to connect via ssh and have the terminal or putty to not
accepted user commands once the terminal is open on the user side, i just want them to only connect and tunnel.

for example is there a way to hide their terminal, make the cursor invisible or reject all prompt commands.

thanks 
TuX

---

### Post by tgalati4 on 2014-09-17
If you give each user a matching user account on the server (the username must match exactly), then you can apply the usual user limits that include limiting the path of commands and using group privileges to limit terminal activity.  Your Use Case does not have enough information to give a definite answer.  What does "tunnel their web data" mean?  Are they simply accessing internal/corporate web pages?

---

### Post by tuxulin on 2014-09-17
hi and thanks tgalati4
its a simple setup where on the client side he/she setup socks in the web browser then create a ssh connection to the server where they can continue browsing web data in some what anonymous manner like a poor mans vpn without all the overheads of open vpn.

so if i setup a folder with the remote ssh users then apply the permissions to the folder would that be sufficient enough from them mucking around with commands in the terminal?

thank you

---

