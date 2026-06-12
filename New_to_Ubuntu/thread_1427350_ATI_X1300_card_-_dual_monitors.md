---
title: "ATI X1300 card - dual monitors"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by adgators89 on 2010-03-11
I am having problems setting up dual monitors with this card.  It only says mirrored screens when i try to set my monitors up for a dual system.  It works perfectly in Windows, but not in Ubuntu.  I tried the ATI drivers but it says they are not supported.  how can I remedy this situation?

---

### Post by Mark Phelps on 2010-03-12
In Ubuntu 9.10, you're stuck with the problem that there are no ATI restricted drivers that will work with your card.

If the open source drivers (installed by default) don't give you the option of multiple displays, there's probably nothing you can do.

---

### Post by adgators89 on 2010-03-12
ok, thank you for the response.  I really messed up my xorg settings trying to do multiple monitors and multi-seating so now when ubuntu loads it goes into the ttyl screen login.  so now I am at a total loss (I know...newbie :):p

---

### Post by Mark Phelps on 2010-03-13
Try using dpkg-reconfigure from a console -- as described in the link below:

[http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure]("http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure")

---

