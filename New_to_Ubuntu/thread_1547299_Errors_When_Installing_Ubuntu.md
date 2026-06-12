---
title: "Errors When Installing Ubuntu"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by mrbojangles123 on 2010-08-06
Hi, my son told me about this, so I'm trying it out; I'm new to this whole thing.  I spent some time searching around, but nothing seems to have worked, and almost all of the posts are about people who already have it installed or are trying to use the "try it out" version.

I downloaded the latest Ubuntu image (ubuntu-10.04-desktop-amd64) and burned the image to a DVD.  I do have a 64-bit computer.

When it boots to the CD, all I see is a black screen with a little man and keyboard at the bottom.  Eventually it goes to a black screen and says "initramfs: unable to find a medium containing a live filesystem".

I rebooted and when I push a key on the screen with the man and keyboard, it goes into a menu with install options.  When I select the Install Ubuntu (not try it out) option, it sits there for a little bit then goes to a loading screen, then after maybe 20 seconds it gives me the same error.

When I push a key on that loading screen, it says "glib-warning: getpwuid_r() **: failed due to unknown user.

I followed some advice in other posts: I checked the MD5 of the image, tried turning RAID on in my BIOS, and tried the different options in the install menu by pressing F6.

Like I said I'm fairly new to this whole thing, but I like the idea and philosophy of Linux so I really want to use it.

Thanks in advance for anyone who can help!

---

### Post by ajgreeny on 2010-08-06
When you get to that menu you talked about try hitting F6 (I think) which will show you a number of different boot options you can type, eg noapic, nolapic and several others, before hitting enter to actually boot into the live desktop, which I would advise, rather than going straight to install.

Try each of those options one by one if needed as it may be a simple boot option that is needed to get you up and running.

EDIT:

I see you have tried this already.  Note to self:  Read original post better before rushing to answer.
I presume none of those boot options worked.

---

### Post by mrbojangles123 on 2010-08-06
Right, none of them seemed to work.

---

