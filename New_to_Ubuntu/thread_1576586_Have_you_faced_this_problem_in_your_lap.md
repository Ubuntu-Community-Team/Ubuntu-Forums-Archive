---
title: "Have you faced this problem in your lap?"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by navaneethan on 2010-09-17
Hi luggies,

          My one of the friend got a latest DELL lap inspiron,core i3 processor which was pre installed with windows 7.He wanted to have Ubuntu one ,so he tried latest ubuntu just installed fine.When he starts the system none of the OS will be listed,It shows like 
 ""No module name found,aborted....
..........
......
pxe e61:media test failure,check cable
pxe-mof :existing pxe rom
.........
.......
insert boot media
..""


He says after installed only once it boots and entering into OS,after restarting it the problem starts..

can you give some suggestion about the problem?your predictions and advises!! Have you faced any problem like this?
The laptop is the new one recently got.


-- 
regards

[http://twitter.com/NavaTux](http://twitter.com/NavaTux)

---

### Post by ubunterooster on 2010-09-17
This appears to be a hardware issue. I recommend you have the harddrive taken out and all connections cleaned with compressed air.

---

### Post by papibe on 2010-09-17
PXE is a protocol used to boot from the network. It seems that in the process of installation (maybe by accident) the boot order got changed. 

Go to the BIOS and VERY carefully look for the boot order. Take PXE out of the boot order. A common boot order would be: 1 CD-ROM, 2 HD, etc.

If PXE is not in there, look for another a menu called "network booting" or similar. When you find where PXE is set, just disable it.

Regards.

---

