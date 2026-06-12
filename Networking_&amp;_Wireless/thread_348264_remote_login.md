---
title: "remote login"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by brad1150 on 2007-01-28
I don't really know where this post is supposed to go but here is my problem. I'm at a boarding school, I have a Ubuntu 6.06 machien at my house. I asked my mom to plug it in to internet and turn it on for me so I could use it while they were gone for 2 wks. She did all that, but didn't log in. I have vnc ports forwarded to that machine, is there anyway I can log into it and use it at my school while its not actually logged on?

---

### Post by highneko on 2007-01-28
If it's not working and you have openssh-server installed on the remote computer, then you could login and make it work.

---

### Post by brad1150 on 2007-01-28
i think i have the ssh installed, but what do you mean by "if its not working"? Can I vnc into it while its logged off an actualy user accoutn on the machine?

---

### Post by kosmic on 2007-01-28
If you have the SSH server installed and working it should be as simple as doing this :

ssh Myusername@MyServerIp

---

### Post by brad1150 on 2007-01-28
im on a windows pc right now. I need to connect to the linux machine from my windows machine, is that command what I use?

---

### Post by kosmic on 2007-01-28
If you are in a windows box you need an ssh client you can try Putty

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by brad1150 on 2007-01-28
It keeps saying Network error: Connection timed out. Is there any othe rpossible way I could get this thing to log in, besides actually being there?

---

### Post by kosmic on 2007-01-28
Are you really sure that you have SSH Server working in your linux box ?? It is listening in is standard port 22 ??

I'm afraid if you dont have the ssh server working the only way is to go phisicaly to the linux box and enter your login and password

---

