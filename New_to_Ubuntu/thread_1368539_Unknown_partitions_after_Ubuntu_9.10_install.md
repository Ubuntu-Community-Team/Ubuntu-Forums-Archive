---
title: "Unknown partitions after Ubuntu 9.10 install"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by oingk on 2009-12-30
hi
I've recently installed Ubuntu 9.10 together with my Windows XP (dualboot). When I switch my computer on it gets to GRUB menu (specifically it says "GNU GRUB version 1.97~beta4"). The menu contains:

1-Ubuntu Linux 2.6.31-16-generic

2-Ubuntu Linux 2.6.31-16-generic (recovery mode)

3-Ubuntu Linux 2.6.31-14-generic

4-Ubuntu Linux 2.6.31-16-generic (recovery mode)

5-Memory test (memtest86+)

6-Memory test (memtest86+, serial console 115200)

7-Microsoft Windows XP Professional (on /dev/sda1)

8-Windows NT/2000/XP (on /dev/sda3)


Can someone please explain what these mean?
[COLOR=Red]**1**[/COLOR] is my Ubuntu and I guess I can use **[COLOR=Red]2[/COLOR]** to recover it. [COLOR=Red]**3 **[/COLOR]and **[COLOR=Red]4[/COLOR]** I don't know what they are but when I try to enter into [COLOR=Red]**3**[/COLOR] it asks for my login password but does not accept my password that I set in Ubuntu. **[COLOR=Red]5[/COLOR]** and **[COLOR=Red]6[/COLOR]** I have no clue what they are (I know that they may even have been there before my Ubuntu installation).

[COLOR=Red]**7**[/COLOR] is my XP and I know **[COLOR=Red]8[/COLOR]** is the small partition where Rescue and Recovery (utility in Lenovo Thinkpad computers) reside.

What are the other things that I don't know about? Why are all these things that I don't know about there?

----------------------------------------
I also have another question: Is this dual boot setup that I have ok (stable)? The GRUB version saying "beta" makes me ask this but it's not that I know so many things about the subject.

Thanks.

---

### Post by tom.swartz07 on 2009-12-30
> **oingk said:**
> hi
I've recently installed Ubuntu 9.10 together with my Windows XP (dualboot). When I switch my computer on it gets to GRUB menu (specifically it says "GNU GRUB version 1.97~beta4"). The menu contains:

1-Ubuntu Linux 2.6.31-16-generic

2-Ubuntu Linux 2.6.31-16-generic (recovery mode)

3-Ubuntu Linux 2.6.31-14-generic

4-Ubuntu Linux 2.6.31-16-generic (recovery mode)

5-Memory test (memtest86+)

6-Memory test (memtest86+, serial console 115200)

7-Microsoft Windows XP Professional (on /dev/sda1)

8-Windows NT/2000/XP (on /dev/sda3)


Can someone please explain what these mean?
[COLOR=Red]**1**[/COLOR] is my Ubuntu and I guess I can use **[COLOR=Red]2[/COLOR]** to recover it. [COLOR=Red]**3 **[/COLOR]and **[COLOR=Red]4[/COLOR]** I don't know what they are but when I try to enter into [COLOR=Red]**3**[/COLOR] it asks for my login password but does not accept my password that I set in Ubuntu. **[COLOR=Red]5[/COLOR]** and **[COLOR=Red]6[/COLOR]** I have no clue what they are (I know that they may even have been there before my Ubuntu installation).

[COLOR=Red]**7**[/COLOR] is my XP and I know **[COLOR=Red]8[/COLOR]** is the small partition where Rescue and Recovery (utility in Lenovo Thinkpad computers) reside.

What are the other things that I don't know about? Why are all these things that I don't know about there?


Thanks.

Hi!

When you updated, it automatically installed the newest version of GRUB, the menu to list available OS's.

Numbers 3-4 are previous versions of your Kernel. A kernel is the code that Linux uses to communicate with your hardware. It is a good general rule of thumb to keep one previous version of your kernel just in case something goes wrong. 

HOWEVER, if you are really dead set about removing them, you could custom edit your Grub menu to hide the extra 2 entries, or you could remove them from Synaptic Package Manager.

5 and 6 are applications used to test your computers memory (RAM). These come in handy as troubleshooting tools, should something go wrong.

For the time being, if it doesnt bother you too much, just let them be, so that you have them if you ever need them.

Future updates of GRUB will actually support themes and graphical choosers. If you want you could look up info about GRUB here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


EDIT: Yes, the version of GRUB you have is very stable, as long as there is no major modifications made to it. The only reason that it is still listed as ~beta~ is because it is still being developed for themes and other neat fixes. The link I provided will answer that in greater detail.

---

### Post by oingk on 2009-12-30
tom, thanks very much.

in regard to3, do you know why it does not accept my Ubuntu login password?
Shouldn't I be able to access it if I ever need it?

thanks

---

### Post by wilee-nilee on 2009-12-30
> **oingk said:**
> tom, thanks very much.

in regard to3, do you know why it does not accept my Ubuntu login password?
Shouldn't I be able to access it if I ever need it?

thanks

You may have just not put the correct password in if the kernel above it works #1 #3 should as well, if you have done no password changes and have just updated.

---

### Post by oingk on 2009-12-30
thanks.
I have tried again and I managed to login.
Don't know what was wrong before.
Thanks guys for the help I will mark this as solved.

*EDIT: In regards to not accepting my password, I was accidentally clicking on "other user" and then typing it, that's why 					 				*

---

