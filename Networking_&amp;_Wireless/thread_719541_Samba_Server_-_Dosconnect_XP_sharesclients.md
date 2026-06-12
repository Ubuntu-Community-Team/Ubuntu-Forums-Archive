---
title: "Samba Server - Dosconnect XP shares/clients"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by KennedyM on 2008-03-09
Hi,

I'm stuck on this one - after much browsing here, scanning about 10 books, etc.

I have an XP-Pro/SP2 client, connected to some Samba shares on a Dapper 6.06.2 LTS server. No probs there. The Samba shares require user PWs.

On the first connect from an XP client, the visible shares appeared, and, when I tried to connect on the UNC shares or as a mapped drive, I got the Username/PW dialog. No problems.

But, how do I DELETE/DISCONNECT these shares, so that I can re-enter the Username/PW pair again - perhaps as a different Samba user?

I'm using only a single (generic) user-ID to log into the (generic) client PC - but I want many users to be able to go to the PC, connect to the Samba shares (with their individual username/pw), and disconnect/logoff when they're finished, so that the next PC user can log into their shares...

I've tried rebooting both systems, registry scans, dozens of "net use" commands, etc, and cannot force the XP system to demand the login-dialog for the Samba shares. "smbstatus" on the server shows the user and shares as active, no matter what I do on the client. I'm assuming the login-data is held somewhere in the client PC, and that it can be purged. If the login criteria are held in the Samba server (perhaps assigned to the PC-MachineName instead of the Samba user), then it would seem quite problematic for an XP user to disconnect their shares.

Thank you for any suggestions or pointers...
  - Mike

---

### Post by Eiríkr on 2008-03-09
The Windows assumption is that one Windows user login is used by one user.  Ergo, any shares that user connects to are saved, with authentication data, for convenience.  This happes on the Windows side, and is not anything that Samba can do anything about, so far as I understand it.  I know of no easy way to force the Samba authentication prompt to reappear, as Windows provides the initially provided authentication data behind the scenes and thereby prevents the prompt from showing up (provided of course that said data is correct).  You're probably much better off creating separate XP logins for each of your Samba users, rather than hunting down the obscure ways in which Windows tries to second-guess the user.  

Cheers,

Eiríkr

---

### Post by KennedyM on 2008-03-09
Eirikr,

Many thanks. My experience certainly matches your comments. [And my apologies for the "dOsconnect" typo in the subject!].

I need a single Windows user-name, for convenience. The client has some hundreds of PCs (and users), and wants to deploy just "standard" PCs, without having to update them for every user-name update.

I'll search a bit more for the caches under XP - maybe they're simple, and maybe I'll get lucky... [Yeah, Right :???:].

Maybe one option is to have 2 x generic users in all PCs, "NULL" (with no shares), and "Data" (with the "current user's" shares). Maybe the following approach will suffice, but it has not been checked...:
  - We assume a PC currently has no Shares cached.
  - User-A signs on to the PC as DATA, connects to Samba, seeks her own shares, and fills in User-A/PW when the Samba dialog appears.
  - Those shares stay linked/cached indefinitely, across Boots, etc, if User-A does nothing.
  - When User-A is not certain that she'll be the next user of that PC, she logs out, and logs in as NULL, and logs out. Hopefully, all those User-A cached shares disappear. Alternatively, if I can find those caches, she could just run a script to purge the caches.

I'll keep digging, and I'll report back if I have anything useful...

Thank you again.
  - Mike

---

### Post by Eiríkr on 2008-03-09
With "just 'standard' PCs", I wonder if the client really needs Windows?  This is totally a shot in the dark, but I rather suspect they don't fully understand what they want / need...  I'm in the midst of just such an uncomfortable situation with a translation client of mine.  :-|  Anyway, good luck helping them get sorted out.  :D

Cheers,

Eiríkr

---

### Post by KennedyM on 2008-03-09
First, those steps I listed in the previous post do NOT work - XP caches the shares for DATA/User-A, across logins by Null. When DATA logs in later (by real User-A or real User-B), the old User-A shares are still available. :(

> With "just 'standard' PCs", I wonder if the client really needs Windows? This is totally a shot in the dark, but I rather suspect they don't fully understand what they want / need...

The client PCs are already in use. The objective is to consolidate existing (and new) apps into new servers.

I'll do some digging!!

  - Mike

---

### Post by KennedyM on 2008-03-10
Hmmmm.... I think I have this facility operational - I'll post a HOWTO on a separate thread...

  - Mike

---

### Post by Eiríkr on 2008-03-10
Definitely let us know what you find; I poked around a bit in the registry, but didn't change anything as I'm mid-project and can't afford the time to much about too much.  :)

Cheers,

Eiríkr

---

