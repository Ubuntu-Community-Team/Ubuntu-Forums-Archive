---
title: "Desktop not working."
date: 2009-10-12
forum: New to Ubuntu
---

### Post by Tavin237 on 2009-10-12
Hello agian Ubuntu people, I have a bit of a problem. The desktop isn't loading and I can't open half of the programs via the Applications tab. The Tool bars at the top and bottom of the scree are working fine though. I says its starting the program then it just stops. As for the desktop it isn't loading even after restart. Anyone have any ideas?

---

### Post by 101011010010 on 2009-10-12
Hello there, I had a similar problem a while ago, fsck sorted it for me. Try the following command in a terminal.

sudo touch /forcefsck && sudo reboot

 If you've not used it before it will restart your pc and run the check. If it finds any problems it may ask you to restart again so it can sort them. I hope this helps.

---

### Post by nandemonai on 2009-10-12
If the fsck doesn't sort out the issue, I'd try running one of the programs that don't seem to load in terminal to see what's causing the issue.

---

