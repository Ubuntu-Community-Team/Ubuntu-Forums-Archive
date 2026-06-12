---
title: "UnBlacklistsing ath5k"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Jim Rimedio on 2009-12-28
I have a Lenovo Z61m running 9.10.  When I ran 
grep -r "ath5k" /etc/modprobe.d/  I got the following:

jim@jim-laptop:~$ grep -r "ath5k" /etc/modprobe.d/
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath5k
jim@jim-laptop:~$ 

I do not know where to go to unblacklist.  I know I have to put a "#" in front of the line, but I do not know how to do that.

Thank you,

---

### Post by bkratz on 2009-12-28
> **Jim Rimedio said:**
> I have a Lenovo Z61m running 9.10.  When I ran 
grep -r "ath5k" /etc/modprobe.d/  I got the following:

jim@jim-laptop:~$ grep -r "ath5k" /etc/modprobe.d/
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath5k
jim@jim-laptop:~$ 

I do not know where to go to unblacklist.  I know I have to put a "#" in front of the line, but I do not know how to do that.

Thank you,

It should be to modify yes a # is a comment

sudo gedit /etc/modprobe.d/blacklist.conf

---

