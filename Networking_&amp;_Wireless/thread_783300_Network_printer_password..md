---
title: "Network printer password."
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by Slatts on 2008-05-05
Why would a printer on a network need a password only from Ubuntu but not a windows wireless connected PC?

The windows WPA wired/wireless network works normaly and prints OK without passwords.

Problem:
8.04, Networking with Smb4k (0.9.3). (Couldn't get Samba to work)
Windows network Router 192.168.2.1. Printer connected to 192.168.2.2. machine.
Ubuntu 192.168.2.4

Ubuntu connects to network via either wire or wireless and browses web etc OK.
Smb4k GUI shows all shared folders and three shared printers, the main HP one (and a two PDF ones as trial).

All shared folders are accessable without passwords. 
All three printers when asked to print ask for username and password. 
No printer passwords are set up in windows.

Setting a Smb4k User/password makes no difference.
All PC/network/router user/passwords have been tried.
All network/Ubuntu/PC/Smb4k/router user/passwords set to same words.
Also tried "user", "guest". (as per CIFS manual)
None of which worked.

Any thoughts?

TIA
Slatts

---

### Post by Kevbo on 2008-05-11
Hi, Slatts, you have described exactly the problem I am having.  Printer is detected, and verified from Ubuntu, but then asks for a password when there are no password accounts on the XP machine.

Anyone have any ideas?  As always, any help is appreciated.

TIA
Kevbo

---

### Post by Kevbo on 2008-05-11
Hi, Slatts, hope this helps.

On another thread, I found this, <gksudo system-config-printer> enter it in a terminal.

Somehow it managed to get passed the password requirement and logs in as guest on XP.

When it finished configuring, I was able to access my printer (hpDeskjet 3520) from Ubuntu through the XP machine but was unable to print.  It would lock up.  Next, go to Control Panel in XP > rightClick printer > selectProperties > on Ports tab uncheck "Enable bidirectional support".

Everything works!  I am happy guy.

Swimming in Ubuntu.
Kevbo

---

