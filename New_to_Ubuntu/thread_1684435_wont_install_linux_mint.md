---
title: "wont install linux mint"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by moose579 on 2011-02-09
hello all,,hope some 1 can help me ,ive downloaded the linux mint ,,i go to install from bootup disc that ive burned ,,and can confirm the disc is ok as i ran the disk before reboot

when reboot ,pressing f12 to boot from disc ,,which it does ,,asks to install and runs,,and the fills my screen with black background and loads of text on it ,,,gets so far and comes to a stop,,,left it 5 mins and it does nothing 

am i doing some thing wrong

im running windows 7 ,,,which i hate and wont to get rid of

---

### Post by P4man on 2011-02-09
what are the last lines you can see on screen?

---

### Post by moose579 on 2011-02-09
[   1.287252] [,ffffffffff8108aee8.] ? kernel_thread_helper+8x8/8x8/8x18/


all this sort of code come up on the screen

---

### Post by P4man on 2011-02-09
What PC is this?
You could try some of the ACPI workarounds explained in my signature. Its for ubuntu, but it will be fairly similar for Mint I think, havent tried mint in a while.

---

### Post by moose579 on 2011-02-09
ive looked in to my bios and there is no ACPI to change

some 1 said to install bitlock but this wont even install

dam hate the computer

its a toshiba satellite c650D

---

### Post by P4man on 2011-02-09
Your machine has a buggy ACPI BIOS. Click the link in my signature, the option you want to add  for your particular machine is this one:

```
acpi=ht
```

(note in my link I havent mentioned that one, but the rest still applies.

You can use ```
acpi=off 
``` temporarily to make it boot or install, but that will disable a lot of other stuff you really want or need on a laptop.

---

### Post by moose579 on 2011-02-09
im a total noob on this how do i use the code

---

### Post by P4man on 2011-02-09
Sigh. Click the link in my signature. IT has all the info you need for ubuntu. I dont know about mint, I think its pretty much identical.

---

### Post by Perfect Storm on 2011-02-09
Please use the mint forum, thanks.

Thread closed.

---

