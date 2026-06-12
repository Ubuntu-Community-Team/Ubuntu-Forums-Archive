---
title: "[SOLVED] Can't get my laptop to see XP boxes"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by kc5hwb on 2007-07-15
This is kinda confusing, I hope that I explain it right.

First off, I setup Samba by these instructions here...
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

I should say that I have 2 Ubuntu Fiesty desktop boxes on my network that I used this EXACT SAME procedure for and they are both working fine.  I have 2 other XP boxes on my network and all 4 boxes can see each other, trade files, share, full access, etc...

So I put Ubuntu on my laptop last week and I did this exact same procedure.  I cannot even see one of my XP boxes on the network at all.  I also have Virtualbox running XP on this laptop and I cannot access that XP share from this laptop either.  From the virtual XP on this laptop, I can see my Ubuntu desktop share fine, but I cannot see this Ubuntu laptop.  

I am running wireless on the laptop and I thought maybe this is why the desktop boxes can't see it, because I had this same problem while running XP  (XP desktops couldn't see the wireless laptop).  However, this doesn't explain (I don't think) why the Virtual XP session under this Ubuntu laptop (which is NAT'd) can't see the Ubuntu OS on the same machine.  Maybe I am wrong...

Anyway, it appears that Samba is simply hosed on this box, but I don't know how to fix it or exactly what is wrong.  I guess that I could try hooking up the hard-line and see if this helps anything, would wireless cause this kind of problem?

---

### Post by tact on 2007-07-15
Very good thread name.

Care to give some information that may help diagnose?  Please list all the IP addresses of all involved machines.  The feisty machines at home, the XP machines, and the XP in the VM as well as the laptop.

As mentioned in another thread...  if that laptop is on a different subnet to all the other machines that will explain why it cannot browse shares on any of the other machines, even the virtual machine.


Regards.

---

### Post by kc5hwb on 2007-07-17
I would appreciate it if you would let someone else answer.

---

