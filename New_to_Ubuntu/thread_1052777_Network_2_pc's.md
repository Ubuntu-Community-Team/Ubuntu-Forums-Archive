---
title: "Network 2 pc's"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by mltom on 2009-01-28
Pc 1 is XP! Pc 2 I changed over to Xubuntu 8.4.. Before change PC 1 could use Pc 2's printer going thru a dsl modem hardwire hookup.
Now PC 1 (win explorer) can sometimes see PC1(Xubuntu) but cannot access PC 2's hardware. The one time I did see PC 2, a message ask me to enter a username & password; which to my knowledge I did not assign any.

I have tried to manulate Xubuntu's system screens a little but to no avail.
Does anyone have a kind of step by step procedure?

tks
tom

---

### Post by affl1cted on 2009-01-28
Please try to read through your post before you post it, it was hard to understand.

Anyhow, from what I understand, you had the problem I had, XP could see Ubuntu, but Ubuntu couldn't see XP. Well that isnt the case, both can see each other, but technically, Ubuntu isnt showing it.

Requires: smbclient (from the Package Manager)

1. Connect and log into both PC's.
2. Setup a Windows Share (on your XP) of any Folder, checking that your viewed as a 'Private' Network.
3. On your Ubuntu using Firefox, type your DSL config address (in my case, 10.1.1.1) and fill in the username & password (if you did not set one yourself, try admin:admin, or reference your dsl manual.
4. Once in, go to the Advanced Tab, then Lan Clients, and it will show Ubuntu & XP PC's (in my case 10.1.1.3 & 10.1.1.4 respectively).
5. Open a new tab in Firefox (from Ubuntu), and type into the address bar: 'smb://10.1.1.4'.

This will open a ftp style file browser, in which you can download the files you want. It is also notable that while using this method, you cannot have any other download active in Firefox, or start any download, as it interfers in the pc-pc download.

This is just a workaround I have to use. In my case, I have made my Lan Clients Interal IP's Static instead of Dynamic, so I can make a Firefox link to 'smb://10.1.1.4'.

Hope this helps

---

