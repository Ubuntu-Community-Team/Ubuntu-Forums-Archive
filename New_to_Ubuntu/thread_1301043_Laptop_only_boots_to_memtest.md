---
title: "Laptop only boots to memtest?"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by DaveGiant on 2009-10-25
Hello, my laptop is stuck booting to memtest.

When I boot it goes into memtest, passes the test and tells me to press escape.. I press escape. It goes back into memtest.

When I look at the boot order..

root ()/ubuntu/disks 

is at the top.

When I press b to boot into this nothing happens. If I try to delete the memtest boot record thing nothing happens.

Any ideas?

---

### Post by muteXe on 2009-10-25
Can you boot from a live cd, then post your /boot/grub/menu.lst please?

---

### Post by DaveGiant on 2009-10-25
I don't have a live CD. I have no recordable disks at the moment. I installed with the wubi installer.

Anyway I can do this from Windows?

---

### Post by DaveGiant on 2009-10-25
Erm, if I boot from live cd then the boot list is that of the default installation. Not my installed version.

---

### Post by DaveGiant on 2009-10-25
Is there anyway to get this installation going again or is everything buggered?

I see no option to boot into a console, I see no repair installation tool on the cd. 

Please advise.

Thanks

---

### Post by DaveGiant on 2009-10-26
Does anyone have any tips / advice for this matter?

---

### Post by fedexfrt357 on 2009-10-28
I may be way off here... but if you go into Startup-Manager, you can set the default there... I had a similar experience after booting back into Vista... When looking at Startup-Manager, the memtest was set to default, after changing, it was all good... Sorry if I am not understanding...

---

