---
title: "Screen goes black and keyboard not worked after login"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by SACHINVD on 2008-12-31
After installing intrepid when i restarted computer upto login screen it is ok
but after entering user name and Password screen went black .

i waited for 10-15 minutes still screen was black and when i check keyboard it is also not working(after pressing num lock and Caps lock led not glow)

same problem i faced with live CD after choosing option "try ubuntu without installing"
so i directly installed with "install ubuntu" 

I have inbuild graphics card of 64MB of intel

What need to do to solve this problem ?

---

### Post by gridd on 2008-12-31
> **SACHINVD said:**
> After installing intrepid when i restarted computer upto login screen it is ok
but after entering user name and Password screen went black .

i waited for 10-15 minutes still screen was black and when i check keyboard it is also not working(after pressing num lock and Caps lock led not glow)

same problem i faced with live CD after choosing option "try ubuntu without installing"
so i directly installed with "install ubuntu" 

I have inbuild graphics card of 64MB of intel

What need to do to solve this problem ?

I have the same problem Intel board exept I'me not shure the keyboard dies. I log in with password then get a beige screen with cursor then a black screen with cursor then nothing for half an hour this is with 8.10 by the way 8.04 works fine.md5 on both were checkd.

---

### Post by SACHINVD on 2009-01-17
Problem solved 

enter command "sudo apt-get remove compiz compiz-core"

and reboot

---

### Post by caro on 2009-01-17
Thanks!  Save me a lot of time.  ;-)  

I just wiped an old Win2K desktop and installed Ubuntu and had the same problem.  Running Live CD was no problem, but I had to install in safe mode.  Now it boots up with the splash screen and then goes black.

---

