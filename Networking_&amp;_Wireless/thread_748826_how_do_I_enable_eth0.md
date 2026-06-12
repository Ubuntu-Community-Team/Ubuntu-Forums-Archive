---
title: "how do I enable eth0?"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by engrpiman on 2008-04-07
Hi 

my wireless does not work and when I run lshw -C network eth0 shows up as disabled 

*-network DISABLED 

how do I enable it? 


also my notebook has a switch to enable wireless: if I boot with it on I have wireless but If it turn if off I loose wireless and never get it back (even if the switch is enabled again)

Thank you

:popcorn:

---

### Post by JawsThemeSwimming428 on 2008-04-07
You can run the following command

            ifconfig eth0 up

---

### Post by engrpiman on 2008-04-07
its now enabled but no internet is not be had.  wireless is enabled

is there a way for me to use the switch on my notebook to enable / disable wireless (it worked in 7.10)

---

### Post by superprash2003 on 2008-04-08
please post results of ifconfig

---

### Post by engrpiman on 2008-04-08
Thanks 

after some searching I found the solution to my problem and my friend got internet working.  

Thanks for your help 

\\:D/

---

