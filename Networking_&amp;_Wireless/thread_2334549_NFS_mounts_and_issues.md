---
title: "NFS mounts and issues"
date: 2016-08-20
forum: Networking &amp; Wireless
---

### Post by veranyon on 2016-08-20
[COLOR=#272A34][FONT=Open Sans]Hi, all.
When I mount an NFS share from my Linux machine in OS X, everything works great, except for one thing: Special characters (like the nordic characters ?, ?, ? for example) are not displayed correctly. File and folder names containing such characters are just displayed with a name of "?" in the Finder. When I mount the same share, but over Samba, there are no problems at all, but I would rather use NFS because of the gained speed.[/FONT][/COLOR]
[COLOR=#272A34][FONT=Open Sans]Would be great if someone could help me out, I don't even know where the problem lies - with nfsd on the Linux machine, or with OS X*.*[/FONT][/COLOR]
[COLOR=#272A34][FONT=Open Sans]Oh, and also, is it possible to prevent OS X from writing .DS_Store files to the NFS share, similar to the "veto files" setting in Samba?[/FONT][/COLOR]

---

### Post by steeldriver on 2016-08-20
Does anything here help?

[osx - Won't read Unicode characters over NFS mount?](http://superuser.com/questions/250926/wont-read-unicode-characters-over-nfs-mount)

---

### Post by veranyon on 2016-08-20
2 [steeldriver]("https://ubuntuforums.org/member.php?u=1627500")
Thank you.
And for all, can I  a veto oplock code to nfs settings? Or do it only for samba?
Just, if be search it in Google that one automatically show results about samba.
For example: [veto oplock nfs]("https://www.google.ru/search?num=100&newwindow=1&site=&source=hp&q=veto+oplock+nfs&oq=veto+oplock+nfs&gs_l=hp.3...1575.6277.0.6467.16.16.0.0.0.0.88.842.16.16.0....0...1c.1.64.hp..0.12.602.0..0j0i10i1k1j0i131k1j0i22i30k1j0i22i10i30k1.cJSCgdh6JRQ").

---

