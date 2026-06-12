---
title: "laptop does not restart and shut down after upgrading to Karmic Koala"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by aaricia on 2009-11-13
Hello everybody,

I have been successfully using Ubuntu 9.04 since August in my laptop. When I installed Ubuntu in January (the previous version), the installation CD automatically created a partition so that I can choose if I want to run Windows Vista or Ubuntu.
I have the Desktop edition as I use it as a OS.

I upgraded to Ubuntu 9.10 yesterday and my problem is that I cannot restart or shut down the laptop. When the Karmic Koala shuts downs there is an ending message say "Stopping MySQL, stopping etc, stopping swap" and then it stucks there.

I read about swap but, as I am a complete beginner in Ubuntu, I don´t want to do anything that may damage my laptop. 
Is it because I don´t have enough space? Should I decrease the value of Swap?

Sorry if my questions are very stupid, I am just learning about Ubuntu.

Thank you very much for your help.

---

### Post by NickJones on 2009-11-13
Swap is the equivalent of Virtual RAM. It's useful, and puts less stress on your real RAM.

---

### Post by aaricia on 2009-11-16
> **NickJones said:**
> Swap is the equivalent of Virtual RAM. It's useful, and puts less stress on your real RAM.

Hello Nick,

Thanks fory your clarification. The exact error message when the laptop gets stuck is "Deactivating swap".

I decreased swap to 10 in the corresponding configuration file, but the problem still persists.

Regards

---

### Post by Weazel on 2009-12-02
I have the same problem..

I think its since I've installed Bootup-Manager.

a few things changed:

1. I no longer see timeout during grub boot menu, so unless I choose an OS from my dual boot, It'll idle grub forever.

2. Every time I open the laptop I have to do "sudo /etc/init.d/vboxdrv start" if I want to open my virtual box

3. I need to Open Samba and go to Server Settings>Security and Re-choose "Share" from Authentication Mode.

4. and of course, as said before, When I want to shutdown, It'll get stuck in "Deactivating Swap" until I manually shutdown from the power button.


I'm kinda noob in these things, but I would really love some help.


thanks in advanced.

Weazel.

---

