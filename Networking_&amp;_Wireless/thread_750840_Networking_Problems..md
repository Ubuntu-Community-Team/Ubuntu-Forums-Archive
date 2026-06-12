---
title: "Networking Problems."
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by Keith F on 2008-04-09
Ok thank you for taking the time to read this. 

Ok I had my Linux  computer wirelessly connected to a router, which was then hard wired to a windows computer. Everything worked great. 

Now I've moved, I got a new Dlink Xtreame N router, and i can access the internet but I can't share files with the windows computers.

I've shared one hard drive, and set it to read only. Everything looks good. Still I can't see the windows computers and they can't see me. 

- I should mention this isn't a wireless thing, we're all hard wired. - 

I've gone through all the settings on my router, and there's nuthing in there indicating any problem. 

I have the i.p. of the router, the i.p.s of all the users and there respective computer names and mac addresses.

I'm fairly green at this, so please break this down so it's easy for me follow.

- I'll list my specs so that it may aid in solving the issue.
My computer, Linux 7.0 I think, Mint, 2.4ghz cpu, 1gbram, using onboard gblan card.
Computer B, Windows xp, It's a tower, thats all i know it's not mine.
Computer C, Windows Vista, Also  Tower and also not mine so specs aren't known.

The vista computer sees the router but  doesn't see my shared folders, under it's network places it just has the router.

My computer has my-desktop and windows network, under windows network it has mshome, and in that theres my shared drive.

I don't think the xp computer sees anything.

Any tips would be great.

---

### Post by superprash2003 on 2008-04-10
have you tried pinging all the computers ??are they able to ping each other successfully?

---

### Post by Eiríkr on 2008-04-10
If you've got shares physically located on your Ubuntu machine that you're trying to access from Windows machines, then you need the Samba package, which it sounds like you've probably already got installed.  The no-network-browsing problem is one I've seen often before and is probably easy to fix.  We'll need to see your Samba configuration file to go further.  Open a terminal on your Ubuntu machine that's the Samba share server, type in the following, and then copy your conf file into a post here.  Please add [noparse]```

```[/noparse] tags around the conf file contents for improved legibility. 
```
less /etc/samba/smb.conf
```
The conf file is almost certainly bigger than one terminal screen, so be sure to scroll down within **less** to copy the whole thing.  

Cheers,

Eiríkr

---

### Post by gsiliceo on 2008-04-13
You can vote to change this in ubuntu using the brainstorm page, theres already an idea voting to make samba easier. Please vote here.
[Improve file/folder sharing experience (Samba)]("http://brainstorm.ubuntu.com/idea/403/")

---

