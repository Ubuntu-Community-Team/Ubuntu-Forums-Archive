---
title: "EasyBCD equivalent for linux"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by abnordude on 2011-05-02
I just installed kubuntu in my computer.
When I switch on my computer, I see [maybe] 4-6 different menus.
Also, I see two ubuntu's [ie. one is the normal ubuntu the other is kubuntu(but with the name ubuntu)].
Well, I remembered a software in windows called EasyBCD, in which I could fix all these problems.
So, all I'm asking is tis' linux equivalent.

---

### Post by wilee-nilee on 2011-05-02
I think easybcd just gets you to that same menu through the ms bootloader. There a ways to customize the grub menu, and limit the kernels showing and remove the memory check stanzas.

> **abnordude said:**
> I just installed kubuntu in my computer.
When I switch on my computer, I see [maybe] 4-6 different menus 

Do you mean 4-6 different kernel sets in the grub menu.

I have heard that easybcd is customizable, but I have never used it, maybe it will do what you want I just don't know.;)

---

### Post by RoflHaxBbq on 2011-05-03
All EasyBCD did was reset the MBR and Bootloader back to the Windows (Vista??) ones.

For example, if you install Windows, then multibooted with Linux, GRUB would be your bootloader. But to remove Linux, you would boot to Windows, then run EasyBCD to reset it, then delete the Linux partitions.

There really is no Linux equivalent of EasyBCD.

What I assume you want to do is to reset your GRUB menu?

To do that you will need to edit GRUB, either by changing your configs accordingly, or reinstalling GRUB.

Let me google it for you.

[http://lmgtfy.com/?q=Modifying+GRUB+settings](http://lmgtfy.com/?q=Modifying+GRUB+settings)

---

### Post by abnordude on 2011-05-03
I think I found one, but I need 64 bit version.

Tis' called "qgrubeditor".

Could you help me to get that.
I searched getdeb, but didn't find it.

---

### Post by wilee-nilee on 2011-05-03
> **abnordude said:**
> I think I found one, but I need 64 bit version.

Tis' called "qgrubeditor".

Could you help me to get that.
I searched getdeb, but didn't find it.

There is this take a look and let us know if it is what your looking for.
[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

---

### Post by abnordude on 2011-05-12
Yes , Thats exacly what i'm looking for.
Thanks guys.

---

