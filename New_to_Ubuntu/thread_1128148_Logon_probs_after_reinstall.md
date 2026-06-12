---
title: "Logon probs after reinstall"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by whiteman on 2009-04-17
I wanted to try something called kqemu. Then Idecided not to. Anyway everytime I booted I got a crazy disk check thing, then I got abnormal shutdown. Then blackness. So I decided to just reinstall. Using 8.1 disk, all went well. But when I tried to access my files from my Macbook, I had probs. I have two samba users, wth(me) and nobody. I can print. So I guess thast something. I have Cups figured out pretty good. But if ZI want to access files, I type in my userid which is "wth" and I type in my passwd whic is "zzzzzz". And it says incrrect. Incorrect? I tried changing password, nothing. Also when I try to add user in samba I notice that where the block says "smab username" it looks like two or three names typed over top of ea other. Am I not logged in as root? Am I not supposed to be? I have most things set up for "alow any user" Ican connect asguest. No prob. But if I need to really do anything, I get shot down. I also have this problem with my windows desktop(ethernet conn)It doesnt want to let me add a printer Same reason. Incorrect logon. One more thing..I used to have a root termnal program. How do I get it back..(type in root and term in snaptic?)Im on the mac right now. BTW I can do changes in Cups using the same logon info) If that helps.

---

### Post by element_G on 2009-04-17
not sure about your issue but here are some caveats:

1. you shouldn't ever need to log on as root, so don't

2. to become root in a terminal type 

```
sudo -i
```

and enter your password. When you are done being root type

```
exit
```

---

