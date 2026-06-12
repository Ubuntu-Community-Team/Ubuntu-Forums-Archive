---
title: "Minor Samba/Win XP roaming profile issue"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by jatos on 2007-09-16
Hi

I have setup roaming profiles on my home network using Samba. Now after a lot of fiddling, I at last actually got it to work.

However I have a little problem in that when I pop up the start menu, three comas appear after the my username at the top of the start menu. Not a major issue, but it is bugging me, so if I can I would like to get rid of three comas.

Jamie

---

### Post by kidders on 2007-09-17
Hi there,

It's been a loooong time since I dabbled in this area, but I *think* I see where the commas are coming from, at least. Try this...```
grep `id -u` /etc/passwd | cut -d: -f5
```That *should* snip out /etc/passwd's gecos field for your own account which, if we're in luck, will contain commas ... just for the sake of illustration. The comma-delimited gecos format is handled specially by certain applications (eg finger).

This account information is non-essential, and has no impact on the way computers' authentication services operate, so you can normally feel quite free to change it for purely cosmetic reasons. It does not *have* to contain multiple comma-delimited arguments, and can even be empty, if you want.

Now, exactly how Windows gets to see this value depends entirely on how your network account management works. For example, you may at one time or another have used a script to port your /etc/passwd to an LDAP database which now acts as a back end for a Samba PDC ... in which case, that's where to start looking. On the other hand, Samba may be reading the value directly out of /etc/passwd, or one of any number of other places.

With any luck, my suspicion about where the extra commas came out of is correct, and you can track down the *current* data source pretty quickly.

---

