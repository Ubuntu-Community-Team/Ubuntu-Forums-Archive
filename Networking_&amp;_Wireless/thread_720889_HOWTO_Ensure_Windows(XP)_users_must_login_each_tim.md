---
title: "HOWTO: Ensure Windows(XP) users must login each time they start up SAMBA Shares"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by KennedyM on 2008-03-10
I'll gladly update the following based on feedback, etc. I've seen many posts here seeking this facility, so I hope this helps...

_Scenario_:
[LIST]
[*]Windows-XP-Pro(SP2) users, connecting to Samba shares (in my case, running on Dapper 6.06.2 LTS). I wanted to support multiple Samba users per PC, but did not need any of the Samba-user info in the PCs - just a single low-priority generic user "Nobody" on the PCs (and, obviously, a secure Admin logon option for normal PC maintenance). In my case, no "Guest" nor unauthenticated access is allowed to the Samba shares.


[*]All users would just sign-in to the PC as "Nobody". Or maybe "Guest"? Then, when any user accesses any of the Samba shares (that are authorised for that specific user), she must submit her full Linux Username/Password.


[*]When the user logs out of the PC, all Samba shares must also be disconnected automatically, so that the next Samba user must supply his Name/PW.
[/LIST]

_Normal operation_:
Normally, XP does NOT "lose" the SMB shares, despite logging off, re-booting, etc. Eg: if User-A logs in for the first time, she must submit her Samba Name/PW. If User-B then logs in (for the first time), she's asked for her Name/PW. Then, User-A logs in later; her Name/PW is cached by XP, and she's not asked for her Name/PW.

Understandably, this caching of the user credentials is to facilitate one or more defined XP users, who do not want the hassle of frequently submitting their SMB Username/PW. This seems to be implemented in Win-XP by retaining folders and files named “credentials” - eg:
[INDENT]\Documents and Settings\<Username>\Application Data\Microsoft\Credentials\...

\Documents and Settings\<Username>\Local Settings\Application Data\Microsoft\Credentials\...[/INDENT]
Perhaps just deleting these would trigger the login dialogs, but that might be naughty, and I've not tried it!

_Solution?_:
To meet the above needs, the caching of the Name/PW data must be disabled. Here's what I've done  on the XP systems :?: [Be careful with RegEdits ;) ]

On XP, click on Start, Run, Type "Control Userpasswords2" (without the quotes!), [Enter]:
[LIST=1]
[*]Advanced tab, Manage Passwords.
[*]Remove any Locations/IPs/Servers already logged.
[/LIST]

Run the Registry Editor [regedit or regedt32], or build the following Reg update in a .Reg file:
[LIST=1]
[*]HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\
[*]If a valuename of CachedLogonsCount (case does not matter) does not exist, create it (type REG_SZ).
[*]Set that value to 0.
[*]Close Regedit, and re-boot.
[/LIST]

_More good info (the end URL refers to VISTA)_:
[INDENT][http://support.microsoft.com/kb/913485/en-us]("http://support.microsoft.com/kb/913485/en-us")
[http://support.microsoft.com/kb/281660/EN-US/]("http://support.microsoft.com/kb/281660/EN-US/")
[http://support.microsoft.com/kb/172931/en-us]("http://support.microsoft.com/kb/172931/en-us")
[http://www.vistax64.com/tutorials/76354-cachedlogonscount.html]("http://www.vistax64.com/tutorials/76354-cachedlogonscount.html")[/INDENT]

HTH.
  - Mike

---

### Post by Eiríkr on 2008-03-24
I should have thanked you earlier for putting in the grunt work.  Good on you, mate.  :)  Or hey, I guess I should say maith thú!

Slán,

Eiríkr

---

### Post by KennedyM on 2008-03-25
> I should have thanked you earlier for putting in the grunt work.  Good on you, mate.  :)

No probs - and thank YOU also.

[Hope the suggestions work "as intended" :-? ]

> Or hey, I guess I should say maith thú!

Slán,

Tá Fáilte Romhat!

  - M.

---

