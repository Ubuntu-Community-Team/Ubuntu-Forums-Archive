---
title: "Backup"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by AlanR8 on 2007-05-30
Evening all, trust you're well.....

Kubuntu on my laptop, son's desktop and a machine I want to use as a file server. Also have XP Pro on the wife's machine.

All the machines talk to each other, get on well together and don't fight. I can even print from my K machines to the printer attached to the Doze machine. In other words all is well on my home network.

However, If I create a folder from my laptop on the "server" and then want to delete it, I can only do it from the laptop. If I try from the "server" I get "Access denied to........."

This is a permissions thing I know but anyone know of a quick fix?

If I try to use the backup program "Keep" it fails 'cos it says it can't create the folder on the remote machine.

Confused.......

---

### Post by blazercist on 2007-05-30
you could use "laptop"" and do  "sudo chmod 777 folder" that will give all users read/write permissions on that folder and anyone could delete it or rename it or whatnot, I hope i've answered your question.

---

### Post by AlanR8 on 2007-05-30
[HTML]sudo chmod 777 folder[/HTML]

Is what I was looking for. Thank you.

Saw a response here the other day suggesting it was usual to wait 24 hours for a response....yours came through in 4 minutes!

Don't you just LOVE the Web huh?

---

### Post by blazercist on 2007-05-30
not only am i a loser but im at work and im bored so i forum crawl, I learn stuff and help others so I put back whatever i get out.

---

### Post by AlanR8 on 2007-05-30
Didn't do the chmond thing, I used Webmin. 

I know some will say you should use the CL but if I can, I prefer to use something graphical. It's a bit like teaching kids these days their times tables, their argument "why? I've got a calculator"!

If Linux is going to be a real desktop contender then graphical has to be the way forwards. 

My opinion as an EX Doze user and loving it!

---

