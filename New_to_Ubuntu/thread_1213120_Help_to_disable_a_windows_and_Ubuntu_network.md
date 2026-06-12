---
title: "Help to disable a windows and Ubuntu network"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by Peterfc on 2009-07-14
Hi All

On my sons machine XP windows he has a virus. Can i disable my Ubuntu machine from the network? We both use the same router.

---

### Post by oldsoundguy on 2009-07-14
your Ubuntu machine won't "catch" the Windows virus. Nor should it have any effect on your ability to network it or use the router.

---

### Post by swoody on 2009-07-14
Peterfc: I don't think you have to worry very much at all, unless your son's machine had access to your Ubuntu machine, and the permission to read/write files. Otherwise, I don't think it could do any real damage. To read up some more about Security in Ubuntu, please take a gander at this excellent post:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by bodhi.zazen on 2009-07-14
I would take a more cautious approach, a compromised machine on your LAM should be managed. Best would be to disinfect the windows box.

Although your Linux box will not be "infected" by the virus, it can be affected by malware or the compromised windows box *could* be used to leverage access to Linux box (as you are no longer "protected" by your router).

I agree that all this is unlikely, but a compromised windows box is a potential risk and should not be ignored.

If it would make you feel safer, block the windows IP with your firewall.

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

Use iptables or gufw if you wish.

---

### Post by Peterfc on 2009-07-14
Hi Guys

I should have mentioned at the start. My son has a windows machine and i have a Ubuntu machine both on the same router. For a little while i have been having a problem with my machine running very slow. I tried cutting down what starts at start up etc. My last chance was my sons machine being at fault for my machine running slow. 

My machine is a Dell Dimention 2400 series 200 gb h/drive 1 gb ram sound/ graphics onboard.

---

