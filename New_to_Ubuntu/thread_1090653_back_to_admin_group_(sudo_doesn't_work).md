---
title: "back to admin group? (sudo doesn't work)"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by minsf on 2009-03-08
i'm the only user on my system.
i accidently removed myself from all my groups, which means i cannot do "sudo" anymore. 
how to get my sudo previleges back?

long story:
in a recent thread of mine about a non-working floppy drive ([http://ubuntuforums.org/showthread.php?t=1089745](http://ubuntuforums.org/showthread.php?t=1089745)), someone suggested to run ```
sudo usermod -G floppy <your user name>
```
but now that i run "groups" i see that my only group is "floppy" (and "minsf" of course) and all the previous groups dissappeared. i guess i can recover the other groups if i can get "sudo" to work.

thanks a lot for your help!

---

### Post by ajgreeny on 2009-03-08
You could try doing it that way using the recovery mode (second in grub menu) but you will probably need to edit the sudoers file with visudo.

Here are three site which may help you put things right:-
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good luck; I'm sure one of them will have the answer.

---

### Post by minsf on 2009-03-08
thanks. i've already solved it, but thanks a lot for the links.
(my solution in short: reboot into recovery mode, drop to root shell, check /var/log/auth.log to see what groups one has been removed from, and then add those groups back with the usermod command. then reboot normally)

---

