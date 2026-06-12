---
title: "Quick Question: Printer sharing"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by peddy on 2007-08-16
Hi everyone, I am new to Ubuntu so bear with me :P

I am having a slight problem with printer sharing. I want to connect an XP box to a printer attatched to my Ubuntu machine. I have followed the instructions here, [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
and it all works fine
UNTIL my silly XP machine asks for a username and password. I have tried using the normal login for me (obviously), but it doesn't work. It just says 'you do not have access to the printer, please try a different user name and password'. PLEASE help me, any help would be appreciated.

Thanks, 

Peddy

---

### Post by peddy on 2007-08-16
Never mind, I have fixed this by adding the XP boxes' private IP to the cupsd.conf files' list of allowed addresses. It pays to think

Thanks 
Peddy

---

