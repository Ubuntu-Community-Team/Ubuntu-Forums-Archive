---
title: "Is it possibly to show grub with only one OS installed?"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by e.jejcic on 2011-02-02
Good afternoon to everybody:
I was wondering if it is posibly to show the grub menu at start-up so I can choose other kernnel. I have only one OS installed ( Ubuntu 10.04 ). Thanks to everybody and regards from Eduardo.

---

### Post by YesWeCan on 2011-02-02
If there is another OS and Grub knows about it, it will show the Grub menu.
To make it always show the menu you need to change settings in '/etc/default/grub' and then run 'sudo update-grub'. See instructions here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by hansolo4949 on 2011-02-02
A temporary workaround, for example if you wanted to see the GRUB screen once, is press the shift key while your computer is booting. Now, I haven't been able to test this, since my computer dual-boots, but it should work. 


Hope that helps!

---

### Post by ajgreeny on 2011-02-02
> **hansolo4949 said:**
> A temporary workaround, for example if you wanted to see the GRUB screen once, is press the shift key while your computer is booting. Now, I haven't been able to test this, since my computer dual-boots, but it should work. 


Hope that helps!
Yes, I can confirm that works.  I have a multiboot desktop which always shows the grub menu, though only for 2 secs, but I also have a laptop with just 10.10, which normally does not show grub.  Hold shift at boot time and up it pops, no problem.

---

### Post by Garthhh on 2011-02-02
> **e.jejcic said:**
> Good afternoon to everybody:
I was wondering if it is posibly to show the grub menu at start-up so I can choose other kernnel. I have only one OS installed ( Ubuntu 10.04 ). Thanks to everybody and regards from Eduardo.

Install StartUp manager from software manager, you will then be able to decide how long the boot menu will appear

---

### Post by e.jejcic on 2011-02-02
Good afternoon:
Well, I installed startup manager and from there I can select the kernel.
YesWeCan and handsolo your suggestions didn't work for me, that's why I tried startup manager.So I am going to put "solved". I really apprerciate your fast response and you made me read the link.Very grateful. Thankyou very much. Regards from the lonnely pampas. Bye from Eduardo. (sorry for my english).

---

