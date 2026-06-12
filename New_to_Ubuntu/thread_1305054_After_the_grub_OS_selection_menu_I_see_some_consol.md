---
title: "After the grub OS selection menu I see some console stuff instead of xsplash...."
date: 2009-10-29
forum: New to Ubuntu
---

### Post by legolas_w on 2009-10-29
Hi
I upgraded to ubuntu 9.10 from 9.04 and now right after I select which OS I want to load from the boot loader I see some console stuff instead of a good looking xsplash.

After I select the OS I want to boot it showes some lines about starting some services like SSH  and then it shows a page like the following:

[IMG]http://img2.tinypic.info/files/4c35tpd0cjsrdpkz6gh0.png[/IMG]

During shutdown process it does not show any graphical splash and instead when I press the shutdown button it turns into console mode and show some steps and then it goes off.

I checked in the synaptic and both xsplash and ubuntu-xsplash-artwork  are installed.


To explain more: I never see the following image during the boot and shutdown process and instead I see some console stuff...

[IMG]http://ubuntu-tutorials.com/wp-content/uploads/2009/10/ubuntu-beta-install-2.png[/IMG]

Is there any way to resolve this problem?

Thanks

---

### Post by john.nicholls on 2009-10-30
There were a number of changes to these areas in the last few days. Is your installation completely up to date?

---

### Post by legolas_w on 2009-10-30
hi,


yes, it is fully up to date.

Thanks

---

### Post by john.nicholls on 2009-10-31
The files I have are:
usplash 0.5.49
usplash-theme-ubuntu 0.27
xsplash 0.8.4-0ubuntu1
ubuntu-xsplash-artwork 0.8.4-0ubuntu1

In previous versions, the display dropped back to the console only when the loading process encountered something unusual. My only suggestion is to disable the splash temporarily, and see if you can see if something is triggering the change to console. In my case, the latest revisions have stopped console messages appearing entirely on bootup and close down.
John

---

### Post by legolas_w on 2009-11-03
I also have those package installed.
The glitch is really pissing me off :)) and I can not fix it nor I want to re-install ubuntu.

---

### Post by winotree on 2009-11-03
Do you think using **Startup Manager** from the repositories would help?  I had a bit of text initially but resolved it *and *[apparently] shortened the boot-time a bit.  Might be worth a look.  ;)

---

### Post by legolas_w on 2009-11-14
Hi

I tried startup manager but it did not affect the boot process and the  ansense of the boot screen.

Any update is most welcome.


Thanks.

---

