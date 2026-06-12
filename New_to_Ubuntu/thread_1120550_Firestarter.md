---
title: "Firestarter"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by old_dope on 2009-04-09
How do i get Firestarter to start automatically whenever i boot up the computer instead of me having to go looking for it and then starting it.
Thanks

---

### Post by frodon on 2009-04-09
You don't need so, you need to open firestarter just once to configure your firewall (understand iptables rules). Then your firewall is active on each boot, you don't need the firestarter GUI to be opened anymore, even worst it represent a security risk to keep it opened as it would give an attacker the possibility to change your firewall rules.

So the way to go is to open the GUI, configure your firewall, and never open the GUI again or just when you need to modify rules or check something.

More infos about security and ubunt there :
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by old_dope on 2009-04-09
So i can just leave Firestarter in the section under System and it will still function properly. Thanks Frodon

---

### Post by iBurger on 2009-04-09
See also this great reference;

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by superprash2003 on 2009-04-09
yes.. you dont need to open firestarter .. it is always on in the background. you just need to open it , incase you wish to make any changes..

---

