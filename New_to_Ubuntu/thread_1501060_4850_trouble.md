---
title: "4850 trouble"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by drodaan on 2010-06-03
i've searched all over for help with 4850 drivers, and have even found people with the same problem as i, but no solution. i've installed the ATI/AMD proprietary FGLRX driver, but it says under System>Admin>hardware drivers "this driver is activated but not currently in use" 

ATI Catalyst Control Center opens fine, but i have no 3d support at all. even the built in chess game won't play in 3d. my windows behave as if i'm in Windows XP, with no video driver installed. huge lag in moving boxes around etc...

what have i done wrong here

---

### Post by drodaan on 2010-06-03
bump

---

### Post by drodaan on 2010-06-03
am i to believe no one else uses a radeon 4850 ?

---

### Post by I8NY on 2010-06-03
well it worked for me(4850) in 9.10 then upgrade to 10.04.  you could try it again or get the driver from ati and install it that way.

---

### Post by Shazzam6999 on 2010-06-03
I have a 4850 on my desktop but I've never had any issues with it. It might be your xorg.conf file. Entering fglrxinfo into a terminal will tell you if it's working or not. Anyways, I'm not really sure how to fix it but heres the official documentation which may or may not help, there's a troubleshooting section towards the bottom [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I hope that helps at least a little.

---

### Post by drodaan on 2010-06-04
i re-did the driver from ati.. it installed successfully and shows up in hardware drivers. i still have no 3d support. no opengl etc.

---

### Post by I8NY on 2010-06-04
you might not have opengl installed, unlikely and i don't know how that is possible.  it could also be a bad install.  but what are u using for a 3d test?

---

### Post by mike2507 on 2010-06-04
i have the same card ( eah48501gb ) and after ubuntu promted me to instal ati driver it worked like it should 
don't know how to solve youre problem since i am an absolute ubuntu newb ,
just to let you know their is a solution out there and it can work

---

### Post by robert shaffer on 2010-08-06
Hello,I also have a 4850 the way i got mine working was i used sgfxi script you can get from smxi website.then ya need to logout and hit cntrl alt f1 login and type sudo service kdm or gdm stop.once ya get x stoped run the script everything goes ok quit and run "aticonfig --initial" then "aticonfig" and reboot your box.that got it working for me.its not perfect but composite works with opengl.Do all that with root privliges.Hope this helps yas.
ps that installs the 10-7 drivers.

By the way the script will install whats needed

---

### Post by Lance7_q on 2010-08-06
Hi.
What trouble is it?
is it can affect to the install site or what ever?

Regards!


[gw2 gold](http://gamegoldreview.com/guild-wars-2-gold)

---

