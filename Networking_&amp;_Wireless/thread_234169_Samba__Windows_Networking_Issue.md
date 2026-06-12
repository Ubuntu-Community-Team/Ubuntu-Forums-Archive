---
title: "Samba / Windows Networking Issue"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by cdg52 on 2006-08-11
I was working with samba and I realised that when I attempted to login from my Windows box's it prompts me to login. Is there any way to set up Samba so when i go to it with my Windows box's it just auto logins with the windows Guest acount? I attempted to add guest but that did not work, well it worked when I typed it in but it did not automaticly log into guest, maybe its because windows attemps Guest and not guest. Please help I am going to be using this box at an event that many people will be using windows and it will be distributing our software.

---

### Post by kaffelars on 2006-08-11
I think that if you mount the shared Linux as a drive in Windows, Windows asks you if you want to save your password.

I can't have my "server" running all the time, so I made a .bat-file mounting the Samba shares, and wrote the username and password in that file. Probably not very safe, but safe enough in my own house ;) And I only need to doubleclick a shortcut to mount the shares, no typing :)

---

