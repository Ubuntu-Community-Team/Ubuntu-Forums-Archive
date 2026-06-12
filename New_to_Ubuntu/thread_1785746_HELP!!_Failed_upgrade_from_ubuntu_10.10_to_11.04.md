---
title: "HELP!! Failed upgrade from ubuntu 10.10 to 11.04"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by chacky1234 on 2011-06-18
Hi guys, 
Hoping someone can help me. I have been using Linux for a little while but still hit brick walls and cannot figure out where to go next with the OS.

Basically I was in a happy place with my laptop (ubuntu 10.10 installed) and seen the option for upgrade so looked up its new features and decided to take that option.

When the upgrade downloaded the necessary files and then started to apply them it then threw up an error and restarted. Now i come to the login splash screen with no active keyboard and mouse available

I can access the hard drive only if i mount it using a live cd

What can i do to fix this?
thanks in advance :)......

---

### Post by Rex Bouwense on 2011-06-18
Did you back up your data?  If the answer is yes just re-install.  If the answer is no and you can get to the hard drive as your post indicates, back up your data and re-install.  Whatever you do back up your data first.  Upgrading used to be a crap shoot so that was the first thing that you had to do.  I thought it had become relatively flawless but apparently evil things still can happen.
Can you boot using the recovery kernal?

---

### Post by fooman on 2011-06-18
when you boot up (from the hard drive itself, not the live cd) and you see the grub menu....choose recovery mode.

when you get to the recovery mode options....try "fix broken packages" and see if that helps.  you will need an internet connection, of course.

---

### Post by chacky1234 on 2011-06-18
Thanks for fast reply. Well i used the 'backintime' application a little while ago, so can boot from live cd and transfer the backup across....

But if i simply reinstalled ubuntu 10.10 then used the 'backintime' application to restore my settings. Do i then try the upgrade again or is it just a bad idea?

in regards to the restore option at the menu, i think i may have remove the options for a faster boot and am unsure if i can access it now :(

---

### Post by chacky1234 on 2011-06-18
Just trying the 'repair broken packages' from the grub menu.....

---

### Post by Rex Bouwense on 2011-06-18
Upgrading is not inherently bad.  I always like to download the ISO and try it out on my hardware before I install it just to make sure that it will work with my hardware.  Some people don't bother.
I would try fooman's suggestion before anything else.

---

### Post by chacky1234 on 2011-06-18
ok fixing the packages did not work. Although it shown it fixed a load of them, it still boots to the same place without keyboard and mouse functionality

Wondering if 'backintime' can restore a snapshot from command line because i can use the command line from recovery...

---

### Post by conbot on 2011-06-18
Did you try to boot from a live Ubuntu USB/LiveCD? If not, try that. Then you can back up your files and install 10.10/11.04; whichever works.

---

### Post by chacky1234 on 2011-06-19
Ok, im thinking maybe try to restore using the live cd. If this fails then i will move the backup across while i reinstall ubuntu 11.04. what files from my backup (running in ubuntu 10.10) will actually be reusable in 11.04?

---

