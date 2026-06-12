---
title: "Can't access windows workgroup shares:  samba authentication."
date: 2016-05-18
forum: Networking &amp; Wireless
---

### Post by b647-11d7-aa56 on 2016-05-18
I'm having no luck whatever trying to set up access to a shared printer on a Windows computer on my home network.

*  Windows 7 computer on workgroup (no domain) named WORKGROUP.
   Windows computer does not have a password set up for the user account, boots directly to the desktop.
   Printer is shared to everyone.
   Windows firewall is turned **off.**
   In control panel, "password protected sharing" is turned [B]off.
   [/B]Other windows computers on the home network can access printer and other shares just fine.

*  Ubuntu computer has 14.04 LTS
   Samba is configured to workgroup named WORKGROUP.

When I try to add New Printer, I choose "Windows Printer via SAMBA" and click Browse.
The SMB Browser shows me the workgroup and the computer with the shared printer.
When I try to expand the computer name, I get a login prompt, "You must log in to access <COMPUTERNAME>"
No matter ***what*** I enter, authentication fails.

There is no password for access, so I leave that entry blank.
The Domain field is filled in as "WORKGROUP" by default.  I've tried leaving it that way, making it blank, or entering the computer name there.
I've tried putting the username in the Username box and the computer name in the Domain box.  I've tried leaving the Domain box blank and entering computername\user or computername/user in the Username box.
I've tried entering the computer name in all caps (the way SMB Browser shows it) and entering it as case sensitive.  (The computer name in the Windows control panel is mixed case).
I can't think of any combination I haven't tried.

There was a similar thread here a while ago ([http://ubuntuforums.org/showthread.php?t=2171712](http://ubuntuforums.org/showthread.php?t=2171712)) which was SOLVED: by turning off "password protected sharing" in the Windows control panel, but that's already off in my case.

---

### Post by b647-11d7-aa56 on 2016-05-18
P.S.
Samba version 4.3.9-Ubuntu

---

